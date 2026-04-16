# Export Pack

## Purpose

Use this pack to share `game-design-experts` with:
- another computer running Claude Code,
- any other Claude surface that supports skills (Claude API, Claude Desktop with skills, Agent SDK projects),
- any environment that can accept a plain prompt bundle when full skill loading is not available.

For wrapper prompts that run the workflow in a bare Claude context without the installed skill, see [claude-export.md](claude-export.md).

## Install On Another Claude Machine

To install on another machine running Claude Code:
1. Copy the entire `game-design-experts/` folder into `~/.claude/skills/`.
   - On Windows: `C:\Users\<username>\.claude\skills\`
   - On macOS or Linux: `~/.claude/skills/`
2. Preserve this folder structure:
   - `SKILL.md`
   - `references/*.md`
3. Start a new Claude Code session so the skill list reloads.
4. Invoke the skill by mentioning its triggers in the conversation (the description will auto-trigger it), by selecting it from the skill picker, or by calling the Skill tool directly.

## Install In A Claude Agent SDK Or API Project

For Claude API or Agent SDK use:
1. Drop the `game-design-experts/` folder into the project's skills directory (usually `.claude/skills/` or wherever the SDK is configured to look).
2. Reference the skill in your system prompt or tool configuration so the agent can load it.

## Portable Core Bundle

Use this block when the target runner does not support skill loading and you want to paste the workflow directly into a bare Claude (or other LLM) context. Paste it before any wrapper prompt from [prompt-templates.md](prompt-templates.md).

```text
Game Design Experts is a chaired software-design workshop.

Team:
- Core agents: Prism, Loop, Forge, Lantern
- Specialists: Relay, Cortex, Vector, Bastion
- Chair: the orchestrator running the workshop

Goal:
- generate candidate ideas,
- expose tradeoffs,
- eliminate weak or unworkable options,
- carry survivors into a final implementation-oriented slate.

Activation:
- start with the 4 core agents,
- activate at least 1 specialist in implementation-minded sessions,
- usually keep early rounds to 1 or 2 specialists unless the brief clearly needs more,
- allow specialists to add overlays from Round 2 onward.

Round 1 IDs:
- agents use temporary IDs such as Prism-1 or Vector-1,
- the chair converts surviving candidates into stable P## IDs after Round 1,
- only stable P## IDs appear from Round 2 onward.

Canonical proposal card YAML:
proposal_id: "Loop-1"
title: ""
user_outcome: ""
design_move: ""
implementation_shape: ""
main_risk: ""
success_test: ""
vote_posture: "hold"
confidence: "medium"

Canonical overlay YAML:
proposal_id: "P01"
change: ""
why_it_matters: ""
implementation_condition: ""
vote_posture: "advance"
confidence: "high"

Voting:
- core champion = +3
- core advance = +2
- core cut = -2
- specialist advance = +1
- specialist cut = -1

Survival and tie-break rules:
- a proposal needs at least one positive core vote,
- a proposal needs a positive net score,
- a not_workable_now proposal is cut unless 3 core agents still support it and the chair reclassifies it as research_spike,
- ties break by champion votes, then positive core votes, then workable_now over research_spike, then chair judgment on user value and implementation risk.

Core ballot YAML:
champion: "P02"
advance: ["P01"]
cut: ["P04"]

Specialist ballot YAML:
advance: ["P03"]
cut: []

Viability labels:
- workable_now
- research_spike
- not_workable_now

Final YAML should usually include:
- problem_frame
- mode
- active_agents
- design_thesis
- proposal_ledger
- house_view
- minority_report
- survivor_slate
- build_now
- research_spikes
- parked_or_cut
- recommended_next_moves

Carry forward enough detail between rounds for downstream review:
- candidate slates should keep each proposal's user_outcome, design_move, implementation_shape, main_risk, and success_test,
- round 3 slates should not collapse to IDs only,
- survivor slates should keep compact proposal details plus viability and score context.
```

See also:
- [claude-export.md](claude-export.md) for quick and full wrapper prompts.
