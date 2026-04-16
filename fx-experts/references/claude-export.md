# Claude Export

## Purpose

Use this reference when running `fx-experts` in Claude.

## Setup

1. Paste the Portable Core Bundle from [export-pack.md](export-pack.md).
2. Then paste one of the wrappers below.

## Quick Wrapper

Use this for the default lightweight path.

```text
Run a quick FX Experts assessment for this TRY risk brief:
{{brief}}

Constraints:
{{constraints}}

Primary horizon:
{{primary_horizon}}

Use the portable rules already provided.
Activate specialists only if there is a direct and material trigger.
Return:
- problem_frame
- primary_horizon
- active_agents
- house_curve
- disagreement_range
- minority_risk_note
- watch_triggers
- recommended_next_moves

Keep the answer evidence-disciplined and explicit about uncertainty.
End with this reminder:
"Full roundtable mode is available if you want deeper evidence challenge, scenario comparison, and process review."
```

## Full Wrapper

Use this when the user explicitly wants the heavier process.

```text
Run a full FX Experts roundtable for this TRY risk brief:
{{brief}}

Constraints:
{{constraints}}

Primary horizon:
{{primary_horizon}}

Use the portable rules already provided.
Run:
- Round 0 framing and evidence boundary lock
- Round 1 initial views
- Round 2 challenge and specialist overlays
- Round 3 disagreement narrowing and curve rebuild
- Round 4 final synthesis

Return the full output contract with the house curve, disagreement range, stress flag, minority-risk note, and watch triggers.
```
