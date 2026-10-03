# Upgrade, restore, and rollback

Use the corresponding [operational prompt](../prompts/README.md). These are agent procedures, not command-line interfaces. Follow [installation](installation.md) for locking, exact discovery, candidate generation creation, and atomic activation.

## Upgrade a selected environment

1. Read `project.md`, the active manifest, portable lock, receipts, validation, retained generations, and live run leases. Record the capabilities that the current environment provides and the user's requested upgrade scope.
2. Query current official release or documented branch information for the selected components. Expand dependencies and coupled groups, including plugins, PDK builders, runtime dependencies, model binaries, and memory technology ports. Record why every additional component changes.
3. Freeze a new resolution plan. Compare sources, dependencies, compiler/runtime versions, build options, and patches, not merely displayed version numbers. Record latest-version status separately from compatibility.
4. Build new installations at new persistent keys. Preserve all active installations and avoid mutating shared PDK data. Verify individual components and every affected workflow that the replacement promises to preserve.
5. Create and verify a complete candidate generation. Activate it atomically only when the required checks pass. Retain the prior valid generation, its installations, and the reference records. An active lease can retain an even older generation.
6. Export the active portable lock, reconcile the project guidance, and remove only eligible temporary artifacts under the [cleanup procedure](cleanup.md). Report changed versions, providers, capabilities, host packages, remaining limitations, and rollback conditions.

If latest components are incompatible, record `blocked_latest_incompatible` and leave the existing environment active. Do not silently insert an older component into an environment presented as latest. With a user-requested compatible selection, create a separately named environment or clearly named generation policy and list every departure from the latest plan.

If discovery is unavailable, record `latest_unknown`; the previous environment can remain usable. If a candidate partly succeeds, keep its valid receipts for resumption but do not replace the active environment with a degraded subset by default. A user-requested reduced scope must be recorded before activating such a candidate.

An existing installation whose identity and checks already match is reused. Repeated upgrade requests without changed inputs should leave the same working environment intact. Ordinary inventory, doctor checks, design runs, and cleanup never initiate upgrades.

For Python changes, follow the [Python environment policy](python-environments.md). Install uv first if missing, then create new environments from frozen inputs. Preserve existing environments, uv binaries and interpreter locations; do not migrate or synchronize an active environment in place. Include a uv change in the plan when requested or required by the selected setup, recording its impact on dependent builds.

## Restore an exact lock

1. Read the lock's record version and confirm its requested sources, channels, dependencies, build options, command providers, PDK families, and workflow requirements. Use the lock's pinned inputs; do not refresh them to current upstream releases.
2. Inspect the new host, resolve its store, and register the project while preserving its existing sources and configuration. Reject stale absolute links as portability evidence.
3. Determine whether the lock's target OS, architecture, runtime, and ABI constraints can be satisfied natively. Record missing assets, inaccessible sources, unsupported combinations, and unpinned dependencies before building.
4. Reuse matching verified installations or rebuild from the exact locked sources and dependencies. Verify downloaded bytes against recorded integrity information and preserve the upstream runtime layout.
5. Create a local manifest with the new host's absolute paths and the unchanged portable source identities. Run component and required workflow checks on this host. A different platform or toolchain creates a new build identity and must be described as such.
6. Activate only the verified result according to the normal transaction. Record whether the evidence supports exact input restoration, matching artifact hashes, and/or the named workflow results. Keep unresolved portions explicit.

An unavailable exact source or dependency blocks the corresponding restore. Do not resolve a newer tag, substitute a fork, change a memory technology port, or omit an input while claiming the original environment was restored. A user-approved alternate environment gets its own lock and explanation. No cross-host or bit-for-bit equivalence is assumed.

Restore the recorded uv version, interpreter build and Python dependency lock before rebuilding its environments. If an older lock predates uv and records another manager, preserve that identity for exact restore and report any missing manager information. Adopting uv requires a separately recorded maintenance change; it must not silently alter the restored inputs.

## Roll back to a retained generation

Locate the requested generation and all its receipts. Confirm that its installations, PDK data, public entrypoints, runtime resources, and documentation remain present and unchanged. Recheck external system installations, system dependencies, and host ABI compatibility; a retained symlink cannot undo a changed operating system.

Protect the requested generation with an operation lease while validating its required capabilities at the level justified by host changes. For activation, acquire the host-change, project, and registry locks in order, inspect active leases, and recheck that host dependency observations remain valid. Replace only `current` with the verified atomic facility while keeping the host-change gate, then reconcile the portable lock export and project guidance. Record the generation before and after the switch and the actual observed result.

Managed installations are versioned and retained, so switching their references does not require rebuilding when all dependencies remain valid. System packages, external installations, GPU drivers, and other host-wide changes may prevent the previous generation from working. Report these limits before claiming rollback success. Never automatically downgrade host packages or delete another project's dependencies as part of a rollback.

## Recovery and retirement

After interruption, inspect the actual filesystem and current symlink under the documented locks. Reconcile records from the observed verified generation, not an assumed last completed step. Preserve ambiguous candidates and their logs. See [activation recovery](installation.md#activate-one-generation).

The default retention set includes the active generation, the previous valid generation, every user-retained generation, and every leased generation. Removing temporary build files is separate from retiring generations or garbage-collecting installations. Explicit retirement changes references only after the user requests it and live leases have ended. [Garbage collection](cleanup.md#explicit-garbage-collection) then evaluates whether any registered project still needs each installation.
