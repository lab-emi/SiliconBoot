# Rendering project guidance and records

These are Markdown templates for the agent to read, copy, and fill. They are not executable files or a template language. Follow the [record contract](../docs/records.md), [project layout](../docs/project-layout.md), and [installation transaction](../docs/installation.md).

The agent fills these templates; users do not supply the internal path placeholders. Use the existing project directory identified from context, defaulting to the discovered SiliconBoot clone. Do not create a workspace or design scaffold. Derive managed tool paths under `~/tools`, PDK paths under `~/pdks`, public binary symlinks under `~/bin` and generated guidance under the existing project's `.siliconboot/`. Matching macOS Homebrew tools use their recorded external provider locations under [the macOS policy](../docs/installation.md#macos-check-homebrew-first), with receipts in the tool store. Expand home paths using the invoking user's actual home directory and record canonical roots.

Replace every square-bracketed uppercase placeholder with a concrete value. Repeat a component, dependency, entrypoint, check, or artifact row as needed. Remove authoring instructions after rendering. For unavailable values use `unknown`, `not applicable`, or `not_run` with a reason. Check results use `pass`, `fail`, `blocked`, or `not_run`; independent capability claims use the values in the [record contract](../docs/records.md). Never publish an active record containing unresolved placeholders. Resolve host paths to absolute paths and make Markdown links point to the actual persistent files; portable locks contain logical identities and project-relative paths instead.

## Project templates

| Template | Rendered destination |
| --- | --- |
| [Project README](project/README.md) | Project `.siliconboot/README.md`, or its bounded SiliconBoot section. |
| [Project agent guide](project/AGENTS.md) | Project `.siliconboot/AGENTS.md`, or its bounded SiliconBoot section. |
| [Project choices](project/PROJECT.md) | Project `.siliconboot/project.md`. |
| [Environment guide](project/ENVIRONMENT.md) | Project `.siliconboot/ENVIRONMENT.md`. |

The headings `SiliconBoot managed section begins` and `SiliconBoot managed section ends` bound the replaceable region in generated guidance under `.siliconboot/`. Keep root project README and AGENTS files authoritative and unchanged by setup. For an existing file, preserve all content outside those headings. If the markers are absent, append a proposed section only after checking for conflicting instructions. If a previous generated section exists, compare it with the previous rendered copy and preserve user edits; do not blindly replace them. Keep a recoverable copy and record the merge. Multiple or malformed boundaries require reconciliation before writing.

Use the actual persistent documentation snapshot path for all project guide links, not the source checkout's temporary location. Keep the generated AGENTS concise; component details belong in recipes and manifests. Do not generate shell activation files, launchers, helper programs, JSON records or ignore-file templates. The authorized PATH change is a bounded section in the detected default shell's existing user configuration, following [shell setup](../docs/project-layout.md#default-shell-path).

## Record templates

| Template | Purpose |
| --- | --- |
| [Host](records/host.md) | Native host, filesystem capabilities, paths, and authorization scope. |
| [Resolution](records/resolution.md) | Frozen official latest discovery and dependency plan. |
| [State](records/state.md) | Resumable operation, ownership, and transaction evidence. |
| [Receipt](records/receipt.md) | One persistent installation's complete identity and evidence. |
| [Manifest](records/manifest.md) | One generation's host-specific tool, PDK, and entrypoint map. |
| [Lock](records/lock.md) | Exact portable sources, dependencies, providers, and required workflows. |
| [Validation](records/validation.md) | Verification claims, actual outcomes, and retained evidence. |
| [Run](records/run.md) | A generation-pinned design or verification run and its lease. |
| [Memory](records/memory.md) | Macro request, provenance, output views, checks, and acceptance record. |
| [Registry](records/registry.md) | Shared-store references, retained generations, and lease protection. |

Use Markdown records for all lifecycle state. Native process facilities provide locking, leases' actual process protection, and atomic replacement; the record itself provides evidence and cannot create those guarantees. Apply atomic complete-file replacement to shared record updates while holding the relevant native locks.

Before accepting any rendered output, check record version, required fields, links, component identities, generation consistency, and the separation of host-specific and portable data. Confirm that latest status, component usability, and workflow readiness each have evidence or an explicit unresolved state.
