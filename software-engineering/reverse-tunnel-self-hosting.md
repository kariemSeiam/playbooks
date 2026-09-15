---
domain: software-engineering
concept: Reverse-Tunnel Self-Hosting Behind CGNAT
source: "Pixy Gateway build (kariemSeiam/pixy) — live production debugging session, Sept 2026"
tags: [networking, self-hosting, reverse-tunnel, fail2ban, cgnat, reliability]
---

# Reverse-tunnel self-hosting behind CGNAT

## Definition

A pattern for exposing a device that has no static IP and can't accept
inbound connections (a phone, a home server behind ISP-grade NAT, any
box on a residential/mobile network) as a public HTTPS service: the
device dials **out** to a cheap VPS with a real IP and holds open a
reverse SSH tunnel (`ssh -R remote_port:localhost:local_port`); the
VPS's own web server (nginx/LiteSpeed) reverse-proxies a real domain to
that tunnel's forwarded port. The device never needs to be reachable —
it only ever needs outbound internet, which is why this survives moving
between WiFi and mobile data with zero reconfiguration.

## When to use

Any time the thing you want to expose sits behind CGNAT, a mobile
carrier, or a home router you don't control the port-forwarding on — and
a mesh VPN (Tailscale, ZeroTier) isn't acceptable as the sole path,
because you need it reachable by tools/scripts/webhooks that were never
enrolled in that mesh (a public domain with a normal bearer token beats
requiring every caller to install a VPN client).

## How it works

1. **Device side**: a supervised loop (`while true; do ssh -R
   127.0.0.1:PORT:127.0.0.1:PORT user@vps -p 22; sleep N; done`) that
   restarts the tunnel the instant it drops, for any reason.
2. **VPS side**: a restricted SSH user whose key is locked to
   `permitopen="127.0.0.1:PORT"` and a forced restricted shell — that
   user can *only* open the one forwarded port, nothing else, even with
   the private key in hand.
3. **Public entry**: the VPS's web server (already terminating TLS for
   a real domain) reverse-proxies to `127.0.0.1:PORT` — from the
   internet's perspective it's indistinguishable from any other
   HTTPS site.
4. **Boot persistence on the device**: if the device is Android/rooted,
   a Magisk `service.d` script runs the tunnel loop as a root daemon
   outside the app lifecycle — immune to Doze and the app-level OOM
   killer that would otherwise kill a plain background app within
   minutes of the screen turning off.

## Example

A rooted Android phone (Pixel 3a XL, `bonito`) runs a Python HTTP API on
`127.0.0.1:8765`. It dials out to a $5/mo VPS as a locked-down
`pixytunnel` user, forwarding that port. The VPS's LiteSpeed vhost for
`pixy.example.com` proxies to `127.0.0.1:8765`. Any HTTP client anywhere
that has the bearer token can now hit `https://pixy.example.com/health`
— the phone was never given a static IP, a port-forward, or DDNS.

## Applying it for a client

If a client wants "always-on API from my [phone/NAS/home server] without
paying for a static IP or exposing my home router," this is the
$5/month answer instead of a $30/month "IoT cloud" SaaS. The one thing
to set expectations on up front: it's exactly as reliable as (a) the
device's own uptime and (b) the VPS's SSH port staying reachable — see
the watch-out below, because #2 is the non-obvious failure mode that
actually bites in production.

## Watch-outs

- **fail2ban collateral bans on shared/CGNAT IPs.** If the device's
  outbound IP is shared with other traffic (mobile carriers, some ISPs),
  unrelated bot attacks hammering the VPS's SSH port from that same
  shared IP get the *whole IP* banned — taking the legitimate tunnel
  down as collateral damage, even though the tunnel's own auth was
  never failing. Confirm this by checking whether the banned IP's
  failed-auth log lines are for your tunnel's own username or someone
  else's (usually `root`) before assuming your setup is broken.
  - Fix: widen `fail2ban`'s `bantime`/`maxretry`/`findtime` to something
    short and forgiving (e.g. `maxretry=20, findtime=120, bantime=60`)
    rather than the aggressive defaults meant for a single-tenant IP,
    and/or run a small watcher that unbans the IP immediately on the
    tunnel's own successful auth. Neither is a full fix — see next
    point.
  - **This is still fundamentally racy.** If a ban lands before the
    tunnel gets even one successful auth in (e.g. right after the
    device switches networks), no reactive watcher can save that
    attempt — only a smarter retry loop (backoff + a pre-connect
    `fail2ban-client unban` call) actually closes the gap, and that's
    real remaining work, not a solved problem.
- **`jail.local` silently overrides `jail.d/*.conf`.** fail2ban's load
  order is `jail.conf` → `jail.d/*.conf` → `jail.local`, so a scoped
  override dropped into `jail.d/` to fix one jail does nothing if a
  pre-existing `jail.local` re-asserts the old values afterward. Verify
  with `fail2ban-client get sshd <param>` after a **restart** (not just
  reload) — don't trust that a config file you dropped in is the one
  actually in effect.
- **Don't assume GNU coreutils semantics on non-Linux-desktop devices.**
  Android's shell is Toybox (not busybox, not GNU) — `find -exec {} +`
  works, `find | xargs -I{}` does not (Toybox's `xargs` has no `-I` at
  all), and `find -printf` isn't supported either. Test the actual
  command on the actual device shell before trusting it in an automated
  pipeline; don't port assumptions from a normal Linux server. This
  generalizes to any embedded/mobile shell — verify, don't assume.
- **A stale tunnel session can wedge the forwarded port on the VPS
  side.** After a tunnel restart, leftover `CLOSE_WAIT` sockets held by
  the *old* sshd child process can block the new tunnel from binding
  the same forwarded port (`Error: remote port forwarding failed`).
  Kill the specific stale `sshd: <user>` PIDs (found via
  `ps -ef | grep "sshd: <user>"`), not just the tunnel process on the
  device side, before assuming the fix didn't take.
- **A restricted-shell "not available" response on a disallowed forward
  target looks like a broken setup but usually isn't.** If
  `permitopen` is scoped to one port and a test hits a different one,
  the resulting rejection message can read like a generic account
  error. Re-test against the actually-whitelisted port before
  concluding the restriction itself is broken.

## Related

- [rest-api-design.md](rest-api-design.md) — the API surface sitting
  behind the tunnel should still follow normal REST/HTTP conventions;
  the tunnel is a transport concern, not an excuse to skip API design.
- `../operations/incident-management-itil-sre.md` — the
  root-cause-before-fix discipline used here (confirming the banned IP's
  failed logins belonged to someone else's traffic, not assuming the
  tunnel config was wrong) is the same SRE instinct that note covers.
