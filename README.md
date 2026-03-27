# Signals Library 

This repository contains the official, version-controlled definitions for all information "Signals" exchanged within our **Information Sharing Networks (ISNs)**.

## 🎯 Purpose
To provide a verifiable, machine-readable standard for data sharing between Port Health Authorities, Port Operators, and Trade Partners, reducing friction in the global supply chain.

## 📂 Signal Domains
Signals are organised by business domain. Each domain folder contains a **Master Schema** that governs all signals within that category.

| Domain | Description | Status |
| :--- | :--- | :--- |
| [**/port-health**](./port-health/) | Pre-notifications, Despatch events, and Port Health status. | 🟢 Active |


## 📄 Structure of a Signal
Each directory is structured to support both humans and machines:
* **`schema.json`**: The technical "Rulebook" used by developers for API validation.
* **`example.json`**: A "Production-Ready" sample message to accelerate integration.
* **`README.md`**: A Plain-English guide on the business logic and field definitions.

## 🚀 Getting Started
1. Navigate to the relevant [Domain Folder](./port-health/).
2. Review the `schema.json` to understand the data requirements.
3. Use the `example.json` files to mock your initial API requests.
