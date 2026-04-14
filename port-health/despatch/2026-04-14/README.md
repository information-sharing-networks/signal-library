**Draft - schema stil being reviewd**

# Port Health Despatch
**Version Snapshot: 2026-04-14**

The **Despatch** signal is sent when goods depart. It confirms the movement is underway and should be linked to the original Movement Notification.

To link a Despatch to its Movement Notification, set `correlation_id` in the **submission wrapper** to the `signal_id` of the original Movement Notification signal. Note: use a different `local_ref` than the original — otherwise the server will treat it as a correction to the original record. See the [OVERVIEW](../../../OVERVIEW.md) for details on the submission wrapper.

## Header

| Field | Type | Description |
| :--- | :--- | :--- |
| `originRecordID` | String | Your internal trip or load ID (e.g., TRIP-4455). |
| `originSystemCode` | String | The name of the dispatching software (e.g., TWIN). |
| `category` | Array | Tags for filtering (e.g., `["despatch", "test-network"]`). |

## Payload

| Field | Requirement | Description |
| :--- | :--- | :--- |
| `plannedDepartureTime` | **Required** | The scheduled time of departure (ISO 8601). |
| `actualDepartureTime` | Optional | The timestamp the vehicle actually left the yard. |
| `portOfExit` | **Required** | The departure port name (e.g., Rotterdam). |
| `portOfExitCode` | **Required** | The 5-character UN/LOCODE for departure (e.g., `NLRTM`). |
| `portOfEntry` | **Required** | The intended UK arrival port (e.g., Sevington). |
| `portOfEntryCode` | **Required** | The 5-character UN/LOCODE for arrival (e.g., `GBSVI`). |
| `destinationPlant` | Optional | The specific processing facility where the consignment is being delivered. |

## Time Formatting
All timestamps must follow the **ISO 8601** (UTC) format:
`YYYY-MM-DDTHH:MM:SSZ`  
*Example:* `2026-03-27T15:20:00Z`
