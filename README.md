# OET-Solana

## One-Line Summary

**OET-Solana gives Solana builders a shared execution language for observable execution facts across orders, fills, balances, positions, fees, funding, settlement, and reported state.**

## Core Idea

**Reproducible, explainable, auditable execution telemetry.**

Solana has the speed for serious execution. OET-Solana gives builders a shared telemetry layer for explaining what each system observed, how state was interpreted, and where execution records disagree.

OET-Solana gives Solana builders a shared language for observable execution facts.

It does not claim that every system will derive the same state in every scenario. Real execution systems contain partial information, delayed observations, protocol-specific semantics, clock disagreement, rounding differences, finality assumptions, and multiple sources of truth.

OET-Solana does not pretend those differences disappear.

Instead, it makes inputs, timestamps, sources, and assumptions explicit enough that differences can be inspected rather than hidden.

In trading infrastructure, the same sequence of observable events should not produce five unexplained interpretations depending on which system reads it. If an order was submitted, accepted, partially filled, cancelled, settled, charged fees, or reflected in a balance change, those facts should be expressible in a regular format that downstream systems can interpret, compare, and audit.

OET-Solana does not attempt to make every Solana protocol behave the same way. Instead, it defines a shared telemetry layer so different systems can describe execution events with enough structure to support reproducible state interpretation.

That means builders should be able to answer questions like:

- What did this system observe?
- When did it observe it?
- Which source reported the event?
- Which order, fill, balance, fee, funding, or settlement event does it relate to?
- Which fills contributed to this position?
- Which balance changes were caused by execution, fees, funding, or settlement?
- Which timestamp was used to interpret event ordering?
- Which reported state disagrees with reconstructed, observed, or interpreted state?
- Which assumptions explain the disagreement?

The goal is not to remove protocol flexibility. The goal is to make execution state reproducible, inspectable, and comparable across systems.

## Problem Statement

Solana execution data is fast, fragmented, and observed from many different places.

A trading system may receive events from wallets, Solana programs, RPC providers, indexers, off-chain bots, routers, risk systems, and internal databases. Each source may use different identifiers, timestamps, event names, precision rules, and assumptions about state.

When something disagrees, teams often have to reconstruct the timeline manually.

OET-Solana exists to reduce that ambiguity by giving builders a regular way to describe observable execution facts.

## What OET Is

OET-Solana is:

- an open execution telemetry standard
- a schema for observable execution facts
- a timestamp vocabulary
- a foundation for replay, reconciliation, and audit workflows
- a public-good layer for Solana trading infrastructure

## What OET Is Not

OET-Solana is not:

- a trading venue
- a matching engine
- an order management system
- a replacement for protocol-specific logic
- a promise that every system will derive identical state
- a proprietary monitoring platform

## Event Categories

OET-Solana defines a common vocabulary for execution-related events.

Initial event categories include:

- order events
- fill events
- balance events
- position events
- fee events
- funding events
- mark price events
- settlement events
- risk state events
- source observation events

These categories are intended to describe the observable facts required to compare execution state across systems.

## Timestamp Semantics

OET-Solana treats timestamps as part of the execution record, not decoration.

Different systems may disagree because they observe different moments:

- when a strategy decided to act
- when an instruction was submitted
- when a protocol emitted an event
- when state appeared on-chain
- when an indexer observed the event
- when an internal system ingested the record
- when a valuation was computed

OET-Solana makes these distinctions explicit so downstream systems can reason about event ordering, latency, delayed observation, and source-of-truth differences.

## Regularity Without Uniformity

Solana protocols should not have to flatten their execution models to fit a generic standard.

OET-Solana is designed to support protocol-specific behavior while preserving a regular telemetry layer. A protocol can keep its own order types, routing model, matching behavior, settlement logic, and state transitions while still exposing observable execution facts in a common format.

The goal is not to make all protocols look identical.

The goal is to make their execution records comparable.

## Reproducible Interpretation, Not Perfect Determinism

OET events should support reproducible interpretation where possible and explicit disagreement where not.

Given the same event record, systems should be able to derive comparable execution state, identify missing context, or explain why two interpretations differ.

This applies to:

- order lifecycle state
- fill history
- position state
- balance state
- fees
- funding
- settlement
- timestamp interpretation
- source-of-truth comparison

OET does not assume execution state is perfectly deterministic. Instead, it makes the evidence structured enough that builders can compare interpretations without relying on screenshots, private dashboards, custom scripts, or venue-specific lore.

## Example Use Cases

### Trading Bots

Capture intent, submitted orders, fills, fees, and wallet balance changes in one structured event record.

### Market Makers

Compare inventory, position exposure, and fill quality across protocols, wallets, routers, and off-chain systems.

### Wallets

Provide clearer transaction-level execution context to users and downstream systems.

### Protocols

Expose a regular execution telemetry layer without giving up protocol-specific order semantics.

### Analytics Providers

Build dashboards, alerts, and forensic tools on top of standardized execution event data.

### Auditors and Risk Teams

Review historical execution records and compare interpreted state against reported state.

## Public-Good Scope

OET-Solana is intended to be released as an open-source public-good standard.

The public scope includes:

- event schemas
- timestamp model documentation
- validation examples
- reference datasets
- adapter examples
- integration guides
- a lightweight demo timeline viewer

The goal is to give Solana builders a shared foundation for execution telemetry that can be adopted, extended, and improved by the community.

## Roadmap

### Phase 1: Specification

- define initial event categories
- document timestamp semantics
- publish example event records
- define extension model for protocol-specific fields

### Phase 2: Reference Toolkit

- add schema validation
- add example event normalization
- add comparison utilities
- publish sample datasets

### Phase 3: Solana Examples

- map Solana wallet and token balance changes into OET records
- map protocol execution events into OET records
- document source, timestamp, and finality assumptions

### Phase 4: Demo

- build a lightweight execution timeline viewer
- load sample OET event records
- show observed, reconstructed, and reported state differences

### Phase 5: Community Feedback

- gather feedback from Solana builders
- refine schema and timestamp model
- publish v1 specification

## Status

Early-stage specification and reference implementation.

This project is based on prior work building execution reconciliation, order lifecycle validation, balance replay, position reconstruction, exposure monitoring, and real-time trading-system observability.

The next step is to extract the public-good layer into an open standard that Solana builders can adopt, test, extend, and improve.

## Contributing

OET-Solana is intended to become a community standard. Contributions are welcome from:

- Solana protocol teams
- trading bot developers
- market makers
- wallet teams
- analytics providers
- risk and reconciliation engineers
- auditors
- infrastructure builders

Useful contributions include:

- schema feedback
- protocol-specific event examples
- replay edge cases
- timestamp model feedback
- adapter implementations
- sample datasets
- documentation improvements

## License

This project is intended to be released under an open-source license.
