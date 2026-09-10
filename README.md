# Soul Brews Studio — Skills

> Four agent skills for **thinking in more than one direction at once.**

```bash
npx skills@latest add Soul-Brews-Studio/skills
```

Every skill here is a single self-contained `SKILL.md`. No scripts, no
dependencies, nothing to build, **no subagents** — each one runs inline in the
agent you already have. They work in Claude Code and any of the
[80+ agents the `skills` CLI supports](https://github.com/vercel-labs/skills).

---

## Contents

- [Which one do I want?](#which-one-do-i-want)
- [Install](#install)
- [`/oracle-prism` — N lenses, one pass](#oracle-prism--n-lenses-one-pass)
- [`/oracle-facet` — one master, deep](#oracle-facet--one-master-deep)
- [`/oracle-roundtable` — the prism, seated](#oracle-roundtable--the-prism-seated)
- [`/plaeng-rang` — transform the method](#plaeng-rang--transform-the-method)
- [DNA — naming the real people](#dna--naming-the-real-people)
- [Rule 6 — the constraint that shapes all four](#rule-6--the-constraint-that-shapes-all-four)
- [Working in Thai](#working-in-thai)
- [Repository structure](#repository-structure)
- [Troubleshooting](#troubleshooting)
- [Where these came from](#where-these-came-from)
- [Contributing](#contributing)

---

## Which one do I want?

The four differ along two axes: **how many viewpoints**, and **do they talk to
each other**.

| | One viewpoint | Many viewpoints |
|---|---|---|
| **No dialogue** | [`/oracle-facet`](#oracle-facet--one-master-deep) — one master, five-part read | [`/oracle-prism`](#oracle-prism--n-lenses-one-pass) — N lenses, one section each |
| **Dialogue** | [`/plaeng-rang`](#plaeng-rang--transform-the-method) — you *become* the method | [`/oracle-roundtable`](#oracle-roundtable--the-prism-seated) — lenses answer each other, then vote |

Put another way:

| You want… | Reach for |
|---|---|
| "What am I missing?" | `/oracle-prism` |
| "What would Rams say about this page?" | `/oracle-facet` |
| "We have to choose, and being wrong is expensive." | `/oracle-roundtable` |
| "Solve this the way Musk would solve it." | `/plaeng-rang` |
| To *disprove* one specific claim | none of these — use an adversarial-analysis skill |

**The critical distinction**: `/oracle-facet` applies a master's **taste to your
artifact** — it critiques. `/plaeng-rang` adopts a master's **method to your
problem** — it builds. Facet judges; plaeng-rang works.

---

## Install

```bash
# everything
npx skills@latest add Soul-Brews-Studio/skills

# one skill
npx skills@latest add Soul-Brews-Studio/skills --skill oracle-prism

# see what's in here without installing anything
npx skills@latest add Soul-Brews-Studio/skills --list

# globally, for Claude Code, no prompts
npx skills@latest add Soul-Brews-Studio/skills --skill oracle-roundtable -g -a claude-code -y
```

> ### ⚠️ Watch the space
> `--skill oracle-prism` installs **one** skill.
> `--skill=oracle-prism` — with an equals sign — is accepted, ignored, and
> **silently installs all four**. Verified against `skills@1.5.25`. This applies
> to any repo you install with this CLI, not just ours.

**As a Claude Code plugin** — installs all four and keeps them updated together:

```
/plugin marketplace add Soul-Brews-Studio/skills
```

**Where files land**

| Scope | Flag | Location |
|---|---|---|
| Project | *(default)* | `./.claude/skills/<name>/SKILL.md` |
| Global | `-g` | `~/.claude/skills/<name>/SKILL.md` |

After installing, type `/oracle-prism` (or any of the four) in your agent. The
skills also self-trigger on their description phrases — say *"what am I
missing?"* and prism should offer itself.

---

## `/oracle-prism` — N lenses, one pass

One agent refracts a question through named lenses **in sequence**, producing one
section per lens. Same light, different colours. No lens answers another — that
is `/oracle-roundtable`'s job.

```
/oracle-prism                                    # analyse the current session
/oracle-prism "the rename migration"             # a specific topic
/oracle-prism --lenses 3                         # 3 instead of 5
/oracle-prism --preset design                    # a different lens set
/oracle-prism --custom "Security Auditor,Perf Engineer,UX Designer"
/oracle-prism --dna                              # each lens names its influences
/oracle-prism --tables                           # inventory mode
```

**Flags**

| Flag | Effect |
|---|---|
| `--lenses N` | 3–7 lenses. Default 5. Prose mode scales to 9–10 comfortably. |
| `--preset retro\|design\|incident\|designer` | Swap the whole lens set (below) |
| `--custom "A,B,C"` | Define your own lenses by name |
| `--dna` | Each lens declares the real practitioners whose method it runs |
| `--tables` | Force inventory style throughout instead of prose |

**The default five**

| # | Lens | Asks |
|---|---|---|
| 1 | 🔍 Archaeologist | What actually happened? Timeline, sequence, facts. |
| 2 | 🐛 Bug Hunter | What problems did we hit? What's still broken? |
| 3 | 💀 Skeptic | What did we do wrong? What would we redo? |
| 4 | 🏗️ Architect | What changed structurally? Before/after? |
| 5 | 📋 Auditor | What's left undone? What's inconsistent? |

**Presets**

| Preset | Lenses |
|---|---|
| `retro` | Historian · Critic · Cheerleader · Connector · Planner |
| `design` | User · Maintainer · Breaker · Simplifier · Integrator |
| `incident` | Firefighter · Detective · Defender · Forecaster · Builder |

**Output — prose by default.** One tight paragraph per lens, the pivot word
bolded inside the sentence, and a **bold verdict** closing each lens:

```markdown
### 💥 Lens 3: Breaker — "How can this fail?"
*DNA: Sidney Dekker (drift into failure) · Nancy Leveson (safety is a control problem)*

Nobody decided to hide the enrolment table — a guard written for a page **with**
data quietly became a lie on a page without it, then propagated by copy to six of
eight. **Breaker verdict**: six pages are drifting, and two don't contain the
string "not set" anywhere.
```

Tables are for genuine inventory — timelines, status lists, before/after,
per-file comparisons. A judgement ("is this confusing?") is prose; a count is a
table. Mixing is correct: table the Auditor, keep the Skeptic in prose.

**Rules it holds itself to**: evidence required (cite files, commits,
timestamps — no vague claims) · lenses are allowed to **disagree** and must not
be harmonised · a cross-lens summary at the end naming what several lenses
converge on.

---

## `/oracle-facet` — one master, deep

> A prism has many facets. This is one of them.

Summons **one** named practitioner as an analytical lens on **one** artifact.

```
/oracle-facet Steve Jobs on the multi-agent deck
/oracle-facet Dieter Rams on index.html
/oracle-facet Deming on our review loop
/oracle-facet ประชา สุวีรานนท์ on the Thai slides
/oracle-facet --roster                    # who's available
/oracle-facet Rams --harsh                # findings only, no encouragement
/oracle-facet Jobs on the deck --th       # answer in Thai
```

**Flags**

| Flag | Effect |
|---|---|
| `--harsh` | Cut "what they'd keep". Findings only. |
| `--th` | Answer in Thai (see [Working in Thai](#working-in-thai)) |
| `--roster` | Print the roster and stop |
| `--pair <name>` | Add a second master **who disagrees** — show the disagreement, don't harmonise it |

**The read, always in five parts** — then a sixth that is mandatory:

1. **What they'd notice first** — the single thing that would stop them, one sentence
2. **Why it matters to them** — the principle, traced to something they actually did or wrote
3. **What they'd cut** — the hardest part; name what goes and what survives
4. **What they'd keep** — real praise, or nothing
5. **The one change** — one concrete action, not a backlog
6. **Where this lens is blind** — what this master would get *wrong* about your situation

> Section 6 is what separates a lens from a fan letter. Every strong lens has a
> matching blindness. The skill refuses to skip it.

**Built-in roster** (you are not limited to it — any practitioner with a real,
checkable body of work is fair game):

| Domain | Masters |
|---|---|
| Product & taste | Steve Jobs · Dieter Rams · Jony Ive |
| Type & layout | Massimo Vignelli · Jan Tschichold · Josef Müller-Brockmann · Susan Kare |
| Colour & feeling | Van Gogh · Kenya Hara · Tibor Kalman |
| Systems & code | John Carmack · Rob Pike · Ken Thompson · Donald Knuth · Linus Torvalds |
| Quality & risk | W. Edwards Deming · Joseph Juran · Nassim Taleb · Sidney Dekker |
| Capital | Warren Buffett · Charlie Munger · Howard Marks · Morgan Housel |
| Story & brand | Seth Godin · Simon Sinek · Donald Miller |
| ไทย — ออกแบบ | ประชา สุวีรานนท์ · ศิลป์ พีระศรี · เฉลิมชัย โฆษิตพิพัฒน์ |
| ไทย — ภาษา | สราวุธ เฮ้งสวัสดิ์ (นิ้วกลม) · คึกฤทธิ์ ปราโมช |
| ไทย — ธุรกิจ | ตัน ภาสกรนที · กระทิง พูนผล · ท๊อป จิรายุส |

**It reads the actual artifact.** No reviewing from the filename. If it can't
open the thing, it says so and stops — a lens applied to an imagined artifact is
theatre.

---

## `/oracle-roundtable` — the prism, seated

> alias: `/roundtable` · `/round-table`

`/oracle-prism` gives you angles. `/oracle-roundtable` seats those same lenses at
one table and makes them **answer each other** — turn by turn, four rounds, then
a vote. Prism analyses; roundtable **decides**.

```
/oracle-roundtable "Should we ship 02 as the course page?"
/oracle-roundtable --preset design "Merge the eight landing pages into one?"
/oracle-roundtable --who "Skeptic,Maintainer,Planner" "Adopt the Algorithm everywhere?"
/oracle-roundtable --seats 7 --preset incident "Why did the deploy die at 18 of 28?"
/oracle-roundtable --all "Delete the two dangling references, or build it?"
/oracle-roundtable --super "Editor" --preset design "Which landing page ships?"
/oracle-roundtable --specialist "Tax Specialist" "Accept the 100M contract?"
/oracle-roundtable --options "build,delete,defer" --aggregator unanimity-or-escalate "…"
```

**Flags**

| Flag | Effect |
|---|---|
| `--seats N` | 3–7 lens seats. Quorum is 3 — with 2 it's a debate, with 1 a monologue |
| `--preset default\|retro\|design\|incident` | Which five lenses sit |
| `--who "A,B,C"` | Seat exactly these, by name, from any preset |
| `--all` | Seat all 20 lenses, with compressed turn budgets |
| `--super ROLE` | Add a **Supervisor** at the head of the table |
| `--specialist ROLE` | Add an invited **Specialist** in the last chair |
| `--dna` | Every seat declares its real-practitioner inheritance in OPEN |
| `--options "a,b,c"` | The canonical ballot. Derived from the question if omitted |
| `--aggregator weighted\|majority\|unanimity-or-escalate` | How the vote resolves. Default `weighted` |

### The four rounds

Each round goes **once around the table in seating order**. Every occupant speaks
once. No interjections, no seat speaking twice.

| Round | Name | What each seat produces |
|---|---|---|
| 1 | **OPEN** | Position · reasoning from its own question · confidence 1–10 · what would change my mind |
| 2 | **DEEPEN** | Names the **one seat it most disagrees with** and critiques it by name · a self-update, or `no change` |
| 3 | **CONVERGE** | The axis that decides its vote · its coalition · its **flip condition** |
| 4 | **VOTE** | Final vote · final confidence · a ≤140-char rationale · a dissent note if voting against the majority |

**Hard ceiling: four rounds.** There is no Round 5. A messy vote goes to the
human — that's what escalation is for.

**Early stop** — the Chair may skip to the vote if all seats hold the same
position at confidence ≥ 8, or if every seat said `no change` in Round 2 and no
new fact entered.

### The head of the table

| | `--super ROLE` — Supervisor | `--specialist ROLE` — Specialist |
|---|---|---|
| Sits | head of the table | last chair |
| Speaks | **last in every round** | last among the voting seats |
| OPEN | no position — states **what the table must not miss** | a position, from its domain |
| DEEPEN | may put **one question to one seat** — the only cross-turn allowed | may be questioned by up to two seats |
| CONVERGE | **names the disagreement axes** | declares its axis like any seat |
| VOTE | **does not vote.** After the tally: `confirm` / `escalate` / `override` | **votes**, confidence counted ×1 |

An **override** must cite a values violation or a fact on the record the table
ignored, and the tally it overrode stays in the minute. An override is never
silent. Expertise earns the Specialist the last word, not extra weight.

### The vote

| Aggregator | Rule |
|---|---|
| `weighted` *(default)* | Sum final confidence per option; highest wins |
| `majority` | Most votes wins; confidence reported, not weighted |
| `unanimity-or-escalate` | Every seat ≥ 7 on the same option, else `ESCALATE` |

**`5` is forbidden at the final vote** — pick 4 or 6. The fence is not a vote,
and forcing the lean is the point.

**It escalates rather than guessing.** No decision is returned when no option
holds ≥ 60% of weighted confidence, when a dissent note cites a values violation
(honesty, safety, consent), or when two seats sit at 10 on opposing sides. Ties
resolve by highest single confidence → fewest dissent notes → **escalate**.
Never auto-pick.

### The minute

Every roundtable writes `ψ/lab/roundtable/{date}_{slug}.md` — full transcript,
per-round, plus a vote table — and one line to `ψ/inbox/decisions/`. A roundtable
that isn't recorded didn't happen.

**The top dissent is always printed beside the decision**: the
highest-confidence seat on the *losing* side, because that's the one most worth
listening to.

---

## `/plaeng-rang` — transform the method

*แปลงร่าง* (plaeng-rang) — *transform*. Not "critique this as Musk would" but
**"solve this the way Musk solves things."** You take the method, not the man.

```
/plaeng-rang Elon Musk "our deploy takes 40 minutes"
/plaeng-rang Musk --algorithm "the onboarding flow"
/plaeng-rang Musk --audit "our AWS bill"
/plaeng-rang Deming "flaky test suite" --th
/plaeng-rang Musk --pair Deming "should we delete the staging environment?"
```

**Flags**

| Flag | Effect |
|---|---|
| `--algorithm` | Force all five steps explicitly, in order, each with a finding |
| `--audit` | Idiot-index pass over an existing system; report the worst three ratios |
| `--th` | Answer in Thai |
| `--pair <name>` | Add a master whose method **conflicts** (Elon ↔ Deming: delete fast vs. reduce variation). Show the conflict; don't resolve it prematurely |

**The flagship method — the Algorithm**, five steps, in this order, never
reordered:

1. **Make the requirements less dumb** — question every requirement, attach a *name* to each
2. **Delete the part or process** — if you're not adding back 10%, you're not deleting enough
3. **Simplify and optimise** — *only after step 2*; the common error is optimising a thing that shouldn't exist
4. **Accelerate cycle time**
5. **Automate** — last, not first

Plus **first principles** (boil to physics, reason up) and the **idiot index**
(a component's cost ÷ its raw-material cost).

> The skill names its own failure mode every run: deletion is cheap to admire and
> expensive to get wrong.

**Note on the name**: the skill's `name` is `plaeng-rang` (ASCII) so every agent
can create its directory — a Thai `name` installs as `unnamed-skill` on some.
Typing **แปลงร่าง** still triggers it; the word is the first thing in its
description.

---

## DNA — naming the real people

`--dna` (on `/oracle-prism` and `/oracle-roundtable`) makes each lens declare its
inheritance before it speaks: the named, documented practitioners whose method it
is running.

```markdown
**💥 Breaker** — *DNA: Sidney Dekker (drift into failure) · Nancy Leveson
(safety is a control problem) · Nassim Taleb (what is fragile)*
```

A persona that enumerates *which real humans contributed which traits* can be
**argued with** — you can go read Dekker and tell us the lens misread him. An
unattributed persona can only be agreed with or ignored.

A sample of the roster (20 lenses are covered in full inside the skill):

| Lens | DNA |
|---|---|
| 🔍 Archaeologist | Marc Bloch · Robert Caro · Edward Tufte |
| 🐛 Bug Hunter | John Carmack · Margaret Hamilton · Brian Kernighan |
| 💀 Skeptic | Richard Feynman · Nassim Taleb · Sidney Dekker |
| 🏗️ Architect | Christopher Alexander · Barbara Liskov · Rob Pike |
| 📋 Auditor | W. Edwards Deming · Joseph Juran · Atul Gawande |
| ✂️ Simplifier | Dieter Rams · John Maeda · Jony Ive |
| 🛡️ Defender | James Reason · Charles Perrow |
| 🔮 Forecaster | Philip Tetlock · Nate Silver |

---

## Rule 6 — the constraint that shapes all four

> **"Oracle Never Pretends to Be Human"** — born 12 January 2026

Three of these four skills invoke real, named people. **None of them impersonate
one.**

| Always | Never |
|---|---|
| *"Through the Rams lens:"* | *"As Dieter Rams, I think…"* |
| *"his position was roughly —"* (paraphrase, flagged) | a quote you cannot attribute |
| A seat speaks **as the archetype** | A seat speaks in first person as a person |
| The minute is signed by the agent as AI | The minute reads like a record of a human meeting |

A fabricated quote attributed to a real person is **the one unrecoverable
failure** of this family. If the skill isn't certain a quote is genuine, it
paraphrases and says so.

Every run closes with the standing caveat:

> *Lens, not verdict — {Master} did not review this. Named influences describe
> the angle taken, not endorsement, and not expertise transferred.*

---

## Working in Thai

All four are bilingual. `--th` switches the output to Thai, and it is written
*as Thai*, not translated English — topic fronted rather than SVO, conditions
first (`พอ… ก็…`), sentence boundaries carried by space rather than periods,
closure particles (`ด้วย`, `อยู่ดี`, `ต่างหาก`), zero anaphora instead of `มัน`,
and `ก็` for pacing.

Real quotes stay in their original language. Technical terms stay English, which
is what Thai technical writing actually does.

If you have a Thai-prose skill installed (something in the shape of
`kien-thai`), `--th` defers to it.

---

## Repository structure

```
.
├── .claude-plugin/
│   ├── plugin.json          # lists every skill path — update when adding one
│   └── marketplace.json     # makes this repo an installable CC plugin marketplace
├── skills/
│   ├── oracle/
│   │   ├── oracle-prism/SKILL.md
│   │   ├── oracle-facet/SKILL.md
│   │   └── oracle-roundtable/SKILL.md
│   └── thinking/
│       └── plaeng-rang/SKILL.md
├── CLAUDE.md                # instructions for agents working *on* this repo
├── LICENSE                  # MIT
└── README.md
```

Each `SKILL.md` carries YAML frontmatter — `name`, `description`, and usually
`argument-hint`. The `description` is what makes a skill self-trigger, so it
lists the phrases that should fire it *and* the ones that shouldn't (`Do NOT
trigger for…`).

---

## Troubleshooting

**`--skill=x` installed everything.** Use a space: `--skill x`. See
[the warning above](#install).

**A skill installed as `unnamed-skill`.** Its frontmatter `name` isn't usable as
a directory name — usually non-ASCII. Ours are all ASCII for this reason.

**The slash command doesn't appear.** Check the file landed at
`.claude/skills/<name>/SKILL.md` (project) or `~/.claude/skills/<name>/SKILL.md`
(global), and restart the agent so it re-reads the skill directory.

**It won't self-trigger from a phrase.** The `description` frontmatter drives
that. Invoke it explicitly by name once — that always works.

**Private repos.** The CLI uses your existing Git credentials, then GitHub CLI,
then SSH. `npx skills add owner/private-repo` works if any of those are
authenticated.

---

## Where these came from

Soul Brews Studio builds **Oracles** — repos that carry their own identity,
memory and working practice across sessions. These four are the analysis
instruments from that toolkit, extracted to stand alone with no dependency on the
rest of it.

`/oracle-roundtable` has a longer story than the others. It existed as an
unimplemented design spec written on 2026-05-16, inspired by a 7-agent, 4-round,
confidence-vote deliberation pattern observed in another practitioner's Oracle
family — and sat unbuilt for four months. Two live references pointed at a skill
that did not exist. It was finally built on 2026-09-08, keeping the spec's four
rounds, its 1–10 confidence scale with `5` forbidden, its three aggregators and
its escalation rules; changing only the occupants (prism's lenses instead of a
persona family) and the execution (inline instead of one subagent per persona).

The spec's own honesty note survives in the skill: the original prompt language
was never recovered, so the turn formats are **inferred from known parameters,
not transcribed**. If the originals surface, the skill should be revised — not
defended.

---

## Contributing

1. Add `skills/<category>/<name>/SKILL.md` with `name` + `description`
   frontmatter. ASCII `name`.
2. Add `"./skills/<category>/<name>"` to `.claude-plugin/plugin.json`.
3. Add a section to this README.
4. Verify discovery: `npx skills@latest add ./ --list`
5. Verify a real install into a scratch directory before opening a PR.

**House rules**: public repo, so no secrets, internal hostnames, personal emails
or private-repo paths — scan before every push. Rule 6 applies to any skill that
invokes real people. A skill is one self-contained `SKILL.md`; if it needs
scripts, it doesn't belong here yet.

---

## License

MIT — see [LICENSE](LICENSE). Use them, fork them, change them.

*Written by an AI, for agents, at Soul Brews Studio.*
