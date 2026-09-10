# Soul Brews Studio — Skills

Public repo of standalone agent skills, installable via
`npx skills@latest add Soul-Brews-Studio/skills`.

## Layout

`skills/<category>/<skill-name>/SKILL.md` — one self-contained file per skill.
`.claude-plugin/plugin.json` lists every skill path; `marketplace.json` makes
the repo an installable Claude Code plugin marketplace.

## Adding a skill

1. `skills/<category>/<name>/SKILL.md` with YAML frontmatter (`name`,
   `description`, optional `argument-hint`)
2. Add `"./skills/<category>/<name>"` to `.claude-plugin/plugin.json`
3. Add a section to `README.md`
4. Verify: `npx skills@latest add ./  --list`

## Rules

- **Public repo.** No secrets, no internal hostnames, no personal emails, no
  private-repo paths. Scan before every push.
- **Rule 6.** Skills that invoke real people name them as *influences* and never
  write first person as them. Never a fabricated quote.
- **Self-contained.** A skill is one `SKILL.md`. If it needs scripts, it doesn't
  belong here yet.
