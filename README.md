# Signals Library 

This repository contains the official, version-controlled definitions for all information "Signals" exchanged within our **Information Sharing Networks (ISNs)**.

## 🎯 Purpose
To provide a verifiable, machine-readable standard for data sharing between Port Health Authorities, Port Operators, and Trade Partners, reducing friction in the global supply chain.

## 📂 Signal Domains
Signals are organised by business domain. Each domain folder contains a **Master Schema** that governs all signals within that category.

| Domain | Description | Status |
| :--- | :--- | :--- |
| [**/port-health**](./port-health/) | Movement Notification, Despatch events, and Port Health status. | 🟢 Active |


## 📄 Structure of a Signal
Inside each folder, you'll find everything needed to understand and integrate the signal:
* **`schema.json`**: Use this to validate your data and ensure your code matches our API requirements.
* **`example.json`**: A sample message to show you exactly how a valid signal looks.
* **`README.md`**: A Plain-English guide explains the signal and defines what every field actually means.

## 🚀 Getting Started
1. Navigate to the relevant [Domain Folder](./port-health/).
2. Review the `schema.json` to understand the data requirements.
3. Use the `example.json` files to mock your initial API requests.
