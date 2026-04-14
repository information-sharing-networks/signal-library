# Signals Library 

This repository contains the version-controlled definitions (_Signal Types_) of data exchanged within **Information Sharing Networks (ISNs)**.

## Signal Domains
Signal Types are organised by business domain. Each domain folder contains with one or more Signal Type definition. The definitions describe the structure of the data that can be exchanged on ISNs where the Signal Type is enabled.

## Versioning Strategy
We use **Date-Based Snapshots** (e.g., `2026-04-10`).

Developers should always refer to the most recent date folder for the latest schema and business logic. Old snapshots are preserved to ensure backward compatibility for existing integrations.

⚠️ Note: Once a Signal Type is registered on an ISN, **do not modify its schema** — register a new version instead.

If a schema is modified, existing ISNs are unaffected (they store the original schema on registration), but any ISN that adopts the updated schema afterwards will behave differently from those that used the original.

## Submitting Signals

signals are wrapped inside a json structure that contains additional data needed by the backend server:

* batch ref (user supplied batch reference to track outcome of signals load)
* correlation_id (optional - used to link to another signal)
* local_ref - a user supplied unique reference for the signal

Signal Types describe the data inside the `content` field.

```json
{
  "batch_ref": "daily-sync-2026-04-02",
  "signals": [
    {
      "content": {},
      "correlation_id": "75b45fe1-ecc2-4629-946b-fd9058c3b2ca",
      "local_ref": "item_id_#1"
    }
  ]
}
```

c.f the [API doco](https://signalsd-staging.corridorone.uk/docs#post-/api/isn/-isn_slug-/signal-types/-signal_type_slug-/v-sem_ver-/signals) for the signals submission API for details
## Signal Type Definitions
Inside each folder, you'll find everything needed to understand and integrate the signal:
* **`schema.json`**: Use this to validate your data and ensure your code matches our API requirements.
* **`example.json`**: A sample message to show you exactly how a valid signal looks.
* **`README.md`**: A Plain-English guide explains the signal and defines what every field actually means.

See the [API docs](https://signalsd-staging.corridorone.uk/docs) on how to send signals to the ISN

## Getting Started
1. Navigate to the relevant [Domain Folder](./port-health/).
2. Review the `schema.json` to understand the data requirements.
3. Use the `example.json` files to mock your initial API requests.
