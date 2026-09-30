# Consignment Example

A `Create` activity where a trade party (`TETA`) reports a new consignment moving from Calais to Dover. The `object` uses the [UN/CEFACT vocabulary](https://vocabulary.uncefact.org/).

### Signal Content
```json
{
  "@context": "https://www.w3.org/ns/activitystreams",
  "type": "Create",
  "actor": {
    "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
    "registeredId": {
      "@type": "https://ref.gs1.org/voc/OrganizationID_Type-DID",
      "@value": "TETA"
    },
    "type": "TradeParty"
  },
  "object": {
    "atArrivalTransportMovement": {
      "arrivalEvent": [
        {
          "type": "TransportEvent",
          "occurrenceLogisticsLocation": {
            "type": "LogisticsLocation",
            "name": "Dover",
            "identifier": {
              "type": "https://ref.gs1.org/voc/LocationID_Type-UN_LOCODE",
              "value": "Dover"
            }
          },
          "scheduledOccurrenceDateTime": "2026-09-21T10:00:00Z"
        }
      ],
      "transportModeCode": "unece:TransportModeCodeList#3",
      "type": "TransportMovement"
    },
    "atDepartureTransportMovement": {
      "departureEvent": [
        {
          "type": "TransportEvent",
          "occurrenceLogisticsLocation": {
            "type": "LogisticsLocation",
            "name": "Calais",
            "identifier": {
              "type": "https://ref.gs1.org/voc/LocationID_Type-UN_LOCODE",
              "value": "Calais"
            }
          },
          "scheduledOccurrenceDateTime": "2026-09-20T09:30:00Z"
        }
      ],
      "transportModeCode": "unece:TransportModeCodeList#3",
      "type": "TransportMovement"
    },
    "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
    "globalId": "urn:uuid:4c6e8b21-9d30-4d63-b31d-1d8435d23d99",
    "identifier": "TETA-Test-Load",
    "includedConsignment": [
      {
        "consigneeParty": {
          "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
          "registeredId": {
            "@type": "https://ref.gs1.org/voc/OrganizationID_Type-EORI",
            "@value": "FR123456789000"
          },
          "role": "Consignee",
          "type": "TradeParty"
        },
        "consignorParty": {
          "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
          "registeredId": {
            "@type": "https://ref.gs1.org/voc/OrganizationID_Type-EORI",
            "@value": "GB123456789000"
          },
          "role": "Consignor",
          "type": "TradeParty"
        },
        "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
        "identifier": "C-001",
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
        "type": "Consignment"
      }
    ],
    "type": "Consignment",
    "utilizedTransportEquipment": [
      {
        "type": "LogisticsTransportEquipment",
        "identifier": "AB12CDE"
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
}
```
