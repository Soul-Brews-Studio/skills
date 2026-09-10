---
name: oracle-facet
description: One master, deep — summon a single named expert as an analytical lens on your work. Use when user says "facet", "oracle-facet", "what would <name> say", "look at this as <name>", "one expert not a panel", "critique as Steve Jobs / Rams / Deming", or names a single practitioner they want a read from. Bilingual EN/ไทย. Do NOT trigger for a panel debate (use /debate), for N lenses in one pass (use /oracle-prism), or for disproving a claim (use /adversarial-analysis).
argument-hint: "<master> [on <what>] [--th] [--harsh] [--roster]"
---

# /oracle-facet — one master, deep

> alias: `/facet`

> A prism has many facets. This is one of them.
>
> `/oracle-prism` gives you N angles fast. `/debate` seats a board that argues.
> `/oracle-facet` gives you **one** practitioner, at depth, on one thing.

## Usage

```
/oracle-facet Steve Jobs on the multi-agent deck
/oracle-facet Dieter Rams on index.html
/oracle-facet Deming on our review loop
/oracle-facet ประชา สุวีรานนท์ on the Thai slides
/oracle-facet --roster                      # who is available
/oracle-facet Rams --harsh                  # no encouragement, findings only
/oracle-facet Jobs on the deck --th         # answer in Thai
```

## Rule 6 — this is a lens, not a séance

**Never write as the person.** Do not open with "I'm Steve Jobs". Do not put
words in their mouth as if quoted. You are Claude applying a documented lens.

Say *"Through the Jobs lens:"* — never *"As Steve Jobs, I think…"*

Signature quotes are allowed **only** when they are real and attributable.
If you are not certain a quote is genuine, paraphrase and say so:
*"his position was roughly —"*. A fabricated quote attributed to a real
person is the one unrecoverable failure of this skill.

Close every run with the standing caveat (see Step 5).

## Step 0 — timestamp, then look for a profile library

This skill is **self-contained**: it works with nothing installed. But if a
persona library happens to be present, researched profiles beat a summary, so
check a few conventional places rather than assuming one:

```bash
date "+🕐 %H:%M %Z (%A %d %B %Y)"

# NB: run this under bash with nullglob. zsh treats an unmatched glob as a
# FATAL error ("no matches found") and aborts the whole block — bash only
# skips it. Most users are on zsh, so do not drop the wrapper.
bash -c 'shopt -s nullglob
for d in ${FACET_PROFILES:-} \
         "$HOME"/.claude/skills/*/consultants \
         "$HOME"/.claude/skills/*/personas \
         "$HOME"/.claude/personas \
         ./consultants ./personas ./.claude/skills/*/consultants; do
  [ -d "$d" ] || continue
  echo "profiles: $d"
  ls "$d" | sed "s/\.md$//"
done'
```

Found nothing? That is the normal case — carry on with the roster below and do
not mention the absence. Only say something if the user names a master you
cannot ground.

`--roster` → print whatever you found plus the built-in roster, then stop.

## Step 1 — resolve the master

Three sources, in order of preference. **You are not limited to the roster.**

**1. A profile library, if one turned up.** Exact then fuzzy match. Prefer it —
researched profiles carry frameworks, real decisions and documented blind spots
you would otherwise approximate.

**2. Your own knowledge.** For a well-documented practitioner you already know
well — their books, talks, shipped work, decisions — just use it. Most masters
worth invoking fall here. Do not stall on a search you do not need.

**3. WebSearch, when your knowledge is thin or stale.** Reach for it when:

- you know the name but not their *method* in usable detail
- the work is recent, or post-dates what you are confident about
- you are about to quote them and want the wording right
- the user names someone regional, contemporary, or niche — a Thai founder, a
  working designer, someone with no biography

Search for their **frameworks, principles and documented decisions** — not
trivia. Two or three good sources is enough. Say in one line that you looked
things up, then get on with the read.

**The roster is a starting point, not a whitelist.** Any practitioner with a
real, checkable body of work is fair game — living or dead, famous or not,
any country.

**If all three fail, stop.** Fictional characters, anonymous "experts", and
people you only know by reputation cannot be grounded. Say so plainly and offer
the nearest master you *can* ground. Never invent a persona — an invented lens
produces confident advice with nothing underneath it.

### Built-in roster (always available)

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

## Step 2 — read the actual thing

Do not review from memory or from the filename. Open it.

- A file or URL → read it
- A deck or page → serve and look at it (`file://` breaks hash nav; use http)
- A decision or plan → restate it in one sentence and get agreement first

If you cannot see the artifact, say so and stop. A lens applied to an
imagined artifact is theatre.

## Step 3 — the read, in five parts

Always these five, in this order:

```markdown
## Through the {Master} lens — {artifact}

**What they'd notice first.** The single thing that would stop them, in one
sentence. Not a list.

**Why it matters to them.** The principle underneath — named, and traced to
something they actually did or wrote.

**What they'd cut.** The hardest part. Name what goes, and what survives.
Be specific: this line, this slide, this component.

**What they'd keep.** Real praise, or nothing. If nothing is good, say
nothing is good.

**The one change.** A single concrete action you could take today. Not three
options — one.
```

Then:

```markdown
**Where this lens is blind.** What this master would get wrong about your
situation. Every strong lens has a matching blindness — name it.
```

That last section is mandatory. It is what separates a lens from a fan letter.

## Step 4 — flags

| Flag | Effect |
|---|---|
| `--harsh` | Cut "what they'd keep". Findings only. Use when you already know it works. |
| `--th` | Answer in Thai. Follow `kien-thai` if installed — topic first, conditions first, closure particles, no mid-paragraph periods. Keep signature quotes in original English. |
| `--roster` | Print the roster and stop. |
| `--pair <name>` | Add a second master **who disagrees**, and show the disagreement. Do not harmonise. Beyond two, use `/debate`. |

## Step 5 — close honestly

End every run with:

> Lens, not verdict — {Master} did not review this. Named influences describe
> the angle taken, not endorsement, and not expertise transferred.

## Rules

1. **One master.** Two only with `--pair`. Three or more → `/debate`.
2. **Read the artifact.** No review from the filename.
3. **Real quotes or none.** Uncertain → paraphrase and flag it.
4. **Name the blindness.** Every run, no exceptions.
5. **One change, not a backlog.** The value is the choice of what matters most.
6. **Never write in first person as the master.** Rule 6.

## Relationship to other skills

| Skill | Shape | Agents | Use when |
|---|---|---|---|
| `/oracle-facet` | one master, deep | 0 | you want a considered read from one point of view |
| `/oracle-prism` | N lenses, one pass | 0 | you want breadth fast, and to stop tunnelling |
| `/debate` | 2–4 debating | 0 | you want the disagreement itself |
| `/adversarial-analysis` | 5 attacking one claim | 5 | being wrong is expensive |

Facet is the cheapest and the narrowest. Reach for it when the problem is
already framed and you want one person's taste applied to it — not a survey.
