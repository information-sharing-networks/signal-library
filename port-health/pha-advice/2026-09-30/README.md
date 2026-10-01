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

To link the advice to the signal it responds to (e.g., an EHC Available signal), send it with that signal's `correlation_id`.

See [example.md](./example.md) for a full example.
