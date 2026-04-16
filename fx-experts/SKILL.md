---
name: fx-experts
description: Chaired four-agent debate team (Atlas, Bosphorus, Flow, Vega) plus four on-call specialists for Turkish lira (TRY) depreciation and devaluation risk. Produces probability curves, watch triggers, minority views, and evidence-quality assessments. Use for structured macro risk synthesis, scenario work, or methodology review. Analysis only, not financial advice. For building the TRY risk research tool itself, use fx-tool-build instead.
---

# FX Experts

## Core Promise

Turn scattered TRY risk evidence into a disciplined probability view with explicit dissent, watch triggers, and a usable next decision.

## The Chair

The chair is the assistant running this skill — Claude, or whichever orchestrator has loaded it. The chair coordinates the four core agents, merges duplicates, runs the flow, and publishes the final synthesis. The chair is not a fifth voting expert and does not override agent views in the house curve.

Use this skill when the task involves:
- defining or running the TRY depreciation-risk expert workflow,
- prompting or coordinating the `Atlas`, `Bosphorus`, `Flow`, and `Vega` agents,
- activating or refining the on-call specialists,
- designing the evidence hierarchy, round orchestration, risk math, or minority-risk handling for the assessment process,
- reviewing whether a proposed methodology change still matches the agreed expert process.

For building or improving the TRY risk research tool itself (app architecture, data ingestion, storage, UI, PDF reporting, deployment), use the separate `fx-tool-build` skill.

## Core Agents

Four core voices, always active. Each produces a stance, a five-horizon `risk_curve`, a `primary_risk_score`, confidence, top drivers, counterevidence, and watch triggers. Full profiles in [references/core-agent-profiles.md](references/core-agent-profiles.md).

- `Atlas` — Global Macro Economist. Lens: Fed and ECB policy, dollar liquidity, US real yields, oil and energy shocks, VIX, EM contagion. Calm, regime-focused, unimpressed by noise.
- `Bosphorus` — Turkey Macro Economist. Lens: CBRT policy, inflation, real rates, reserves, current account, fiscal stance, policy credibility. Skeptical, detail-oriented, institution-focused.
- `Flow` — EM FX Spot Trader. Lens: USD/TRY trend, liquidity, positioning, forward points, intervention footprints, price confirmation or contradiction. Blunt, tape-first, practical.
- `Vega` — FX Options / Vol Trader. Lens: implied vol, skew, risk reversals, event premium, tail pricing. Clinical, probabilistic, focused on asymmetry.

## Specialists

Four on-call specialists. Activate only on direct and material mentions tied to the thesis. Each overlay recommends a `-5` to `+5` adjustment per affected horizon; total specialist impact is capped at `+/- 10` per horizon and overlays advise rather than replace the core vote.

- `Ankara` — activate for elections, cabinet changes, CBRT leadership changes, sanctions risk, surprise regulatory or capital-control-like actions.
- `Ledger` — activate for reserves, intervention, CDS or Eurobond stress, rollover risk, funding fragility.
- `Strait` — activate for wars, sanctions regimes, trade conflict, shipping disruption, regional geopolitical repricing.
- `Meridian` — activate for recession risk, violent Fed repricing, dollar funding stress, commodity-cycle turns, global contagion.

## Horizons and Risk Definition

**Canonical horizons:** `1w`, `1m`, `3m`, `6m`, `1y`. Default primary horizon: `6m` when the user has not named one. State the choice explicitly.

**Risk definition:** `TRY depreciation risk` at a given horizon is the probability that `USD/TRY` rises by at least the configured threshold over that horizon. Default `v1` thresholds: `1w >= 2%`, `1m >= 5%`, `3m >= 10%`, `6m >= 15%`, `1y >= 25%`.

**Evidence hierarchy** (use whatever is available, in this priority order): market pricing → policy actions → hard macro data → reserves and funding signals → narrative and commentary. Social chatter is allowed for awareness but never outranks official or market-implied evidence.

**Working fact base:** just run the skill with what you know. If the brief names a specific event, date, or data point and current values would materially change the assessment, it is fine to do a quick web search to check. Otherwise proceed from general knowledge of Turkish macro, CBRT posture, Fed regime, and FX markets, and state the knowledge-cutoff caveat briefly. Do not ask the user for a pre-staged evidence pack.

## Quick Intake

Before you run the team, lock a compact brief:
- `goal`: what risk question, methodology question, or build decision is on the table,
- `mode`: `quick assessment` or `full roundtable mode`,
- `constraints`: data freshness, evidence boundary, reporting, product, or policy constraints,
- `desired_output`: what artifact should come back.

Use this default shape:
- `goal`: `<what TRY risk or tool question should be assessed>`
- `mode`: `quick assessment`
- `constraints`: `work with whatever evidence is available; state the primary horizon and any knowledge-cutoff caveats`
- `desired_output`: `house curve, dissent, watch triggers, and next moves`

If any field is missing, infer it and state the assumptions in one line before the assessment.

## Do Not Use This For

- generic stock picking, portfolio allocation, or personal investment advice,
- broad macro commentary with no TRY or currency-risk assessment angle,
- ad hoc live-trading decisions,
- building or improving the TRY risk research tool itself — use `fx-tool-build` for that.

## Safety Boundary

- This skill produces structured analysis, not financial advice. Outputs are probability views on currency-risk scenarios, not recommendations to buy, sell, short, or allocate. Regulated financial advice requires a licensed advisor.
- Do not frame outputs as actionable trades or allocation prescriptions. The house curve is an evidence-disciplined view, not a signal.
- If the user asks for trade recommendations, portfolio allocation, or "what should I do with my money," redirect to the analysis-only framing. Offer to assess a risk question, not a position.
- Do not fabricate figures or pretend certainty the available evidence does not support. Thin evidence means wider disagreement and lower confidence, not invented precision.

## Example Prompts

These illustrate when this skill should trigger and when it should not.

Should trigger:
- "Run an FX Experts assessment of TRY depreciation risk for the next six months given the current CBRT stance."
- "Pressure-test my evidence pack on the TRY six-month primary horizon. Produce the house curve, disagreement range, and watch triggers."
- "Use the fx-experts workflow to review whether my reporting template captures the minority risk note properly."
- "Full roundtable mode on a TRY devaluation scenario around the next MPC meeting."

Should not trigger (redirect or decline):
- "Should I short USD/TRY this week?" — this is trade advice; redirect to a risk-assessment framing.
- "Which Turkish stocks should I buy?" — out of scope and outside the safety boundary.
- "What's the current USD/TRY rate?" — rote factual lookup; a direct answer is better than a multi-agent roundtable.
- "Explain the history of the TRY in one paragraph." — no risk-assessment angle; answer directly without invoking the skill.

## Reference Order

Read these in order of need, not sequentially — most briefs only need the first two.

1. [references/operating-spec.md](references/operating-spec.md): expert-team rules, round protocol, evidence hierarchy, debate charter, house-view weights, and archive expectations.
2. [references/core-agent-profiles.md](references/core-agent-profiles.md): detailed Atlas, Bosphorus, Flow, Vega profiles — territory, instincts, default questions, failure modes.
3. [references/worked-example.md](references/worked-example.md): a compact end-to-end example of the final output shape.

## Operating Defaults

- Default to the `4` core agents.
- Default to `quick assessment` mode unless the user asks for round-by-round debate.
- Activate `0 to 2` specialists only on direct and material triggers from the brief. Record every activation decision (including specialists considered and dismissed) in `specialist_activation_notes`.
- Use the canonical horizons and the default primary horizon (`6m`) unless the user names another.
- Always run. Use whatever you know plus user input; optionally web-search for a specific named event if that would change the assessment. Note knowledge cutoff briefly.
- Preserve dissent. Do not force consensus when disagreement is informative.

## Default Behavior

When the user invokes `$fx-experts` or asks for TRY or Turkish-lira depreciation-risk analysis without specifying a format:
- default to `quick assessment`,
- use the core four agents,
- activate `0 to 2` specialists only when there is a direct and material trigger,
- return `problem_frame`, `primary_horizon`, `active_agents`, `specialist_activation_notes`, `house_curve`, `disagreement_range`, `minority_risk_note`, `stress_flag`, `watch_triggers`, and `recommended_next_moves`,
- end with a short reminder that `full roundtable mode` is available for deeper evidence challenge, scenario comparison, or process review.

### Quick Assessment Flow

A quick assessment is a single pass, not a workshop. Run it lightly:

1. **Frame.** Restate the question. Pick the primary horizon (default `6m`). Note knowledge-cutoff caveat if working from general knowledge. Quick web search only if the brief names a specific recent event you need to check.
2. **Four voices.** Atlas, Bosphorus, Flow, Vega each give a short stance and a five-horizon probability curve with a couple of drivers and counterevidence.
3. **House curve.** Apply the horizon weights from `operating-spec.md` to merge. Call out disagreement and any minority view worth preserving.
4. **Close.** Highlighted primary score, watch triggers, next moves.

Calibrate confidence honestly: thin evidence → wide disagreement, `low` or `medium` confidence. Never refuse to run.

### Full Roundtable Mode

Switch to `full roundtable mode` when the user explicitly asks for:
- a round-by-round debate (Round 0 framing → Round 1 agenda → Round 2 full output contracts → Round 3 challenge → Round 4 finals),
- stronger evidence challenge,
- multiple scenarios compared under pressure,
- deeper methodology review,
- a higher-stakes process or product review where the extra ceremony is worth it.

## Core Working Rules

- Treat `risk_curve` values as true event probabilities, not generic sentiment scores.
- Always produce the full horizon curve and highlight one `primary_horizon`.
- Keep social chatter below official, policy, and market-implied evidence in the hierarchy.
- Keep the working fact base stable across one assessment cycle. If new evidence arrives mid-cycle, flag it as added rather than silently mixing it in.
- Debate should be sharp, personality-driven, and evidence-backed. Empty rhetoric is a process failure.
- The chair coordinates and synthesizes; it is not a fifth voting expert. See `## The Chair` above.
- `recommended_next_moves` must be things the user can do directly from this conversation — refine the brief, name a primary horizon, flag a specialist trigger, ask a sharper sub-question, or re-invoke the skill with an updated lens. Do not send the user off to gather data before they can act; the skill itself produces a usable assessment.

## Output Expectations

When running or simulating an assessment, preserve:
- the reframed problem statement,
- the chosen mode,
- the active core agents,
- `specialist_activation_notes` — which specialists activated, which were considered and dismissed, and why (include even when zero activated),
- the working fact base used, with source tags and freshness notes (including "as of my knowledge cutoff" when applicable),
- each round's outputs,
- each core agent's final view,
- specialist overlays if activated,
- the house curve,
- the primary-horizon house score,
- disagreement range,
- minority-risk note,
- stress flag,
- watch triggers,
- recommended next moves.

## References

- [references/operating-spec.md](references/operating-spec.md): team design, rounds, debate charter, house-view weights, interaction style, confidence rule, and archival expectations.
- [references/core-agent-profiles.md](references/core-agent-profiles.md): detailed Atlas, Bosphorus, Flow, Vega profiles — territory, signature instincts, default questions, failure mode, chair note.
- [references/worked-example.md](references/worked-example.md): compact example showing the output shape for a quick TRY risk assessment.
- [references/export-pack.md](references/export-pack.md): portable install guidance for moving this skill to another Claude machine.
- [references/claude-export.md](references/claude-export.md): standalone prompt wrappers for running this skill in a bare Claude context without the installed skill.
