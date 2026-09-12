---
domain: product-management
concept: Assessing Customer Need Before Building an MVP
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [mvp, customer-research, interviews, surveys, validation]
---

# Assessing Customer Need Before Building an MVP

Before writing a line of code for a minimum viable product, you validate that the need is real using two complementary research tools: customer interviews (exploratory, small-sample, qualitative) and customer surveys (confirmatory, large-sample, quantitative). Using the wrong one for the stage — surveying before you know what to ask, or interviewing when you need statistical confidence — wastes the exact time an MVP is supposed to save.

## When to use

Interviews first, always, when you don't yet know the shape of the problem — pre-MVP, pre-feature, any time you're exploring a new hypothesis about user pain. Surveys second, once interviews have generated a hypothesis you need to measure and validate at scale before committing engineering resources. Never skip straight to a survey on an unvalidated hypothesis — you'll get precise answers to the wrong question.

## How it works

**Two tools, two purposes:**

| | Customer Interviews | Customer Surveys |
|---|---|---|
| **Purpose** | Exploration — theory building: generate new hypotheses, gain in-depth understanding, understand motivations/opinions/pain points | Validate, measure, compare — theory testing: measure variables, test hypotheses, establish relationships between behaviors |
| **Sample size** | Small | Large |
| **Data type** | Non-numeric, descriptive, rich and detailed | Numeric, statistical |

**Interview structure has three levels**, each trading structure for depth:

- **Structured** — standard format, predetermined question set, closed-ended questions, fixed responses. Advantages: easy to analyze (quantified), objective (minimizes interviewer bias). Limitation: lacks depth — can't explore a participant's perspective beyond the fixed questions.
- **Unstructured** — no set format, free conversation, open-ended and exploratory, qualitative. Advantages: rich data collection, exploration of new topics. Limitations: lack of standardization, time-consuming.
- **Semi-structured** — combination of structure and flexibility, open-ended questions, qualitative data. Advantages: depth of user understanding + flexibility. Limitation: analysis complexity (qualitative responses are harder to code than fixed-choice ones).

**Areas to explore in an interview** (regardless of structure level):

1. Behavioral — frequency, when and why
2. Satisfaction
3. Motives and pains — what's the best part, what's the worst part
4. Feedback on features
5. Feedback on value proposition

## Example

A startup considering a grocery-delivery MVP runs 8 semi-structured interviews first (small sample, open-ended: "walk me through the last time you needed groceries urgently") and discovers the real pain isn't delivery speed, it's minimum-order thresholds forcing over-buying. That becomes the hypothesis. Only then do they run a survey of 500 people asking closed, quantified questions ("how often have you over-ordered to hit a free-delivery minimum? Never / Rarely / Often / Always") to confirm the pain is widespread enough to build for — before writing a single line of the MVP.

## Applying it for a client

For a startup client with no existing user base, mandate interviews before any MVP scoping conversation — 5-8 semi-structured interviews is usually enough to surface a real hypothesis, and it's cheap enough to do in a week. For a clinic or established business client that already has patients/customers, you have an existing base to survey — use that advantage: run a short structured survey first to find where satisfaction is lowest, then follow up with unstructured interviews on that specific segment to understand *why*. The sequencing (interview→survey vs. survey→interview) should follow whichever direction you're missing information in, not a fixed rule — the point is never validate a hypothesis with the same tool that generated it.

## Watch-outs

- Interviews generate hypotheses; they don't validate them at scale. A compelling story from 3 interviewees is not evidence the problem is common — that's what the survey step is for.
- Structured interviews and surveys both introduce a subtle risk: you can only learn about the options you thought to include in the question. If you haven't done exploratory interviews first, your structured survey will systematically miss the answer you didn't think to ask about.
- Don't conflate "assessing customer need" with "asking customers what to build" — the deck's framing is about validating the *problem*, not outsourcing the *solution* design to the interviewee.

## Related

- [customer-value-4cs.md](../product-management/customer-value-4cs.md)
- [segmentation-personas.md](../product-management/segmentation-personas.md)
- [product-management-fundamentals.md](../product-management/product-management-fundamentals.md)
