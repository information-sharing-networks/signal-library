# Port Health Movement Notification & Despatch (Combo)
**Version Snapshot: 2026-04-10**

This directory contains the unified standard for the Information Sharing Network (ISN). This combined approach allows developers to manage the entire Port Health lifecycle—from initial intent to physical departure—using a single validation framework.

## 🏗️ Core Metadata & Provenance
To ensure a clear audit trail between originating systems and the ISN, the following fields are **required** for all signals:

* **`originRecordID`**: Your internal system reference (e.g., Job Number, Invoice Ref, or PRE-number).
* **`originSystemCode`**: The unique identifier for your software (e.g., `TWIN`, `DESTIN8`, `CNS`).
* **`correlationId`**: A UUID used to thread multiple signals together. 
    > **Note:** When sending a sequential **Despatch** signal, the `correlationId` must match the one used in the original **Movement Notification**.

## 📍 Location Standards (UN/LOCODE)
This schema enforces the use of international standards for port identification to reduce data entry errors.
* **Port Names**: Human-readable strings (e.g., "Rotterdam").
* **Port Codes**: Strict **UN/LOCODE** format (e.g., `NLRTM`).
* **Validation**: The `portOfExitCode` and `portOfEntryCode` must follow the regex pattern `^[A-Z]{2}[A-Z2-9]{3}$` (5 uppercase characters).

## 🧩 Integration Patterns
The [Master Schema](./2026-04-10/schema.json) is polymorphic, supporting three distinct delivery methods:

### 1. Movement Notification (Initial Intent)
Sent when the goods are first declared. Focuses on **what** is being moved (CN codes, CHEDs, Importer EORI).
* **Key Requirement**: Must include `transportMeans` and `commodityDescription`.

### 2. Despatch (Movement Confirmation)
Sent when the goods depart. Focuses on **when** and **where** the movement is happening.
* **Key Requirement**: Must include `plannedDepartureTime`.

### 3. Combined "Combo" Signal
You may send a single payload containing both sets of data. The `oneOf` logic in the schema will validate the payload against either the Movement or Despatch definitions.

## 📁 File Directory
| File | Purpose |
| :--- | :--- |
| [schema.json](./2026-04-10/schema.json) | The master validation file for all Port Health signals. |
| [movement-notification-example.json](./2026-04-10/movement-notification-example.json) | Reference for initial intent declarations. |
| [despatch-example.json](./2026-04-10/despatch-example.json) | Reference for departure/arrival timing. |
| [movement-notification-README.md](./2026-04-10/movement-notification-README.md) | Detailed field-level guide for cargo data. |
| [despatch-README.md](./2026-04-10/despatch-README.md) | Detailed field-level guide for transport data. |

---

### 🚀 Questions & Feedback
1. **Data Redundancy**: The `sealNumbers` field currently contains a summary array of all seals mentioned in the payload. Is this necessary given that seal data can be extracted from the `transportMeans` array during processing?
    * *Reference: [Movement Notification Details](./2026-04-10/movement-notification-README.md)*
2. **Logic Validation**: The combo signal allows for the submission of either a Movement Notification, a Despatch, or both simultaneously. Does this logic align with the technical requirements for the ISN? 

---