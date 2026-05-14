## Milestones and Budget

Total requested funding: $50,000 USD

### Milestone 1: OET schema specification and timestamp model
Amount: $8,000
Estimated completion: 3 weeks

Deliverables:
- Define initial OET event categories for orders, fills, balances, positions, fees, funding, mark prices, settlement, risk state, and source observation.
- Document timestamp semantics for decision time, submission time, observed time, ledger time, valuation time, and source-specific event time.
- Publish initial schema documentation and example records.

### Milestone 2: Validation and normalization toolkit
Amount: $12,000
Estimated completion: 4 weeks

Deliverables:
- Build open-source validation tooling for OET event records.
- Add example normalization utilities.
- Provide tests and sample input/output files.
- Publish developer documentation for integrating OET into Solana applications.

### Milestone 3: Solana adapter examples and sample datasets
Amount: $12,000
Estimated completion: 4 weeks

Deliverables:
- Provide examples for mapping Solana wallet/token balance changes into OET records.
- Provide examples for mapping protocol execution events into OET records.
- Publish sample datasets showing orders, fills, balances, fees, settlement, and observed state.
- Document source, timestamp, finality, RPC, and indexer assumptions.

### Milestone 4: Lightweight execution timeline viewer
Amount: $10,000
Estimated completion: 3 weeks

Deliverables:
- Build a lightweight local demo viewer for OET event records.
- Visualize execution timelines across orders, fills, balances, positions, fees, and settlement events.
- Highlight where observed, reconstructed, and reported state disagree.
- Include setup instructions and sample data.

### Milestone 5: Community feedback and v1 release
Amount: $8,000
Estimated completion: 3 weeks

Deliverables:
- Gather feedback from Solana builders, trading infrastructure teams, and protocol developers.
- Refine schemas and timestamp model.
- Publish v1 specification, changelog, contribution guide, and roadmap.
