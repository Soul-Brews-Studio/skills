---
name: oracle-prism
description: Multi-perspective analysis — one agent refracts through N named lenses in sequence, no subagents. Use when user says "prism", "oracle-prism", "multi-perspective", "look at this from different angles", "what am I missing", "did we miss anything", "critique this from N angles", or asks for a design/retro/incident review through several viewpoints. Presets - retro, design, incident, designer. Do NOT trigger for adversarial verification of a single claim (use /adversarial-analysis) or for spawning parallel agents (use /sonnet).
argument-hint: "[--lenses N] [--preset retro|design|incident|designer] [--custom \"A,B,C\"] [--tables] [--dna] [topic]"
---
# /oracle-prism — Multi-Perspective Analysis

> "แสงเดียวผ่านปริซึม แตกเป็นหลายสี — เรื่องเดียวกัน มองจากหลายมุม เห็นต่างกัน"

One agent, five perspectives, no subagents. Transform inline — shift between lenses to dig through work, decisions, or problems from angles that a single viewpoint would miss.

## Usage

```
/oracle-prism                        # Analyze current session (default)
/oracle-prism "the rename migration"  # Analyze a specific topic
/oracle-prism --lenses 3              # Use 3 lenses instead of 5
/oracle-prism --custom "Security Auditor,Performance Engineer,UX Designer"
/oracle-prism --tables                # inventory mode — tables instead of prose
/oracle-prism --dna                   # each lens names the real practitioners behind it
```

## How It Works

**No subagents.** The main agent transforms between perspectives sequentially, producing one section per lens. Each lens sees the same facts but asks different questions.

This is NOT adversarial analysis (which tries to disprove). This is **prismatic analysis** — same light, different colors.

## Default 5 Lenses

| # | Lens | Emoji | Question it asks |
|---|------|-------|-----------------|
| 1 | Archaeologist | `🔍` | "What actually happened? Timeline, sequence, facts." |
| 2 | Bug Hunter | `🐛` | "What problems did we hit? What's still broken?" |
| 3 | Skeptic | `💀` | "What did we do wrong? What would we redo?" |
| 4 | Architect | `🏗️` | "What changed structurally? What's the before/after?" |
| 5 | Auditor | `📋` | "What's left undone? What's inconsistent?" |

## DNA — the real people behind each lens

`--dna` makes each lens declare its inheritance before it speaks: the named,
documented practitioners whose method it is running. Boy Pinyo's distillation
pattern — a persona that enumerates *which real humans contributed which traits*
is more honest than a persona that is an unattributed blob.

**Rule 6 governs this absolutely.** The lens speaks **as the archetype**, never
as the person. Write `**💀 Skeptic** — DNA: Feynman (don't fool yourself) · …`
and then reason. Never `As Feynman, I…`. Never a quote you cannot attribute. If
a documented position is being paraphrased, say *paraphrase*. For one named
master applied in depth, that is `/oracle-facet`, not this.

| Lens | DNA — what each contributes |
|---|---|
| 🔍 Archaeologist | **Marc Bloch** (evidence before narrative) · **Robert Caro** (exhaust the record) · **Edward Tufte** (show the data, not the claim) |
| 🐛 Bug Hunter | **John Carmack** (run it, measure it) · **Margaret Hamilton** (error handling is the system) · **Brian Kernighan** (debugging is harder than writing) |
| 💀 Skeptic | **Richard Feynman** (the first principle is not to fool yourself) · **Nassim Taleb** (what is fragile) · **Sidney Dekker** (blame hides cause) |
| 🏗️ Architect | **Christopher Alexander** (patterns, not parts) · **Barbara Liskov** (substitutability) · **Rob Pike** (simplicity is the design) |
| 📋 Auditor | **W. Edwards Deming** (the system produces the result) · **Joseph Juran** (the vital few) · **Atul Gawande** (the checklist catches the obvious) |
| 👤 User | **Don Norman** (affordance and signifier) · **Jakob Nielsen** (heuristics) · **Susan Kare** (recognisable at a glance) |
| 🔧 Maintainer | **Michael Feathers** (legacy is code without tests) · **Barbara Liskov** (contracts survive people) · **Rob Pike** |
| 💥 Breaker | **Sidney Dekker** (drift into failure) · **Nancy Leveson** (safety is a control problem) · **Nassim Taleb** |
| ✂️ Simplifier | **Dieter Rams** (as little design as possible) · **John Maeda** (laws of simplicity) · **Jony Ive** (reduce toward inevitable) |
| 🔗 Integrator | **Massimo Vignelli** (one system, everywhere) · **Kenya Hara** (the whole context) · **Tim Berners-Lee** (interoperate) |
| 📜 Historian | **Marc Bloch** · **Robert Caro** |
| ✏️ Critic | **Pauline Kael** (say what you actually think) · **Jane Jacobs** (observe before theorising) |
| 📣 Cheerleader | **Tom Peters** (celebrate what works) · **Teresa Amabile** (progress is the motivator) |
| 🧩 Connector | **James Burke** (connections across domains) · **Steven Johnson** (the adjacent possible) |
| 🎯 Planner | **Andy Grove** (output, not activity) · **Dwight Eisenhower** (planning over plans — paraphrase of a documented remark) |
| 🚒 Firefighter | **Richard Cook** (how complex systems fail) · **Gene Kranz** (work the problem) |
| 🔎 Detective | **Sidney Dekker** · **Nancy Leveson** |
| 🛡️ Defender | **James Reason** (the Swiss cheese model) · **Charles Perrow** (normal accidents) |
| 🔮 Forecaster | **Philip Tetlock** (calibrate, then score) · **Nate Silver** (signal vs noise) |
| 🧱 Builder | **Taiichi Ohno** (stop the line, fix the cause) · **W. Edwards Deming** |

Named influences describe the angle taken — not endorsement, not expertise
transferred, and not a claim that anyone reviewed this.

## Alternate Lens Sets

Use `--custom` to define your own, or pick a preset:

### `--preset retro` (session retrospective)
| Lens | Question |
|------|----------|
| Historian | What happened, in what order? |
| Critic | What went poorly or slowly? |
| Cheerleader | What went well? What should we repeat? |
| Connector | What patterns connect to past work? |
| Planner | What's the next move? |

### `--preset design` (design review)
| Lens | Question |
|------|----------|
| User | Is this easy to use? What's confusing? |
| Maintainer | Is this easy to change later? |
| Breaker | How can this fail? Edge cases? |
| Simplifier | What can be removed? |
| Integrator | How does this fit with everything else? |

### `--preset incident` (post-incident)
| Lens | Question |
|------|----------|
| Firefighter | What happened and how was it fixed? |
| Detective | What was the root cause chain? |
| Defender | What guards existed? Why didn't they catch it? |
| Forecaster | What similar things could happen next? |
| Builder | What systemic fix prevents recurrence? |

## Output Format

**Prose by default.** One tight paragraph per lens. Bold the pivot word inside
the sentence, and close each lens with a **bold verdict** — the one line someone
would quote back. This is what lets a prism carry 7–10 lenses without becoming a
spreadsheet.

```markdown
### 🔍 Lens 1: Archaeologist — "What happened?"
*DNA: Bloch (evidence before narrative) · Caro (exhaust the record)*  ← only with --dna

The rename landed in three passes, not one — `a1b2c3` moved the files, `d4e5f6`
fixed the imports it broke, `g7h8i9` caught the two it missed. The gap between
them is where the **stale references** survived. **Archaeologist verdict**: the
migration is done, its cleanup is not.

### 🐛 Lens 2: Bug Hunter — "What broke?"
[one paragraph, same shape]

### 💀 Lens 3: Skeptic — "What went wrong?"
[…]

---

**Cross-lens summary:** [2-3 sentences on what multiple lenses converge on]
```

**Reach for a table only when the content is genuinely inventory** — a timeline,
a status list, a before/after, a per-file comparison. A judgement ("is this
confusing?", "is the voice consistent?") is prose; a count is a table. Mixing is
fine: table the Auditor, keep the Skeptic in prose.

`--tables` forces the inventory style throughout, for when the whole subject is
a list.

## Rules

1. **No subagents** — all lenses run in the main agent, sequentially
2. **Each lens gets a section** with its emoji, name, and guiding question as header
3. **Evidence required** — cite files, commits, commands, timestamps. No vague claims
4. **Lenses disagree** — if the Architect says "clean" but the Auditor says "incomplete", show both. Don't harmonize
5. **Cross-lens summary at the end** — what do multiple lenses converge on?
6. **Prose over tables** — one paragraph per lens, bold pivot, bold verdict. Tables only for genuine inventory (timelines, status lists, before/after), or throughout with `--tables`
7. **Session context by default** — if no topic given, analyze the current session's work
7b. **DNA is inheritance, not impersonation** — with `--dna`, name the practitioners in a one-line italic under the header, then reason as the archetype. Rule 6: never first person as a real person, never a fabricated quote
8. **3-7 lenses** — minimum 3, maximum 7. Default 5. Use `--lenses N` to adjust. Prose scales further than tables do; 9-10 lenses is workable in prose mode

## When to Use

| Situation | Why prism helps |
|-----------|----------------|
| End of session | Catch what you missed before closing |
| After a migration/rename | Find inconsistencies across the change |
| Design decision | See tradeoffs from user/maintainer/breaker angles |
| Post-incident | Structured multi-angle without blame |
| "Did we miss anything?" | The Auditor lens exists for this |

## Relationship to Other Skills

| Skill | Pattern | Agents |
|-------|---------|--------|
| `/oracle-prism` | Multi-perspective, same agent | 0 (inline transform) |
| `/adversarial-analysis` | Try to disprove a claim | 5 parallel subagents |
| `/rrr` | Session retrospective | 0 (or 5 in --deep) |
| `/roundtable` | Discussion between personas | 0 (inline) |

Prism is the **lightest** multi-perspective tool — no agents, no spawning, no coordination overhead. Use it when you want angles, not adversaries.
