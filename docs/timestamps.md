# Timestamp Model

OET-Solana treats timestamps as part of the execution record, not decoration.

Execution-sensitive systems often observe different moments in the same lifecycle. A trading bot, protocol, wallet, indexer, RPC provider, and internal system may each attach a different timestamp to what appears to be the same event.

OET-Solana makes these timestamp distinctions explicit so downstream tools can reason about ordering, delayed observation, finality assumptions, and source-of-truth differences.

## Timestamp Fields

| Field | Meaning |
|---|---|
| `decision_timestamp` | When a strategy, user, or system decided to act. |
| `submitted_timestamp` | When an instruction, order, or transaction was submitted. |
| `source_event_timestamp` | When the source system reports that the event occurred. |
| `ledger_timestamp` | When the event was associated with on-chain or ledger state. |
| `observed_timestamp` | When the local system observed or ingested the event. |
| `valuation_timestamp` | When a balance, exposure, price, or reported state was valued. |

## Why Multiple Timestamps Matter

A single timestamp is often not enough to explain execution state.

For example, an indexer may observe a fill before a wallet observer sees the related balance change. That does not necessarily mean the state is incorrect. It may mean the systems observed the same execution at different times.

OET-Solana is designed to make that distinction visible.

## Design Principle

OET-Solana does not assume perfect determinism across all systems.

Instead, it aims to make the inputs, sources, timestamps, relationships, and assumptions explicit enough that execution records can be inspected, compared, and explained.

## Example

A synthetic fill event may include:

```json
{
  "event_id": "evt_003",
  "event_type": "fill_observed",
  "timestamps": {
    "source_event_timestamp": "2026-05-14T14:00:01.100Z",
    "ledger_timestamp": "2026-05-14T14:00:01.120Z",
    "observed_timestamp": "2026-05-14T14:00:01.340Z"
  }
}