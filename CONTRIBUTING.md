# Contributing to SiliconBoot

## Scope

Contributions improve the instructions an agent follows. Keep English as the development language, including documentation, examples, reviews, and commit messages. Preserve this repository's prompt and documentation architecture: do not add code, scripts, executable examples, installer wrappers, or CI configuration that runs programs.

Use Markdown for catalog entries, recipes, prompts, records, and scenario descriptions. Directory diagrams and field names are documentation; shell programs, command sequences, RTL, and language examples belong in upstream projects or the user's local `workspace/`, which stays out of SiliconBoot commits.

## Add or update a component

1. Choose a stable, unique ID in the [catalog](catalog/README.md). Separate aliases, package identity, repository identity, and executable names. Check similarly named projects before choosing a source.
2. Link the maintainer's homepage, repository, installation documentation, release policy, and license evidence. Record canonical migrations. Treat a repository default branch as evidence to inspect, not automatic proof of the recommended maintenance branch.
3. State the recipe's coverage and platform evidence honestly. `planned` means installation instructions still need resolution; `experimental` means a procedure exists without the required native validation; `verified` requires host-specific evidence. An upstream platform claim alone cannot verify SiliconBoot.
4. Describe dependencies, ABI restrictions, coupled updates, runtime layout, public entrypoints, and concrete acceptance checks. If an upstream installer assumes a different deployment model, investigate a supported native route and report gaps.
5. Update the relevant profile and recipe. Use uv by default for Python environments, with official evidence for any upstream-managed runtime exception under the [Python environment policy](docs/python-environments.md). Catalog ownership, shared defaults, and explicit exceptions should make a component's effective instructions unambiguous.
6. Check the [record contract](docs/records.md), especially portable reproduction inputs and host-specific receipts. Add a prose [acceptance scenario](docs/acceptance.md) if the change affects behavior.

Do not add copied installation scripts, permanent version pins presented as latest, or a new dependency on a particular agent vendor. Do not silently expand a suite into unspecified packages. List its exact members and official sources, or retain an unresolved scope entry.

## Evidence for a support claim

Supply the OS and version, architecture, native execution context, selected channel/provider, full revisions, build settings, dependency versions, recipe revision, and date. Link logs and report artifacts after removing credentials and private host details. Include a real component check and all workflows being claimed. Record skipped and failed checks explicitly.

For PDKs, record raw data, builder, submodules, generated models, technology files, and corners. For memory, include the compiler, technology port, PDK, configuration, required views, and the actual timing/DRC/LVS outcome. Successful installation does not establish fabrication readiness.

## Review before submitting

- Follow the [documentation acceptance checklist](docs/acceptance.md).
- Confirm all local links resolve and every catalog entry reaches a recipe or an explicit unresolved outcome.
- Review external links against primary sources. Recheck version-sensitive claims and date the review without turning it into an installation claim.
- Confirm templates agree on field names, paths, state meanings, and ownership.
- Preserve the existing license and unrelated user files. Keep local host records, downloads, installations, design outputs, and temporary planning documents out of contributions.

Commit messages should name the behavior the documentation changes, such as “Document PDK model rebuild checks” or “Clarify generation rollback records.”
