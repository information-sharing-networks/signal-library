# EHC Superseded Example

The EHC for consignment `ACME-Test-Load` has been reissued with a corrected net weight. The new certificate replaces `EHC-EU-2026-000123`.

### Signal Content
```json
{
  "occurred_at": "2026-09-30T16:10:00Z",
  "ehc_reference": "EHC-EU-2026-000124",
  "reason": "Replaces EHC-EU-2026-000123: net weight corrected from 12,500 kg to 13,250 kg."
}
```

### Submission Wrapper
The content is sent inside the submission wrapper. `correlation_id` is required: set it to the `signal_id` of the Consignment signal.
```json
{
  "batch_ref": "ehc-2026-09-30",
  "signals": [
    {
      "local_ref": "ehc-superseded-EHC-EU-2026-000124",
      "correlation_id": "3f2b8c1e-7d4a-4e9b-a6c2-5b1d0e8f9a47",
      "content": {
        "occurred_at": "2026-09-30T16:10:00Z",
        "ehc_reference": "EHC-EU-2026-000124",
        "reason": "Replaces EHC-EU-2026-000123: net weight corrected from 12,500 kg to 13,250 kg."
      }
    }
  ]
}
```
