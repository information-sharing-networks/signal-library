# PHA Advice Example

The Port Health Authority confirms that the initial document check on EHC `EHC-EU-2026-000124` (which superseded `EHC-EU-2026-000123`) was satisfactory.

### Signal Content (required fields only)
```json
{
  "occurred_at": "2026-09-30T17:00:00Z"
}
```

### Signal Content with extra fields
`example_extra_field` and `another_example_field` are placeholders, not real fields. Any extra fields you add are allowed and are not validated, and you can leave them out (see the [README](./README.md)).
```json
{
  "occurred_at": "2026-09-30T17:00:00Z",
  "example_extra_field": "any value",
  "another_example_field": {
    "nested": "objects are allowed too"
  }
}
```

### Submission Wrapper
The content is sent inside the submission wrapper. `correlation_id` is required: set it to the `signal_id` of the Consignment signal.
```json
{
  "batch_ref": "pha-advice-2026-09-30",
  "signals": [
    {
      "local_ref": "pha-advice-EHC-EU-2026-000124-001",
      "correlation_id": "3f2b8c1e-7d4a-4e9b-a6c2-5b1d0e8f9a47",
      "content": {
        "occurred_at": "2026-09-30T17:00:00Z"
      }
    }
  ]
}
```
