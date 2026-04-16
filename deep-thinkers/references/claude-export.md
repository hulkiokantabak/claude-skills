# Claude Export

## Purpose

Use this reference when running `deep-thinkers` in Claude.

## Setup

1. Paste the Portable Core Bundle from [export-pack.md](export-pack.md).
2. Then paste one of the wrappers below.

## Quick Wrapper

Use this for the default lightweight path.

```text
Run a quick Deep Thinkers pass for this brief:
{{brief}}

Constraints:
{{constraints}}

Mode:
{{mode}}

Use the portable rules and YAML shapes already provided.
If `mode` is blank, choose the best-fit mode such as `brainstorm`, `deep_analysis`, `decision_review`, or `root_cause`.
Activate 0 to 2 on-call thinkers automatically only if they materially improve the reasoning.
If `mode` is `reflection`, do not force a fake winner.
If `mode` is `technical_research`, end with tests and edge cases rather than only conclusions.
Return:
- mode
- problem_frame
- active_agents
- idea_clusters
- key_tensions
- house_view
- minority_report
- recommended_next_moves

Keep the answer compressed, modern, and high-signal rather than writing seven long monologues.
End with this reminder:
"Full roundtable mode is available if you want deeper debate, stronger challenge, and explicit round-by-round synthesis."
```

## Full Wrapper

Use this when the user explicitly wants the heavier process.

```text
Run a full Deep Thinkers roundtable for this brief:
{{brief}}

Constraints:
{{constraints}}

Mode:
{{mode}}

Use the portable rules and YAML shapes already provided.
Run:
- Round 0 framing and specialist activation
- Round 1 insight generation
- Round 2 cross-examination and specialist overlays
- Round 3 rebuild
- Round 4 decision and synthesis

Adjust Round 4 to the mode:
- `brainstorm` = prioritize and package,
- `root_cause` = rank mechanisms and likely failure chains,
- `reflection` = weigh tensions and name practices,
- `technical_research` = rank hypotheses or architectures, then end with tests and edge cases.

Return the full final output contract with a visible minority report and any relevant technical or decision outputs.
```
