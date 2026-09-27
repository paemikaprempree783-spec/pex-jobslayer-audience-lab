# Pex JobSlayer Decision Record Schema

Use one row per competing audience bet or message cell.

| Field | Meaning |
|---|---|
| record_id | Stable cell/bet ID |
| outcome | Awareness, conversations, leads, or sales |
| situation | Trigger and context, not demographic stereotype |
| friction | Current problem or objection |
| desired_progress | Outcome the person wants |
| signal_family | Broad, adjacent, behavior, custom, or retargeting |
| signal_id | Exact returned ID or unknown |
| signal_name | Exact returned name or user-provided label |
| signal_size | Exact returned value or unknown |
| signal_path | Exact returned path or unknown |
| provenance | Tool or source that supplied the signal |
| evidence_state | KNOWN, INFERRED, TO_CHECK, DO_NOT_USE |
| mechanism | Why the signal may map to the situation |
| message_angle | Creative promise/proof angle |
| failure_mode | Broadness, low intent, ambiguity, overlap, stage, policy, unknown |
| hold_constant | What remains unchanged in the test |
| primary_metric | Main outcome metric |
| guardrail | Quality, cost, or policy protection |
| read_rule | Keep, iterate, merge, broaden, narrow, or stop |
