---
name: roundtable
description: Multi-persona deliberation — seat N of oracle-prism's 20 lenses at one table and let them discuss a stakes-bearing question turn by turn across 4 rounds (OPEN → DEEPEN → CONVERGE → VOTE), then vote with confidence. One agent, no subagents. Use when user says "roundtable", "round table", "round-table", "convene the council", "deliberate this", "seat N lenses", "seat all twenty", or asks to "add a supervisor" / "bring in a specialist", or wants a decision debated rather than analysed. Do NOT trigger for angles without a decision (use /oracle-prism), one master deep (use /oracle-facet), or disproving a claim (use /adversarial-analysis).
argument-hint: "[--seats N] [--preset default|retro|design|incident] [--who \"A,B,C\"] [--all] [--super ROLE] [--specialist ROLE] [--dna] [--options \"a,b,c\"] [--aggregator weighted|majority|unanimity-or-escalate] question"
---
# /roundtable — the prism, seated

> alias: `/round-table`

> `/oracle-prism` refracts one question through N lenses, each in its own
> section, none answering the others. `/roundtable` seats those same lenses
> at one table and makes them **answer each other** — turn by turn, four
> rounds, then a vote. Prism gives you angles. Roundtable gives you a decision.

**Lineage.** Boy Pinyo's "Fortal LED 100M Round Table Meeting" — 7 agents,
4 rounds, confidence vote. Specified by mother-oracle as
`ψ/lab/boy-method/round-table-skill-spec.md` (2026-05-16, never built).
This is that spec, built — with one change: the occupants are prism's 20
lenses, and the whole thing runs in one agent, inline, like prism.

## Usage

```
/roundtable "Should we ship 02 as the course page?"
/roundtable --preset design "Merge the eight landing pages into one?"
/roundtable --who "Skeptic,Maintainer,Planner" "Adopt the Algorithm for every page?"
/roundtable --seats 7 --preset incident "Why did the deploy die at 18 of 28?"
/roundtable --all "Delete /roundtable's two dangling references, or build it?"
/roundtable --super "Editor" --preset design "Which of the eight landing pages ships?"
/roundtable --specialist "Tax Specialist" --preset default "Accept the 100M contract?"
/roundtable --dna --preset design "Which of the eight landing pages ships?"
/roundtable --options "build,delete,defer" --aggregator unanimity-or-escalate "…"
```

## Who can sit — the 20

Every seat is one of `/oracle-prism`'s lenses. They are **role archetypes**,
not real people, which is what makes Rule 6 easy here.

| Preset | Seats | Question each brings to the table |
|---|---|---|
| `default` | 🔍 Archaeologist · 🐛 Bug Hunter · 💀 Skeptic · 🏗️ Architect · 📋 Auditor | what happened · what broke · what went wrong · what changed · what's left |
| `retro` | Historian · Critic · Cheerleader · Connector · Planner | in what order · what went poorly · what to repeat · what connects · what next |
| `design` | User · Maintainer · Breaker · Simplifier · Integrator | easy to use? · easy to change? · how it fails · what to remove · how it fits |
| `incident` | Firefighter · Detective · Defender · Forecaster · Builder | what was fixed · root cause chain · why guards missed · what's next · systemic fix |

**Seating rules**
- `--preset X` seats that preset's five. Default: `default`.
- `--seats N` (3–7) takes the first N of the preset; more than 7 needs `--super`.
- `--who "A,B,C"` seats exactly those, by name, from any preset. Names not in the 20 are allowed but must be **archetypes** ("Security Auditor"), never a real person — for a real practitioner use `/oracle-facet`.
- `--all` seats **all 20**. Turns compress (see budgets). Expect a long minute.
- `--super ROLE` adds a **Supervisor** at the head of the table; `--specialist ROLE` adds an invited **Specialist**. Both are extra seats, both archetypes, both optional — see the next section. At most one of each.
- **Quorum is 3.** Two is a debate; one is a monologue. The skill refuses to convene under three.
- The Oracle itself is **Chair and Clerk** — it keeps order, enforces the rules below, writes the minute, and does not vote.

## DNA — seating real inheritance

`--dna` gives every seat the roster from `/oracle-prism`'s **DNA** section: the
named practitioners whose method that lens runs. Each seat declares its
inheritance once, in OPEN, on one italic line under its name — then argues as
the archetype for the rest of the table.

This is Boy Pinyo's distillation pattern applied to deliberation: a seat that
says *which real humans contributed which traits* can be argued with, where an
unattributed persona cannot.

**Rule 6, restated for a table where seats disagree:** a seat may say
*"the Breaker lens, after Dekker, reads this as drift"* — it may never say
*"as Dekker, I read this as drift"*, and it may never quote anyone it cannot
attribute. A Supervisor's **ruling** is signed by the archetype through the
Oracle, never by a person. If a named practitioner's documented position is
being paraphrased, the minute says *paraphrase*. For one master at depth,
use `/oracle-facet`.

## The head of the table — Supervisor and Specialist

Boy's known roster had a hub seat that convened and did not argue. Two optional
seats carry that idea. Both are **archetypes** ("Editor", "Security Specialist",
"Tax Specialist"), never a real person.

| | `--super ROLE` — Supervisor | `--specialist ROLE` — Specialist |
|---|---|---|
| Sits | head of the table | last chair |
| Speaks | **last in every round**, having heard the whole table | last among the voting seats |
| OPEN | no position — states **what the table must not miss** and any fact it adds to the record | a position, like any seat, from its domain |
| DEEPEN | may put **one question to one seat**, which that seat answers in one line — the only cross-turn allowed at the table | may be **questioned** by up to two seats, and answers in one line each |
| CONVERGE | **names the axes** (takes this from the Chair) | declares its axis and flip condition like any seat |
| VOTE | **does not vote** in the tally. After the tally, gives a **ruling**: `confirm` · `escalate` · `override → {option}` — an override must cite a values violation or a fact on the record the table ignored, and is written into the minute as an override | **votes**, confidence counted ×1 — expertise earns the last word, not extra weight |
| Rule 6 | its ruling is signed as the archetype through the Oracle, never as a person | same |

A Supervisor cannot rescue a bad question — if the question has no stakes,
Step 0 still redirects to `/oracle-prism`. A Specialist cannot be invited for a
domain no seat has questioned; it sits because the question needs it.

## Step 0 — convene

```bash
date "+🕐 %H:%M %Z (%A %d %B %Y)"
```

Then restate, in one line each, before any seat speaks:

1. **The question** — as asked, plus the canonical options. If `--options` is absent, derive 2–4 from the question and print them; the vote must land on one of these.
2. **The seating** — names in speaking order. Order is the preset's order, or `--who` order; then the Specialist, then the Supervisor last.
3. **The context** — what facts the table is allowed to use: files, commits, numbers already on the record. Seats **do not fetch mid-round**. If a fact is missing, the Chair adds it here or it stays missing.

If the question has no stakes — nothing irreversible, nothing costly, nothing being wrong about is expensive — say so and offer `/oracle-prism` instead. Roundtable is for decisions.

## The four rounds — turn by turn

Each round goes **once around the table in seating order**. Every occupant speaks once per round. No one speaks twice in a round. The Chair does not editorialise between turns.

### Round 1 — OPEN · positions stated cold
Each seat, having heard no one: **position** (one sentence) · **reasoning** from its own question (2–4 sentences) · **confidence now** (1–10) · **what would change my mind** (one sentence).
Specialist: the same, from its domain. Supervisor, last: **what the table must not miss** — scope, a missing fact, a constraint — and no position.

### Round 2 — DEEPEN · cross-examination
Each seat names **the one seat it most disagrees with** and critiques that position (2–3 sentences, citing the seat by name), then states a **self-update**: what shifted after hearing Round 1, or `no change` — and its position and confidence now.
Seats may put one question each to the Specialist (max two); it answers in one line each. Supervisor, last: at most **one question to one seat**, answered in one line. Nothing else crosses turns.

### Round 3 — CONVERGE · narrow the axis
The **Supervisor** (or the Chair, if there is none) first lists the **disagreement axes** heard so far (2–4, one line each). Then each seat: **the axis that decides my vote** · **coalition with** (names) · **flip condition** — the one thing that would make it vote the other way · position and confidence now.

### Round 4 — VOTE · binding
Each seat: **final vote** (one canonical option) · **final confidence** (1–10, **5 forbidden** — pick 4 or 6, the fence is not a vote) · **one-line rationale** (≤140 chars, minute-ready) · **dissent note** only if voting against the emerging majority.
The Specialist votes. The Supervisor does not — it waits for the tally, then rules.

### Turn budgets
| Seats | OPEN | DEEPEN | CONVERGE | VOTE |
|---|---|---|---|---|
| 3–7 | full turn | full turn | full turn | full turn |
| `--all` (20) | position + confidence, one line | challenge line only; `no change` allowed silently | roll-call by axis: the Chair groups seats under each axis, seats add a flip condition only if they have one | table row |

### Early stop — the Chair may skip ahead
After Round 2 or 3, fast-forward to VOTE if **all** seats hold the same position at confidence ≥ 8, or if every seat said `no change` in Round 2 and no new fact entered. If one seat sits at 10 and the rest at ≤ 3 with no challenge, stop and **ask the human** whether to defer to it.

**Hard ceiling: four rounds.** There is no Round 5. A messy vote goes to the human — that is what escalation is for.

## The vote

**Aggregators** — `--aggregator`, default `weighted`:
- `majority` — most votes wins; confidence reported, not weighted
- `weighted` — sum final confidence per option; highest wins
- `unanimity-or-escalate` — every seat ≥ 7 on the same option, else `ESCALATE`

**Ties** (weighted): highest single confidence wins → fewer dissent notes wins → **escalate**. Never auto-pick.

**Ruling** — if a Supervisor sits, it speaks once after the tally:
- `confirm` — the decision stands as tallied
- `escalate` — to the human, with the reason
- `override → {option}` — only on a **values violation** or a **fact on the record the table ignored**; the grounds go in the minute, and the tallied result is kept beside the ruling so the override is visible, not silent

**Escalate** — return no decision and hand the human the minute — when: no option holds ≥ 60% of weighted confidence · any dissent note cites a values violation (honesty, safety, consent, Rule 6) · two seats at 10 on opposing sides.

## The minute — what gets written

`ψ/lab/roundtable/{YYYY-MM-DD}_{slug}.md`, and one line to `ψ/inbox/decisions/{YYYY-MM-DD}_{slug}.md` so `/recap` and `/standup` pick it up.

```markdown
# Roundtable — {question}
{date · time} · {N} seats · preset {X} · aggregator {Y}
Options: {a} / {b} / {c}
Context on the record: {one line per fact}

## Round 1 — OPEN
**🔍 Archaeologist** — position · reasoning · confidence 6 · would change my mind: …
**🐛 Bug Hunter** — …

## Round 2 — DEEPEN
**🔍 Archaeologist** → challenges **Skeptic**: … · self-update: … · now {position}, 7
…

## Round 3 — CONVERGE
Axes: (1) … (2) …
**🔍 Archaeologist** — axis 2 · with Auditor, Architect · flips if … · {position}, 7
…

## Round 4 — VOTE
| Seat | Vote | Conf | Rationale | Dissent |
|---|---|---|---|---|
| Archaeologist | b | 7 | … | — |
| … |

**DECISION: {option}** — weighted {n} vs {m} vs {k}.
**Ruling ({Supervisor role}):** confirm / escalate / override → {option}, because … *(omit if no Supervisor)*
**Top dissent:** {the highest-confidence seat on the losing side, and its one line} — the one most worth listening to.

— Chair & Clerk: {Oracle name} (AI). Seats are prism lenses, not people. Rule 6.
```

## Rule 6 — lenses, never séances

- Seats are **archetypes**. They speak *as the Skeptic*, not as anyone who exists. Write "**Skeptic** —", never "I, Dieter Rams —". The same holds for the Supervisor and Specialist roles.
- If `--who` names a real practitioner, apply `/oracle-facet`'s rule at that seat: paraphrase a documented position, flag it as paraphrase, **never fabricate a quote**.
- The minute is signed by the Oracle as AI. It is not a record of a human meeting and must not read like one.
- Confidence must be honest. A seat that inflates to 9 to win the weighted vote corrupts the aggregate — the Chair says so in the minute if it sees it.

## Rules

1. **One agent, no subagents.** Every seat is the main agent transforming inline, in order. Same discipline as `/oracle-prism`.
2. **Turn by turn.** Once around the table per round, seating order, one turn each. No interjections, no seat speaking twice.
3. **Quorum 3, ceiling 7** among lens seats unless `--all`, which is 20 and compressed. Supervisor and Specialist sit on top of that count.
4. **Exactly four rounds**, fewer by early-stop, never more.
5. **No fetching mid-round.** Facts enter at convene or not at all.
6. **5 is forbidden at the vote.**
7. **Escalate rather than guess.** A tie or a values dissent goes to the human with the minute attached.
8. **Write the minute.** A roundtable that isn't recorded didn't happen (Nothing is Deleted).
9. **Surface the top dissent** next to the decision, always.
9b. **DNA names inheritance, never identity** — with `--dna` each seat declares its practitioners in OPEN and then speaks as the archetype. No first person as a real person, no fabricated quotes, in the room or in the minute.
10. **The Supervisor rules, it does not vote.** An override is never silent — the tally it overrode stays in the minute.

## Relationship to other skills

| Skill | Shape | Agents | Reach for it when |
|---|---|---|---|
| `/oracle-prism` | N lenses, one pass, no dialogue | 0 | you want angles, fast |
| `/oracle-facet` | one master, deep | 0 | you want one taste applied |
| `/roundtable` | N lenses, four rounds, a vote | 0 | you want a **decision** and the disagreement that produced it |
| `/adversarial-analysis` | 5 attacking one claim | 5 | being wrong is expensive |

## Open questions (carried from the spec)

1. Boy's actual prompt language is unrecovered — turn formats here are inferred from the known parameters, not transcribed. If the three original screenshots surface, revise this file; don't preserve it as canon.
2. Boy used 7 seats. Default here is 5 (prism's default). Whether 7 is the number or "3–8 is the range" is still his to say.
