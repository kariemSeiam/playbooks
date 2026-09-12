---
domain: product-management
concept: Scrum Framework
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [scrum, agile, sprints, roles, artifacts, ceremonies]
---

# Scrum Framework

Scrum is the most widely used Agile framework for project management, particularly in software development — an iterative and incremental approach emphasizing collaboration, flexibility, and rapid delivery of value in fixed time boxes called sprints. It matters because it's the concrete operating system that turns Agile's abstract values (see [waterfall-vs-agile.md](waterfall-vs-agile.md)) into a repeatable weekly/biweekly rhythm a team can actually run.

## When to use

Use Scrum when a team needs a structured but adaptable cadence for shipping incremental value against a backlog that will keep changing — most product development teams by default. It's the natural operational layer under a product roadmap and a prioritized backlog: the roadmap says *what and roughly when*, prioritization says *what order*, and Scrum is *how the team actually executes that, sprint by sprint*.

## How it works

**Why Scrum matters:**

- Improved focus and clarity — working in sprints with a defined goal (delivering a product increment) keeps teams focused and avoids scope creep
- Enhanced team collaboration — daily stand-ups and other Scrum events promote communication within the development team
- Faster time to market — regular delivery of product increments allows for early feedback and faster launches
- Increased adaptability — Scrum is flexible, letting teams adapt to changing priorities or requirements within a sprint

**Core elements — Roles:**

- **Product Owner** — represents the stakeholders and prioritizes the product backlog, ensuring it reflects business needs and user value
- **Scrum Master** — facilitates the Scrum process, removes roadblocks for the development team, and ensures adherence to Scrum principles
- **Development Team** — a self-organizing, cross-functional team with the skills necessary to deliver product increments

**Core elements — Artifacts:**

- **Product Backlog** — a prioritized list of features, user stories, and other work items that need to be completed for the product (this is exactly where [prioritization-techniques.md](prioritization-techniques.md) and [user-stories-acceptance-criteria.md](user-stories-acceptance-criteria.md) feed in)
- **Sprint Backlog** — a subset of items pulled from the product backlog, chosen for a specific sprint
- **Product Increment** — the usable product functionality delivered at the end of each sprint

**Sprints:** Scrum operates in time-boxed iterations called sprints, typically lasting 1-4 weeks. Each sprint focuses on delivering a potentially shippable product increment that adds value to the product. Short sprint cycles allow for rapid feedback and let the team adapt to changing requirements or priorities.

**Scrum Events (the ceremonies that structure each sprint):**

1. **Sprint Planning** — the development team and product owner collaboratively plan the work for the upcoming sprint, selecting items from the product backlog
2. **Daily Stand-up Meetings** — brief daily meetings (often 15 minutes) where team members discuss progress, identify impediments, and plan the upcoming day
3. **Sprint Review** — a meeting at the end of the sprint to showcase the completed product increment to stakeholders and gather feedback
4. **Sprint Retrospective** — a meeting after the sprint review where the team reflects on what went well, what could be improved, and how to adapt their approach for future sprints

The cycle runs: Sprint Planning → (sprint work, with Daily Scrums throughout) → Sprint Review → Sprint Retrospective → back into the next Sprint Planning, pulling refined items from the Product Backlog into the next Sprint Backlog.

## Example

A team commits to a 2-week sprint to deliver a redesigned checkout flow (the Product Increment). The Product Owner has already prioritized "checkout flow" to the top of the Product Backlog using RICE scoring (see [prioritization-techniques.md](prioritization-techniques.md)); Sprint Planning breaks it into user stories with acceptance criteria (see [user-stories-acceptance-criteria.md](user-stories-acceptance-criteria.md)) that become the Sprint Backlog. Daily 15-minute stand-ups surface a blocked payment-API integration on day 4, which the Scrum Master clears by day 5. At the Sprint Review, stakeholders see the working checkout flow and flag that error messaging is confusing — that feedback goes into the next sprint's backlog. At the Retrospective, the team notices stand-ups were running long and agrees to a stricter 15-minute time-box going forward.

## Applying it for a client

For a startup client with no existing process, introduce Scrum's four roles and four ceremonies as a minimum viable structure — don't over-engineer with extra artifacts before the basic rhythm (Planning → Daily → Review → Retro) is running reliably. For a client team resistant to "another process," frame the Retrospective specifically as the mechanism that lets the team fix Scrum itself over time — it's the built-in continuous-improvement loop, which is usually the ceremony most likely to survive skepticism because it visibly produces change (shorter stand-ups, clearer Definition of Done) rather than just adding meetings. Watch for a Product Owner role that's actually absent or shared awkwardly across multiple stakeholders on the client side — a Scrum implementation with no single person accountable for the backlog is the most common reason client Scrum adoptions stall.

## Watch-outs

- Running the ceremonies without empowering the roles isn't Scrum — a "Scrum Master" who has no authority to remove impediments, or a "Product Owner" who isn't actually authorized to make prioritization calls, produces the ceremony schedule without the framework's actual function.
- Sprint length (1-4 weeks) should match the team's actual cycle for gathering meaningful feedback — a 1-week sprint on a feature that needs 3 weeks of user data to evaluate produces false urgency without real signal.
- Scrum artifacts assume a healthy Product Backlog feeding them — if the backlog isn't prioritized (see [prioritization-techniques.md](prioritization-techniques.md)) or the items aren't written as testable user stories (see [user-stories-acceptance-criteria.md](user-stories-acceptance-criteria.md)), Sprint Planning has nothing solid to pull from.

## Related

- [waterfall-vs-agile.md](../product-management/waterfall-vs-agile.md)
- [user-stories-acceptance-criteria.md](../product-management/user-stories-acceptance-criteria.md)
- [product-roadmap.md](../product-management/product-roadmap.md)
