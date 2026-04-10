# Despatch Signal
The **Despatch** signal is the second step in the Port Health workflow. It is sent when the goods have physically departed the loading location and are en route to the UK.

## 🔗 The Importance of Correlation
This signal **must** include a `correlationId`. This UUID is the unique identifier you received from the API after submitting the **Movement Notification**. 

Without this ID, the system cannot link the departure time to the commodity data (CHEDs, CN Codes), which will delay the risk assessment at the port.

## 📋 Data Dictionary

### Header Fields
| Field | Type | Description |
| :--- | :--- | :--- |
| `originRecordID` | String | Your internal trip or load ID (e.g., TRIP-4455). |
| `originSystemCode` | String | The name of the dispatching software (e.g., WMS-LIVERPOOL). |
| `correlationId` | UUID | **Mandatory.** The ID from the Movement Notification signal. |

### Payload Details
| Field | Requirement | Description |
| :--- | :--- | :--- |
| `plannedDepartureTime` | **Required** | The scheduled time of departure (ISO 8601). |
| `actualDepartureTime` | Optional | The timestamp the vehicle actually left the yard. |
| `portOfExit` | **Required** | The departure port name (e.g., Rotterdam). |
| `portOfExitCode` | Optional | UN/LOCODE of the actual departure point (e.g., `NLRTM`). |
| `portOfEntry` | **Required** | The intended UK arrival port (e.g., Sevington). |
| `portOfEntryCode` | Optional | UN/LOCODE of the intended UK arrival point (e.g., `GBSVI`). |
| `destinationPlant` | Optional | The final delivery location for the goods. |

## 🕒 Time Formatting
All timestamps must follow the **ISO 8601** (UTC) format:
`YYYY-MM-DDTHH:MM:SSZ`  
*Example:* `2026-03-27T15:20:00Z`

## 📁 Related Links
* [View Despatch Example](./despatch-example.json)
* [Back to Master Port Health Guide](../README.md)
