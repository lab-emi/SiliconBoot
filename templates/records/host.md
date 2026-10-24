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
| User-supplied installation root and canonical store path | [LEGACY_ROOT_OR_NOT_APPLICABLE_FOR_HOME_LAYOUT] |
| Invoking user and actual home directory | [NONSECRET_USER_ID_AND_HOME_ABSOLUTE_PATH] |
| Tool installation root | [TOOLS_ABSOLUTE_AND_CANONICAL_PATHS] |
| PDK installation root | [PDKS_ABSOLUTE_AND_CANONICAL_PATHS] |
| Public binary directory | [BIN_ABSOLUTE_AND_CANONICAL_PATHS] |
| Root ownership, write access and existing symlinks | [INSPECTION_EVIDENCE_AND_CONFLICTS_OR_NONE] |
| Default login shell and detection evidence | [SHELL_EXECUTABLE_ACCOUNT_LOOKUP_OR_RECORDED_FALLBACK] |
| Effective shell startup configuration | [CONFIGURATION_ABSOLUTE_PATH_AND_DISCOVERY_EVIDENCE] |
| PATH update, backup and fresh-shell checks | [CHANGE_OR_EXISTING_RULE_BACKUP_AND_EVIDENCE_OR_BLOCKER] |
| Documentation snapshot | [REVISION_DIGEST_AND_ABSOLUTE_PATH] |
| Project/store filesystem types | [FILESYSTEMS_AND_MOUNT_CHARACTERISTICS] |
| Free disk and memory | [MEASUREMENTS_AND_TIME] |
| Build concurrency limit | [LIMIT_AND_REASON] |
| Native compilers and runtimes | [VERSIONS_AND_PROVIDERS] |
| uv discovery | [ABSOLUTE_PATH_VERSION_PROVIDER_AND_NATIVE_ARCHITECTURE_OR_MISSING] |
| Python setup prerequisite | [UV_REUSE_OR_OFFICIAL_INSTALL_PLAN_AND_INTERPRETER_REQUIREMENTS] |
| System package manager | [PROVIDER_AND_STATE_REFERENCE] |
| macOS Homebrew | [EXECUTABLE_VERSION_NATIVE_ARCHITECTURE_PREFIX_OWNERSHIP_WRITE_ACCESS_AND_AVAILABILITY_OR_NOT_APPLICABLE] |
| Homebrew external locations and retention limits | [CONCRETE_KEG_CASKROOM_APPLICATION_PATHS_DEPENDENCIES_AND_RECORD_REFERENCES_OR_NOT_APPLICABLE] |
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

Setup uses no sudo or administrator-managed package changes. Scoped, user-writable macOS Homebrew changes follow [the macOS policy](../../docs/installation.md#macos-check-homebrew-first); record affected package and dependency versions, retained-generation impact and rollback limits here. Record missing privileged dependencies as blockers and any separately requested administrator action here. For such separate changes, record package names and versions before and after changes, affected workflows and run leases, and any rollback limitations. Do not record passwords, tokens, or sensitive approval material.
