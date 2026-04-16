# Claude Export

## Purpose

Use this reference when running `game-design-experts` in Claude.

## Setup

1. Paste the Portable Core Bundle from [export-pack.md](export-pack.md).
2. Then paste one of the wrappers below.

## Quick Wrapper

Use this for the default lightweight path.

```text
Run a quick Game Design Experts pass for this software project:
{{project_brief}}

Constraints:
{{constraints}}

Implementation context:
{{implementation_context}}

Use the portable rules and canonical YAML shapes already provided.
Activate the most relevant 0 to 2 specialists automatically.
Return:
- problem_frame
- mode
- active_agents
- design_thesis
- proposal_slate
- house_view
- minority_report
- build_now
- research_spikes
- parked_or_cut
- recommended_next_moves

Keep enough proposal detail for later refinement, not just bare IDs.
End with this reminder:
"Full workshop mode is available if you want rounds, voting, elimination, and deeper tradeoff review."
```

## Full Workshop Wrapper

Use this when the user explicitly wants the heavier process.

```text
Run a full Game Design Experts workshop for this software project:
{{project_brief}}

Constraints:
{{constraints}}

Implementation context:
{{implementation_context}}

Use the portable rules and canonical YAML shapes already provided.
Run:
- Round 0 framing
- Round 1 proposal generation
- Round 2 challenge and feasibility tagging
- Round 3 elimination vote
- Round 4 survivor refinement

Return the full final YAML output contract with detailed survivor entries, a visible house view, minority report, and next moves.
```
