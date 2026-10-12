# Consignment Signal
**Version Snapshot: 2026-09-30**


The **Consignment** signal carries a [UN/CEFACT Consignment](https://vocabulary.uncefact.org/Consignment). The consignment data sits directly at the root of the signal content — there is no wrapper object.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `identifier` | **Required** | String | The unique identifier for this consignment (e.g., `ACME-Test-Load`). |
| `atArrivalTransportMovement.arrivalEvent.occurrenceLogisticsLocation.identifier.@value` | **Required** | String | The 5-character UN/LOCODE of the arrival location (e.g., `GBDVR`): a 2-letter country code followed by 3 uppercase letters or digits 2–9. Must match `^[A-Z]{2}[A-Z2-9]{3}$`. |

### Arrival UN/LOCODE (required for routing)

The arrival UN/LOCODE in `atArrivalTransportMovement` is **required**, because it is used to route each Consignment signal to the right ISN. Signals without it, or with a value that isn't a valid UN/LOCODE, are rejected.

```json
"atArrivalTransportMovement": {
  "arrivalEvent": {
    "occurrenceLogisticsLocation": {
      "identifier": {
        "@type": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
        "@value": "GBDVR"
      },
      "name": "Dover",
      "type": "LogisticsLocation"
    }
  }
}
```

Use this path as the routing field in signalsd:

```
atArrivalTransportMovement.arrivalEvent.occurrenceLogisticsLocation.identifier.@value
```

All other fields are optional and are not validated. Senders should follow the [UN/CEFACT Consignment](https://vocabulary.uncefact.org/Consignment) vocabulary, for example:

| Field | Description |
| :--- | :--- |
| `@context` | JSON-LD context (e.g., `https://vocabulary.uncefact.org/unece-context-D23B.jsonld`). |
| `type` | The UN/CEFACT class of the data (`Consignment`). |
| `globalId` | A globally unique ID for the consignment (e.g., a `urn:uuid:`). |
| `atDepartureTransportMovement` | Departure details: location, scheduled time and transport mode. |
| `atArrivalTransportMovement` | Arrival details: scheduled time and transport mode (the arrival UN/LOCODE inside it is required — see above). |
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
