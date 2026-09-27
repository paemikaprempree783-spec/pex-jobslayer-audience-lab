# Pex JobSlayer Targeting Decision Schema

Use one record per audience hypothesis or ad set cell. Keep unknowns explicit; never turn missing data into a confident claim.

| Field | Notes |
|---|---|
| hypothesis_id | Stable label, e.g. H1 |
| business_outcome | awareness, conversations, leads, sales |
| situation | Trigger/context, not a stereotype |
| desired_progress | Outcome the person wants |
| objection | Main reason the offer may be rejected |
| signal_family | broad_interest, adjacent_interest, behavior, custom_audience, retargeting |
| source_tool | search_interest, suggest_interest, first_party, user_supplied, unknown |
| interest_id | Tool-returned ID or unknown |
| interest_name | Exact returned name or user label |
| interest_size | Exact returned value or unknown |
| interest_path | Exact returned path or unknown |
| fit_reason | Why the signal may map to the situation |
| message_match | Creative angle required |
| risk | Too broad, too narrow, low intent, overlap, policy, unknown |
| evidence_level | KNOWN, INFERRED, TO_VERIFY, UNSAFE |
| primary_metric | Metric tied to the business outcome |
| guardrail | Quality, cost, or policy protection |
| read_rule | Keep, iterate, merge, narrow, expand, or stop rule |
