---
name: customer-feedback-analysis
description: Aggregate customer feature requests from meeting notes, community chat and CRM notes via their MCP servers, score them into one dataset, and run an EDA that cross-checks the roadmap against what customers actually ask for.
---

# Skill: Customer feedback analysis

Pull customer feature requests out of every place they hide — meeting notes, a community
channel, sales notes — score them consistently, and produce a dataset plus an exploratory
analysis you can take into a roadmap planning session.

## Trigger

User asks to analyse customer feedback, build a feature-request dataset, find the most
demanded features, or cross-check a roadmap against customer demand.

## Prerequisites

The source MCP servers must be connected. Defaults below; substitute whatever the user
actually runs.

```bash
claude mcp add --transport http granola   https://mcp.granola.ai/mcp
claude mcp login granola

claude mcp add --transport http pipedrive https://mcp.pipedrive.ai/mcp
claude mcp login pipedrive

claude plugin install slack
```

`--transport http` is required. Without it the URL is registered as a stdio command and the
server fails to start. Check the wiring with `claude mcp list` before doing anything else —
each server should report connected rather than `Needs authentication`.

## Workflow

### 1. Confirm scope

Ask, and do not guess:

- **Period** — default to the current calendar year, monthly grain.
- **Sources** — which of the connected servers to read.
- **Product context** — what the product is and who the customers are. Feature names are
  only comparable across sources if there is a shared vocabulary to map them onto.

### 2. Pull the raw mentions

Query each source separately and keep them separate until scoring is done. For every
mention capture: date, source, customer, the feature asked for, verbatim quote, and the
surrounding context.

Note the **coverage** of each source — how many meetings/messages/deals were actually
searched. This bounds every conclusion drawn later, and belongs in the output.

### 3. Normalise feature names

Different sources name the same thing differently ("SSO", "Okta login", "SAML"). Build an
explicit mapping to one canonical feature name, and **show the user the mapping** before
scoring. This is the step that most often needs correction, and it silently corrupts
everything downstream if it is wrong.

### 4. Score each mention

Score every mention on these factors, then combine into a weighted average per feature ×
month × lifecycle stage:

| Factor | Signal |
| --- | --- |
| Tone | "urgent", "must have", "critical", "blocker", "dealbreaker" |
| Customer LTV | contract value, normalised across the customer base |
| Lifecycle stage | lead / new customer / loyal customer |
| Competitor reference | a competitor named as already having the feature |
| Churn linkage | the feature was given as a reason for leaving or not buying (1/0) |

State the weights explicitly and show them to the user. Any weighting is a judgement call —
an unstated one is an unauditable one. Do not present a score as objective.

### 5. Emit the dataset

Write a CSV with one row per feature × month × lifecycle stage:

| Column | Type | Notes |
| --- | --- | --- |
| `month` | `YYYY-MM` | calendar month of the mention |
| `feature` | text | canonical name from step 3 |
| `description` | text | one line, what the customer actually wants |
| `lifecycle_stage` | enum | `lead`, `new customer`, `loyal customer` |
| `mentions` | int | number of distinct mentions in that cell |
| `weighted_mention_score` | float 0–100 | weighted average — **never sum this column** |
| `competitors` | `;`-separated | named competitors, empty if none |
| `churn_linked` | 0/1 | mention tied to a churn or lost-deal event |
| `lost_revenue_usd` | int | attributed revenue, 0 when `churn_linked` is 0 |

`lifecycle_stage` and `mentions` are what make the churn and trend questions answerable —
a table of feature and score alone cannot separate "leads walk away over this" from
"long-time customers leave over this".

### 6. Run the EDA

Generate a notebook that answers, each with a table *and* a chart:

1. Which features drive the most churn for **leads**, and which for **loyal customers**?
2. Which three features **grew** most in mention score over the period, and which three
   **declined**?
3. Which **competitors** come up most, and what churn cost attaches to each?

`assets/customer_feedback_eda.ipynb` is a worked example against
`assets/feature_requests_2026.csv` (mock data, 185 rows, Jan–Aug 2026). Reuse its structure.

**Analysis rules:**

- Fit trends only on months that have data. Interpolating a gap invents mentions nobody
  made, and a leading gap turns the fit into `NaN`.
- Explode `competitors` before counting — it is a multi-value column.
- Rank competitors by cost per mention as well as raw volume. They rarely agree, and the
  disagreement is the interesting part.
- Never sum `weighted_mention_score`; it is already an average.

### 7. Cross-check the roadmap

Only once the analysis stands on its own, ask for the current roadmap and compare:

- Roadmap items with **no** supporting demand signal — why are they there?
- High-demand features **absent** from the roadmap.
- Features where demand is **falling** while the roadmap investment is rising.

Present these as questions for the planning session, not as verdicts.

## Guardrails

Say these out loud in the output; do not bury them.

- **Correlation, not causation.** A feature named in a cancellation call is correlated with
  the loss. Reasons given at the moment of leaving are the least reliable data in the set.
- **Selection bias survives the analysis.** The loudest customers are still the loudest
  customers after scoring. Weighting by LTV dampens this; it does not remove it.
- **It is backwards-looking by construction.** Nothing in the data sees a need customers
  have not voiced yet. It cannot originate strategy — only test one.

## Assets

| File | What it is |
| --- | --- |
| `assets/feature_requests_2026.csv` | Mock dataset in the output schema — 185 rows, 10 features, Jan–Aug 2026 |
| `assets/customer_feedback_eda.ipynb` | Worked EDA answering the three questions, with charts |

The notebook reads the CSV from its own directory, so run it from `assets/`. It needs
`pandas`, `numpy` and `matplotlib`.
