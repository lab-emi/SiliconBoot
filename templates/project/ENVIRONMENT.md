# Project environment instructions

## SiliconBoot managed section begins

Project: [PROJECT_ABSOLUTE_PATH]\
Persistent store: [STORE_ABSOLUTE_PATH]\
Persistent guidance: [GUIDE_ABSOLUTE_PATH]\
Generation used to prepare this guide: [GENERATION_ID]\
Authoritative active map: [ACTIVE_MANIFEST_ABSOLUTE_PATH]

This document describes environment setup in prose. Apply the values through the host's native session or process environment facilities. The active manifest is authoritative: confirm that this guide's generation and paths still match before starting new work. If an interrupted activation left this guide stale, reconcile it from the actual current manifest before using any rendered paths. No activation script or custom launcher is provided.

## Begin a session or run

1. Read `project.md` and resolve `.siliconboot/current` to its absolute generation directory. Confirm that its manifest, lock, and validation identify the same verified or explicitly partial generation.
2. For a long workflow, acquire the host-change admission lock, project lock, and registry lock in that order. Re-resolve `current` and recheck its records under those locks, then record a run lease before starting any processes. Release these transaction locks after the lease is durable. Keep that concrete generation for all subsequent steps. Follow [run instructions]([GUIDE_ABSOLUTE_PATH]/prompts/run.md).
3. Place the concrete generation's `bin` directory at the front of this session's command search path once, preserving other entries and avoiding duplicates. Keep original values if the session will later be restored.
4. Set only the selected PDK and tool variables documented below. Use concrete generation or installation paths throughout the run. Do not combine unrelated Python environments or add broad dynamic-library search paths.
5. Launch each upstream entrypoint with its recorded interpreter if required and the documented working directory. Use the component's private runtime for library imports. Keep outputs under a unique project run directory.
6. Record process outcomes and artifact evidence. Release a run lease only after all child processes and workflow steps finish. Restore original session values when leaving a temporary environment.

## Common environment settings

| Setting | Concrete value or selection rule | Required for | Verification evidence |
| --- | --- | --- | --- |
| Command search path prefix | [GENERATION_BIN_ABSOLUTE_PATH] | [SELECTED_PUBLIC_COMMANDS] | [CHECK_REFERENCE] |
| PDK root, when required | [PDK_ROOT_OR_NOT_APPLICABLE] | [RECIPES_REQUIRING_IT] | [CHECK_REFERENCE] |
| PDK variant, when required | [PDK_VARIANT_OR_NOT_APPLICABLE] | [RECIPES_REQUIRING_IT] | [CHECK_REFERENCE] |
| Other verified variable | [NAME_AND_VALUE_OR_NONE] | [COMPONENT] | [CHECK_REFERENCE] |

## Per-tool use

| Component | Upstream entrypoint or library/host tool | Interpreter | Required environment | Working directory | Runtime resource path | Known limits |
| --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [ABSOLUTE_ENTRYPOINT_OR_LIBRARY_USE] | [INTERPRETER_OR_NOT_APPLICABLE] | [EXACT_SETTINGS_OR_NONE] | [CWD_RULE] | [PERSISTENT_RESOURCES] | [LIMITS_OR_NONE] |

Keep invocations as task-specific native process actions performed by the agent; do not turn this table into shell code or a launcher. Libraries and plugins without an upstream public CLI have no project binary entry.

## Environment checks and recovery

Fresh-process check: [OUTCOME_AND_EVIDENCE].\
Different-working-directory check: [OUTCOME_AND_EVIDENCE_OR_DOCUMENTED_RESTRICTION].\
GUI availability and check: [OUTCOME_AND_EVIDENCE_OR_NOT_RUN].\
Known latest or compatibility limitations: [LIMITATIONS_OR_NONE].

If links, versions, environment settings, or the active generation disagree with these records, stop the affected run and follow [doctor instructions]([GUIDE_ABSOLUTE_PATH]/prompts/doctor.md). Do not repair the mismatch by installing or upgrading silently.

## SiliconBoot managed section ends
