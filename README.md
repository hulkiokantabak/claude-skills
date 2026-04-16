# Claude Skills

Personal Claude Code skills — four chaired multi-agent workflows I use regularly, kept under git so they sync across machines.

If you're landing here from GitHub: these are [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) skills. Claude Code auto-loads any folder under `~/.claude/skills/` that contains a `SKILL.md`. You can clone this repo into your own `~/.claude/skills/` to use the same workflows, or fork it as a starting point for your own skills.

Everything here is released under [CC0](LICENSE) — use, fork, remix, no attribution required.

## The Skills

| Skill | Purpose |
|---|---|
| [`fx-experts`](./fx-experts) | Chaired four-agent debate team (Atlas, Bosphorus, Flow, Vega) plus four on-call specialists (Ankara, Ledger, Strait, Meridian) for Turkish lira (TRY) depreciation-risk analysis. Produces probability curves, watch triggers, minority views. Analysis only, not financial advice. |
| [`fx-tool-build`](./fx-tool-build) | Architecture and implementation guidance for building the local-first TRY risk research tool (Python + FastAPI + HTMX + SQLite). Separate from the analysis workflow. |
| [`game-design-experts`](./game-design-experts) | Chaired four-agent design workshop (Prism, Loop, Forge, Lantern) plus four on-call specialists (Relay, Cortex, Vector, Bastion) for product, game, onboarding, retention, and gamification design. |
| [`deep-thinkers`](./deep-thinkers) | Chaired seven-persona historical roundtable (Sagan, Socrates, Coltrane, Marcus Aurelius, Leonardo, Terence Tao, Musk) plus twelve on-call thinkers for deep analysis, brainstorming, critical review, decision review, reflection, and technical research on any subject. |

## Design Principles

All skills follow these principles:

- **Easy to invoke.** No pre-staging, no mandatory inputs, no external packs to assemble. Just ask.
- **Use what's available.** Work with user-supplied context or the assistant's own knowledge. Web search is optional if something specific needs checking; no skill gates on external data.
- **Quick mode by default.** Each skill has a lightweight default path and a heavier "full roundtable / workshop" mode on explicit request.
- **Preserve dissent.** Minority views are reported, not smoothed over.
- **No refusals to run.** Thin evidence produces wider disagreement and lower confidence — not a refusal.
- **Actionable next moves only.** `recommended_next_moves` are things the user can do directly from the conversation or alone at their desk. Skills do not prescribe field research programs, multi-person studies, production telemetry setup, or anything that creates external dependencies.

## Install

On any machine where you run Claude Code:

```bash
# First time — clone into ~/.claude/skills
cd ~/.claude
git clone https://github.com/hulkiokantabak/claude-skills.git skills

# Updates — on any machine
cd ~/.claude/skills
git pull
```

Start a new Claude Code session. The skills are auto-loaded and available by name (e.g. "run deep-thinkers on this brief") or via the Skill tool.

If `~/.claude/skills/` already exists on the target machine and contains other skills, copy the folders you want instead of cloning over the top:

```bash
git clone https://github.com/hulkiokantabak/claude-skills.git /tmp/claude-skills
cp -r /tmp/claude-skills/{fx-experts,fx-tool-build,game-design-experts,deep-thinkers} ~/.claude/skills/
```

## Invoking A Skill

Once installed, Claude auto-loads each `SKILL.md` on session start and triggers when the conversation matches a description. You can also:

- Mention the skill by name (e.g. "run deep-thinkers on this brief").
- Call the `Skill` tool directly with the skill name.
- Pick it from the skills picker if your Claude surface offers one.

Each skill has an `## Example Prompts` section in its `SKILL.md` showing both triggering and non-triggering examples.

## Running Without Claude Code

If you want to run one of these workflows in a Claude context that doesn't support skills (bare API call, Claude Desktop without skills, another LLM entirely), open the skill's `references/export-pack.md` and paste the "Portable Core Bundle" block, then a wrapper from `references/claude-export.md`.

## Adding A New Skill

1. Create a folder under this repo: `<skill-name>/`.
2. Add `SKILL.md` with at minimum a frontmatter block containing `name` and `description`.
3. Optionally add `references/*.md` for detailed content Claude loads on demand.
4. Commit and push.

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

Claude auto-loads `SKILL.md`. The `references/*.md` files are loaded on demand when `SKILL.md` points to them.

## Provenance

These skills started as Codex-targeted workflows and were adapted to Claude in April 2026. Then each skill was used to review itself and the others — `deep-thinkers` ran a meta-review of all three, `game-design-experts` proposed invocation-UX improvements, and `fx-experts` self-reviewed its scope and protocol. Recommendations from each self-review were applied inline. Cold spot-tests confirmed each skill produces real, useful output when invoked with minimal context.

## License

[CC0 1.0 Universal](LICENSE) — effectively public domain. Use, fork, remix, modify, redistribute. No attribution required.
