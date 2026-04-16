# Operating Spec

## Purpose

Use this team as a chaired design workshop for software concepts that may turn into real implementation work.

The goal is not only to brainstorm. The goal is to:
- generate candidate ideas,
- expose tradeoffs,
- eliminate weak or unworkable options,
- carry surviving suggestions into a final implementation-oriented slate.

This spec is portable: any capable orchestrator (Claude, another assistant, or a human facilitator) may chair as long as it follows this spec and preserves the output contract.

## Team Structure

The workflow has:
- `4` core agents,
- up to `4` active on-call specialists,
- `1` chair.

## Chair Role

When this skill runs in Claude, Claude chairs by default. Any capable orchestrator may chair as long as it follows the same rules.

The chair should:
- restate the brief in game-design language,
- identify likely specialist activations early,
- assign stable proposal IDs,
- merge duplicates,
- keep a round-by-round proposal ledger,
- tag proposal viability as `workable_now`, `research_spike`, or `not_workable_now`,
- prevent late-round drift into endless new idea generation,
- distill surviving ideas into implementation-ready recommendations.

The chair is not a fifth design voter.

The chair may:
- reject obviously impossible or contradictory formulations,
- break ties using the tie-break rules below,
- move a proposal from `not_workable_now` to `research_spike` only if the team meaningfully revises it.

## Specialist Activation

Activation should be easier and more frequent than a strict "only if directly requested" model.

Use this posture:
- activate at least `1` specialist in most sessions that are likely to lead to implementation,
- consider `2` specialists in early rounds when the brief clearly spans both product design and delivery risk,
- cap early rounds at `2` specialists unless the brief obviously needs more,
- let specialists self-activate in Round `2` if a proposal enters their territory,
- keep inactive specialists available for short overlays instead of pretending they do not exist.

Soft activation guidance:
- activate `Bastion` for most public, multi-user, data-touching, or permissioned systems,
- activate `Cortex` for onboarding, learning, retention, cognitive load, or behavior-shaping systems,
- activate `Vector` for automation, scoring, search, recommendations, agents, generation, ranking, or AI-adjacent designs,
- activate `Relay` for hardware, peripherals, offline environments, sensors, scanners, kiosks, or edge constraints.

## Canonical Objects

Use YAML by default for portability across Claude and other orchestrators.

In non-voting rounds, set `vote_posture` to `hold`.

Round `1` proposal IDs are temporary and agent-local:
- use forms such as `Prism-1`, `Loop-2`, or `Vector-1`,
- the chair converts surviving candidates into stable `P##` IDs during the Round `1` merge step,
- after the merge step, only stable `P##` IDs should be used.

### `proposal_card`

```yaml
proposal_id: "Loop-1"
title: "Guided Query Paths"
user_outcome: "New admins can complete common database tasks safely without memorizing SQL."
design_move: "Offer guided workflows for backup, restore, audit, and safe bulk edits."
implementation_shape: "Permission-gated workflow wizard with dry-run previews and undo-friendly checkpoints."
main_risk: "Power users may feel constrained if direct tools become harder to reach."
success_test: "Prototype the backup flow and compare first-time completion rate plus operator error rate."
vote_posture: "hold"
confidence: "medium"
```

### `proposal_overlay`

Use overlays only after a stable `proposal_id` exists.

```yaml
proposal_id: "P01"
change: "Require a read-only diff preview before destructive actions."
why_it_matters: "The current proposal is too trusting for sensitive admin tasks."
implementation_condition: "Needs preview generation and permission-aware audit logging."
vote_posture: "advance"
confidence: "high"
```

### `proposal_ledger_entry`

```yaml
proposal_id: "P01"
title: "Guided Query Paths"
source_agents:
  - "Loop"
  - "Lantern"
merged_from:
  - "Loop-1"
  - "Lantern-2"
summary: "Guided workflows for high-risk recurring admin tasks."
viability: "workable_now"
status: "active"
```

### `elimination_log_entry`

```yaml
proposal_id: "P04"
round: "Round 3"
outcome: "cut"
reason: "Negative score after core votes and unresolved implementation risk."
score: -2
notes: "Could return later as a research spike if the dependency picture changes."
```

### `final_survivor_entry`

```yaml
proposal_id: "P01"
why_it_survived: "Strong cross-lens support and low implementation ambiguity."
viability: "workable_now"
smallest_coherent_implementation: "One permission-gated workflow for backup with preview and audit logging."
next_test: "Run a clickable prototype with first-time admins."
do_not_ship_reason: "If preview or rollback is missing, the flow becomes more dangerous than the current tool."
```

## Round Protocol

### Round 0: Frame

The chair:
- restates the brief,
- names the user fantasy, core loop, value exchange, and main constraints,
- activates the initial specialist set,
- opens the proposal ledger.

### Round 1: Generate

Each core agent submits:
- `2 to 3` full `proposal_card` objects.

Each active specialist submits:
- `1 to 2` full `proposal_card` objects.

Round `1` specialists do not submit overlays because stable proposal IDs do not exist yet.
Round `1` agents use temporary agent-local IDs, not stable `P##` IDs.

The chair then:
- deduplicates similar ideas,
- merges obvious variants,
- converts surviving candidates into stable `P##` IDs,
- preserves enough detail in the candidate slate for later review, including `user_outcome`, `design_move`, `implementation_shape`, `main_risk`, and `success_test`,
- publishes the candidate slate.

### Round 2: Challenge And Feasibility

All active agents review the candidate slate and respond using YAML.

Each response should identify:
- what to `advance`,
- what to `hold`,
- what to `cut`,
- what should merge,
- what implementation blocker or enabling condition matters most.

Active specialists may now submit `proposal_overlay` objects tied to existing `proposal_id` values.

The chair then tags every candidate:
- `workable_now`,
- `research_spike`,
- or `not_workable_now`.

The Round `3` slate should preserve compact proposal details, not only bare IDs.

Any candidate with zero core support after this round is eliminated.

### Round 3: Elimination Vote

Each core agent must cast a YAML ballot in this shape:

```yaml
champion: "P02"
advance:
  - "P01"
  - "P03"
cut:
  - "P04"
```

Rules:
- `champion` may be `null` only if the slate is fatally weak,
- `advance` may contain `0 to 2` proposal IDs,
- `cut` may contain `0 to 2` proposal IDs,
- use empty lists instead of filler IDs.

Each active specialist must cast a YAML ballot in this shape:

```yaml
advance:
  - "P03"
cut: []
```

Rules:
- specialists never emit `champion`,
- `advance` may contain `0 or 1` proposal ID,
- `cut` may contain `0 or 1` proposal ID,
- specialists only vote inside their domain.

Score proposals as:
- core `champion` = `+3`
- core `advance` = `+2`
- core `cut` = `-2`
- specialist `advance` = `+1`
- specialist `cut` = `-1`

Survival rules:
- a proposal must receive at least one positive core vote,
- a proposal must finish with a positive net score,
- a `not_workable_now` proposal is cut unless `3` core agents still support it and the chair can responsibly reclassify it as `research_spike`.

Tie-break rules:
- more `champion` votes,
- then more positive core votes,
- then `workable_now` over `research_spike`,
- then chair judgment on clearer user value and lower implementation risk.

If fewer than `3` proposals survive with positive scores, carry forward the thinner slate and note that the workshop needs another generation pass.

If more than `5` proposals survive, keep the best `5` after tie-breaks.

The survivor slate should preserve compact proposal details plus viability and score context so Round `4` does not refine proposals blindly.

### Round 4: Refine Survivors

The team stops broad ideation and works only on survivors.

Each core agent:
- sharpens the surviving proposals from its own lens,
- identifies the minimum lovable version,
- names one tradeoff to accept.

Each active specialist:
- tightens implementation notes,
- removes hidden blockers where possible,
- flags any survivor that still should not ship.

The chair:
- merges compatible survivors,
- cuts contradictions,
- converts the result into a practical final slate.

## Final Output Contract

The chair should publish YAML with:
- `design_thesis`
- `active_agents`
- `proposal_ledger`
- `elimination_log`
- `survivor_slate`
- `build_now`
- `research_spikes`
- `parked_or_cut`
- `implementation_notes`
- `open_questions`

Each entry in `survivor_slate` should follow the `final_survivor_entry` shape.

## Distilling Implementation Suggestions

Because this workshop can lead directly into software delivery, the chair must translate design language into software action.

For every surviving proposal, the chair should answer:
- is this workable now,
- what is the smallest coherent implementation,
- what dependency or skill is required,
- what should be prototyped before full build,
- what makes this a bad idea to ship unchanged.

Use these labels consistently:
- `workable_now`: clear enough and bounded enough to implement next,
- `research_spike`: promising but needs a spike, experiment, or technical proof,
- `not_workable_now`: strategically interesting but currently too risky, vague, or contradictory.

## Prompting Rule

Use [prompt-templates.md](prompt-templates.md) to run the rounds inside this skill.

Use [export-pack.md](export-pack.md) when sharing the workflow with another Claude machine.

Keep these invariants across prompts:
- preserve stable `proposal_id` values across rounds,
- do not let late-round prompts reopen ideation from scratch,
- always make the chair publish viability tags and elimination logic,
- force agent outputs back into the canonical YAML shapes if they drift.
