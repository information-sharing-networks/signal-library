# Pre-notification Signal

This signal is used to notify Port Health Authorities of an arriving consignment. It is the primary data exchange for high-risk goods entering the UK via the Information Sharing Network (ISN).

## 🚚 Transport Identifiers
To ensure searchability, please use the following standards for the `identifier` field:
* **For RoRo (Trucks):** Enter the Vehicle Registration Number (VRN).
* **For LoLo (Containers):** Enter the Container Number.

## 🔑 Organization Tracking
* **sourceRef**: The unique reference or job number from the originating system for traceability.
* **system_code**: This should be the name of the software sending the data (e.g., `TWIN`, `DESTIN8`, `INTERNAL_ERP`).

## 📁 Related Files
* [View Technical Schema](./schema.json)
* [View Sample Data (Truck Example)](./example.json)

