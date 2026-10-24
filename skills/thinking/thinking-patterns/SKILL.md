---
name: thinking-patterns
description: Think a question through with structured mental models — first principles, falsifiable hypotheses, pre-mortem, inversion, How Might We, affordable loss, constraint relaxation, Feynman's essential puzzle, leverage points, calibrated questions, analogical reasoning, OODA. Works on any topic (strategy, product, career, technical design, a negotiation, a personal decision). Use when the user asks to think something through, stress-test an idea or plan, find non-obvious options, get unstuck, or names one of these models.
---

# Skill: Thinking patterns

By default we match patterns, reason by analogy and assume things will go well. Each
mechanism in this skill forces you out of one of those habits. The skill picks the few
mechanisms that fit the question and runs each to a fixed output shape. It ends with a
recommendation, not a tour of frameworks.

## Trigger

The user asks to think through, analyse, stress-test or pressure-test something. Other
triggers: the user feels stuck, wants breakthrough or non-obvious ideas, or names a
mechanism ("do a pre-mortem on…", "first-principles this", "invert it").

## Workflow

### 1. Frame the question

Write the **core question** in one sentence, phrased as a decision or a tension: "Can X win
Y against Z?", "Should I do A or B by when?", "Why does this keep happening?"

Under it, list the **known starting point**: facts already established, each marked `[F]`
with its source, plus the constraints the user has stated.

If the question is too vague to frame in one sentence, ask one clarifying question.
Otherwise go ahead and state any framing assumptions you made.

### 2. Pick three lenses (four at most)

If the user named lenses, use those. If not, choose by the shape of the question and say
in one line why each lens was picked. Don't run all twelve. Switching methods costs more
than the variety brings, and three lenses done properly beat twelve done shallowly.

| The question is about… | Reach for |
| --- | --- |
| Strategy, positioning, or "why is it done this way?" | First principles, Inversion, Leverage points |
| A plan or bet you're about to commit to | Hypotheses, Pre-mortem, Affordable loss |
| Being stuck, or every option looks bad | Constraint relaxation, How Might We, Analogy |
| A user or customer problem | How Might We, First principles, Calibrated questions |
| A hard technical or analytical problem | Feynman, First principles, Constraint relaxation |
| A system that keeps behaving the same way (team, market, habit, growth loop) | Leverage points, Inversion, Hypotheses |
| A conversation: negotiation, interview, stakeholder | Calibrated questions, Inversion, Pre-mortem |
| A fast-moving situation: competitor move, crisis, pivot | OODA, Hypotheses, Affordable loss |
| A decision under deep uncertainty with limited resources | Affordable loss, Hypotheses, Pre-mortem |

**Default trio** when nothing clearly fits: **First principles → Hypotheses → Pre-mortem**.
They chain well. First principles produces beliefs, hypotheses make those beliefs testable,
and the pre-mortem attacks the plan built on them.

### 3. Run each lens

Read [references/mechanisms.md](references/mechanisms.md) for each chosen lens's steps and
output template. Give each lens its own numbered section, and follow these rules:

- **Give every item an ID** (truths `1…n`, hypotheses `H1…`, pre-mortem `P1…`, inversion
  `I1…`, and so on) so later sections can point back to it.
- **Build on the earlier lenses.** Hypotheses test the beliefs that first principles
  produced. The pre-mortem attacks the plan the hypotheses imply. Cross-reference by ID.
- **End every lens with an Implication line.** It says what the lens means for the core
  question, phrased as something to test, not as a conclusion.
- **Be concrete.** If a line would fit any company, person or topic, rewrite it with
  specifics or drop it.

### 4. Synthesise

- **What to resolve first.** Two or three items, ordered by how much they affect the
  decision. Each one links IDs across lenses (e.g. "H4 → P1") and names the single choice
  underneath them.
- **Recommendation.** Commit to a view, and say what evidence would change it.
- **Risks and opportunities** (optional, for strategic topics). Use the tables at the end
  of the reference. Rank opportunities by how much you'd bet on each.
- **Open questions.** What you couldn't answer, and what data would answer it.

### 5. Deliver

For a quick question, answer in chat. For a substantial analysis, or when the working
folder already holds numbered analysis docs, write `NN-<slug>.md` and continue the
numbering. Use this skeleton:

```markdown
# NN — <Title>: <topic> through <N> lenses

*First pass, <date>. Facts marked [F] are sourced; everything else is reasoning or hypothesis to test.*

**Core question:** …

Known starting point:
- [F] …

---

## 1. <Lens>
… (template from the reference)

**Implication (to test, not conclude):** …

## 2. <Lens>
## 3. <Lens>

---

## Synthesis: what to resolve first
1. **<Choice> (H_ → P_).** …

**Recommendation:** …

## Open questions
- …

*Sources: …*
```

If the user comes back with feedback or new facts, add a dated section (e.g. "Key risks
and opportunities — added <date> after review") rather than silently rewriting the first
pass.

## Working norms

- **Keep facts apart from reasoning.** Mark sourced facts `[F]` and link the source.
  Everything else is reasoning or hypothesis, and never presents itself as a finding.
- **Verify fast-moving facts** (prices, features, funding, headcounts, statistics, who
  holds which role) against a current source, and note the date.
- **Call out analogy posing as principle.** "Because competitor X does it" and "that's how
  it's done" are analogies. Label them as such.
- **Kill criteria are thresholds.** Write "< 1.3× difference", not "if it doesn't work".
- **Recommend, don't survey.** Give a clear call, and say what would change it.
- **Write plainly.** Use tables for parallel items and keep sentences short. In the
  output, the lens names are the only framework vocabulary.
