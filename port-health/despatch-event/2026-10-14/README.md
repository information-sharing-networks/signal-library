# Despatch Event
**Version Snapshot: 2026-10-14**

The **Despatch** event records that a consignment has been despatched: the goods have departed and the movement is underway.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `occurred_at` | **Required** | String (date-time) | When the consignment was despatched, as an ISO 8601 timestamp (e.g., `2026-10-10T02:20:00Z`). |

Any other fields are allowed and are not validated, so senders can add extra details in whatever format suits them. Departure and arrival locations are already in the Consignment signal, so they don't need to be repeated here.

## Correlation ID (required)

This is an event signal type, so each signal **must** be sent with a `correlation_id` in the submission wrapper, set to the `signal_id` of the Consignment signal that was despatched. Requests containing an event without a `correlation_id` are rejected (400), and a `correlation_id` that isn't found in the same ISN fails with `invalid_correlation_id`.

See [example.md](./example.md) for a full example.
