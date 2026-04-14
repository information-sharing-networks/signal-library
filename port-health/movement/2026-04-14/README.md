**Draft - schema stil being reviewd**

# Port Health Movement Notification
**Version Snapshot: 2026-04-14**

The **Movement Notification** is the first message sent in the Port Health workflow. It lets the Port Health Authority (PHA) know of a planned import and provides them with the necessary data to perform a risk assessment before the goods arrive.

## Header

| Field | Type | Description |
| :--- | :--- | :--- |
| `originRecordID` | String | Your internal system reference (e.g., JOB-12345). |
| `originSystemCode` | String | The name of your software platform (e.g., TWIN). |
| `category` | Array | Tags for filtering (e.g., `["Movement Notification", "test-network"]`). |

`originRecordID` is an identifier that helps users navigate to the original content on your system.

## Payload

| Field | Requirement | Description |
| :--- | :--- | :--- |
| `portOfExit` | **Required** | The name of the departure port (e.g., Rotterdam). |
| `portOfExitCode` | **Required** | The 5-character UN/LOCODE for departure (e.g., `NLRTM`). |
| `portOfEntry` | **Required** | The UK port where the goods will arrive (e.g., Sevington). |
| `portOfEntryCode` | **Required** | The 5-character UN/LOCODE for arrival (e.g., `GBSVI`). |
| `commodityDescription` | **Required** | Plain-text description of the goods. |
| `cnCodes` | **Required** | Array of 10-digit Commodity Codes. |
| `countryOfOrigin` | **Required** | 2-character ISO country code (e.g., `IE`). |
| `chedNumbers` | **Required** | The Common Health Entry Document references. |
| `importerEORI` | **Required** | The GB EORI number of the importing entity. |
| `location` | **Required** | The current location of the goods at the time of reporting (e.g., the frontier point or departure terminal). |
| `mode` | **Required** | The transit method (e.g., `RoRo` or `LoLo`). |
| `transportMeans` | **Required** | Array of objects identifying the Truck, Trailer, or Container. |
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
```
