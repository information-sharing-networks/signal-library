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

## Correlation ID (required)

This is an event signal type, so each signal **must** be sent with a `correlation_id` in the submission wrapper, set to the `signal_id` of the Consignment signal the EHC is for. Requests containing an event without a `correlation_id` are rejected (400), and a `correlation_id` that isn't found in the same ISN fails with `invalid_correlation_id`.

Correlate to the Consignment directly, not to the original EHC Available signal (correlation is only one level deep, so events correlated to other events don't appear with the Consignment). Identify the replaced EHC in `reason`.

See [example.md](./example.md) for a full example.
