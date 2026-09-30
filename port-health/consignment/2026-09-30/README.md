# Consignment
**Version Snapshot: 2026-09-30**

The **Consignment** signal describes something an actor has done to a consignment, following the [Activity Streams 2.0](https://www.w3.org/TR/activitystreams-core/) pattern: *who* (`actor`) did *what* (`type`) to *which thing* (`object`).

The schema only requires these three fields and leaves `actor` and `object` free-form, so senders can supply whatever JSON their use case needs — for example a UN/CEFACT consignment, a transport movement or a certificate.

## Fields

| Field | Requirement | Type | Description |
| :--- | :--- | :--- | :--- |
| `type` | **Required** | String | The activity being performed (e.g., `Create`, `Update`, `Delete`). |
| `actor` | **Required** | Object | The party performing the activity. Any JSON object is accepted. |
| `object` | **Required** | Object | The subject of the activity. Any JSON object is accepted. |

Other top-level fields (e.g., `@context`, `id`, `published`) are allowed and are not validated.

## Actor

The schema does not check the contents of `actor`. We recommend including a `type` and identifying the party with a `registeredId`, for example:

```json
"actor": {
  "@context": "https://vocabulary.uncefact.org/unece-context-D23B.jsonld",
  "type": "TradeParty",
  "registeredId": {
    "@type": "https://ref.gs1.org/voc/OrganizationID_Type-DID",
    "@value": "TETA"
  }
}
```

## Object

The `object` holds the business data. The schema does not check its contents, so agree the structure with the other members of the ISN. Including a `type` and an `@context` inside the object is recommended, so receivers can tell what kind of data it holds and how to interpret it.

Because the schema doesn't define the fields inside `object`, routing rules can use any path under it (e.g., `object.identifier`).

See [example.md](./example.md) for a full example using the UN/CEFACT vocabulary.
