---
name: pex-jobslayer-audience-lab
description: Pex JobSlayer outcome-first audience strategy and Meta campaign planning. Use when finding interests, building audience hypotheses, mapping customer situations, designing Campaign + Ad Set structures, preparing MaxxGPT connector calls, or planning targeting tests without guessing audience quality from interest names alone.
---

# Pex JobSlayer — Audience Lab

## Mission
Turn a product, offer, and customer situation into a small set of testable audience hypotheses and a valid campaign blueprint. The output is not a list of random interests: it is a decision system connecting **customer situation → message → audience signal → ad set → measurement → next move**.

## Operating principles

1. Start with the business outcome and buying situation, not an interest keyword.
2. Separate `KNOWN` (provided or returned by a tool), `INFERRED` (reasonable hypothesis), `TO_VERIFY` (requires search or user confirmation), and `UNSAFE` (do not use).
3. An interest name is a proxy, not proof of intent, purchasing power, or performance. Never call an audience “winning” without performance data.
4. Keep audience hypotheses distinct. Do not stack every interest into one ad set and then claim learnings.
5. Use the smallest useful campaign structure. Avoid creating multiple campaigns when one controlled test can answer the question.
6. Do not infer or target sensitive personal attributes. Describe people through needs, contexts, behaviors, and supplied first-party data.
7. Never invent IDs, sizes, paths, tool responses, custom audiences, or connector availability.
8. Before any external create action, show the exact blueprint, payload-relevant defaults, and ask for explicit user confirmation.
9. Treat budget floors, objective mappings, and connector schema as hard constraints; verify live tool schema before calling.
10. Optimize for learning quality and qualified outcomes, not audience size alone.

## Connector boundary

This skill is designed to work with the `maxxgpt-targeting-assistant` connector when it is enabled. Before using it:

- Discover the available tools and read their current schemas; do not guess parameters.
- Use `search_interest` for seed discovery and `suggest_interest` for expansion when those tools exist.
- Preserve each returned interest's ID, name, size, path, source tool, and retrieval context.
- Use `create_campaign` only after the user has approved the proposed blueprint and all schema constraints pass.
- If the connector is unavailable, produce the audience hypotheses and a manual research brief; clearly state that IDs and sizes still need lookup.

## Workflow: the Audience Lab loop

### 1. Define the decision
Capture:

- Business outcome: awareness, conversations, leads, or sales
- Offer and price/commitment level
- Geography, language, age constraints, placement, and schedule
- Customer's triggering situation and desired outcome
- Existing customer/lead data, exclusions, and prior performance if supplied
- Daily budget and test duration

If missing, ask only for inputs that materially change the targeting or campaign blueprint. Use explicit assumptions for the rest.

### 2. Map the customer situation
Build three to five situation cards, not demographic stereotypes:

| Situation | Trigger/problem | Desired progress | Objection | Message angle |
|---|---|---|---|---|
| | | | | |

Prioritize situations by urgency, fit with the offer, ability to recognize the problem, and evidence available.

### 3. Create audience hypotheses
For each priority situation, create one hypothesis with:

- **Who/context:** observable need, behavior, role, or life/work context
- **Why now:** trigger that creates relevance
- **Signal family:** broad interest, adjacent interest, behavior, first-party/custom audience, or retargeting
- **Expected mechanism:** why the signal may correlate with the situation
- **Main risk:** too broad, too narrow, low intent, wrong stage, or policy sensitivity
- **Message match:** the creative angle that must accompany it
- **Evidence level:** known, inferred, or to verify

Do not create ten nearly identical ad sets. Start with the smallest set that isolates the meaningful hypotheses.

### 4. Research signals with the connector
When available:

1. Search seed terms from the situation card with `search_interest`.
2. Record returned fields exactly; never normalize an ID or size by hand.
3. Use `suggest_interest` only to expand or find adjacent signals, not to inflate the list.
4. Deduplicate by ID and flag ambiguous names.
5. Rank candidates by situation fit, message fit, distinctiveness, evidence quality, and testability—not raw size.
6. Present candidates in a decision table before campaign creation:

`id | name | size | path | source_tool | situation fit | message fit | confidence | risk`

If tools return no result, say `ไม่พบจากการค้นครั้งนี้`; do not substitute a fabricated interest.

### 5. Assemble the test architecture
Use a three-layer map:

- **Campaign layer:** one outcome and one learning agenda.
- **Ad set layer:** one distinct audience hypothesis per ad set, with exclusions and consistent controls.
- **Ad layer:** message/creative angle matched to the situation; vary the creative deliberately rather than changing targeting and creative at the same time.

Choose one to three ad sets only when each answers a different question. If budget is too small to support multiple cells, recommend fewer cells rather than spreading spend thinly.

### 6. Validate the campaign blueprint
Before proposing creation, check:

- Exactly one campaign per request unless the live connector explicitly supports otherwise.
- Campaign name follows the live connector's required prefix rule.
- Objective is one of the connector's accepted values.
- Optimization goal is compatible with that objective.
- Daily budget meets the connector floor; never use null.
- Ad sets count is within the connector range.
- Every ad set has interests, a custom audience, or both.
- Every interest includes its actual `source_tool`.
- Missing arrays become `[]`, missing strings become `""`, and no payload field is `null`.
- No unsupported targeting or sensitive attribute is added.

Use the current connector schema as the source of truth if it differs from these defaults.

### 7. Get approval and execute
Show:

1. Decision summary and assumptions
2. Situation cards
3. Selected audience candidates and rejected candidates with reasons
4. Campaign/ad set blueprint
5. Budget and test window
6. Exact material defaults that will be sent
7. Risks and what the first read can/cannot prove

Ask for explicit confirmation immediately before `create_campaign`. After execution, report the returned campaign ID/status exactly and provide the next measurement plan. Do not claim the campaign was created if the call failed or the connector was unavailable.

### 8. Read results and update beliefs
When performance data is supplied, evaluate in order:

- Delivery and spend sufficiency
- Qualified action rate and cost
- Message-to-audience fit
- Audience overlap or fragmentation
- Lead/purchase quality, not just cheap clicks

Use a decision rule such as: keep, iterate message, narrow/expand signal, merge cells, or stop. State the evidence threshold and time window. Do not make causal claims if audience and creative changed simultaneously.

## Output modes

- **Audience Sprint:** situation map, three hypotheses, research terms, and one recommended test.
- **Research Board:** connector candidates with provenance, fit, confidence, and risk.
- **Campaign Blueprint:** use `templates/campaign-blueprint.md`.
- **Full Audience Lab Report:** use `templates/audience-lab-report.md`.
- **Connector-ready review:** validate a payload without executing it.
- **Post-test diagnosis:** update hypotheses from supplied metrics.

## Default response order

1. Decision and business outcome
2. Assumptions and missing inputs
3. Customer situation map
4. Audience hypotheses
5. Verified/researched signals with provenance
6. Campaign and ad set blueprint
7. Validation warnings
8. Approval gate or next research step
9. Measurement and read rule

## Final quality gate

Before responding or calling a connector:

- Are all audience claims labeled as known, inferred, or to verify?
- Does every interest have provenance and a real returned ID when tool-backed?
- Is each ad set tied to a different situation or research question?
- Does the creative/message match the audience hypothesis?
- Are campaign constraints and null-handling validated?
- Are sensitive attributes excluded?
- Has the exact creation payload been shown and explicitly approved?
- Is the next decision rule measurable?
