# Connector Adapter — Targeting Research and Campaign Creation

Read this file only when the MaxxGPT targeting connector is enabled or a connector-ready payload is requested. The live MCP schema is authoritative; inspect the current tool definitions before calling.

## Research mapping

- Seed discovery: `search_interest`
- Adjacent expansion: `suggest_interest`
- Creation action: `create_campaign`

Preserve the returned fields exactly. Every interest record used in a payload must retain its actual source tool. If a tool is missing or returns no result, mark the field `TO_CHECK` and do not invent a substitute.

## Payload guardrails from the current adapter contract

- One campaign per request.
- Campaign name must use the connector-required prefix; inspect the live schema before sending.
- Accepted objectives currently include `OUTCOME_AWARENESS`, `OUTCOME_ENGAGEMENT`, and `OUTCOME_SALES`.
- Current objective mapping: awareness → `REACH`; engagement/sales → `CONVERSATIONS`.
- Daily budget must be a numeric value at or above the connector floor (currently 150 unless the live schema changes).
- Use 1–3 ad sets when required by the current schema.
- Every ad set needs `interests`, `custom_audience`, or both.
- Every interest must include `source_tool` with the real discovery tool.
- Missing arrays use `[]`; missing strings use `""`; never send `null`.
- Do not send unsupported or sensitive targeting.

## Preflight sequence

1. Inspect current tool schemas; never rely on memory for parameter names.
2. Compile the approved Cell Plan into the connector payload.
3. Run every guardrail above and report any mismatch.
4. Show the final material defaults and exact campaign/ad set plan.
5. Obtain explicit user confirmation.
6. Call `create_campaign` once.
7. Report returned ID/status verbatim; never imply success after an error.
