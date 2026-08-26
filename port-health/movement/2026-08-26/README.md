# Port Health Movement Notification
**Version Snapshot: 2026-08-25**

The **Movement Notification** is the first message sent in the Port Health workflow. It lets the Port Health Authority (PHA) know of a planned import and provides them with the necessary data to perform a risk assessment before the goods arrive.

## Header

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `originRecordID` | **Required** | String | Your internal system reference (e.g., JOB-12345). |
| `originSystemCode` | **Required** | String | The name of your software platform (e.g., TWIN). |
| `category` | Optional | Array | Tags for filtering (e.g., `["Movement Notification", "test-network"]`). |

`originRecordID` is an identifier that helps users navigate to the original content on your system.

## Payload

| Field | Requirement | Description |
| :--- | :--- | :--- |
| `portOfExit` | Optional | The name of the departure port (e.g., Rotterdam). Human readable|
| `portOfExitCode` | Optional | The 5-character UN/LOCODE for departure (e.g., `NLRTM`). |
| `portOfEntry` | Optional | The UK port where the goods will arrive (e.g., Sevington). Human readable form|
| `portOfEntryCode` | **Required** | The 5-character UN/LOCODE for arrival (e.g., `GBSVI`). |
| `commodityDescription` | Optional | Plain-text description of the goods. |
| `cnCodes` | Optional | Array of 10-digit Commodity Codes. |
| `countryOfOrigin` | Optional | 2-character ISO country code (e.g., `IE`). |
| `chedNumbers` | Optional | The Common Health Entry Document references. |
| `importerEORI` | Optional | The GB EORI number of the importing entity. |
| `exporterEORI` | Optional | The EORI number of the exporting entity. |
| `location` | Optional | The last known location of the goods at the time of reporting (e.g., the frontier point or departure terminal). |
| `mode` | Optional | The transit method (e.g., `RoRo` or `LoLo`). |
| `transportMeans` | Optional | Array of objects identifying the Truck, Trailer, or Container. |
| `sealNumbers` | Optional | Array of all security seal numbers applied to the load. |

For **RoRo** (Roll-on/Roll-off) movements, please provide both the Truck and the Trailer identifiers if available:

```json
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
]