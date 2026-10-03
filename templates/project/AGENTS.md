# IC Project Agent Guide

## SiliconBoot managed section begins

Start with `project.md`, `ENVIRONMENT.md`, and `.siliconboot/current/manifest.md`. The current manifest is authoritative for paths and environment settings; rendered guidance can lag an interrupted activation. Reconcile any mismatch before running tools. Check the active validation record before claiming a tool or workflow is usable. Locate exact versions, providers, entrypoints, libraries, runtime settings, and official sources in the manifest and referenced receipts. Read the relevant recipe in the persistent [SiliconBoot guidance snapshot]([GUIDE_ABSOLUTE_PATH]/README.md), whose revision and digest are recorded in the manifest.

Use `tools` and `pdk` to locate installations and `bin` for their public executable links. Apply documented per-tool interpreter, environment, and working-directory requirements. A library or plugin may have no executable. Do not invent entrypoints or generate launchers. For a long or reproducible run, follow the [run procedure]([GUIDE_ABSOLUTE_PATH]/prompts/run.md): resolve the generation once, register a lease, and use fixed generation paths throughout the full process tree.

Keep user sources in `design` and `verification`, overrides in `config`, memory requests in `ip/memory/configs`, accepted macro records in `ip/memory/manifests`, and generated outputs in `runs`. Never write outputs into a shared tool or PDK. Preserve existing user files and instructions. A successful process exit alone proves neither design correctness nor timing, DRC, LVS, or memory acceptance.

When asked to upgrade, read the component's official sources, catalog, recipe, and receipts; follow the [upgrade procedure]([GUIDE_ABSOLUTE_PATH]/docs/upgrade.md). Resolve official latest inputs into a new frozen plan, build versioned installations, and verify affected workflows before atomic activation. Preserve the working generation on failure or latest incompatibility. Do not upgrade during ordinary design work or doctor checks.

Follow the [validation procedure]([GUIDE_ABSOLUTE_PATH]/docs/validation.md) for inspection and the [cleanup procedure]([GUIDE_ABSOLUTE_PATH]/docs/cleanup.md) for owned temporary artifacts. Preserve runtime sources, licenses, retained generations, and shared installations. Garbage collection is a separate explicit operation. Record exact inputs, genuine exit statuses, evidence, failures, and limitations in English Markdown. Use elevated privileges only within the user's authorization and host rules; never store passwords.

## SiliconBoot managed section ends
