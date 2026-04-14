# movement
```json
{
  "originRecordID": "PRE123456",
  "originSystemCode": "TWIN",
  "category": ["Movement Notification"],
  "payload": {
    "portOfExit": "Rotterdam",
    "portOfExitCode": "NLRTM",
    "portOfEntry": "Sevington", 
    "portOfEntryCode": "GBSVI",
    "commodityDescription": "Fresh boneless bovine meat",
    "cnCodes": ["0201300010", "0201200090"],
    "countryOfOrigin": "IE",
    "chedNumbers": ["GBX123456789"], 
    "importerEORI": "GB123456789",
    "location": "Port of Dover",
    "mode": "RoRo",
    "transportMeans": [ 
      {
        "transportMovementType": "Truck",
        "identifier": "ABC123"
      },
      {
        "transportMovementType": "Trailer",
        "identifier": "TRL12345",
        "affixedSeal": "SEAL1234"
      }
    ],
    "sealNumbers": ["SEAL1234"] 
  }     
}
```
# despatch 
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

To link this Despatch to its Movement Notification, set `correlation_id` in the submission wrapper:
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

