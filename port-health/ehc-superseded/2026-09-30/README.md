# EHC Superseded Notification Signal
**Version Snapshot: 2026-09-30**

The **EHC Superseded** signal alerts Port Health Authorities (PHAs) that an Export Health Certificate (EHC) has been superseded by a new one. PHAs should use the new EHC and disregard the one it replaces.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `occurred_at` | **Required** | String (date-time) | When the EHC was superseded, as an ISO 8601 timestamp (e.g., `2026-09-30T16:10:00Z`). |
| `ehc_reference` | **Required** | String | The reference of the **new** EHC (e.g., `EHC-EU-2026-000124`). |
| `reason` | **Required** | String | Why the original EHC was replaced. Include the old EHC reference here (e.g., `Replaces EHC-EU-2026-000123: net weight corrected`). |

Any other fields are allowed and are not validated, so senders can add extra details in whatever format suits them.

To link this signal to the original EHC Available signal in the ISN, send it with that signal's `correlation_id`.

See [example.md](./example.md) for a full example.
