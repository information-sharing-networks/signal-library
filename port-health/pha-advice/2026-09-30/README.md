# PHA Advice Signal
**Version Snapshot: 2026-09-30**

The **PHA Advice** signal carries feedback, advice or comments from the Port Health Authority (PHA) back to traders and forwarders.

The data structure has not yet been finalised with the PHA, so this schema is deliberately open.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `occurred_at` | **Required** | String (date-time) | When the PHA issued the advice, as an ISO 8601 timestamp (e.g., `2026-09-30T17:00:00Z`). |

All other fields are optional and are not validated. Typical fields include:

| Field | Description |
| :--- | :--- |
| `ehc_reference` | The Export Health Certificate the advice relates to. |
| `status` | A short status code (e.g., `DOCUMENT_SATISFACTORY`). |
| `decision` | The PHA's decision or next step. |
| `comments` | Any further notes from the PHA. |

## Correlation ID (required)

This is an event signal type, so each signal **must** be sent with a `correlation_id` in the submission wrapper, set to the `signal_id` of the Consignment signal the advice is about. Requests containing an event without a `correlation_id` are rejected (400), and a `correlation_id` that isn't found in the same ISN fails with `invalid_correlation_id`.

Correlate to the Consignment directly, not to the EHC Available or other event it responds to (correlation is only one level deep). Use `ehc_reference` to identify the EHC.

See [example.md](./example.md) for a full example.
