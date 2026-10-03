# Cleanup and shared-store garbage collection

Use the [cleanup prompt](../prompts/cleanup.md) for installation residue and the separate [garbage-collection prompt](../prompts/gc.md) for unreferenced persistent installations. Follow [installation locking](installation.md#lock-operations-and-preserve-running-work) and the [record contract](records.md).

## Routine cleanup

Routine cleanup removes temporary files owned by the completed operation. It does not retire generations or remove installed versions. A successful installation normally triggers cleanup of its verified temporary inputs after activation and evidence retention.

1. Read the operation's ownership inventory, receipts, runtime requirements, state, logs, registry, and leases. Identify candidate downloads, archive extractions, installers, temporary clones, and build intermediates.
2. Confirm that required verification passed and that persistent runtime sources and resources exist independently of each candidate. An editable installation referencing a temporary clone is not cleanup-ready; repair its persistent installation first.
3. Resolve canonical parents and inspect the path type without traversing user-controlled links. Confirm that each candidate is inside the operation's owned temporary root and matches its recorded ownership. A name or location alone is insufficient evidence of ownership.
4. Acquire the applicable native locks, recheck ownership and active uses immediately before deletion, and stop if the filesystem state changed. Never follow a symlink into another tree. If native facilities cannot perform safe no-follow deletion with the required guarantees, leave the candidate and report why.
5. Preserve source URLs, integrity records, final receipts, licenses, validation evidence, logs, and measured resource information. Delete only the exact approved owned candidates and record outcomes, reclaimed space where measured, and skipped paths.

Do not delete runtime source, language environments, PDK technology data, shared family resources, model binaries, active installations, previous generations, user design data, verification inputs, accepted memory macros, run artifacts, or third-party files. Do not recursively sweep a broad store, home, project, or system directory.

Failed builds may retain diagnostic working directories. List their measured size, owner operation, and resume value. A later explicit cleanup can remove those temporary files once no active operation uses them; keep the failure logs and record that rebuilding will be required. Unknown ownership remains a blocker to deletion.

System package caches, shared package-manager caches, installed system packages, and external providers are outside routine cleanup. Changing them requires a separate user request with its own scope.

## Explicit garbage collection

Garbage collection is a separate explicit action. Start with a reviewable candidate report showing the exact canonical installation paths, owning receipts, sizes where measured, reasons for eligibility, and references checked. A request for a dry run authorizes only this report. Perform deletion only when the user's request authorizes it; if approval is required, the completed candidate report is what the user approves.

Protect all of the following:

- Every registered project's current generation and previous valid generation.
- User-retained generations, incomplete activation transactions, and pinned environments.
- Every live or unresolved run/operation lease and its transitive dependencies.
- Any installation whose registry, receipt, ownership, or project references cannot be read or reconciled.
- PDK family members and shared resources as one coupled installation.
- Documentation snapshots referenced by protected generations or project guidance.

A missing or inaccessible project does not prove that its references are dead. Do not automatically unregister a project because its path was temporarily unavailable or moved. Require an explicit retirement or migration record and resolve leases first. Keep registry identities consistent across projects sharing the same store.

Inspect all registered generations and their transitive receipt dependencies, not just top-level component links. Detect stale registry entries by comparing them with accessible manifests, but keep uncertain references protected. An unregistered installation or unknown directory is not a deletion candidate until ownership and absence of use are established.

To delete an eligible installation, acquire component locks and required project locks in the documented order, then the registry lock. Re-read references and leases under the locks; if the candidate set changed, update the report and skip newly referenced paths. Retain a deletion record with the installation identity and supporting evidence. Delete only the owned installation tree using no-follow native facilities, then reconcile the registry. Never remove an external system installation through this procedure.

No automatic store-wide garbage collector exists. Agents must register references before use and follow the same lock protocol. If another actor can create unmanaged references outside that protocol, disclose the uncertainty and preserve affected installations.

## Completion report

Report deleted paths, retained paths and reasons, remaining diagnostic work, measured reclaimed space, and any registry repair needed. Confirm active and retained generation links still resolve after cleanup. If an operation was interrupted or any reference check remains ambiguous, keep the data and describe the next inspection step.
