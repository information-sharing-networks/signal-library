# Consignment Signal
**Version Snapshot: 2026-09-30**


The **Consignment** signal carries a [UN/CEFACT Consignment](https://vocabulary.uncefact.org/Consignment). The consignment data sits directly at the root of the signal content — there is no wrapper object.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `identifier` | **Required** | String | The unique identifier for this consignment (e.g., `ACME-Test-Load`). |

All other fields are optional and are not validated. Senders should follow the [UN/CEFACT Consignment](https://vocabulary.uncefact.org/Consignment) vocabulary, for example:

| Field | Description |
| :--- | :--- |
| `@context` | JSON-LD context (e.g., `https://vocabulary.uncefact.org/unece-context-D23B.jsonld`). |
| `type` | The UN/CEFACT class of the data (`Consignment`). |
| `globalId` | A globally unique ID for the consignment (e.g., a `urn:uuid:`). |
| `atDepartureTransportMovement` | Departure details: location, scheduled time and transport mode. |
| `atArrivalTransportMovement` | Arrival details: location, scheduled time and transport mode. |
| `includedConsignment` | The consignments in the load, including consignor, consignee and goods items. |
| `utilizedTransportEquipment` | The vehicles or equipment used (e.g., a trailer registration). |
| `weightUnitGrossWeightMeasure` | Gross weight of the load. |
| `weightUnitNetWeightMeasure` | Net weight of the load. |

## What the old wrapper fields are replaced by

| Old field | Now handled by |
| :--- | :--- |
| `type` (`Create` / `Update`) | New signals are sent without a `correlation_id`; updates use the `correlation_id` of the signal they relate to. |
| `actor` | signalsd records the account that submitted each signal. |
| `object` | The consignment data now sits at the root of the signal content. |

See [example.md](./example.md) for a full example.
