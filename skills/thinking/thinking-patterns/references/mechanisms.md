# Thinking mechanisms

Twelve mechanisms, each with: when to reach for it, the steps, the output template, and
what to watch for. Each one overrides a specific default habit of thought. That forcing
function is why each works, so don't soften it.

Order roughly follows usefulness for product and business questions. The first four are
the workhorses.

1. [Hypotheses](#1-hypotheses) — turn beliefs into testable predictions
2. [First principles](#2-first-principles) — rebuild from what is true regardless of convention
3. [Pre-mortem](#3-pre-mortem) — assume it failed, explain why
4. [Inversion](#4-inversion) — list the ways to guarantee failure, then avoid them
5. [How Might We](#5-how-might-we) — reframe problems as opportunity questions
6. [Affordable loss](#6-affordable-loss) — decide by downside you can bear, not upside you predict
7. [Constraint relaxation](#7-constraint-relaxation) — find the self-imposed limits
8. [Feynman's essential puzzle](#8-feynmans-essential-puzzle) — distil to the core solvable problem
9. [Leverage points](#9-leverage-points) — find where small changes move the system
10. [Calibrated questions](#10-calibrated-questions) — get hidden information out of people
11. [Analogy](#11-analogy) — import structure from another domain
12. [OODA](#12-ooda) — break and rebuild your mental model as the situation moves

---

## 1. Hypotheses

**Overrides:** after-the-fact rationalisation, optimism, sunk cost.
**Use when:** a plan rests on beliefs that could be wrong and there's a way to check them.

**Steps**
1. Collect the beliefs the plan depends on. Take them from first principles if that lens
   ran, otherwise from the user's framing.
2. Write each one as: *belief → why we think so → prediction if true → cheapest test →
   kill criterion*.
3. Make the kill criterion a threshold decided **before** testing, and give it a timeframe
   where relevant.
4. Order by decision impact. Mark which hypotheses decide *what we do* and which only
   tune *how*.
5. After a test, the call is persevere, pivot or abandon.

**Output**

| # | Hypothesis | Prediction if true | Cheapest test | Kill criterion |
| --- | --- | --- | --- | --- |
| H1 | **<Belief in bold.>** <One-line rationale.> | <Observable, with a number> | <Smallest experiment or data cut> | <Threshold that drops it> |

Close with: "H_, H_ decide <what>; the rest tune execution."

**Watch for:** predictions you couldn't observe, tests that cost more than the decision is
worth, and kill criteria vague enough to never trigger.

*Origin: Lean Startup (Ries, 2011); HBS note 812-095 (Eisenmann, Ries, Dillard).*

---

## 2. First principles

**Overrides:** reasoning by analogy ("it's always done this way", "competitor X does it").
**Use when:** the conventional answer may just be a shared assumption, or you need
differentiation rather than incremental improvement.

**Steps**
1. Strip the labels. What job is actually being done, and for whom? If there are several
   jobs, separate them (a table works well).
2. List everything believed about the problem. For each, ask: *Why do I think this? How do
   I know it's true? What if the opposite were true?*
3. Keep only what is true regardless of convention: physical, economic, behavioural or
   logical constraints. Flag the rest as inherited belief.
4. Reason upward. Each truth gets an arrow (→) to what it implies.
5. Rebuild an answer from the truths alone.

Musk's battery example shows the move. Price the raw materials ($80/kWh) instead of
accepting the industry price ($600/kWh). The gap is the opportunity.

**Output**

Optional jobs table:

| Job | Who owns it | Nature |
| --- | --- | --- |

**Things that are true no matter what others do:**
1. **<Truth in bold.>** <Why.> → *<What it implies for the core question.>*
2. …

**Implication (to test, not conclude):** <The rebuilt frame in one or two sentences.>

**Watch for:** "truths" that are really industry convention, and truths too generic to
imply anything.

*Origin: Aristotle, Metaphysics; Musk (TED 2013); Tim Urban, "The Cook and the Chef" (2015).*

---

## 3. Pre-mortem

**Overrides:** optimism, and the social pressure not to voice doubt.
**Use when:** you're about to commit to a plan, strategy, launch or big decision.

**Steps**
1. Set a concrete future date, usually 1–2 years out, and state the failure vividly:
   "It's <date>. <Plan> has failed: <specific bad outcome>. What happened?"
2. Write the most plausible failure stories, each independently. Imagining that the
   failure already happened surfaces about 30% more reasons than asking "what could go
   wrong?"
3. For each story, give the early-warning signal you could watch **now** and a
   pre-emptive move.
4. Name the most likely failure, and the single unresolved choice it comes down to.

**Output**

> *It's <date>. <Plan> has <failed outcome>. What happened?*

| # | Failure story | Early-warning signal (watch now) | Pre-emptive move |
| --- | --- | --- | --- |
| P1 | **<Short name.>** <The story.> | <Measurable signal> | <Action, linking H_ if relevant> |

**Which failure is most likely?** <P_, and why. Which others compound it. The one choice
underneath.>

**Watch for:** generic failures ("bad execution", "market changed"), and signals you
can't actually observe.

*Origin: Gary Klein, "Performing a Project Premortem", HBR (2007); Mitchell et al. (1989);
Kahneman calls it his favourite decision technique.*

---

## 4. Inversion

**Overrides:** looking only at success scenarios. It is often easier to see what *not* to
do.
**Use when:** you're setting a strategy or goal, avoiding known failure modes, or filtering
out stupidity before planning forward.

**Steps**
1. State the goal clearly.
2. Invert it: "How would I *guarantee* this fails?" List the paths systematically, across
   people, money, time, product, market and reputation.
3. Check which of these the current plan is already doing. That's the uncomfortable part,
   and the valuable one.
4. Turn the list into avoid-rules, then combine them with forward planning.

Munger: "All I want to know is where I'm going to die, so I'll never go there."

**Output**

**Goal:** …

| # | How to guarantee failure | Are we doing it now? | Avoid-rule |
| --- | --- | --- | --- |
| I1 | … | Yes / Partly / No — evidence | … |

**Implication:** <the avoid-rules that change the plan>

**Watch for:** overlap with the pre-mortem. If both run, inversion covers the *rules* and
the pre-mortem covers the *stories and signals*.

*Origin: Charlie Munger, "A Lesson on Elementary Worldly Wisdom" (USC, 1994).*

---

## 5. How Might We

**Overrides:** defensive, problem-focused framing that shuts down options.
**Use when:** you're in discovery, synthesising user research, or have a problem with no
obvious solution space.

**Steps**
1. Write a point of view: **[user] needs [need] because [insight]**.
2. Generate HMW questions with these variations:
   - *Amp up the good:* HMW use <positive element> to <benefit>?
   - *Remove the bad:* HMW separate <negative element> from <experience>?
   - *Explore the opposite:* HMW make <problem> the best part?
   - *Question an assumption:* HMW remove <assumed constraint> entirely?
3. Calibrate the scope. "Redesign travel" is too broad. "A perfect seatbelt from recycled
   bottles" is too narrow.
4. Pick the two or three questions that open the most promising space, and sketch a first
   idea for each.

**Output**

**Point of view:** …

| # | Lens | How might we… | First idea |
| --- | --- | --- | --- |
| W1 | Amp up the good | … | … |

**Most promising:** W_, W_, and why.

*Origin: Sidney Parnes (1960s), P&G, IDEO; Stanford d.school Bootcamp Bootleg; Google Design Sprint.*

---

## 6. Affordable loss

**Overrides:** decisions based on predicted returns when the future can't be predicted.
**Use when:** uncertainty is deep (probabilities are unknowable), resources are limited,
and the choice is whether or how much to commit.

**Steps**
1. Take stock of the means:
   - *Who am I?* Identity, values, preferences.
   - *What do I know?* Skills, expertise.
   - *Whom do I know?* Network, partners.
2. Replace "What's the expected return?" with "What can I afford to lose entirely?" Cover
   time, money, and reputation or relationships.
3. Design the smallest action that fits inside that envelope and still teaches something.
4. Note who could join and bring resources. Commitments from others grow the means.

**Output**

| Means | What we have |
| --- | --- |
| Who we are | … |
| What we know | … |
| Whom we know | … |

| Resource | Affordable loss | Why this number |
| --- | --- | --- |
| Time | … | … |
| Money | … | … |
| Reputation / relationships | … | … |

**First move within the envelope:** … **Who could co-invest:** …

*Origin: Saras Sarasvathy, "Causation and Effectuation", AMR (2001); study of 27 expert
entrepreneurs.*

---

## 7. Constraint relaxation

**Overrides:** invisible assumptions about what is allowed.
**Use when:** you're stuck, every option looks bad, or progress has plateaued.

**Steps**
1. Name the impasse explicitly.
2. List every assumption: what can't change, which moves are allowed, what a solution
   must look like.
3. For each, ask: "What if this didn't have to be true?" Some will be real constraints.
   Many won't be.
4. Break down "chunks" you treat as indivisible (a team, a product, a price, a process)
   into parts you can rearrange.
5. Explore the paths that open up.

The nine-dots puzzle can't be solved until you drop the unstated rule that lines must stay
inside the grid.

**Output**

**Impasse:** …

| # | Assumed constraint | Real or self-imposed? | If relaxed, what opens up |
| --- | --- | --- | --- |
| C1 | … | … | … |

**Chunks broken down:** …

**New paths worth exploring:** …

*Origin: Knoblich, Ohlsson et al., JEP:LMC (1999), matchstick-arithmetic experiments.*

---

## 8. Feynman's essential puzzle

**Overrides:** being overwhelmed by complexity, and fuzzy problem statements.
**Use when:** the problem is hard and technical or analytical, an architecture decision,
or anything where nobody can say precisely what the problem is.

**Steps**
1. Write the problem down precisely. Often the formulation starts the solution.
2. Ask: *What is the simplest example? How would I tell if an answer is right?*
3. Keep distilling until you reach an essential puzzle you believe you can solve.
4. List the techniques you have, including ones from other fields, and try each against
   the puzzle.
5. Park any remaining puzzles in a running "unsolved" list. Revisit it whenever you learn
   a new technique.

**Output**

**Precise statement:** …
**Simplest example:** …
**How we'd know an answer is right:** …
**Essential puzzle:** …

| Technique (any field) | Applied to the puzzle | Hit? |
| --- | --- | --- |

**Still unsolved (park for later):** …

*Origin: Danny Hillis, "Richard Feynman and The Connection Machine", Physics Today (1989).*

---

## 9. Leverage points

**Overrides:** pushing on obvious, shallow parameters that rarely change anything.
**Use when:** a system keeps producing the same outcome (an organisation, a market, a
growth loop, a habit), or you're prioritising where to put effort.

**Steps**
1. Map the system:
   - *Stocks:* what accumulates.
   - *Flows:* what changes the stocks.
   - *Feedback loops:* which ones reinforce and which ones balance.
2. Scan for intervention points from shallow to deep: parameters → delays → loop strength
   → information flows → rules and incentives → power to self-organise → goals → mindset
   or paradigm.
3. Ask: "Where is everyone else pushing?" Usually on parameters, and often in the wrong
   direction.
4. Ask: "What would change the goal or the mindset?"

**Output**

**System map:** stocks …; flows …; loops (R = reinforcing, B = balancing) …

| # | Level | Intervention | Expected effect | Effort |
| --- | --- | --- | --- | --- |
| L1 | Information flow | … | … | … |

**Where everyone else pushes:** … **Highest-leverage move:** …

*Origin: Donella Meadows, "Leverage Points: Places to Intervene in a System" (1999).*

---

## 10. Calibrated questions

**Overrides:** defensive conversations, and "why" questions that sound like accusations.
**Use when:** a conversation lies ahead (customer discovery, negotiation, a stakeholder,
a hiring call) and the other side holds information you need.

**Steps**
1. Anticipate the other party's emotional state and concerns.
2. Prepare labels that name them: "It seems like…", "It sounds like…". After a label,
   wait in silence for four seconds or more.
3. Aim for "That's right". It means you've captured their view accurately ("you're right"
   doesn't).
4. Prepare calibrated questions that start with **How** or **What**, never Why: "What's
   the biggest challenge you face with…?", "How am I supposed to do that?", "What would
   make this work for you?"
5. Leave silence after each question, and mirror the last few words they say.

**Output**

**Their likely position and emotions:** …

| # | Moment | Label or question | What it should surface |
| --- | --- | --- | --- |
| Q1 | Opening | "It seems like…" | … |
| Q2 | Discovery | "What's the hardest part of…?" | … |

**Information we most need:** … **Walk-away / red lines:** …

*Origin: Chris Voss, Never Split the Difference (2016); FBI hostage negotiation practice.*

---

## 11. Analogy

**Overrides:** looking for answers only inside your own domain.
**Use when:** another industry or field has probably already solved the same kind of
problem.

**Steps**
1. State the target problem's **structure**: the relations between things, not surface
   features.
2. Find **two** source problems from different domains with the same structure. Comparing
   two sources produces a reusable pattern, which is far more reliable than one analogy.
3. Map them: source objects → target objects, source relations → target relations.
4. Carry over relations the target is missing. Those are the candidate ideas.
5. Abstract the common pattern, then adapt it to the target's constraints. State where the
   analogy breaks.

In Gick & Holyoak's radiation problem, 10% of people solve it unaided. With two analogous
stories, 52% solve it without a hint.

**Output**

**Target structure:** …

| Source A element | Source B element | Target element |
| --- | --- | --- |

**Common pattern:** … **Carried over to target:** … **Where it breaks:** …

*Origin: Gick & Holyoak, Cognitive Psychology (1980, 1983).*

---

## 12. OODA

**Overrides:** forcing old mental models onto new situations. Models decay without fresh
information.
**Use when:** the situation is fast-moving (a competitor move, a crisis, a pivot), or the
current mental model clearly no longer fits.

**Steps**
1. **Observe** with relaxed alertness. List what is actually happening, without filtering
   it through the current story.
2. **Orient.** Destructive deduction: break the current mental model into its parts and
   assumptions. Creative induction: recombine those fragments with the new observations
   into a new model. This is Boyd's "snowmobile" built from skis, an outboard motor,
   handlebars and tank treads.
3. **Decide.** Pick the model that best fits reality.
4. **Act** in a way that tests it, then feed the results back into Observe. Tempo matters:
   cycle faster than the environment changes.

**Output**

**Observations (unfiltered):** …

| Old model's assumption | Still holds? | Evidence |
| --- | --- | --- |

**New model:** … **Decision:** … **Test action and what we'll observe next:** …

*Origin: John Boyd, "Destruction and Creation" (1976); Osinga, Science, Strategy, and War (2007).*

---

## Synthesis tables (optional, for strategic topics)

**Risks**

| # | Risk | What it looks like | Link to above |
| --- | --- | --- | --- |
| R1 | **<Name>** | <Concrete form; split into sub-threats if they differ, and say which to watch> | P_, H_ |

**Opportunities, ranked by how much we'd bet on each**

| # | Opportunity | Why it matters | Caveat / what to verify |
| --- | --- | --- | --- |
| O1 | **<Name>** | <Why structural rather than tactical; which risk it defends against> | <Unverified claims, linked hypothesis> |

Close with **How they fit together:** which opportunities defend against which risks, which
reinforce each other, and where tensions exist (e.g. an opportunity that speeds up a
risk).
