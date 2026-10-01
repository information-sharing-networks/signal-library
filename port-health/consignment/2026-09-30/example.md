# Consignment Example

The client's test consignment (Calais → Dover), using the [UN/CEFACT vocabulary](https://vocabulary.uncefact.org/). The data sits directly at the root of the signal content.

### Signal Content
```json
{
  "type": "Consignment",
  "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
  "globalId": "6-GB-GB123456789000-Test-Load",
  "identifier": "ACME-Test-Load",
  "atArrivalTransportMovement": {
    "type": "TransportMovement",
    "transportModeCode": "unece:TransportModeCodeList#3",
    "arrivalEvent": {
      "type": "TransportEvent",
      "scheduledOccurrenceDateTime": "2026-09-21T10:00:00Z",
      "occurrenceLogisticsLocation": {
        "type": "LogisticsLocation",
        "name": "Dover",
        "identifier": "GBDVR"
      }
    }
  },
  "atDepartureTransportMovement": {
    "type": "TransportMovement",
    "transportModeCode": "unece:TransportModeCodeList#3",
    "departureEvent": {
      "type": "TransportEvent",
      "scheduledOccurrenceDateTime": "2026-09-20T09:30:00Z",
      "occurrenceLogisticsLocation": {
        "type": "LogisticsLocation",
        "name": "Calais",
        "identifier": "FRCQF"
      }
    }
  },
  "includedConsignment": [
    {
      "type": "Consignment",
      "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
      "identifier": "C-001",
      "consigneeParty": {
        "type": "TradeParty",
        "role": "Consignee",
        "identifier": "FR123456789000",
        "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld"
      },
      "consignorParty": {
        "type": "TradeParty",
        "role": "Consignor",
        "identifier": "GB123456789000",
        "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld"
      },
      "includedConsignmentItem": [
        {
          "goodsTypeCode": "1602",
          "information": "Chicken Wings",
          "originCountry": {
            "type": "Country",
            "countryId": "PL"
          }
        }
      ],
      "loadingLocation": {
        "type": "LogisticsLocation",
        "name": "Test Factory",
        "physicalGeographicalCoordinate": {
          "type": "GeographicalCoordinate",
          "latitudeMeasure": 52.404874,
          "longitudeMeasure": 18.596362
        },
        "postalAddress": {
          "type": "TradeAddress",
          "streetName": "1 Test Road",
          "tradeAddressCountryId": "PL"
        }
      },
      "unloadingLocation": {
        "type": "LogisticsLocation",
        "name": "Test Supermarket",
        "physicalGeographicalCoordinate": {
          "type": "GeographicalCoordinate",
          "latitudeMeasure": 51.372264,
          "longitudeMeasure": -1.83537
        },
        "postalAddress": {
          "type": "TradeAddress",
          "streetName": "2 Test Road",
          "tradeAddressCountryId": "GB"
        }
      },
      "specifiedTransportMovement": {
        "type": "TransportMovement",
        "transportModeCode": "unece:TransportModeCodeList#3",
        "loadingEvent": {
          "type": "TransportEvent",
          "scheduledOccurrenceDateTime": "2026-09-20T08:00:00Z"
        },
        "unloadingEvent": {
          "type": "TransportEvent",
          "scheduledOccurrenceDateTime": "2026-09-21T16:30:00Z"
        }
      },
      "weightUnitGrossWeightMeasure": {
        "type": "WeightUnitMeasureType",
        "weightUnitMeasureTypeValue": 15000,
        "weightUnitMeasureTypeCode": "KGM"
      },
      "weightUnitNetWeightMeasure": {
        "type": "WeightUnitMeasureType",
        "weightUnitMeasureTypeValue": 13250,
        "weightUnitMeasureTypeCode": "KGM"
      }
    }
  ],
  "utilizedTransportEquipment": [
    {
      "type": "LogisticsTransportEquipment",
      "identifier": "TR41LER"
    }
  ],
  "weightUnitGrossWeightMeasure": {
    "type": "WeightUnitMeasureType",
    "weightUnitMeasureTypeValue": 15000,
    "weightUnitMeasureTypeCode": "KGM"
  },
  "weightUnitNetWeightMeasure": {
    "type": "WeightUnitMeasureType",
    "weightUnitMeasureTypeValue": 13250,
    "weightUnitMeasureTypeCode": "KGM"
  }
}
```
