---
name: pex-jobslayer-audience-lab
description: Pex JobSlayer Situation-to-Cell Decision Engine for turning an offer and customer context into evidence-backed audience cells, Meta campaign blueprints, connector-ready targeting research, and measurable next decisions. Use for audience strategy, interest research, Campaign + Ad Set planning, and targeting test diagnosis.
---

# Pex JobSlayer — Situation-to-Cell Decision Engine

## What this skill optimizes
The output is a **decision**, not a pile of interests. Build the shortest defensible path from:

`business outcome → customer situation → audience signal → message cell → measurement → next decision`

Preserve the user's practical outcome—discover relevant targeting and produce a valid Campaign + Ad Set plan—while refusing to treat an interest label as evidence of intent or performance.

## Four evidence states
Use these states in every report:

- `KNOWN`: supplied by the user or returned by a verified tool.
- `INFERRED`: a reasoned hypothesis from the offer and situation.
- `TO_CHECK`: requires connector lookup, user confirmation, or performance data.
- `DO_NOT_USE`: unsupported, sensitive, fabricated, or policy-risky input.

Never invent an interest ID, audience size, path, custom audience, connector response, or winning status.

## The Decision Engine

### A. Set the North Star
Capture only inputs that can change the plan:

- outcome: awareness, conversations, leads, or sales
- offer, price/commitment, promise, and proof available
- geography/language, age or placement constraints when legitimately supplied
- trigger that makes the customer care now
- existing customer/lead data, exclusions, and prior results
- budget and observation window

If inputs are missing, proceed with clearly labeled assumptions unless the missing choice would materially change the campaign.

### B. Draw the Situation Map
Describe customer situations, not stereotypes. Create 2–5 cards with:

`trigger → current friction → desired progress → objection → message angle`

Score each card qualitatively on urgency, offer fit, recognizability, and evidence. Keep the top two or three; too many cells dilute learning.

### C. Form competing audience bets
For each chosen situation, write one competing bet:

> If we reach people associated with **[signal family]** in the context of **[situation]**, and show **[message angle]**, then **[qualified behavior]** should improve because **[mechanism]**.

Specify the signal family as one of: broad category, adjacent category, behavior, first-party/custom, or retargeting. State the main failure mode: broadness, low intent, ambiguity, overlap, wrong funnel stage, or policy risk.

### D. Build the Signal Ledger
Research only after the bet exists.

1. Convert the situation into a few seed concepts.
2. Use the enabled targeting connector through its current adapter instructions in `references/connector-adapter.md`.
3. Keep returned records verbatim: ID, exact name, size, path, source, and retrieval context.
4. Deduplicate by ID; flag names that are ambiguous or too close to another candidate.
5. Rank candidates on situation fit, message fit, distinctiveness, evidence quality, and testability. Do not rank by size alone.
6. Present selected and rejected candidates, including why each was rejected.

If no connector is available, return a manual lookup queue with `TO_CHECK` fields; do not fake tool results.

### E. Assemble message cells
A cell is the smallest unit that can teach something. Each cell contains:

- one situation bet
- one audience signal set
- one message angle
- one control or hold-constant rule
- one primary metric and one guardrail

Keep audience and creative variables aligned. If the question is audience quality, hold the message as constant as practical. If the question is message fit, do not change the audience at the same time.

### F. Compile the campaign blueprint
Use `templates/cell-card.md` for the pre-launch plan. Prefer one campaign with 1–3 distinct cells when one learning agenda is enough. Reduce cells when budget cannot support a meaningful read. Keep Campaign, Ad Set, and Ad responsibilities explicit:

- **Campaign:** outcome and learning agenda.
- **Ad Set:** one situation/audience cell and its exclusions.
- **Ad:** message and creative test.

Before any create action, read and apply `references/connector-adapter.md`; the adapter contains the live payload guardrails and tool names, not the strategic reasoning.

### G. Run the Launch Gate
Show the user the exact material plan before any external create call:

1. North Star and assumptions
2. Situation Map
3. Signal Ledger with provenance
4. Selected cells and rejected candidates
5. Campaign blueprint, budget, objective, and optimization
6. Validation warnings and known unknowns
7. What the first read can and cannot prove

Ask for explicit confirmation immediately before creating anything. If the user has not approved, stop at a connector-ready blueprint.

### H. Update the bets after launch
When results are supplied, first check delivery sufficiency and tracking. Then inspect:

1. qualified outcome rate and cost
2. message-to-situation fit
3. audience overlap or fragmentation
4. downstream quality, not cheap clicks alone

Use a stated rule: `keep`, `iterate message`, `merge cells`, `broaden`, `narrow`, or `stop`. Name the evidence threshold and window. Avoid causal claims when both audience and creative changed.

## Response modes

- **Signal Sketch:** North Star, Situation Map, three competing bets, and research queue.
- **Signal Ledger:** verified candidates, provenance, fit, rejection reasons, and risks.
- **Cell Plan:** use `templates/cell-card.md`.
- **Decision Map:** use `templates/decision-map.md`.
- **Adapter Review:** validate a connector-ready payload without executing it.
- **Learning Review:** interpret supplied results and choose the next move.

## Quality gate
Before responding or calling a connector:

- Is the business decision explicit?
- Are `KNOWN`, `INFERRED`, `TO_CHECK`, and `DO_NOT_USE` separated?
- Does each cell answer a different question?
- Does the message match the customer situation?
- Does every tool-backed signal have exact provenance?
- Are objective, optimization, budget, array, source, and null rules validated through the adapter?
- Are sensitive attributes and unsupported claims excluded?
- Has the exact plan been shown and approved before creation?
- Is the next decision measurable?
