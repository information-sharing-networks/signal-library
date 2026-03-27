# Pre-notification Signal
The **Pre-notification** is the first message sent in the Port Health workflow. It declares the "Intent to Import" and provides the Port Health Authority (PHA) with the necessary data to perform a risk assessment before the goods arrive.

## 📋 Data Dictionary

### Header Fields
| Field | Type | Description |
| :--- | :--- | :--- |
| `sourceRef` | String | Your internal system reference (e.g., JOB-12345). |
| `systemCode` | String | The name of your software platform (e.g., TWIN). |
| `category` | Array | Tags for filtering (e.g., `["pre-notification", "live"]`). |

### Payload Details
| Field | Requirement | Description |
| :--- | :--- | :--- |
| `chedNumbers` | **Required** | The Common Health Entry Document reference. |
| `cnCodes` | **Required** | 10-digit Commodity Codes for the goods. |
| `portOfEntry` | **Required** | The UK port where the goods will arrive (e.g., Sevington). |
| `portOfEntryCode` | Optional | The 5-character UN/LOCODE (e.g., `GBSVI`). |
| `transportMeans` | **Required** | An array of objects identifying the Truck, Trailer, or Container. |
| `importerEORI` | **Required** | The GB EORI number of the importing entity. |

## 🚛 Transport Identification
For **RoRo** (Roll-on/Roll-off) movements, please provide both the Truck and the Trailer identifiers if available. This allows the PHA to locate the specific unit on the quay.

```json
"transportMeans": [
  {
    "transportMovementType": "Truck",
    "identifier": "ABC 123"
  },
  {
    "transportMovementType": "Trailer",
    "identifier": "TRL 456",
    "affixedSeal": "SEAL-001"
  }
]
