# Architecture Decision Records (ADRs)

This directory will explain why I make important technical choices as LionraForge develops. Each ADR will have a permanent sequential ID, a descriptive filename and links to the relevant implementation labs.

## Proposed format

- **Context:** What problem or requirement is being addressed?
- **Options:** What realistic alternatives were considered?
- **Decision and rationale:** What did I select, and why?
- **Trade-offs:** What limitations and consequences do I accept?
- **Validation plan:** How will I test the choice?
- **Observed results:** What did testing actually establish? (Added after implementation.)
- **Related labs and changes:** Where is it used, and what later decisions supersede it?

Illustrative naming: `0001-virtualisation-platform.md`. No ADR number is assigned until an individual record is drafted and reviewed.

## Decision status and history

A planned decision is not a test result. When implementation changes the original assumptions, I'll update the decision history or create a superseding ADR. Previous revisions remain available through Git history.

A subject-based index will be added as records accumulate. Topics are likely to include networking, identity, virtualisation, IT operations and security.

**Current state:** No individual ADRs have been written or verified. The technical design is described in [Architecture and Design](../architecture/README.md).