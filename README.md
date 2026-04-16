# Claude Skills

Personal Claude Code skills, kept under git so they can be synced across machines.

## Location

User-level Claude skills live at `~/.claude/skills/` on every Claude Code machine. Any folder here with a `SKILL.md` is auto-loaded at session start.

## Skills In This Repo

| Skill | Purpose |
|---|---|
| `fx-experts` | Chaired four-agent debate team (Atlas, Bosphorus, Flow, Vega) plus four on-call specialists (Ankara, Ledger, Strait, Meridian) for Turkish lira (TRY) depreciation-risk analysis. Analysis only, not financial advice. |
| `fx-tool-build` | Architecture and implementation guidance for building the local-first TRY risk research tool (Python + FastAPI + HTMX + SQLite). Separate from the analysis workflow. |
| `game-design-experts` | Chaired four-agent design workshop (Prism, Loop, Forge, Lantern) plus four on-call specialists (Relay, Cortex, Vector, Bastion) for product, game, onboarding, retention, and gamification design. |
| `deep-thinkers` | Chaired seven-persona historical roundtable (Sagan, Socrates, Coltrane, Marcus Aurelius, Leonardo, Terence Tao, Musk) plus twelve on-call thinkers for deep analysis, brainstorming, critical review, decision review, reflection, and technical research. |

## Design Principles

All skills follow these principles:

- **Easy to invoke.** No pre-staging, no mandatory inputs, no external packs to assemble. Just ask.
- **Use what's available.** Work with user-supplied context or the assistant's own knowledge. Web search is optional if something specific needs checking; no skill gates on external data.
- **Quick mode by default.** Each skill has a lightweight default path and a heavier "full roundtable / workshop" mode on explicit request.
- **Preserve dissent.** Minority views are reported, not smoothed over.
- **No refusals to run.** Thin evidence produces wider disagreement and lower confidence — not a refusal.
- **Actionable next moves only.** `recommended_next_moves` are things the user can do directly from the conversation or alone at their desk. Skills do not prescribe field research programs, multi-person studies, production telemetry setup, or anything that creates external dependencies.

## Sync To Another Machine Via Git

On a new machine:

```bash
# First time only:
cd ~/.claude
git clone <your-remote-url> skills

# Or, if ~/.claude/skills/ already exists:
cd ~/.claude/skills
git pull
```

Start a new Claude Code session and the skills are available.

## Adding A New Skill

1. Create a folder under `~/.claude/skills/<skill-name>/`.
2. Add `SKILL.md` with at minimum a frontmatter block containing `name` and `description`.
3. Optionally add `references/*.md` for detailed content Claude loads on demand.
4. Commit and push.

## Updating A Skill Across Machines

1. Edit on any machine.
2. `git commit` and `git push`.
3. On other machines: `git pull`, start a new Claude Code session.

## Skill Structure

```
<skill-name>/
  SKILL.md                 # Frontmatter + operating guide (auto-loaded by Claude)
  references/
    operating-spec.md      # Team design, rounds, output contract
    core-agent-profiles.md # Detailed per-agent profiles
    on-call-*.md           # Specialist overlays and activation rules
    prompt-templates.md    # Reusable prompts for cold invocation
    worked-example.md      # Compact end-to-end example
    export-pack.md         # How to share the skill with another Claude machine
    claude-export.md       # Standalone wrappers for bare-Claude contexts
    (additional skill-specific references)
```

Claude auto-loads `SKILL.md`. The `references/*.md` files are loaded on demand when SKILL.md points to them.
