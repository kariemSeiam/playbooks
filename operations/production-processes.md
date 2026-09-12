---
domain: operations
concept: Production Processes
source: sources/operations/civiconnectors-resources-operations.pdf.card.md
tags: [production, operations-model, job-production, batch-production, flow-production, services]
---

# Production Processes

Production is the set of processes that transform inputs — raw materials, unfinished goods, information, ideas — into the outputs a business sells, whether that output is a physical good or a service. The classification that matters operationally isn't "what do you make" but "what shape does your production take": one-off and custom, repeated in batches, or continuous — because that shape decides how you cost, staff, and schedule the business.

## When to use

- Scoping a new venture: before writing a business plan, pin down which production type the business actually is — it changes almost every other operational decision (staffing model, equipment, inventory policy, pricing logic).
- Diagnosing an operations problem: if a client's costs, lead times, or quality are inconsistent, check whether they're running one production type but pricing/staffing/scheduling as if they were another (e.g. quoting flow-production prices for job-production work).
- Comparing a client's operations to sector norms: manufacturers, retailers, and restaurants/food service each carry a structurally different mix of activities, and a client benchmarking themselves against the wrong reference sector will draw the wrong conclusions.

## How it works

### Goods vs. services

Production classically applies to physical goods (manufacturing something from raw components, increasing the quantity of a commodity to sell it). Services are the intangible counterpart, and they behave differently along four dimensions worth knowing by name even if a client's deck never uses them:

- **Intangibility** — a service can't be touched, transported, manufactured, mined, or stored as inventory.
- **Perishability** — it can't be stockpiled for later; it expires the moment the provider stops delivering it (an empty seat on a flight, an idle consulting hour).
- **Inseparability** — the service and its provider can't be separated; if the provider isn't available, the service simply doesn't happen.
- **Heterogeneity (variability)** — no two deliveries of "the same" service are identical; there's always some variation between one instance and the next, even when the provider tries to standardize it.

This matters for a client because it means service businesses can't use goods-style operational levers (build ahead of demand, hold safety stock, decouple production from delivery) — their operational problem is almost always capacity and scheduling, not inventory.

### Production types

| Type | What it is | Typical examples |
|---|---|---|
| **Job production** | One-off or highly customized output built to an individual customer's request. Volume is low, specs vary job to job, and machines/processes often need to be reconfigured per job. | Building a bridge, printing a book, building a dam, building a ship, bespoke furniture, a custom software build. |
| **Batch production** | Repetitive production of identical goods in defined batches, sized to actual or expected customer demand rather than to a single order. | A bakery running one batch of a bread type per day, a garment maker cutting 200 shirts of one design, a supplement brand producing one flavor per production run. |
| **Flow production** (a.k.a. continuous / line production) | Manufacture through a series of *sequential* production steps, where each unit passes through the same successive stages — the defining trait is continuity of the process, not the size of the run. | An assembly line, a beverage bottling line, a mushroom-growing cycle run continuously through sterilization → inoculation → incubation → harvest. |

These three sit on a spectrum from fully custom/low-volume (job) to fully standardized/high-volume (flow), with batch production as the middle ground most small and early-stage businesses actually live in — it lets them standardize a product without committing to the fixed infrastructure a true flow line requires.

### Operations differ by sector

The activities a business actually performs are shaped by which sector it sits in, not by production type alone:

- **Manufacturers** revolve around purchasing raw materials and transforming them into finished products — processing, machining, grinding, painting, assembly and sub-assembly. Each of these steps is expected to add value to both the product and the company.
- **Retailers** manufacture nothing. They buy finished products from manufacturers and wholesalers and resell them to customers — so their operational center of gravity is logistics (getting the right stock to the right shelf) and marketing (moving it off the shelf), not production.
- **Restaurants and food companies** sit between the two: they purchase raw inputs *and* prepare/transform them like a manufacturer, but they also carry retail-style customer-facing responsibilities — costing each meal/dish/drink, tracking labor cost per cover, direct customer service, and following up on satisfaction. This dual load is why food-service operations are harder to benchmark against either pure manufacturers or pure retailers.

## Example

A small bakery decides to add a wedding-cake line alongside its daily bread. The daily bread is **batch production** — same recipe, same process, run in batches sized to expected daily footfall. The wedding cakes are **job production** — every cake is a one-off built to a specific couple's brief, at a much lower volume and higher price per unit. Treating both the same way (e.g. pricing cakes like batch bread, or trying to batch-run custom cakes ahead of orders) is exactly the kind of mismatch this framework is meant to catch.

## Applying it for a client

Start by asking the client to describe their last ten units of output — are they identical, or does each one carry different specs? That single question usually reveals which production type they're actually running, regardless of what they call themselves. Then check three things against it: (1) is their **costing method** matched to the type — job costing per unit for job production, batch costing for batch runs, process costing for flow; (2) is their **inventory policy** matched — flow production justifies holding raw-material stock ahead of demand, job production usually shouldn't; (3) is their **sector-driven activity mix** realistic — a client calling themselves a "manufacturer" but who actually just assembles bought-in components and resells them is operationally closer to a retailer, and should be benchmarked and staffed as one. This reframing alone often explains why a client's margins don't match the "typical" margins they've been chasing from an ill-fitting reference sector.

## 2024→2026: AI-assisted operations

**Status: emerging-but-credible** — the direction is real and already showing up in client operations, but the specific tools and vendor claims below are still maturing faster than independent evidence can confirm them; treat this section as "worth investigating with a client," not "proven at the maturity of the rest of this note."

AI is changing where the effort sits in operational improvement work, in three concrete ways:

- **Accelerating DMAIC's Measure and Analyze phases** (see [lean-six-sigma.md](lean-six-sigma.md)) — process-mining tools can now reconstruct an actual value stream map directly from system event logs (timestamps in an ERP, ticketing system, or transaction database) rather than requiring a team to manually time and observe each step. Root-cause analysis that used to require a trained Black Belt manually building a fishbone diagram can now be assisted by models that surface correlations across a much larger set of process variables than a human team would practically check by hand. The practical effect for a consultant: the Measure phase, historically the slowest and most resented part of a DMAIC project, can often be compressed from weeks to days for clients with digitized process data — though the Analyze phase still needs a human to confirm a statistical correlation is an actual causal mechanism, not a coincidence in the data.
- **Predictive maintenance** — sensor/IoT data feeding machine-learning models that forecast equipment failure before it happens, rather than relying on fixed maintenance schedules or waiting for a breakdown. This is most directly relevant to flow and batch production (see above) where unplanned downtime is expensive and schedule-driven maintenance either over-services healthy equipment or misses failures between scheduled checks. Early evidence from industrial deployments is genuinely promising, but the accuracy of any specific vendor's failure-prediction claims should be validated against the client's own before/after downtime data, not taken on the vendor's benchmark alone — prediction accuracy varies enormously by equipment type and how much historical failure data exists to train on.
- **Process automation** — robotic process automation (RPA) handling structured, rules-based back-office steps has existed for years, but agentic AI tooling is now extending automation into less rigidly structured, multi-step workflows (drafting, triaging, routing, first-pass decisioning) that previously required a human simply because the steps weren't cleanly ruleable. This is most relevant to service businesses and back-office production processes rather than physical manufacturing, and is the area with the least settled evidence of the three — pilot before committing headcount decisions to it.

The consultant's job with all three is the same discipline this note already teaches for production type generally: don't let a client (or a vendor) skip the Measure step — ask for the client's own before/after numbers on any AI tool under consideration, the same way you'd insist on real timing data rather than memory for a manual value stream map.

## Watch-outs

- Don't let a client mislabel a batch business as a "custom" (job) business just because they offer some customization — check whether the *core process* repeats identically or is reconfigured per order.
- Service businesses cannot be fixed with goods-style operational tools (build inventory, decouple supply from demand) — because of perishability and inseparability, their real constraint is almost always capacity/scheduling.
- A restaurant or food business run purely on a retailer's operational playbook (stock and sell) will under-cost labor and prep time, because those costs are real production costs the retailer model doesn't carry.
- Production type isn't fixed for the life of the business — a business that starts as job production (custom builds for early clients) often needs to deliberately migrate toward batch production to scale, and that migration is itself a project, not something that happens automatically.

## Related

- [value-chain.md](../operations/value-chain.md) — production processes are the "operations" link in the value chain; how a business produces determines what its inbound logistics and outbound logistics need to look like.
- [procurement-and-logistics.md](../operations/procurement-and-logistics.md) — the purchasing policy (as-needed, small-batch, or advance-for-storage) that feeds a production line should match the production type chosen here.
- [lean-six-sigma.md](../operations/lean-six-sigma.md) — DMAIC and value stream mapping are the concrete tools for diagnosing the cost/lead-time/quality problems named above, and the ones AI is now accelerating in the Measure and Analyze phases.
