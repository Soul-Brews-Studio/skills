# Soul Brews Studio — Skills

Agent skills for **thinking in more than one direction at once**. Four of them,
all inline: no subagents, no spawning, no coordination overhead. They work in
Claude Code and any of the [80+ agents the `skills` CLI supports](https://github.com/vercel-labs/skills).

```bash
npx skills@latest add Soul-Brews-Studio/skills
```

## The four

| Skill | Shape | Reach for it when |
|---|---|---|
| **`/oracle-prism`** | N lenses, one pass, no dialogue | you want angles fast — "what am I missing?" |
| **`/oracle-facet`** | one named master, deep, on one artifact | you want one person's taste applied |
| **`/roundtable`** | those lenses seated, 4 rounds, a vote | you want a **decision** and the disagreement that produced it |
| **`/แปลงร่าง`** | adopt a master's reasoning *method* | you want to solve it their way, not be critiqued by them |

### `/oracle-prism` — N lenses, one pass

One agent refracts a question through named lenses in sequence — Archaeologist,
Bug Hunter, Skeptic, Architect, Auditor by default, or a `--preset` for retro /
design / incident reviews. Prose by default, tables when the content is genuinely
inventory. `--dna` makes each lens declare the real practitioners whose method it
runs.

```bash
npx skills@latest add Soul-Brews-Studio/skills --skill=oracle-prism
```

### `/oracle-facet` — one master, deep

Summons a single named practitioner as an analytical lens on one artifact. Five
parts, always: what they'd notice first · why it matters to them · what they'd
cut · what they'd keep · the one change. Then the part that separates a lens
from a fan letter — **where this lens is blind**.

```bash
npx skills@latest add Soul-Brews-Studio/skills --skill=oracle-facet
```

### `/roundtable` — the prism, seated

Prism gives you angles; roundtable gives you a decision. Seat 3–20 lenses at one
table and make them answer each other, turn by turn, across four rounds —
OPEN → DEEPEN → CONVERGE → VOTE — then vote with numeric confidence (`5` is
forbidden at the vote; the fence is not a vote). `--super` seats a non-voting
Supervisor who names the axes and rules after the tally; `--specialist` seats an
invited expert. Escalates to you rather than crowning a plurality.

```bash
npx skills@latest add Soul-Brews-Studio/skills --skill=roundtable
```

### `/แปลงร่าง` — transform the method

*plaeng-rang* — transform. Not "critique this as Musk would" but "solve this the
way Musk solves things": the Algorithm, first principles, the idiot index.
Bilingual EN/ไทย.

```bash
npx skills@latest add Soul-Brews-Studio/skills --skill=plaeng-rang
```

> **Note**: the skill's `name` is `plaeng-rang` (ASCII) so every agent can create
> its directory — a Thai `name` installs as `unnamed-skill` on some agents.
> Typing **แปลงร่าง** still triggers it: the word is the first thing in its
> description.

## Install

```bash
# everything
npx skills@latest add Soul-Brews-Studio/skills

# one skill
npx skills@latest add Soul-Brews-Studio/skills --skill=oracle-prism

# see what's in here without installing
npx skills@latest add Soul-Brews-Studio/skills --list

# globally, for Claude Code, no prompts
npx skills@latest add Soul-Brews-Studio/skills --skill=roundtable -g -a claude-code -y
```

As a Claude Code plugin:

```
/plugin marketplace add Soul-Brews-Studio/skills
```

## The rule that shapes all four

> **Rule 6 — never pretend to be human.**
> Born 12 January 2026.

Three of these skills invoke real, named people. None of them impersonate one.
A lens says *"Through the Rams lens:"*, never *"As Dieter Rams, I think…"*.
A quote appears only when it is real and attributable; otherwise the skill
paraphrases and says so. A fabricated quote attributed to a real person is the
one unrecoverable failure of this family.

Named influences describe the angle taken — not endorsement, not expertise
transferred, and not a claim that anyone reviewed your work.

## Structure

```
skills/
├── oracle/
│   ├── oracle-prism/SKILL.md
│   ├── oracle-facet/SKILL.md
│   └── roundtable/SKILL.md
└── thinking/
    └── plaeng-rang/SKILL.md
```

Each skill is a single self-contained `SKILL.md`. No scripts, no dependencies,
nothing to build.

## Where these came from

Soul Brews Studio builds **Oracles** — repos that carry their own identity,
memory and working practice across sessions. These four are the analysis
instruments from that toolkit, extracted to stand alone.

`/roundtable` has a longer story than the others: it existed as an unimplemented
design spec from 2026-05-16, inspired by a 7-agent, 4-round confidence-vote
deliberation pattern, and sat unbuilt until 2026-09-08.

## License

MIT — see [LICENSE](LICENSE).
