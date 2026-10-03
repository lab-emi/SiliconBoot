# Native host record

Record version: 1\
Record type: Host\
Observed at: [UTC_TIME]

| Field | Value |
| --- | --- |
| Host identifier | [LOCAL_NONSECRET_ID] |
| Native OS and release | [OS_RELEASE] |
| CPU architecture | [CPU_ARCHITECTURE] |
| Process architecture | [PROCESS_ARCHITECTURE] |
| Execution environment | [DIRECT_NATIVE_OR_EXPLICIT_ENVIRONMENT_DESCRIPTION] |
| Discovered SiliconBoot clone | [REPOSITORY_ABSOLUTE_PATH] |
| Project identifier and canonical path | [PROJECT_ID_AND_ABSOLUTE_PATH] |
| User-supplied installation root and canonical store path | [ABSOLUTE_PATH_AND_REQUEST_REFERENCE] |
| Documentation snapshot | [REVISION_DIGEST_AND_ABSOLUTE_PATH] |
| Project/store filesystem types | [FILESYSTEMS_AND_MOUNT_CHARACTERISTICS] |
| Free disk and memory | [MEASUREMENTS_AND_TIME] |
| Build concurrency limit | [LIMIT_AND_REASON] |
| Native compilers and runtimes | [VERSIONS_AND_PROVIDERS] |
| System package manager | [PROVIDER_AND_STATE_REFERENCE] |
| GUI/display availability | [OBSERVATION_AND_LIMITATIONS] |
| Network or source-access limits | [LIMITATIONS_OR_NONE] |
| Existing installation inventory | [INVENTORY_REFERENCE] |

## Native filesystem capabilities

| Capability | Native mechanism | Evidence on selected filesystem | Result and limits |
| --- | --- | --- | --- |
| Exclusive operation lock | [MECHANISM] | [EVIDENCE] | [RESULT] |
| Lock owner/lifetime observation | [MECHANISM] | [EVIDENCE] | [RESULT] |
| Symbolic links | [MECHANISM] | [EVIDENCE] | [RESULT] |
| Atomic sibling-symlink replacement | [MECHANISM] | [EVIDENCE] | [RESULT] |
| Atomic record-file replacement | [MECHANISM] | [EVIDENCE] | [RESULT] |
| Safe no-follow deletion | [MECHANISM] | [EVIDENCE] | [RESULT] |

## Authorization and system changes

| Operation | User-authorized scope and request reference | Host approval requirements | Actual change and result |
| --- | --- | --- | --- |
| [OPERATION_OR_NONE] | [SCOPE] | [REQUIREMENTS] | [OUTCOME] |

Record package names and versions before and after changes, affected workflows and run leases, and any rollback limitations. Do not record passwords, tokens, or sensitive approval material.
