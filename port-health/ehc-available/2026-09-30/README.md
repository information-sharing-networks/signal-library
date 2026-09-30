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
| `consignment_id` | The `identifier` of the related Consignment signal (e.g., `ABC-Test-Load`). |
| `issuing_authority` | The authority that issued the EHC. |
| `commodity_description` | Plain-text description of the goods. |

To link this signal to an existing Consignment signal in the ISN, send it with that signal's `correlation_id`.

See [example.md](./example.md) for a full example.
