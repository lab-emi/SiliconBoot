# Architecture decision: an agent protocol expressed in documents

**Status:** Accepted.\
**Scope:** SiliconBoot repository and its agent-facing interface.

## Decision

Use Markdown prompts, a catalog, recipes, procedures, and record templates. The agent reads them and applies the host's existing tools and the selected components' official installation procedures. SiliconBoot supplies no executable implementation, generated launcher, shell activation file, or background service.

This keeps the project usable by any agent that can read files, inspect official sources, and operate a terminal. It also makes source choices, failure handling, and validation criteria reviewable before changes reach a machine.

## Responsibilities

| Layer | Responsibility |
| --- | --- |
| Prompt | User intent, selected project, operation, and scope |
| Root AGENTS.md | Core constraints and reading order |
| Catalog | Component identity, source policy, dependencies, and recipe routing |
| Recipe | Upstream-specific decisions and concrete checks |
| Lifecycle docs | Preservation, resolution, installation, activation, and recovery |
| Project records | What actually happened on one host and what can be reproduced |
| Project .siliconboot/AGENTS.md | How another agent locates and uses that recorded environment alongside the project's existing instructions |

The agent must convert prose requirements into concrete, reviewed host operations. Documentation cannot provide an atomic transaction or enforce a lock by itself. The agent must use suitable native facilities, verify their behavior, and stop activation or destructive cleanup when it cannot establish the required guarantees.

## Consequences

- There is no SiliconBoot command syntax to learn or execute. Operation names in the prompt index describe tasks.
- Markdown records are an interchange convention for humans and agents. They are not a machine-validated database. Missing fields, contradictions, and unresolved placeholders are errors to resolve before activation.
- Reproducibility depends on complete input records and continued access to the recorded upstream artifacts. Exact restore must report unavailable inputs or changed host dependencies.
- Persistent installations and whole-generation selection reduce partial upgrades. External system packages remain outside reliable rollback guarantees.
- Recipes can evolve with upstream documentation without embedding a second installation implementation. A source review and an installation test remain different forms of evidence.

See [records](records.md) for the contract and [acceptance](acceptance.md) for the required checks.
