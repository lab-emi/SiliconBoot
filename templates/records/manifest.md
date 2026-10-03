# Environment generation manifest

Record version: 1\
Record type: Manifest\
Project ID: [PROJECT_ID]\
Generation ID: [GENERATION_ID]\
Created at: [UTC_TIME]\
Generation status: [READY_PARTIAL_OR_BLOCKED]\
Requested scope: [PROFILE_COMPONENTS_AND_WORKFLOWS]\
Native host: [HOST_RECORD_REFERENCE]\
Generation absolute path: [ABSOLUTE_PATH]\
Store absolute path: [ABSOLUTE_PATH]\
Documentation snapshot: [ABSOLUTE_PATH_REVISION_AND_DIGEST]\
Frozen resolution: [PATH_AND_DIGEST]\
Portable lock: [GENERATION_LOCK_PATH_AND_DIGEST]\
Validation: [GENERATION_VALIDATION_PATH_AND_DIGEST]

## Components

| Catalog ID | Kind/provider/channel | Exact source/version | Installation key and receipt | Installation view/target | State | installed_latest | component_usable | workflow_ready |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [ID] | [IDENTITY] | [VERSION_AND_COMMIT] | [KEY_AND_RECEIPT_PATH] | [LINK_AND_CANONICAL_TARGET] | [STATE] | [RESULT_AND_TIME] | [RESULT_AND_EVIDENCE] | [PER_WORKFLOW_RESULTS] |

Include every selected entry, even if it has no installed target. Record missing entries explicitly rather than omitting them from this table.

## Entrypoint map

| Exported name | Component/provider | Upstream public target | Interpreter or host tool | Environment requirements | Working-directory rule | Collision choice evidence |
| --- | --- | --- | --- | --- | --- | --- |
| [NAME] | [IDENTITY] | [ABSOLUTE_PATH] | [REQUIREMENT_OR_NONE] | [SETTINGS_OR_NONE] | [RULE] | [PROJECT_CHOICE_OR_UNAMBIGUOUS] |

## Libraries, PDKs, and coupled resources

| Resource | Installation view | Actual use | Coupled members/shared files | Source/builder/model/technology identities | Verification evidence |
| --- | --- | --- | --- | --- | --- |
| [RESOURCE_ID] | [ABSOLUTE_PATH] | [INTERPRETER_HOST_TOOL_OR_PDK_USE] | [MEMBERS_OR_NONE] | [IDENTITIES] | [EVIDENCE] |

## Python environments

| Component or coupled group | Manager identity and executable | Environment and fixed interpreter paths | Runtime receipt and dependency lock | Setup settings | Upstream runtime exception |
| --- | --- | --- | --- | --- | --- |
| [ID_OR_NOT_APPLICABLE] | [UV_RECEIPT_AND_ABSOLUTE_PATH_OR_RECORDED_MANAGER] | [ABSOLUTE_PATHS] | [RECEIPT_LOCK_REFERENCE_AND_DIGEST] | [UV_STORAGE_AND_ENVIRONMENT_SETTINGS] | [REASON_AND_EVIDENCE_OR_NONE] |

Keep uv, interpreters and package inputs in the dependency references protected by this generation. Record any required uv-based run invocation in the entrypoint map with synchronization, lock updates and downloads disabled.

## Generation checks and limits

- Link, target, permission, and cycle checks: [EVIDENCE].
- Per-tool environment and fresh-process checks: [EVIDENCE].
- Required workflow outcomes: [EVIDENCE].
- Planned, unsupported, failed, blocked, latest-unknown, and unverified entries: [IDS_AND_REASONS_OR_NONE].
- Missing views, untested corners, GUI limits, and upstream restrictions: [DETAILS_OR_NONE].
- External mutable dependencies and host rollback caveats: [DETAILS].
- Run lease and retention policy: [REGISTRY_REFERENCES].

Activation outcome is recorded separately in the operation state so this generation's manifest remains immutable.
