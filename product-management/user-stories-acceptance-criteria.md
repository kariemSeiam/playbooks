---
domain: product-management
concept: User Stories and Acceptance Criteria
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [user-stories, acceptance-criteria, given-when-then, backlog]
---

# User Stories and Acceptance Criteria

A user story is a brief, informal description of a feature from the end user's perspective — what they want to achieve and why it's valuable to them. Acceptance criteria are the predefined, testable requirements that must be met for that story to count as done. Together they're the smallest unit of the product backlog that a development team can actually pick up and build against without ambiguity.

## When to use

Write user stories when breaking a roadmap initiative or an Epic down into backlog items small enough for a single sprint (see [scrum-framework.md](scrum-framework.md)). Write acceptance criteria for every user story before it enters a Sprint Backlog — a story without acceptance criteria has no agreed definition of done, which is exactly the ambiguity Scrum's Sprint Review is designed to catch (too late, and expensively).

## How it works

**Hierarchy:** Epic → User Story → Task. An Epic is a large body of work (e.g., "checkout experience"); it breaks down into multiple User Stories (e.g., "remove an item from my basket," "enter my credit card number"); each User Story breaks down further into Tasks the development team executes.

**User story structure** — no single prescribed format, but the standard template is:
> **As a** \<user role\>, **I want** \<desired action/goal\>, **so that** \<benefit/reason\>.

This structure forces the team to consider three things explicitly: **who** will use the feature, **what** they want to achieve, and **why** it matters to them.

*Example:* "As a customer, I want to be able to search for products by category, so that I can easily find the items I'm looking for."

**Benefits of user stories:**

- Simple and understandable — easy for everyone involved in the project to grasp
- Focus on user value — helps prioritize features based on their significance to users
- Promote communication and collaboration — facilitate discussions and keep everyone on the same page
- Flexibility and adaptability — can be easily modified as requirements evolve

**Acceptance criteria** — a set of predefined requirements that must be met to mark a user story complete; also called the "definition of done" because they determine the scope and requirements developers must execute to consider the story finished.

**Given/When/Then format** (Gherkin-style), the standard acceptance-criteria template:
> **Scenario:** (explain the scenario). **Given** (how things begin), **When** (action taken), **Then** (outcome of taking that action).

*Worked example from the deck:*

- **User story:** As a product manager, I want to score potential ideas, so that I can decide what to include on my product roadmap.
- **Acceptance criteria:** Given that I have added two or more ideas and scored them using the Benefit vs. Cost scoring model, When I click the Rank button, Then ideas are sorted with the top-scoring ideas at the top.

**Why acceptance criteria are needed** (four functions):

1. Managing expectations
2. Defining scope and reducing ambiguity
3. Establishing testing criteria for QA
4. Defending against scope creep mid-sprint

**Traits of effective acceptance criteria:**

- **Testable** — since they form the definition of done for engineers, they need to be easy to test, and results must leave no room for interpretation; tests should reveal straightforward yes/no or pass/fail outcomes
- **Clear and concise** — this isn't comprehensive documentation; keep criteria as simple and straightforward as possible
- **Understandable to everyone** — criteria are useless if developers can't understand them; if you're unsure whether something is clear, ask and adjust until it is
- **Written from user perspective** — acceptance criteria are a way of looking at the problem from the customer's standpoint; write them in the context of a real user's experience, not internal implementation detail

## Example

Epic: "Checkout Experience." User Story: "As a customer, I want to save my card details, so that I don't have to re-enter them on my next purchase." Acceptance criteria: "Scenario: returning customer with a saved card. Given I have a saved payment method on file, When I reach the payment step on a subsequent order, Then my saved card is pre-selected and I can complete checkout without re-entering card details." This is testable (pass/fail: is the card pre-selected or not?), concise, understandable without engineering jargon, and written entirely from the customer's vantage point.

## Applying it for a client

When helping a client team move from vague requirements documents ("the app should have search") to an actual backlog, force every requirement through the "As a / I want / so that" template first — if the team can't fill in a coherent "so that," the requirement likely isn't validated yet and belongs back in customer research (see [mvp-customer-validation.md](mvp-customer-validation.md)), not the backlog. For acceptance criteria specifically, use the four-function checklist (expectations, scope, QA testing, scope-creep defense) as a review gate before any story enters a sprint — a story that fails the "testable" trait (can't be resolved to pass/fail) is the single most common reason sprints run over, because the team discovers mid-sprint that "done" was never actually defined. For a non-technical client stakeholder (e.g., a clinic administrator or brand marketing lead), the Given/When/Then format is often the first artifact that lets them meaningfully review and sign off on a requirement without needing to read code or wireframes.

## Watch-outs

- A user story that reads like a task list ("build a search bar") instead of a need ("so that I can easily find items") has lost the "why," which is exactly the information that helps later prioritization decisions.
- Acceptance criteria that aren't testable (subjective language like "the app should feel fast") aren't acceptance criteria — they're aspirations. Rewrite them until a QA tester or automated test could produce an unambiguous pass/fail.
- Don't let acceptance criteria balloon into full documentation — the deck is explicit that this isn't the place for comprehensive specs; keep it to the scenario needed to define "done" for this specific story.

## Related

- [scrum-framework.md](../product-management/scrum-framework.md)
- [prioritization-techniques.md](../product-management/prioritization-techniques.md)
- [mvp-customer-validation.md](../product-management/mvp-customer-validation.md)
