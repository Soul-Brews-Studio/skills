---
name: แปลงร่าง
description: แปลงร่าง (plaeng-rang) — transform your REASONING METHOD into a named master's, then solve the problem with it. Elon Musk is the flagship (the Algorithm, first principles, idiot index). Use when user says "แปลงร่าง", "plaeng-rang", "transform", "think like Elon / Musk / <master>", "solve this like <name> would", "bring <name>'s DNA", "first principles this", "apply the algorithm". Bilingual EN/ไทย. Do NOT trigger for a critique of an existing artifact (use /oracle-facet), a panel debate (use /debate), or N lenses in one pass (use /oracle-prism).
argument-hint: "<master> <problem> [--th] [--algorithm] [--audit]"
---

# /แปลงร่าง

> alias: `plaeng-rang`

> **แปลงร่าง = transform.** Not "who would review this" — *"how would they think
> through it."*
>
> `/oracle-facet` points a master **at your work**. This puts their **method in your
> hands** and then does the work with it.

## Usage

```
/แปลงร่าง elon — ทำไม deck build ช้า
/แปลงร่าง elon on our multi-agent deck pipeline
/แปลงร่าง elon --algorithm         # run the 5 steps explicitly, in order
/แปลงร่าง elon --audit             # idiot index on an existing system
/แปลงร่าง deming on our review loop
/แปลงร่าง carmack on the render path --th
```

## Rule 6 — you take the method, not the man

**You are Claude reasoning with a documented method.** You are not Elon Musk.

- ✅ *"First principles: what is physically required here?"*
- ✅ *"Running the Algorithm on this —"*
- ❌ *"I'm Elon. Here's what I'd do."*
- ❌ Inventing a quote, a tweet, or an opinion he has not expressed

Real, attributable quotes only. Uncertain → paraphrase and mark it.
**A fabricated quote attributed to a living person is the one unrecoverable
failure of this skill.**

## Step 0 — ground the method

```bash
date "+🕐 %H:%M %Z (%A %d %B %Y)"
# NB: run under bash with nullglob. zsh treats an unmatched glob as a FATAL
# error ("no matches found") and aborts the block — bash only skips it.
# Most users are on zsh, so do not drop the wrapper.
bash -c 'shopt -s nullglob
for d in ${FACET_PROFILES:-} \
         "$HOME"/.claude/skills/*/personas \
         "$HOME"/.claude/skills/*/consultants \
         "$HOME"/.claude/personas \
         ./personas ./consultants; do
  [ -d "$d" ] || continue
  echo "profiles: $d"
  ls "$d" | sed "s/\.md$//"
done'
```

Three sources, in order of preference. **You are not limited to what ships here.**

**1. A profile library, if one turned up.** Prefer it — researched frameworks
and documented decisions beat recollection.

**2. Your own knowledge.** For a practitioner whose method you already know in
usable detail, just use it. Do not stall on a search you do not need.

**3. WebSearch, when your knowledge is thin or stale.** Reach for it when you
know the name but not the *method*, when the work is recent, when you are about
to quote them, or when the user names someone regional or niche. Search for
frameworks, principles and real decisions — not trivia. Say in one line that
you looked things up, then run the method.

**If all three fail, stop.** A method you cannot ground is not a method. Say so
and offer the nearest one you can.

## Step 1 — the flagship method: Elon Musk

Source: Isaacson biography; born in Tesla production hell.

### The Algorithm — five steps, **in this order, never reordered**

| # | Step | The trap it exists to prevent |
|---|---|---|
| 1 | **Question every requirement.** Each must come with a **person's name** — not "the legal department". | *"Requirements from smart people are the most dangerous"* — nobody questions them. |
| 2 | **Delete any part or process you can.** | *"If you do not end up adding back at least 10%, you didn't delete enough."* Under-deleting is the norm. |
| 3 | **Simplify and optimise.** Only after 2. | *"A common mistake is to simplify a part that should not exist."* |
| 4 | **Accelerate cycle time.** Only after 1–3. | Speeding up something that shouldn't exist. |
| 5 | **Automate.** Always last. | *"The big mistake was trying to automate every step first."* |

**Doing these out of order is the failure mode the Algorithm exists to
prevent.** If you catch yourself automating first, stop and go back to 1.

### First principles

Boil the problem to physics or arithmetic that must be true, then reason up.
Never reason from analogy ("everyone does it this way") — that inherits
someone else's constraints.

### The idiot index

`cost of finished part ÷ cost of its raw materials`

A high index means the problem is design or process, not procurement. Applies
beyond hardware: **time spent ÷ irreducible time required.**

### The rest

- **"The best part is no part."** The corollary of step 2.
- **"Take the approach that you're wrong."** Actively seek the disproof.
- **5 Whys** to reach root cause before touching anything.

## Step 2 — transform, then do the work

Do not describe the method. **Run it.**

```markdown
## แปลงร่าง: {Master} → {problem}

**The problem, restated in their terms.** One sentence. For Elon: what is
physically or arithmetically required, stripped of convention.

**Running the method.**
  — For Elon with --algorithm, all five steps in order, each with a real
    finding from the actual system. Name a person for every requirement.
  — Otherwise, the master's own loop applied step by step.

**What this deletes.** The concrete list. Files, steps, meetings, components.

**What survives, and why.** Including the ≥10% you expect to add back.

**Do this first.** One action, today.

**Where this method breaks.** Mandatory — see below.
```

## Step 3 — name the failure mode

Every method has one. Never omit this section.

**Elon's, specifically:**
- **Timelines.** Chronically optimistic — "Elon time" is a documented pattern.
- **People cost.** The Algorithm optimises systems; it under-weights what the
  surge costs the humans running it.
- **Over-deletion.** Step 2 taken past the point of safety margin. He rebuilt
  deleted things more than once.
- **Analogy has uses.** First principles is expensive; sometimes convention
  encodes hard-won knowledge you'd pay to relearn.

## Step 4 — flags

| Flag | Effect |
|---|---|
| `--algorithm` | Force all five steps explicitly, in order, each with a finding. |
| `--audit` | Idiot index pass over an existing system. Report the worst three ratios. |
| `--th` | Answer in Thai. Follow `kien-thai` — topic first, conditions first, closure particles, no mid-paragraph periods. Keep real quotes in original English. |
| `--pair <name>` | Add a master whose method **conflicts** (Elon ↔ Deming: delete fast vs. reduce variation). Show the conflict; do not resolve it prematurely. |

## Step 5 — close honestly

> แปลงร่าง = method, not identity. {Master} did not write this and has not
> reviewed it. Named influences describe the reasoning applied, not
> endorsement, and not expertise transferred.

## Rules

1. **Run the method, don't summarise it.** Output is the work, not a lecture.
2. **Order is the method.** For the Algorithm, never reorder or skip.
3. **Every requirement gets a name.** "The system requires it" is not an answer.
4. **Real quotes or none.**
5. **Name the failure mode.** Every run.
6. **Never first person as the master.** Rule 6.
7. **One master.** Two only with `--pair`. More → `/debate`.

## Relationship to other skills

| Skill | What it does | Direction |
|---|---|---|
| `/แปลงร่าง` | adopt their **method**, then solve | inward — you change |
| `/oracle-facet` | one master reviews **your artifact** | outward — they judge |
| `/oracle-prism` | N lenses, one pass, no debate | breadth |
| `/debate` | 2–4 personas argue | disagreement |

facet asks *"what would they say about this?"*
แปลงร่าง asks *"how would they have built it in the first place?"*
