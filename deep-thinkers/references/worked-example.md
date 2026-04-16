# Worked Example

## Contents

- Brief
- Problem Frame
- Sample Insight Ledger
- Sample Cluster Slate
- Sample House View
- What This Example Demonstrates

Use this example as a compact reference for what a strong quick-mode run looks like.

## Brief

`Should a mid-sized city launch an AI tutor pilot in public schools next year?`

## Problem Frame

```yaml
problem_frame: "Decide whether to run a bounded AI tutor pilot in public schools next year."
goal_posture: "decision"
task_type: "decision"
stakes:
  - "Student learning outcomes"
  - "Teacher trust and workload"
  - "Privacy, fairness, and procurement risk"
constraints:
  - "One school-year timeline"
  - "Limited procurement budget"
  - "Need for public legitimacy"
known_unknowns:
  - "Actual learning gains by student segment"
  - "Teacher adoption behavior"
  - "Failure modes around bad answers and data handling"
active_agents:
  core:
    - "Carl Sagan"
    - "Socrates"
    - "John Coltrane"
    - "Marcus Aurelius"
    - "Leonardo da Vinci"
    - "Terence Tao"
    - "Elon Musk"
  on_call:
    - "Peter Drucker"
    - "W.E.B. Du Bois"
activation_notes:
  - agent: "Peter Drucker"
    why_activated: "The pilot is also an organizational design problem involving school roles, incentives, procurement, and ownership."
    scope: "Use Drucker to test decision rights, teacher workflow fit, and whether the district knows what success means operationally."
  - agent: "W.E.B. Du Bois"
    why_activated: "The city cannot evaluate the pilot honestly without asking which students benefit, which students are exposed to risk first, and how official success claims differ across groups."
    scope: "Use Du Bois to test unequal burden, access, data visibility, and the gap between formal fairness and lived experience."
```

## Sample Insight Ledger

```yaml
insight_ledger:
  - insight_id: "Carl-1"
    agent: "Carl Sagan"
    title: "Run an evidence-first pilot"
    kind: "option"
    core_claim: "A narrow pilot is justified only if success and failure are measurable before launch."
    confidence: "high"
  - insight_id: "Socrates-1"
    agent: "Socrates"
    title: "Define tutoring success precisely"
    kind: "frame"
    core_claim: "The city has not yet defined whether success means test scores, confidence, equity, or teacher time saved."
    confidence: "high"
  - insight_id: "Coltrane-1"
    agent: "John Coltrane"
    title: "Treat the tool as a practice partner"
    kind: "reframe"
    core_claim: "The pilot becomes more interesting if the tutor is framed as a flexible practice companion instead of a replacement teacher."
    confidence: "medium"
  - insight_id: "Marcus-1"
    agent: "Marcus Aurelius"
    title: "Protect trust before scale"
    kind: "warning"
    core_claim: "A visible failure with children can destroy legitimacy faster than small gains can build it."
    confidence: "high"
  - insight_id: "Leonardo-1"
    agent: "Leonardo da Vinci"
    title: "Prototype the classroom flow"
    kind: "option"
    core_claim: "Map the student, teacher, and admin interactions visually before procurement."
    confidence: "medium"
  - insight_id: "Tao-1"
    agent: "Terence Tao"
    title: "Use a toy model first"
    kind: "option"
    core_claim: "Start with one subject, one grade band, and a few measurable interventions before generalizing."
    confidence: "high"
  - insight_id: "Elon-1"
    agent: "Elon Musk"
    title: "Do not pilot so timidly that nothing is learned"
    kind: "challenge"
    core_claim: "A pilot that is too small or too bureaucratic will only prove that bureaucracy is slow."
    confidence: "medium"
  - insight_id: "Drucker-1"
    agent: "Peter Drucker"
    title: "Name the decision owner"
    kind: "option"
    core_claim: "The pilot will drift unless the district decides who owns educational outcomes, teacher workflow, vendor accountability, and stop-go decisions."
    confidence: "high"
  - insight_id: "DuBois-1"
    agent: "W.E.B. Du Bois"
    title: "Test unequal outcomes early"
    kind: "warning"
    core_claim: "A pilot that reports average gains may still deepen inequality if weaker schools become the proving ground for a less reliable system."
    confidence: "high"
```

## Sample Cluster Slate

```yaml
cluster_slate:
  - cluster_id: "C01"
    title: "Bounded pilot with hard metrics"
    type: "option"
    summary: "Run a narrow pilot with predefined measures for learning, trust, and failure."
    supporting_agents:
      - "Carl Sagan"
      - "Marcus Aurelius"
      - "Terence Tao"
    objecting_agents:
      - "Elon Musk"
    main_tension: "Measured caution versus ambition and speed."
    status: "lead"
  - cluster_id: "C02"
    title: "Classroom workflow prototype before procurement"
    type: "option"
    summary: "Diagram and simulate how teachers and students will actually use the system before selecting vendors."
    supporting_agents:
      - "Leonardo da Vinci"
      - "Socrates"
    objecting_agents: []
    main_tension: "More up-front design work versus timeline pressure."
    status: "open"
  - cluster_id: "C03"
    title: "Practice-partner framing"
    type: "frame"
    summary: "Position the system as guided practice support, not as an autonomous teacher."
    supporting_agents:
      - "John Coltrane"
      - "Marcus Aurelius"
    objecting_agents:
      - "Elon Musk"
    main_tension: "Safer public framing versus potentially weaker ambition."
    status: "open"
specialist_overlays:
  - agent: "Peter Drucker"
    target_cluster: "C01"
    pressure: "A pilot without explicit role clarity will create theater instead of learning."
    what_this_lens_sees: "The district has not yet specified who decides continuation, who absorbs workflow overhead, and who is accountable for failure."
    upgrade_path: "Assign decision ownership, operating metrics, and stop-go criteria before launch."
    severity: "high"
  - agent: "W.E.B. Du Bois"
    target_cluster: "C01"
    pressure: "Average success reporting can hide unequal burden."
    what_this_lens_sees: "The pilot needs subgroup visibility and a plan for which schools or students bear the first-wave risk."
    upgrade_path: "Define equity reporting and guard against sacrificing the least-protected students for cleaner pilot data."
    severity: "high"
```

## Sample House View

```yaml
house_view:
  thesis: "Proceed with a bounded pilot, but design it tightly enough to learn something real."
  why: "The strongest consensus is that the city should test the idea, but only with explicit success criteria, visible safeguards, and a classroom workflow that teachers can actually trust."
  best_option_or_frame: "C01"
  minority_report: "Elon Musk argues for a more aggressive pilot scope and warns that excessive caution can turn the project into symbolic theater."
  key_uncertainties:
    - "How teachers adapt after the first visible error"
    - "Whether benefits are concentrated in one student segment"
    - "How procurement constraints distort the product choice"
  recommended_next_moves:
    - "Define success metrics and kill criteria before vendor selection."
    - "Assign pilot ownership and district decision rights explicitly."
    - "Require subgroup reporting so average gains do not hide unequal harm."
    - "Storyboard the teacher and student workflow."
    - "Run a one-subject pilot before any city-wide commitment."
```

## What This Example Demonstrates

- `Carl Sagan`, `Marcus Aurelius`, and `Terence Tao` form the caution-and-rigor spine.
- `Socrates` forces definitional clarity before the city confuses goals.
- `John Coltrane` improves the framing rather than merely adding another feature idea.
- `Leonardo da Vinci` turns the debate into a workflow and prototype question.
- `Elon Musk` keeps the group from mistaking timid process for real learning.
- `Peter Drucker` forces ownership, operating clarity, and real management responsibility.
- `W.E.B. Du Bois` prevents the city from calling the pilot fair based only on district-wide averages.

That balance is the point of the skill: original thinking, but with enough pressure that the result can survive contact with reality.
