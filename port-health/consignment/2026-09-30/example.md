# Consignment Example

A road consignment from Calais (`FRCQF`) to Dover (`GBDVR`), using the [UN/CEFACT vocabulary](https://vocabulary.uncefact.org/). The data sits directly at the root of the signal content.

The arrival UN/LOCODE is at `atArrivalTransportMovement.arrivalEvent.occurrenceLogisticsLocation.identifier.@value`.

### Signal Content
```json
{
  "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
  "atArrivalTransportMovement": {
    "arrivalEvent": {
      "occurrenceLogisticsLocation": {
        "identifier": {
          "@type": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
          "@value": "GBDVR"
        },
        "name": "Dover",
        "type": "LogisticsLocation"
      },
      "scheduledOccurrenceDateTime": "2026-10-10T05:00:00+01:00",
      "type": "TransportEvent"
    },
    "departureEvent": null,
    "loadingEvent": null,
    "transportModeCode": "unece:TransportModeCodeList#3",
    "type": "TransportMovement",
    "unloadingEvent": null
  },
  "atDepartureTransportMovement": {
    "arrivalEvent": null,
    "departureEvent": {
      "occurrenceLogisticsLocation": {
        "identifier": {
          "@type": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
          "@value": "FRCQF"
        },
        "name": "Calais",
        "type": "LogisticsLocation"
      },
      "scheduledOccurrenceDateTime": "2026-10-10T03:00:00+01:00",
      "type": "TransportEvent"
    },
    "loadingEvent": null,
    "transportModeCode": "unece:TransportModeCodeList#3",
    "type": "TransportMovement",
    "unloadingEvent": null
  },
  "consigneeParty": null,
  "consignorParty": null,
  "globalId": "6-GB-GB123456789000-260510-018",
  "identifier": "Test-260510-018",
  "includedConsignment": [
    {
      "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
      "atArrivalTransportMovement": null,
      "atDepartureTransportMovement": null,
      "consigneeParty": null,
      "consignorParty": null,
      "globalId": null,
      "identifier": "260510-018",
      "includedConsignment": null,
      "includedConsignmentItem": null,
      "loadingLocation": null,
      "packageQuantity": null,
      "specifiedTransportMovement": {
        "arrivalEvent": null,
        "departureEvent": null,
        "loadingEvent": {
          "occurrenceLogisticsLocation": null,
          "scheduledOccurrenceDateTime": "2026-10-08T22:00:00",
          "type": "TransportEvent"
        },
        "transportModeCode": "unece:TransportModeCodeList#3",
        "type": "TransportMovement",
        "unloadingEvent": {
          "occurrenceLogisticsLocation": null,
          "scheduledOccurrenceDateTime": "2026-10-11T12:00:00",
          "type": "TransportEvent"
        }
      },
      "summaryDescription": null,
      "type": "Consignment",
      "unloadingLocation": null,
      "utilizedTransportEquipment": null,
      "weightUnitGrossWeightMeasure": {
        "type": "WeightUnitMeasureType",
        "weightUnitMeasureTypeCode": "KGM",
        "weightUnitMeasureTypeValue": 22480
      },
      "weightUnitNetWeightMeasure": {
        "type": "WeightUnitMeasureType",
        "weightUnitMeasureTypeCode": "KGM",
        "weightUnitMeasureTypeValue": 19831.8
      }
    }
  ],
  "includedConsignmentItem": null,
  "loadingLocation": null,
  "packageQuantity": null,
  "specifiedTransportMovement": null,
  "summaryDescription": null,
  "type": "Consignment",
  "unloadingLocation": null,
  "utilizedTransportEquipment": [
    {
      "identifier": "WZ750EE",
      "type": "LogisticsTransportEquipment"
    }
  ],
  "weightUnitGrossWeightMeasure": {
    "type": "WeightUnitMeasureType",
    "weightUnitMeasureTypeCode": "KGM",
    "weightUnitMeasureTypeValue": 22480
  },
  "weightUnitNetWeightMeasure": {
    "type": "WeightUnitMeasureType",
    "weightUnitMeasureTypeCode": "KGM",
    "weightUnitMeasureTypeValue": 19831.8
  }
}
```
