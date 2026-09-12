---
domain: software-engineering
concept: REST API design — resource modeling, versioning, errors, pagination
source: research — synthesized from 2026 API design references (RFC 9457 Problem Details, RFC 8594/9745 deprecation headers, Microsoft/Google/Stripe/GitHub API guidance), 2026
tags: [api-design, rest, http, versioning, error-handling, pagination]
---

# REST API design: resources, versioning, errors, pagination

A REST API is a contract, not a reflection of a database schema — the
single idea underneath every rule below. The moment a client depends on
how your database happens to be structured today, every future schema
change becomes a breaking change for that client, which is exactly the
coupling [software-architecture-principles.md](software-architecture-principles.md) warns against, just
manifesting at the HTTP layer instead of inside a codebase.

## When to use

- Designing a new API surface for a service, before any endpoint code is
  written — the shape of the contract should exist before the
  implementation, not emerge from it.
- A client integration keeps breaking when the backend changes something
  that "shouldn't have mattered" — usually a sign the API leaked internal
  structure instead of exposing a stable resource model.
- Introducing a breaking change to an existing API and needing a rollout
  path that doesn't break every current consumer simultaneously.
- An API returns errors as ad hoc strings or generic `{"error": "..."}"`
  objects, and clients have started parsing message text to decide what
  to do — a sign the error contract itself needs designing.

## How it works

**Resource modeling** — URIs name nouns in the domain, not verbs or
database tables: `GET /orders`, `POST /orders` (plural collection),
`GET /orders/{id}` (singular item). Keep nesting shallow — roughly
collection/item/collection at most (`/customers/1/orders`) — deeper
nesting (`/customers/1/orders/99/products/5/reviews`) couples the URL
structure to the database's foreign-key structure and becomes fragile the
moment that structure changes. Custom actions that don't fit CRUD use a
colon separator (`POST /videos:process`), not a verb folded into the path
(`/processVideo`) — verbs in a path duplicate what the HTTP method is
already for.

**HTTP method semantics** — `GET`, `PUT`, and `DELETE` are idempotent
(repeating the same request produces the same end state); `POST` and
`PATCH` are not guaranteed to be. This isn't a style preference — clients
and infrastructure (retries, load balancers) rely on idempotency being
true for the methods that promise it; violating it silently (a `PUT` that
isn't actually safe to repeat) breaks retry logic that has no way to know
it's unsafe.

**Errors — RFC 9457 Problem Details** — a standardized JSON error shape
(`application/problem+json`) with five base fields: `type` (a URI
identifying the error category), `title` (human-readable summary),
`status` (the HTTP status code, repeated in the body for convenience),
`detail` (specifics of this particular occurrence), `instance` (an
identifier for this occurrence, useful for support/logging correlation).
Never return `200 OK` for a failure — it forces every client to parse the
response body just to learn what a status code already exists to signal
instantly.

**Versioning** — three real strategies, differing in isolation strength:
URL-path versioning (`/v1/` → `/v2/`, hard isolation, but every client
must manually migrate), header versioning (soft isolation, same base URL,
lighter client burden), and date-based versioning (Stripe's model — a
version pinned per API key, with a transformation layer converting
responses for older pinned versions so business logic never needs
version-conditional branches). The principle underneath all three:
versioning exists to isolate breaking changes from existing consumers,
not to produce a version number — pick the mechanism that achieves the
isolation your consumer base actually needs.

**Pagination** — offset-based (`?page=2&limit=20`) is fine for small,
bounded lists (admin tables, settings); it degrades at scale because it
scans and discards rows to reach an offset, and results can shift under
concurrent writes. Cursor-based pagination (a stable key marking "resume
after here") avoids the scan cost and stays correct under concurrent
inserts/deletes, at the cost of losing random page-jumping. At real
scale, expose pagination via a `Link` header (GitHub's approach) rather
than requiring clients to hand-construct the next page's query.

## Example

A `POST /orders` endpoint that fails validation returns:

```json
{
  "type": "https://api.example.com/errors/validation-failed",
  "title": "Validation failed",
  "status": 422,
  "detail": "Field 'quantity' must be a positive integer",
  "instance": "/orders/req-8f2c1a"
}
```

with HTTP status `422`, not `200` with an error buried in the body — a
client branches on `response.status` first (fast, no parsing needed), and
only reads `detail` when it needs to show the specific problem to a user
or log it for support. When the order-creation contract needs a breaking
change (say, `quantity` becomes required where it was previously
optional), that change ships as `/v2/orders`, with `/v1/orders` continuing
to serve existing integrations until a published deprecation date passes.

## Applying it for a client

Push for an API-first process — write the contract (even informally,
before a formal OpenAPI spec) before backend implementation starts, and
review it with whoever's building the consuming frontend/mobile
client before either side writes code. This catches resource-modeling
mistakes (over-nested URLs, verbs-as-paths) while they're a five-minute
edit instead of a shipped-and-now-breaking-change. When a client's
existing API already leaks database structure (common in a system that
grew organically from `/api/users_table` style endpoints), don't
recommend a big-bang rewrite — introduce a new versioned surface that
wraps the old structure behind a cleaner resource model, and let old
consumers migrate on their own timeline against the old endpoints, which
keep working unchanged until deprecation.

## Watch-outs

- A "breaking change" isn't just removing a field — adding a new
  *required* field to a request, or changing a field's type, silently
  breaks existing clients too. Anything that changes what a client must
  send, or what shape a client must expect back, needs the same
  versioning discipline as an obviously bigger change.
- Silent breaking changes (bumping behavior without a `Deprecation`/
  `Sunset` header or a migration window) is the single most common way
  API changes damage client trust — always signal a deprecation with both
  a machine-readable header and a human-readable notice period (6–12
  months is common practice), not one or the other.
- Rate limiting without a `Retry-After` header forces clients to guess
  when to retry, and without jitter in the client's backoff, many clients
  retrying on the same schedule re-synchronize and re-trigger the same
  limit — both need to be part of the contract, not left to client
  authors to figure out.
- HATEOAS (embedding discoverable links in responses) is easy to over-
  apply — it earns its complexity for genuinely stateful workflow APIs,
  not for simple CRUD, where it adds payload size and client complexity
  for navigation the client already knows how to do.

## Related

- [software-architecture-principles.md](software-architecture-principles.md) — an API's resource model *is*
  the stable contract that principle describes; this note is that
  principle's concrete mechanism at the HTTP layer.
- [ai-agent-architecture-patterns.md](ai-agent-architecture-patterns.md) — tool-use/function-calling in an
  agent architecture is structurally the same problem as API design: a
  contract (the tool's schema) that must stay stable while the
  implementation behind it changes freely.
