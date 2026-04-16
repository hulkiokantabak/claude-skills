# Export Pack

## Purpose

Use this pack to share `fx-experts` with:
- another computer running Claude Code,
- any other Claude surface that supports skills (Claude API, Claude Desktop with skills, Agent SDK projects),
- any environment that can accept a plain prompt bundle when full skill loading is not available.

For wrapper prompts that run the workflow in a bare Claude context without the installed skill, see [claude-export.md](claude-export.md).

## Install On Another Claude Machine

To install on another machine running Claude Code:
1. Copy the entire `fx-experts/` folder into `~/.claude/skills/`.
   - On Windows: `C:\Users\<username>\.claude\skills\`
   - On macOS or Linux: `~/.claude/skills/`
2. Preserve this folder structure:
   - `SKILL.md`
   - `references/*.md`
3. Start a new Claude Code session so the skill list reloads.
4. Invoke the skill by mentioning its triggers in the conversation (the description will auto-trigger it), by selecting it from the skill picker, or by calling the Skill tool directly.

## Install In A Claude Agent SDK Or API Project

For Claude API or Agent SDK use:
1. Drop the `fx-experts/` folder into the project's skills directory (usually `.claude/skills/` or wherever the SDK is configured to look).
2. Reference the skill in your system prompt or tool configuration so the agent can load it.

## Portable Core Bundle

Use this block when the target runner does not support skill loading and you want to paste the workflow directly into a bare Claude (or other LLM) context.

```text
FX Experts is a chaired TRY depreciation-risk roundtable.

Team:
- Core agents: Atlas, Bosphorus, Flow, Vega
- Specialists: activate only on direct and material triggers
- Chair: the orchestrator running the assessment

Scope:
- Turkish lira (TRY) depreciation or devaluation risk,
- structured macro and market-risk analysis,
- methodology, reporting, and product decisions for the TRY risk tool.

Not for:
- generic stock picking,
- portfolio allocation,
- personal investment advice,
- ad hoc live-trading prompts that bypass evidence discipline.

Evidence hierarchy:
- official and policy evidence,
- structured market evidence,
- reputable attributed reporting,
- social chatter only as a low-priority trigger source.

Cycle discipline:
- freeze one evidence pack per cycle,
- do not mix in ad hoc facts mid-round unless they are explicitly added as new evidence,
- preserve dissent instead of forcing consensus.

Quick-mode output should usually include:
- problem_frame
- primary_horizon
- active_agents
- house_curve
- disagreement_range
- minority_risk_note
- watch_triggers
- recommended_next_moves

Key rule:
- `risk_curve` values are probabilities, not vibes or sentiment labels.
```

See also:
- [claude-export.md](claude-export.md) for quick and full wrapper prompts.
