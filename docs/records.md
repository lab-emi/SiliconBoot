# Markdown record contract

All SiliconBoot records are English Markdown with **Record version: 1** and **Record type** near the top. Templates live in [templates/records](../templates/README.md). Tables are intended to be readable by humans and agents; no parser, JSON schema, or helper executable is required.

Use stable field labels from the templates. Add sections for new information instead of overloading an existing field's meaning. Record timestamps with date, time, and UTC offset, preferably UTC. Record full source commits, named digest algorithms, and complete public evidence URLs. Use `unknown`, `not applicable`, or `not_run` with a reason; do not leave ambiguous empty fields. Check outcomes use `pass`, `fail`, `blocked`, and `not_run`. Keep secrets, access tokens, credentials, and signed private download parameters out of records and logs.

A future incompatible contract must increment the record version, document migration, and preserve the original. An agent must stop writes to an unknown record version until it has read compatible instructions; it may still report its contents without interpreting unsupported semantics.

## Record inventory

| Type | Location | Scope |
| --- | --- | --- |
| Project | `project.md` | Desired choices, scope, policies, and required workflows; largely portable. |
| Host | `.siliconboot/host.md` | Native platform, paths, capabilities, approvals, and system dependency observations; host-specific. |
| Resolution | `.siliconboot/resolutions/<operation-id>.md` | Frozen discovery results, official evidence, dependency graph, and planned build identities. |
| State | `.siliconboot/state.md` | Resumable operation transitions, ownership, locks, pending work, and recovery status; host-specific. |
| Receipt | Store installation directory's `receipt.md` | Immutable identity and evidence for one verified managed installation; host-specific. |
| Manifest | Generation's `manifest.md` | Host-specific installation, entrypoint, environment, and capability map. |
| Lock | Generation's `lock.md`; exported as `config/environment.lock.md` | Exact portable sources, build choices, dependencies, and declared compatibility limits. |
| Validation | Generation's `validation.md` | Component and workflow checks tied to exact inputs and artifacts. |
| Run | `runs/<run-id>/run.md` | Generation-pinned process and design evidence; separate from install verification. |
| Memory | Run's memory evidence; accepted copy under `ip/memory/manifests/<macro-id>.md` | Exact macro request, all output views, independent check results, and explicit acceptance. |
| Registry | Store's `registry.md` | Project references, retained generations, installation ownership, and run leases; host-specific. |

The generation manifest, lock, and validation form one consistency unit. A candidate is not eligible for activation until their generation identity and component identities agree. Once activated, preserve these records with their generation; add new diagnostic/run evidence separately and create a new generation for changed environment claims. Post-cleanup checks and actual cleanup outcomes belong in separate run/state/log records linked from the immutable records. If those checks invalidate an active capability, record the current failure prominently in state, block affected runs, and reconcile or roll back; never conceal the failure by editing historical evidence.

## Three independent outcomes

Every selected component and workflow report carries these fields independently:

| Field | Allowed meanings |
| --- | --- |
| `installed_latest` | `yes`, `no`, or `unknown`, with channel, observed time, and frozen discovery evidence. `yes` means latest at that observation, not indefinitely. |
| `component_usable` | `yes`, `no`, or `unknown`, with the exact checks and host scope. |
| `workflow_ready` | `yes`, `no`, `unknown`, or `not applicable`, assessed separately for every named tool/PDK/memory combination. |

Use lifecycle states from [installation](installation.md#state-and-resumption) in addition to these fields. A latest component can be unusable with another latest component; record `blocked_latest_incompatible` without disguising it as a successful downgrade. A passing version check is insufficient to set functional or workflow readiness to `yes`. `not_run` is evidence absence, never a pass.

A generation's aggregate status is `ready`, `partial`, or `blocked`, relative to the complete recorded requested scope. `ready` requires every required component and workflow to meet that scope. Any selected catalog item left planned, unsupported, unresolved, failed, or unverified must be counted and listed. A narrowed user-selected profile can be ready for its scope without claiming that the full catalog is ready.

## Exact sources and installation receipts

Record the component's canonical catalog ID, kind, package name, repository identity, provider, and public entrypoints separately. This prevents matching an unrelated package by name. A receipt contains:

- Official homepage, source repository, installation documentation, release/tag, full source commit, channel, maintained branch where relevant, discovery timestamp, and canonical redirects.
- Every source asset and final download URL, content digest, upstream checksum source, and signature verification result or absence. Record recursively required submodule and source dependencies.
- Native host and process architecture, OS release, compiler and runtime versions, build options, dependency identities, ABI constraints, isolated interpreter location, and final installation prefix.
- Runtime resources, upstream public entrypoints, interpreter/host-tool usage, required environment variables, working-directory constraints, and PDK technology/model layout.
- Modifications and their provenance, affected sources, rationale, version bounds, digests, and removal condition. Modified source is labeled `modified`. SiliconBoot stores the description and identities in Markdown; any upstream-approved patch remains an upstream installation input rather than new repository code.
- Ownership boundaries, temporary artifact inventory, persistent runtime files, system package changes, native process exit statuses, logs, verification artifact digests, and achieved scope.

Receipt publication after verification makes the managed installation reusable; a provisional receipt remains explicitly incomplete. A published receipt includes the cleanup policy and a stable reference to the operation's later outcome record. Write actual cleanup results and later inspections there instead of editing the receipt. Never rewrite a verified managed installation to fit a new dependency set. External installations are mutable by their owners and require current rechecks before reuse.

## Canonical build identity

The receipt template includes a two-column build-identity table. Hash only that table, including its fixed header and separator rows, using SHA-256. Preserve the exact table as identity evidence. Apply these rules before hashing:

- Use UTF-8 without a byte-order mark, Unicode NFC text, LF line endings, and exactly one final newline. Use the template's single-space padding around each table cell, without alignment padding or trailing spaces.
- Use lowercase ASCII field keys and sort all data rows by their keys using ASCII byte order. Each key occurs once. Use catalog component IDs and normalized lowercase OS/architecture identifiers; preserve the case of upstream references and build-option values.
- Keep one scalar value in each row. Represent each source, dependency, build option, ABI requirement, and patch in its own uniquely named field using its stable component/input identifier. Use full commits and lowercase hexadecimal digests. A set's row order comes from its keys, never discovery order.
- Encode a literal percent sign, vertical bar, carriage return, or newline in a value as its uppercase percent-encoded UTF-8 byte form so the table retains one unambiguous row per field. Do not otherwise reformat a value after freezing the plan.
- Include exact source, provider, channel, host OS/release and target architecture, toolchain/runtime, dependency build identities, relevant ABI requirements, build options, model/technology inputs, and patch identities. Exclude timestamps, usernames, temporary paths, and final installation paths; the final prefix is derived from the key and recorded separately.

If an upstream build embeds another path that changes its behavior, include the path-independent choice when that accurately captures the input; otherwise record the actual relevant path as a host-bound build input and disclose the portability limit. An identity cannot be declared complete while required dependency identities remain unresolved. Reuse the frozen table verbatim on resume instead of reconstructing its formatting from memory. Native text and digest facilities are sufficient; no custom hashing program is required.

## Portable locks and reproducibility limits

The portable lock contains exact component/provider/channel identities, source revisions and content digests, dependency graph, coupled groups, PDK data and builder/model inputs, build options, patch identities, selected command providers, required workflows, and documentation revision. Every patch or additional source input needs a retrievable upstream URL or preserved portable asset reference as well as its digest; a hash alone cannot restore its content. Use logical dependency identities and project-relative design paths. Exclude local store prefixes, private host identifiers, temporary paths, local interpreter paths, and lease/lock owners.

Keep target OS/architecture and ABI constraints in the lock because they are part of the requested environment. Host-specific locations belong in the manifest. A restore on another platform may rebuild the same source choices but must report that it is a different binary environment, create a new local identity, and rerun relevant checks. If the exact dependency or supported platform is unavailable, report the restore as blocked; a substitute is a separately requested environment.

Pin transitive dependencies where the upstream ecosystem provides an exact resolution. Record unresolved or unpinnable dependencies explicitly. Exact input records support repeatability but do not prove bit-for-bit reproducible builds. Report `exact source restore`, `verified equivalent workflow`, or `bit-for-bit match` only when the corresponding evidence exists.

Keep the active lock authoritative at `.siliconboot/current/lock.md`. The version-controlled export must identify the same generation's source resolution without including its machine-local paths. A stale export after an interrupted activation is repaired from the actual active generation, with the recovery recorded.

## Evidence, ownership, and safe recovery

Validation records identify the check, expected criterion, actual outcome, real exit status, parsed report result, input sources, generation, PDK/corner/technology port, logs, and artifacts. Keep a digest and relative location for retained evidence. A successful process exit alone does not prove timing closure, correct numeric output, DRC, LVS, or memory completeness. See [validation](validation.md).

State and registry records map each owned file tree to the operation that created it. Include canonical roots, expected type, allowed temporary children, completion state, registered references, leases, and native lock evidence. Markdown records are bookkeeping and evidence; native locking and atomic filesystem behavior supply concurrency guarantees.

Use write-to-a-sibling-file and native atomic replacement for complete Markdown record updates where supported. Under the relevant locks, compare the previously observed revision before replacing a shared record, and preserve a recoverable previous revision. An ambiguous or conflicting revision requires re-reading and reconciling; never overwrite another agent's new references.

Deletion requires current ownership and reference checks, as described in [cleanup](cleanup.md). A missing registry entry does not prove that a directory is disposable. Interrupted work, inaccessible registered projects, and uncertain leases must remain protected until resolved.
