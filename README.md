## Core Idea

OET-Solana is built around one principle: **execution state should be deterministic**.

In trading infrastructure, the same sequence of observable events should not produce five different interpretations depending on which system reads it. If an order was submitted, accepted, partially filled, cancelled, settled, charged fees, or reflected in a balance change, those facts should be expressible in a regular format that downstream systems can interpret consistently.

OET-Solana does not attempt to make every Solana protocol behave the same way. Instead, it defines a shared telemetry layer so different systems can describe execution events with enough structure to support deterministic state interpretation.

That means builders should be able to answer questions like:

- What was the final lifecycle state of this order?
- Which fills contributed to this position?
- Which balance changes were caused by execution, fees, funding, or settlement?
- Which timestamp was used to interpret event ordering?
- Which reported state disagrees with the deterministic event record?

The goal is not to remove protocol flexibility. The goal is to make execution state reproducible, inspectable, and comparable across systems.
