# Pre-notification Signal
The **Pre-notification** is the first message sent in the Port Health workflow. It declares the "Intent to Import" and provides the Port Health Authority (PHA) with the necessary data to perform a risk assessment before the goods arrive.

## 📋 Data Dictionary

### Header Fields
| Field | Type | Description |
| :--- | :--- | :--- |
| `sourceRef` | String | Your internal system reference (e.g., JOB-12345). |
| `systemCode` | String | The name of your software platform (e.g., TWIN). |
| `category` | Array | Tags for filtering (e.g., `["pre-notification", "test-network"]`). |

### Payload Details
| Field | Requirement | Description |
| :--- | :--- | :--- |
| `portOfExit` | **Required** | The name of the departure port (e.g., Rotterdam). |
| `portOfExitCode` | Optional | The 5-character UN/LOCODE for departure (e.g., `NLRTM`). |
| `portOfEntry` | **Required** | The UK port where the goods will arrive (e.g., Sevington). |
| `portOfEntryCode` | Optional | The 5-character UN/LOCODE for arrival (e.g., `GBSVI`). |
| `commodityDescription` | **Required** | Plain-text description of the goods. |
| `cnCodes` | **Required** | Array of 10-digit Commodity Codes. |
| `countryOfOrigin` | **Required** | 2-character ISO country code (e.g., `IE`). |
| `chedNumbers` | **Required** | The Common Health Entry Document references. |
| `importerEORI` | **Required** | The GB EORI number of the importing entity. |
| `location` | **Required** | The current location of the goods at the time of reporting (e.g., the frontier point or departure terminal). |
| `mode` | **Required** | The transit method (e.g., `RoRo` or `LoLo`). |
| `transportMeans` | **Required** | Array of objects identifying the Truck, Trailer, or Container. |
| `sealNumbers` | Optional | Array of all security seal numbers applied to the load. |

## 🚛 Transport Identification
For **RoRo** (Roll-on/Roll-off) movements, please provide both the Truck and the Trailer identifiers if available.

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
