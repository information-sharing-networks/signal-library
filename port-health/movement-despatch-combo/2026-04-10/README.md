**Deprecated - use the individual _movement_ and _despatch_ signal types for new isns

# Port Health Movement Notification & Despatch (Combo)
**Version Snapshot: 2026-04-10**

This directory contains the combined movement/despatch signal type definitions. 

## 🧩️ Header data
| Field | Type | Description |
| :--- | :--- | :--- |
| `originRecordID` | String | Your internal system reference (e.g., JOB-12345). |
| `originSystemCode` | String | The name of your software platform (e.g., TWIN). |
| `category` | Array | Tags for filtering (e.g., `["Movement Notification", "test-network"]`). |

`originRecordID` is an identifier that helps users navigate to the original content on your system.

## 🧩 Payload
Two payloads are supported: _Movement_ and _Despatch_.
 The `oneOf` logic in the schema will validate the payload against either the Movement or Despatch definitions.

### 1. Movement payload
The **Movement payload** is the first message sent in the Port Health workflow. It let's the Port Health Authority (PHA) know of a planned import and provides them with the necessary data to perform a risk assessment before the goods arrive.


### Payload Details
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

### 2. Despatch (Movement Confirmation)
Sent when the goods depart. Focuses on when and where the movement is happening.

Note: use a different `local_ref` than the original Movement Notification — otherwise the server will treat it as a correction to the original record. To link the Despatch to the original Movement Notification, set `correlation_id` in the **submission wrapper** to the `signal_id` of the original Movement Notification signal. See the [OVERVIEW](../../../OVERVIEW.md) for details on the submission wrapper.

### Header Fields
| Field | Type | Description |
| :--- | :--- | :--- |
| `originRecordID` | String | Your internal trip or load ID (e.g., TRIP-4455). |
| `originSystemCode` | String | The name of the dispatching software (e.g., TWIN). |

### Payload Details
| Field | Requirement | Description |
| :--- | :--- | :--- |
| `plannedDepartureTime` | **Required** | The scheduled time of departure (ISO 8601). |
| `actualDepartureTime` | Optional | The timestamp the vehicle actually left the yard. |
| `portOfExit` | **Required** | The departure port name (e.g., Rotterdam). |
| `portOfExitCode` | **Required** | The 5-character UN/LOCODE for departure (e.g., `NLRTM`). |
| `portOfEntry` | **Required** | The intended UK arrival port (e.g., Sevington). |
| `portOfEntryCode` | **Required** | The 5-character UN/LOCODE for arrival (e.g., `GBSVI`). |
| `destinationPlant` | Optional | The specific processing facility where the consignment is being delivered. |

## 🕒 Time Formatting
All timestamps must follow the **ISO 8601** (UTC) format:
`YYYY-MM-DDTHH:MM:SSZ`  
*Example:* `2026-03-27T15:20:00Z`

## 📁 Related Links
* [Back to Master Port Health Guide](../README-porth-health.md)