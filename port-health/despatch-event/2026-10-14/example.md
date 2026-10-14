# Despatch Event Example

A freight forwarder records that a consignment has left its departure location.

### Signal Content (required fields only)
```json
{
  "occurred_at": "2026-10-10T02:20:00Z"
}
```

### Submission Wrapper
The content is sent inside the submission wrapper. `correlation_id` is required: set it to the `signal_id` of the Consignment signal.
```json
{
  "batch_ref": "despatch-2026-10-10",
  "signals": [
    {
      "local_ref": "despatch-ACME-Test-Load",
      "correlation_id": "3f2b8c1e-7d4a-4e9b-a6c2-5b1d0e8f9a47",
      "content": {
        "occurred_at": "2026-10-10T02:20:00Z"
      }
    }
  ]
}
```
