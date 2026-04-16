# Prompt Templates

## Contents

- Quick Mode Chair Prompt
- Full Roundtable Kickoff Prompt
- Specialist Activation Prompt
- Round 1 Generate Prompt
- Round 2 Cross-Examination Prompt
- Round 3 Rebuild Prompt
- Round 4 Decision Prompt
- Final Synthesis Prompt

Use these templates when the skill needs explicit round prompts or portable wrappers.

Replace bracketed placeholders before use.

## Quick Mode Chair Prompt

```text
Use $deep-thinkers in quick mode on the following brief:

[BRIEF]

Use all seven core personas:
- Carl Sagan
- Socrates
- John Coltrane
- Marcus Aurelius
- Leonardo da Vinci
- Terence Tao
- Elon Musk

Instructions:
- Before the first generation pass, decide whether `0 to 2` on-call thinkers from `references/on-call-thinkers.md` should activate.
- Publish `goal_posture`, `active_agents`, and `activation_notes` before the insight pass.
- If no specialist materially helps, publish `activation_notes: []`.
- Treat each persona as a reasoning lens, not theatrical roleplay.
- If the brief is unsafe, redirect to defensive, ethical, or refusal-compatible analysis instead of operational help.
- Give exactly one `insight_card` per core persona.
- Give one `insight_card` per active on-call thinker.
- Merge those into `3 to 5` `idea_cluster` entries.
- Run one cross-examination pass with one `cross_exam_note` per core persona.
- Allow each active on-call thinker to emit one `cross_exam_note` or `specialist_overlay`.
- End with a `house_view`, a `minority_report`, `key_uncertainties`, and `recommended_next_moves`.
- Keep dissent visible if it reveals a real tradeoff.
- Surface only the most consequential voices and tensions in the final answer; compress the rest into clusters instead of writing equal-length mini-essays.
- Shape the visible answer to the posture instead of forcing the same headings on every brief.

Output in YAML where practical.
```

## Full Roundtable Kickoff Prompt

```text
Use $deep-thinkers in full roundtable mode on the following brief:

[BRIEF]

Goal:
- [BRAINSTORMING / ANALYSIS / CRITICAL_REVIEW / DECISION / REFLECTION / TECHNICAL_RESEARCH]

Instructions:
- Use all seven core personas unless the brief explicitly narrows the panel.
- Activate `1 to 3` on-call thinkers from `references/on-call-thinkers.md` if the brief has real specialist depth.
- Round 0: publish `problem_frame`, `goal_posture`, `task_type`, `stakes`, `constraints`, `known_unknowns`, `evaluation_criteria`, `active_agents`, and `activation_notes`.
- If the brief is unsafe, shift to defensive, ethical, governance, or refusal-compatible analysis.
- Round 1: each core persona emits `1 to 2` `insight_card` objects.
- Round 1: each active on-call thinker emits `1` `insight_card`.
- Merge Round 1 outputs into stable `C##` cluster IDs.
- Round 2: each core persona emits `1 to 2` `cross_exam_note` objects.
- Round 2: each active on-call thinker emits `1 to 2` `cross_exam_note` or `specialist_overlay` objects.
- Round 3: refine only surviving clusters; stop creating brand-new ideas.
- Round 4: if `goal_posture` is `decision`, `analysis`, or `critical_review`, use the normal voting scheme.
- Round 4: if `goal_posture` is `brainstorming`, prioritize and package instead of over-cutting.
- Round 4: if `goal_posture` is `reflection`, do not force a fake winner; weigh tensions and name practices instead.
- Round 4: if `goal_posture` is `technical_research`, use the voting scheme only to rank hypotheses or architectures, then end with tests and edge cases.
- Active on-call thinkers may cast narrow `advance` or `cut` votes inside their domain when voting is in use.
- Publish the final `house_view` plus `minority_report`, `specialist_overlays`, and `recommended_next_moves`.
- Before finalizing, check that the visible answer shape matches the posture and that every active specialist materially changed the reasoning.

Keep the process sharp, compact, and high-signal.
```

## Specialist Activation Prompt

```text
Choose the on-call thinkers for $deep-thinkers.

Brief:
[BRIEF]

Task:
- Select `0 to 2` specialists for quick mode or `1 to 3` specialists for full roundtable mode.
- Use `references/on-call-thinkers.md` to justify each choice.
- Publish one `activation_note` per selected specialist.
- Explain briefly why similar specialists were not selected if the overlap matters.
- Do not activate specialists just to make the cast look larger.
- If no specialist materially helps, return `activation_notes: []`.
```

## Round 1 Generate Prompt

```text
Round 1 for $deep-thinkers.

Brief:
[BRIEF]

Active agents:
[ACTIVE_AGENTS]

Task:
- Emit `1 to 2` `insight_card` objects per core persona.
- Emit `1` `insight_card` per active on-call thinker.
- Keep each insight distinct.
- Prefer specific reasoning over generic advice.
- Do not critique other personas yet.
- Specialists must stay inside their actual domain.
```

## Round 2 Cross-Examination Prompt

```text
Round 2 for $deep-thinkers.

Current cluster slate:
[CLUSTER_SLATE]

Active agents:
[ACTIVE_AGENTS]

Task:
- Emit `1 to 2` `cross_exam_note` objects per core persona.
- Emit `1 to 2` `cross_exam_note` or `specialist_overlay` objects per active on-call thinker.
- Target overreach, hidden assumptions, edge cases, ethical blind spots, implementation fantasy, or domain-specific risk.
- For each challenge, state what would strengthen the target claim.
- Do not invent new clusters unless the chair explicitly allows it.
```

## Round 3 Rebuild Prompt

```text
Round 3 for $deep-thinkers.

Surviving clusters:
[SURVIVING_CLUSTERS]

Active agents:
[ACTIVE_AGENTS]

Task:
- Strengthen, merge, or narrow the surviving clusters.
- Each core persona should name one condition required for confidence and one experiment or question that reduces uncertainty.
- Each active on-call thinker should name one specialist constraint, one upgrade path, and one naive implementation risk.
- Prefer better structure over more novelty.
```

## Round 4 Decision Prompt

```text
Round 4 for $deep-thinkers.

Surviving clusters:
[SURVIVING_CLUSTERS]

Active agents:
[ACTIVE_AGENTS]

Task:
- For each core persona, label each cluster as `champion`, `advance`, `hold`, or `cut`.
- For each active on-call thinker, cast narrow `advance` or `cut` votes only within that specialist's domain.
- Keep judgments short and decisive.
- Preserve at least one meaningful dissent if the council is split for a real reason.
```

## Final Synthesis Prompt

```text
Produce the final output for $deep-thinkers.

Include:
- `problem_frame`
- `goal_posture`
- `active_agents`
- `activation_notes`
- `insight_ledger`
- `tension_map`
- `cluster_slate`
- `specialist_overlays`
- `house_view`
- `minority_report`
- `key_uncertainties`
- `recommended_next_moves`

If the brief is a decision:
- include `best_option`, `rejected_options`, and `decision_criteria`.

If the brief is reflective or philosophical:
- replace option-heavy wording with `interpretation_clusters` and `guiding_principles`.

If the brief is technical or research-heavy:
- include `hypotheses`, `toy_models`, `tests_or_experiments`, and `edge_cases`.

Translate the council's output into clear language for a human reader while preserving the real disagreements.
Match the visible sections to the posture:
- `brainstorming` = opportunity clusters and next prototypes,
- `analysis` = explanatory frame and key uncertainties,
- `critical_review` = surviving objections and what would change the verdict,
- `decision` = best option, alternatives, criteria, and next moves,
- `reflection` = tensions, principles, and practices or questions,
- `technical_research` = hypotheses, toy models, tests, and edge cases.
```
