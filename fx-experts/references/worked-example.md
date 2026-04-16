# FX Experts Worked Example

Use this as a compact end-to-end reference for the `fx-experts` workflow.

## Brief

Assess `3-month` Turkish lira depreciation risk after a surprise inflation print, renewed reserve pressure concerns, and mixed local-policy signaling. The user wants a quick assessment for an internal risk note, not a trading call.

## Expected Shape

Return:
- `problem_frame`,
- `primary_horizon`,
- `active_agents`,
- `house_curve`,
- `disagreement_range`,
- `minority_risk_note`,
- `watch_triggers`,
- `recommended_next_moves`.

## Example House View

- `problem_frame`: near-term TRY depreciation risk is elevated because inflation credibility, reserve durability, and policy consistency are pulling in different directions.
- `primary_horizon`: `3-month`
- `house_curve`: near-term risk elevated, medium-horizon risk conditional on policy follow-through, longer-horizon risk sensitive to reserve quality and external funding.
- `disagreement_range`: narrower on short-horizon stress risk, wider on whether policy credibility can stabilize expectations.
- `minority_risk_note`: one minority view may argue the market is underpricing a sharper step-change if confidence breaks suddenly.
- `watch_triggers`: reserve deterioration, off-cycle policy communication, inflation surprise persistence, local political shocks, and abrupt external-financing stress.
- `recommended_next_moves`: refresh the evidence pack, compare market-implied pricing versus official narrative, and rerun the cycle if one of the watch triggers fires.

## Notes

- Keep this kind of example evidence-backed and structured.
- Do not turn it into stock-picking or personal investment advice.
