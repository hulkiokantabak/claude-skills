# Worked Example

## Purpose

Use this as a compact end-to-end forward-test reference for the `game-design-experts` workflow.

This example is intentionally software-heavy and specialist-relevant:
- `Relay` for scanner hardware and intermittent connectivity,
- `Vector` for AI-assisted lookup,
- `Bastion` for permissions and auditability.

## Sample Brief

Design a warehouse operations tablet app for support staff.

The app should:
- scan barcodes,
- work during intermittent connectivity,
- let staff inspect inventory and shipment records,
- use AI-assisted search to explain where an item likely is,
- support role-based access for supervisors versus floor staff,
- keep a clear audit trail for edits and overrides.

## Expected Activation

Likely active agents:
- core: `Prism`, `Loop`, `Forge`, `Lantern`
- specialists: `Relay`, `Vector`, `Bastion`

## Example Final YAML

```yaml
design_thesis: "Make warehouse staff feel fast, certain, and safe even when connectivity or data quality is imperfect."
active_agents:
  core:
    - "Prism"
    - "Loop"
    - "Forge"
    - "Lantern"
  specialists:
    - "Relay"
    - "Vector"
    - "Bastion"
proposal_ledger:
  - proposal_id: "P01"
    title: "Scan-First Item Recovery"
    source_agents:
      - "Loop"
      - "Lantern"
      - "Relay"
    merged_from:
      - "Loop-1"
      - "Lantern-1"
      - "Relay-1"
    summary: "Center the app around scan-first recovery, recent-item context, and offline-safe item detail views."
    viability: "workable_now"
    status: "survived"
  - proposal_id: "P02"
    title: "Explainable AI Search Assist"
    source_agents:
      - "Prism"
      - "Vector"
    merged_from:
      - "Prism-2"
      - "Vector-1"
    summary: "Offer AI-assisted search and likely-location suggestions with visible evidence and confidence."
    viability: "research_spike"
    status: "survived"
  - proposal_id: "P03"
    title: "Supervisor Override Rail"
    source_agents:
      - "Forge"
      - "Bastion"
    merged_from:
      - "Forge-1"
      - "Bastion-1"
    summary: "Gate high-risk edits behind supervisor approval, reason codes, and audit logging."
    viability: "workable_now"
    status: "survived"
elimination_log:
  - proposal_id: "P04"
    round: "Round 3"
    outcome: "cut"
    reason: "Gamified team scoring increased speed incentives but created risky behavior around inventory corrections."
    score: -3
    notes: "Interesting motivation idea, but safety and audit quality matter more than speed signaling here."
survivor_slate:
  - proposal_id: "P01"
    why_it_survived: "It directly improves the primary operator loop and is feasible with current platform constraints."
    viability: "workable_now"
    smallest_coherent_implementation: "Barcode scan, cached item detail view, and recent scan history with offline fallback."
    next_test: "Run a tablet prototype in a low-connectivity aisle and measure time-to-item lookup."
    do_not_ship_reason: "If offline cache invalidation is sloppy, staff may act on stale inventory information."
  - proposal_id: "P02"
    why_it_survived: "It could create major usability gains, but only if explanations and confidence handling are trustworthy."
    viability: "research_spike"
    smallest_coherent_implementation: "Read-only AI suggestions over indexed shipment and location data with evidence snippets."
    next_test: "Offline evaluation of top-5 suggested item locations against historical warehouse records."
    do_not_ship_reason: "If the assistant sounds more certain than the data deserves, staff will over-trust bad guidance."
  - proposal_id: "P03"
    why_it_survived: "It controls the main abuse and safety risks without blocking the common operator path."
    viability: "workable_now"
    smallest_coherent_implementation: "Supervisor-only override action with mandatory reason code and immutable audit event."
    next_test: "Role-based usability check for override request and approval turnaround."
    do_not_ship_reason: "If overrides bypass logging or are too easy to approve, the system loses trust immediately."
build_now:
  - "P01"
  - "P03"
research_spikes:
  - "P02"
parked_or_cut:
  - "P04"
implementation_notes:
  - "Prefer local-first caching and explicit sync states before expanding AI scope."
  - "Show evidence and confidence with every AI-assisted suggestion."
  - "Keep override permissions narrow and auditable."
open_questions:
  - "What is the acceptable freshness window for offline item data?"
  - "Should AI suggestions be available to all staff or supervisors only?"
  - "Which edit actions truly require supervisor approval versus post-hoc audit?"
```

## What This Example Tests

This example checks that the workflow can:
- activate multiple specialists early without replacing the core four,
- preserve stable `P##` proposal IDs after Round `1`,
- carry enough proposal detail through elimination and refinement,
- separate `build_now` ideas from `research_spike` ideas,
- keep implementation warnings attached to survivors instead of only the cut ideas.
