# intro
the port-health signals are used to notify PHA's about two events:
1. planned movement of goods (early warning that SPS goods are planned for the PHA's location)
2. despatch event (confirmation goods are on the way)

## 📁 Integration Options
The initial implementation of the PHA ISNs used a combined singal type to cover both events - this is deprecated, and the new _individual signal_ approach is recommended for new PHA ISNs.

### 1. Individual Signal Approach (recommended)
Use these if you prefer to keep the Movement and Despatch definitions strictly separated in your logic.
* **Movement Notification:** [Schema & Examples](./pre-notification/)
* **Despatch:** [Schema & Examples](./despatch/)

### 2. Combined Approach (deprecated)
Use this if you want a single schema that handles both signal types or combined payloads.
* [Combined Standards & Documentation](./pre-notification-combo/)
* Includes the master schema, field guides, and combo examples.
---

## 🔗 Quick Links (Latest 2026-04-10 Snapshot)
* [Master JSON Schema](./pre-notification-combo/2026-04-10/schema.json)
* **Movement Notification Guide:** [Field Guide](./pre-notification-combo/2026-04-10/movement-notification-README.md)
* **Despatch Guide:** [Field Guide](./pre-notification-combo/2026-04-10/despatch-README.md)