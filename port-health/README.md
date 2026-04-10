# Port Health Signals
This library contains the standards for notifying Port Health Authorities of arriving consignments. These signals are the primary data exchange for high-risk goods entering the UK via the Information Sharing Network (ISN).

## 🔄 The Workflow
The Port Health journey consists of two linked signals:
1. **Movement Notification:** The initial notification of intent to import (sent by the Agent/Importer).
2. **Despatch:** The confirmation of departure and intended arrival time (sent by the Haulier/Agent).

## 🔗 Correlation Logic
To link these signals, the **Despatch** signal must include the `correlationId` generated during the **Movement Notification** step. This ensures all data remains attached to the same physical shipment.

## 🚚 Transport Identifiers
For the `identifier` field within the `transportMeans` array, please use:
* **For RoRo (Trucks/Trailers):** Enter the VRN or Trailer Number.
* **For LoLo (Containers):** Enter the Container Number.

## 🔑 Tracking Metadata
* **originRecordID:** The unique reference or job number from the originating system.
* **originSystemCode:** The name of the software sending the data (e.g., `TWIN`, `DESTIN8`).

## 📁 Documentation & Examples
* [Master JSON Schema](./schema.json)
* **Movement Notification:** [Field Guide](./movement-notification-README.md) | [JSON Example](./movement-notification-example.json)
* **Despatch:** [Field Guide](./despatch-README.md) | [JSON Example](./despatch-example.json)