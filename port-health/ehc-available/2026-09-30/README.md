# EHC Available Notification Event
**Version Snapshot: 2026-09-30**

The **EHC Available** signal notifies Port Health Authorities (PHAs) that an Export Health Certificate (EHC) is ready to pull from the ISN.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `occurred_at` | **Required** | String (date-time) | When the EHC became available, as an ISO 8601 timestamp (e.g., `2026-09-30T14:25:00Z`). |
| `ehc_reference` | **Required** | String | The unique EHC reference number (e.g., `EHC-EU-2026-000123`). |

Any other fields are allowed and are not validated. Useful optional fields include:

| Field | Description |
| :--- | :--- |
| `consignment_id` | The `identifier` of the related Consignment signal (e.g., `ACME-Test-Load`). |
| `issuing_authority` | The authority that issued the EHC. |
| `commodity_description` | Plain-text description of the goods. |

## Correlation ID (required)

This is an event signal type, so each signal **must** be sent with a `correlation_id` in the submission wrapper, set to the `signal_id` of the Consignment signal the EHC is for. Requests containing an event without a `correlation_id` are rejected (400), and a `correlation_id` that isn't found in the same ISN fails with `invalid_correlation_id`.

See [example.md](./example.md) for a full example.
