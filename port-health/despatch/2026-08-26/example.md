# Despatch Example

The signal content (submitted in the `content` field of the wrapper):
```json
{
  "originRecordID": "TRIP-4455",
  "originSystemCode": "TWIN",
  "category": ["despatch"],
  "payload": {
    "plannedDepartureTime": "2026-03-27T15:00:00Z",
    "actualDepartureTime": "2026-03-27T15:20:00Z",
    "destinationPlant": "Avara foods",
    "portOfExit": "Rotterdam",
    "portOfExitCode": "NLRTM",
    "portOfEntry": "Sevington",
    "portOfEntryCode": "GBSVI"
  }
}
```

To link this Despatch to its Movement Notification, set `correlation_id` in the submission wrapper to the `signal_id` of the original Movement Notification:
```json
{
  "batch_ref": "daily-sync-2026-03-27",
  "signals": [
    {
      "content": {},
      "correlation_id": "ae761d05-a10f-4507-a091-290c987d8b5e",
      "local_ref": "TRIP-4455"
    }
  ]
}
```
