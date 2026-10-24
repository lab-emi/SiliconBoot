# Project environment instructions

## SiliconBoot managed section begins

Project: [PROJECT_ABSOLUTE_PATH]\
Tool installation root: [TOOLS_ABSOLUTE_PATH]\
PDK installation root: [PDKS_ABSOLUTE_PATH]\
Public binary directory: [BIN_ABSOLUTE_PATH]\
Persistent guidance: [GUIDE_ABSOLUTE_PATH]\
Generation used to prepare this guide: [GENERATION_ID]\
Authoritative active map: [ACTIVE_MANIFEST_ABSOLUTE_PATH]

This document describes environment setup in prose. Apply the values through the host's native session or process environment facilities. The active manifest is authoritative: confirm that this guide's generation and paths still match before starting new work. If an interrupted activation left this guide stale, reconcile it from the actual current manifest before using any rendered paths. No activation script or custom launcher is provided. All project-relative paths in this guide are relative to [PROJECT_ABSOLUTE_PATH], not this file's `.siliconboot/` directory. Setup creates no workspace or design scaffold.

On macOS, install or upgrade tools using [Homebrew-first selection]([GUIDE_ABSOLUTE_PATH]/docs/installation.md#macos-check-homebrew-first) when its package matches the latest official upstream release and native requirements. Homebrew-managed tools are external exceptions to the tool root above. Record their actual prefix, concrete runtime targets, dependencies and retention limits in the manifest and receipts: [HOMEBREW_EXTERNAL_RECORD_REFERENCES_OR_NOT_APPLICABLE]. Recheck these targets before use; a fixed generation does not make external files immutable. Ordinary runs do not refresh packages or change providers.

## Begin a session or run

1. Read `.siliconboot/project.md` and resolve `.siliconboot/current` to its absolute generation directory. Confirm that its manifest, lock, and validation identify the same verified or explicitly partial generation.
2. For a long workflow, acquire the host-change admission lock, project lock, and registry lock in that order. Re-resolve `current` and recheck its records under those locks, then record a run lease before starting any processes. Release these transaction locks after the lease is durable. Keep that concrete generation for all subsequent steps. Follow [run instructions]([GUIDE_ABSOLUTE_PATH]/prompts/run.md).
3. Place the concrete generation's `bin` directory at the front of this session's command search path once, preserving other entries and avoiding duplicates. Keep original values if the session will later be restored.
4. Set only the selected PDK and tool variables documented below. Use concrete generation or installation paths throughout the run. Do not combine unrelated Python environments or add broad dynamic-library search paths.
5. Launch each upstream entrypoint with its recorded interpreter if required and the documented working directory. Use the component's private runtime for library imports. Keep outputs under a unique project run directory.
6. Record process outcomes and artifact evidence. Release a run lease only after all child processes and workflow steps finish. Restore original session values when leaving a temporary environment.

## Default shell PATH

Detected default login shell and evidence: [SHELL_EXECUTABLE_AND_DETECTION_EVIDENCE].\
Effective startup configuration: [SHELL_CONFIGURATION_ABSOLUTE_PATH].\
Existing PATH rule or bounded SiliconBoot section and backup: [PATH_RULE_AND_BACKUP_OR_NO_EDIT_NEEDED].\
Fresh interactive shell and applicable login check: [OUTCOMES_AND_EVIDENCE].\
Repeated startup or sourcing check: [NO_DUPLICATE_PATH_EVIDENCE_OR_BLOCKER].

Public binary symlinks live in [BIN_ABSOLUTE_PATH], expanded from the invoking user's `~/bin`. Follow [default-shell setup]([GUIDE_ABSOLUTE_PATH]/docs/project-layout.md#default-shell-path) for the selected bashrc, zshrc or fish configuration, honoring ZDOTDIR and fish's configuration directory. Preserve other shell settings and unrelated binary entries. Ordinary interactive discovery uses this directory; reproducible runs use a concrete generation's bin directory as described above. Unknown shells or startup overrides require an explicit blocker, not edits to a guessed configuration.

## Common environment settings

| Setting | Concrete value or selection rule | Required for | Verification evidence |
| --- | --- | --- | --- |
| Command search path prefix for a pinned run | [GENERATION_BIN_ABSOLUTE_PATH] | [SELECTED_PUBLIC_COMMANDS] | [CHECK_REFERENCE] |
| PDK root, when required | [PDK_ROOT_OR_NOT_APPLICABLE] | [RECIPES_REQUIRING_IT] | [CHECK_REFERENCE] |
| PDK variant, when required | [PDK_VARIANT_OR_NOT_APPLICABLE] | [RECIPES_REQUIRING_IT] | [CHECK_REFERENCE] |
| Other verified variable | [NAME_AND_VALUE_OR_NONE] | [COMPONENT] | [CHECK_REFERENCE] |

## AppImage temporary directory

For LibreLane AppImage, create a private `tmp` directory inside the new run under [PROJECT_ABSOLUTE_PATH]/runs. Set `TMPDIR` to its canonical absolute path for that process and its children, and record the concrete path in the run record. Verify that the host's FUSE mount policy permits the real location. On restricted AppArmor hosts, a project directory under the user's home may be allowed while another writable location is denied. Keep the executable under the persistent store and diagnose mountpoint denials before changing the installed provider or capability claims.

Follow [temporary mount guidance]([GUIDE_ABSOLUTE_PATH]/docs/project-layout.md#appimage-temporary-mounts). Wait for every child process and mount to finish before removing the owned temporary directory. If AppImage is not selected, record this setting as not applicable in the per-tool map.

## Per-tool use

| Component | Upstream entrypoint or library/host tool | Interpreter | Required environment | Working directory | Runtime resource path | Known limits |
| --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [ABSOLUTE_ENTRYPOINT_OR_LIBRARY_USE] | [INTERPRETER_OR_NOT_APPLICABLE] | [EXACT_SETTINGS_OR_NONE] | [CWD_RULE] | [PERSISTENT_RESOURCES] | [LIMITS_OR_NONE] |

Keep invocations as task-specific native process actions performed by the agent; do not turn this table into shell code or a launcher. Libraries and plugins without an upstream public CLI have no public binary entry.

## Python environments

Use uv for Python setup and maintenance, installing it first if missing according to the [uv recipe]([GUIDE_ABSOLUTE_PATH]/recipes/uv/README.md). Follow the [Python environment policy]([GUIDE_ABSOLUTE_PATH]/docs/python-environments.md) for exact inputs and upstream runtime exceptions. Populate this table from the manifest and receipts; use `not applicable` with a reason for components without Python.

| Component or coupled group | Manager version and executable | Environment path | Exact interpreter, provider and receipt | Dependency lock and digest | Upstream runtime exception |
| --- | --- | --- | --- | --- | --- |
| [COMPONENT_OR_GROUP] | [UV_VERSION_AND_ABSOLUTE_PATH_OR_RECORDED_MANAGER] | [ENVIRONMENT_ABSOLUTE_PATH] | [PYTHON_IDENTITY_PATH_AND_RECEIPT] | [LOCK_REFERENCE_AND_DIGEST] | [REASON_AND_OFFICIAL_EVIDENCE_OR_NONE] |

For setup operations, record each runtime's concrete `UV_PYTHON_INSTALL_DIR` and `UV_PYTHON_BIN_DIR`, the store's `UV_CACHE_DIR`, and `UV_PROJECT_ENVIRONMENT` when an upstream uv project requires it: [PER_COMPONENT_SETTINGS_AND_EVIDENCE]. Keep these settings scoped to the intended operation and environment.

For design runs, use the table's verified upstream entrypoint or fixed interpreter directly. If the workflow requires `uv run`, use only its recorded invocation that disables synchronization, lock updates and downloads. Do not resolve new packages or create a replacement environment implicitly. Missing dependencies require a maintenance operation.

## Environment checks and recovery

Fresh-process check: [OUTCOME_AND_EVIDENCE].\
Different-working-directory check: [OUTCOME_AND_EVIDENCE_OR_DOCUMENTED_RESTRICTION].\
GUI availability and check: [OUTCOME_AND_EVIDENCE_OR_NOT_RUN].\
Known latest or compatibility limitations: [LIMITATIONS_OR_NONE].

If links, versions, environment settings, or the active generation disagree with these records, stop the affected run and follow [doctor instructions]([GUIDE_ABSOLUTE_PATH]/prompts/doctor.md). Do not repair the mismatch by installing or upgrading silently.

## SiliconBoot managed section ends
