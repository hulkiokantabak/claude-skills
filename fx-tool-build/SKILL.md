---
name: fx-tool-build
description: Architecture and implementation guidance for building the local-first TRY risk research tool — a Python + FastAPI + HTMX + SQLite web app with PDF/DOCX reporting, evidence-pack storage, and a local-first-then-deploy path. Use when the task is about building, refactoring, or extending the tool itself (app architecture, data ingestion, storage schema, UI, reporting, deployment). For running the TRY risk analysis workflow itself, use fx-experts instead.
---

# FX Tool Build

## Core Promise

Build the TRY risk research tool as a polished local-first Python web app that is also ready for later deployment — without a split frontend/backend in `v1`.

## When To Use

Use this skill when the task involves:
- designing the app architecture, stack choices, or deployment path for the TRY risk tool,
- data ingestion pipelines and source tiering (official vs market vs reporting vs chatter),
- storage schema decisions (SQLite for structured data, filesystem for evidence packs and reports, Git for code),
- UI flows, server-rendered templates, HTMX interactions,
- PDF or DOCX report rendering,
- cycle archival and history,
- extending or refactoring a feature in an existing implementation.

For running the TRY risk analysis workflow itself (Atlas / Bosphorus / Flow / Vega debate, probability curves, watch triggers), use the `fx-experts` skill instead.

## Do Not Use This For

- running a TRY risk assessment (that's `fx-experts`),
- generic web-app architecture unrelated to the TRY risk tool,
- macro analysis or market commentary,
- financial advice.

## Safety Boundary

- Architecture guidance only — the skill produces design choices and code patterns, not trades or investment advice.
- Do not embed fabricated market data in examples. Use synthetic placeholders or clearly-labelled samples.
- Keep secrets out of the repo. API keys, credentials, and personal notes belong in environment variables or a local config ignored by Git.

## Example Prompts

Should trigger:
- "Design the SQLite schema for storing assessment cycles in the TRY risk tool."
- "Sketch the HTMX interaction for the evidence-pack editor."
- "Use fx-tool-build to review my PDF report renderer for the TRY risk app."
- "How should I structure the data ingestion tier for the TRY tool?"
- "Refactor the TRY risk tool's cycle archival layer for better query performance."

Should not trigger (redirect or decline):
- "Assess TRY risk for six months." — use `fx-experts`.
- "Should I short USD/TRY?" — trade advice; decline.
- "Build a React SPA for tracking my portfolio." — different product entirely.

## Reference Order

1. [references/build-guidelines.md](references/build-guidelines.md): the full build spec — stack, product shape, storage rules, source strategy, reporting, deployment path.

## Operating Defaults

- Stay inside the preferred stack (`Python`, `FastAPI`, server-rendered HTML, `HTMX`, `SQLite`, local filesystem) unless the user explicitly asks for a deviation with a reason.
- Prefer a single-service architecture in `v1`. Do not propose a split frontend/backend unless the brief demands it.
- Every storage decision states where the data lives: `SQLite`, filesystem, or Git. No ambiguity.
- Every feature proposal states its v1 scope and what is deferred to v2.
- When reasoning about the analysis workflow, refer to `fx-experts` rather than duplicating its logic.

## Default Behavior

When the user invokes `$fx-tool-build` or asks for tool-build guidance:
- read `references/build-guidelines.md` to confirm the current spec,
- restate the brief and the relevant slice of the spec,
- produce concrete implementation guidance: schema fragments, endpoint sketches, template patterns, or file-layout suggestions,
- flag any proposed deviation from the preferred stack explicitly,
- highlight v1-versus-later tradeoffs where relevant,
- end with a short next-step or implementation checklist.

## Core Working Rules

- Local-first: the tool must run on one machine with no cloud dependencies for v1. Deployment compatibility is a bonus, not a blocker.
- Simple beats clever. One service, one database, one UI.
- Evidence packs and reports are durable artifacts — they go on the filesystem with a date-stamped path, not inside SQLite blobs.
- Git is for code, templates, prompts, specs, methodology — and optionally sanitized reports. Not for live analytical data.
- Do not reinvent the `fx-experts` analysis workflow inside the tool. The tool hosts, renders, and archives the workflow; it does not replace it.

## Output Expectations

When producing build guidance, preserve:
- the restated brief,
- the relevant slice of the build spec being applied,
- concrete code, schema, or layout sketches (not just abstract advice),
- explicit v1 scope and v2 deferrals,
- flagged deviations from the preferred stack with justification,
- a short next-step or implementation checklist.

## References

- [references/build-guidelines.md](references/build-guidelines.md): stack, product shape, storage rules, source strategy, reporting, deployment path.
