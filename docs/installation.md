# Agent-managed installation lifecycle

Use this procedure with a component's [catalog entry](../catalog/README.md), [recipe](../recipes/README.md), [records contract](records.md), and [platform assessment](platforms.md). There is no SiliconBoot executable, installer, controller, or background service. The agent uses available native facilities and upstream instructions without adding custom executable files to this repository or the generated project setup.

## Discover and freeze official versions

Perform discovery at the start of an explicitly requested installation or upgrade. Record the observation time in UTC and its evidence. Use upstream's version ordering and channel rules, not alphabetical tag ordering.

| Upstream situation | Resolution rule |
| --- | --- |
| Official stable releases exist | Select the latest official non-draft, non-prerelease release and record its immutable source identity. |
| Only tags exist | Establish which tags upstream treats as releases before selecting one. |
| No formal release exists | Follow the officially documented maintained branch, recording its name and full commit. Confirm the branch; do not assume its name. |
| PDK is continuously maintained | Resolve the original data sources as well as the builder, models, dependencies, and submodules. A recent builder does not establish recent PDK data. |
| Binary assets exist | Require the selected version, native OS, and native architecture to match. Record runtime and ABI requirements. |
| A package manager trails upstream | Use a matching official binary or native source build when supported; otherwise report the unmet latest requirement. |
| Network, rate limit, or source ambiguity prevents discovery | Record `latest_unknown`; preserve any usable existing installation without asserting fresh latest-version status. |

Use sources linked by the catalog and confirmed by upstream. A search result can locate official documentation but cannot establish permission to execute a third-party installer. Record canonical repository migrations and redirects, official release or commit evidence, asset URLs, and allowed download hosts. Record upstream checksums and signature verification when available. A locally calculated content hash identifies bytes; it does not establish upstream authenticity.

Record prerelease, nightly, fork, and source-snapshot channels explicitly. A non-default provider or channel must follow the user's request or an explicit accepted plan; it must never masquerade as the official stable release.

Freeze the resolution before installation. Include selected components, dependency edges, compatible ABI requirements, source revisions, build options, provider, channel, requested workflows, and blockers. Reuse that plan on resume. If an input changes, create a new dated plan and explain which nodes require rebuilding. Do not silently re-resolve a moving branch halfway through a build.

## Plan dependencies and installation identity

Expand all required dependencies and coupled groups. Distinguish runtime dependencies, build-only dependencies, system packages, PDK source data, model builders, and workflow-only requirements. Topologically order the dependency graph. Resolve a cycle only through an upstream-documented staged build; otherwise stop that component and explain the cycle.

Include uv as the default setup dependency and install it first if missing. Follow the [uv recipe](../recipes/uv/README.md) and [Python environment policy](python-environments.md). Freeze prerequisite uv/interpreter inputs before installing them, then freeze dependent package inputs before constructing each environment. Include uv, interpreter and package identities in the affected build records.

An installation key identifies the full build, not just the version. Record the component and provider, exact upstream source, host OS and architecture, compiler/toolchain, relevant ABI and dependency identities, build options, isolated language runtime, and patch digests. Use the SHA-256 digest of the canonical build-identity table defined in [records](records.md#canonical-build-identity), and retain that exact table in the receipt. A different input requires a different key. Version labels alone are insufficient for reuse.

Reused installations must match the identity, have a complete receipt, and pass the required current checks. Use the user's installation root for managed tools, SRAM compilers, and PDKs. Reusing a component installed elsewhere requires an explicitly accepted location exception. System-managed installations are `external`: record their canonical path, package provider, version, ownership, and dependency state. Reference external files without moving, deleting, or treating them as immutable managed content.

## Lock operations and preserve running work

Use the host's supported exclusive-lock facility with an observable owner and lifetime. A Markdown lock record describes the lock; writing that file does not acquire a lock. If no suitable facility is available, or its behavior cannot be established on the selected filesystem, stop mutation and record the missing capability. Never infer exclusivity from a timestamp or the absence of a running agent message.

Use a host-change lock for system dependency changes and admission of new or expanded leases, a per-component/store lock for installation changes, a per-project lock for generation changes, and a registry lock for shared references and leases. Where several locks are needed, acquire them in that order, sorting multiple component or project locks by canonical path. Never acquire an earlier lock while holding a later one; release and retry with a fresh state check. Hold the registry lock only for the short shared-reference transaction. Use native facilities that keep required locks alive for the whole operation.

Records identify the host, project, operation, lock mechanism, owner process and start identity, acquisition time, and affected paths. An interrupted operation does not justify breaking a lock until the owner is proven inactive. PID reuse, remote hosts, inaccessible projects, or uncertain process identity require preserving the lock or lease and reporting the uncertainty.

Before a long design run, acquire the host-change lock, project lock, and then registry lock, resolve `current` once to a concrete generation, and register a run lease protecting that generation, its documentation snapshot, and every direct or transitive installation dependency. Release these short transaction locks after the lease is durable. Creating or expanding an installation/validation operation lease follows the same host admission gate, with component locks acquired in the normal order where needed. The run uses the concrete generation throughout, including child processes and later workflow steps. End the lease only after the complete process tree is finished and outputs are recorded. See the [run prompt](../prompts/run.md).

An upgrade may activate a new generation while a leased old generation runs, because managed installations are immutable. Host package changes are different: hold the host-change lock while evaluating active leases and external dependencies, performing authorized compatible changes, and recording their result. Release the registry lock after the reference scan; the host lock prevents new lease admission until the mutation ends. If a change would conflict with a protected run/build, or compatibility is uncertain, defer it and release the host lock so that the running work can finish. A lease does not isolate a run from operating-system changes by actors outside this protocol.

## Install at the final prefix

Reserve a unique final installation location under the store and record its ownership before writing. Under the host-change, component, and registry locks in that order, create an operation lease protecting the installation, all direct/transitive dependencies, the documentation snapshot, and any candidate generation before releasing those locks. Reacquire the required component locks for the build while the lease remains durable. Keep that protection until a retained generation has registered the same references or an explicit failure-retention decision is recorded. A newly verified installation must not become an unprotected garbage-collection candidate between installation and activation.

Build out of tree where upstream supports it, configuring the persistent final prefix. A virtual environment or binary containing absolute runtime references must not be moved from a temporary directory and assumed relocatable.

Keep upstream's required runtime layout, resources, licenses, technology data, relative links, and language environments. Use uv to create and manage independent Python environments at their final prefixes. Follow the Python environment policy for compatible interpreters, exact dependencies, shared coupled groups and documented upstream-managed runtime exceptions. Isolate Ruby and other ecosystem dependencies as appropriate. Never overwrite the OS-managed Python environment or combine unrelated Python packages through a global import path.

Use official public entrypoints at their actual persistent locations. A project binary link may point into an installed runtime environment or an upstream-supplied entrypoint. Do not generate a custom launcher to compensate for runtime requirements. Record the required interpreter, environment variables, working directory, and invocation method in the manifest and `ENVIRONMENT.md`. Libraries and plugins are used through their interpreter or host tool; they do not receive invented binaries.

Read the actual build outcome and preserve native exit codes. Finish the receipt with the exact resolved sources, build dependencies, host changes, entrypoint map, runtime requirements, content digests, and verification evidence. Make a successfully verified managed installation immutable by procedure; new changes always create a new installation identity.

## State and resumption

| State | Meaning and next action |
| --- | --- |
| `planned` | Selected, with no discovery or install result yet. |
| `resolving` | Official version discovery is in progress. |
| `latest_unknown` | Latest status cannot be established; do not claim it is current. |
| `downloading` | Verified-source acquisition is in progress. |
| `building` | Installation or source build is in progress. |
| `installed` | Persistent files exist; required verification remains. |
| `verified` | Named checks passed for the recorded scope. |
| `failed` | The attempted action failed; retain cause, exit status, logs, and resume point. |
| `blocked_dependency` | A named dependency prevents progress. |
| `unsupported` | The selected component or combination lacks applicable native support. |
| `blocked_latest_incompatible` | The selected latest versions fail the required compatibility conditions. |

Record transitions and candidate paths in the operation state. After interruption, re-read the frozen plan, ownership, locks, receipts, and filesystem. Check incomplete downloads and build trees before using them. Reuse only complete matching inputs and verified installations. A directory's existence or an `installed` state cannot authorize activation. Retry only unfinished or changed nodes, with downstream rebuilding when an input identity changes.

Independent failures do not prevent unrelated work. A first bootstrap can activate a verified subset as `partial`, with missing requirements and affected workflows listed. A later upgrade preserves the existing generation until the promised capabilities pass; latest incompatibility leaves the previous environment available. A separately named compatible environment can be created when requested, with every non-latest selection disclosed.

## Activate one generation

1. Confirm that a durable operation lease protects every candidate installation, its transitive dependencies, and its documentation snapshot. Extend that lease under the host admission gate before using any new input. Under the appropriate component locks, finish verification and immutable receipts. Publish their registry entries under the registry lock, preserving concurrent references and the operation lease before releasing component locks.
2. Create a candidate under `.siliconboot/generations/` with a unique generation identifier. Fill its `tools`, `pdk`, and `bin` views plus `manifest.md`, `lock.md`, and `validation.md`. Preserve PDK families and shared files together.
3. Verify every link's canonical target, executable permission where applicable, provider identity, resource paths, and required environment. Detect broken or cyclic links and command-name collisions. Test namespaced entrypoints as well as selected default providers. Do not expose failed components.
4. Run required component and affected workflow checks against this concrete candidate, from a fresh process and a different working directory where the recipe permits. Confirm that temporary build files are unnecessary. Record untested GUI or other capabilities honestly.
5. Acquire the host-change lock, project lock, and registry lock in that order. Re-read the active generation, project configuration, host dependency observations, references, and validation evidence. Abort and replan if they changed incompatibly since the candidate was built. Register the candidate and retain the previous valid generation before activation. Transfer protection from the operation lease only after the retained candidate's complete references are durable; preserve the lease through validation and every preceding gap. Keep the host-change gate through the switch so system mutation cannot invalidate these observations during activation.
6. Prepare a replacement `current` symlink beside the existing one on the same filesystem. Use the host's verified atomic replacement facility to replace that single symlink. Never update top-level `tools`, `pdk`, and `bin` one at a time to change versions. If atomic replacement cannot be established, leave the previous generation active and report the blocker.
7. Resolve `current` and verify that all three views and the manifest, lock, and validation belong to the intended generation. Record the previous and new generation, replacement facility, time, and observed result. A failed or ambiguous switch needs reconciliation under the lock before any cleanup.
8. Export the active portable lock to `config/environment.lock.md` using atomic file replacement, then reconcile the bounded project guidance and registry. The active generation's `lock.md` is authoritative during recovery; a stale exported copy is a reported recovery task. Keep the prior generation and references until the transaction record is complete.

On interruption, inspect the actual resolved `current` under the project and registry locks. If it identifies the verified old generation, the candidate remains inactive; if it identifies the verified new generation, finish the export and registry reconciliation. If neither result can be proven, fail closed, preserve both generations, and report the unresolved activation. Do not guess from the operation's last written state.

Refer to [upgrade and recovery](upgrade.md), [cleanup](cleanup.md), and [validation](validation.md) for the remaining lifecycle rules.
