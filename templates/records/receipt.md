# Installation receipt: [COMPONENT_ID]

Record version: 1\
Record type: Receipt\
Receipt status: [PROVISIONAL_OR_VERIFIED]\
Installation key: [INSTALL_KEY]\
Created by operation: [OPERATION_ID]\
Verified at: [UTC_TIME_OR_NOT_VERIFIED]

## Identity and sources

| Field | Value |
| --- | --- |
| Canonical component ID and kind | [ID_AND_KIND] |
| Package identity, repository identity, and aliases | [IDENTITIES] |
| Provider and channel | [PROVIDER_AND_CHANNEL] |
| Ownership | [MANAGED_OR_EXTERNAL_AND_OWNER] |
| Official homepage | [URL] |
| Official repository and canonical redirects | [URL_AND_REDIRECTS_OR_NONE] |
| Official installation documentation | [URL] |
| Release/tag/version | [EXACT_LABEL] |
| Maintained branch, if applicable | [BRANCH_AND_EVIDENCE_OR_NOT_APPLICABLE] |
| Full source commit | [FULL_COMMIT_OR_NOT_APPLICABLE] |
| Latest discovery time and resolution evidence | [UTC_TIME_AND_RECORD] |
| Recipe/guidance revision and digest | [IDENTITY] |
| Source modification status | [UNMODIFIED_OR_MODIFIED_WITH_REASON] |

## Inputs and integrity

| Input | Source/final asset URL | Exact revision/version | Content digest | Upstream checksum evidence | Signature result |
| --- | --- | --- | --- | --- | --- |
| [INPUT_INCLUDING_SUBMODULE_OR_MODEL] | [URL] | [IDENTITY] | [ALGORITHM_AND_DIGEST] | [EVIDENCE_OR_NOT_PROVIDED] | [RESULT_OR_NOT_PROVIDED] |

## Native build and runtime

| Field | Value |
| --- | --- |
| Native OS/release and CPU/process architecture | [PLATFORM] |
| Compiler/toolchain and isolated runtime | [VERSIONS_AND_PATHS] |
| Final persistent prefix | [ABSOLUTE_PATH] |
| Normalized installation-identity fields and digest | [INPUTS_AND_DIGEST] |
| Build options | [EXACT_CHOICES] |
| Dependency receipts and ABI constraints | [EXACT_DEPENDENCIES_AND_CONSTRAINTS] |
| Coupled group and complete PDK layout | [GROUP_AND_RESOURCES_OR_NOT_APPLICABLE] |
| PDK source, builder, model and technology revisions | [EXACT_IDENTITIES_OR_NOT_APPLICABLE] |
| Required runtime source/resources/licenses | [PERSISTENT_PATHS] |
| Upstream patch inputs and provenance | [SOURCE_DIGEST_REASON_VERSION_BOUNDS_REMOVAL_CONDITION_OR_NONE] |

## Canonical build identity

Render this table using the normalization rules in the records contract. Add uniquely named rows for each exact input, sort the data rows by ASCII key, and hash only the completed table. Retain the exact hashed text. The fixed header and separator rows below are part of the digest.

| Field | Value |
| --- | --- |
| channel | [CHANNEL] |
| component | [CATALOG_ID] |
| host-architecture | [NORMALIZED_ARCHITECTURE] |
| host-os | [NORMALIZED_OS_AND_RELEASE] |
| provider | [PROVIDER] |
| source-identity | [EXACT_SOURCE_IDENTITY] |

Identity digest: [SHA256_DIGEST].

## Public entrypoints and library use

| Public name or library | Upstream persistent target | Interpreter/host tool | Required environment | Required working directory | Exported project name |
| --- | --- | --- | --- | --- | --- |
| [NAME_OR_LIBRARY] | [ABSOLUTE_PATH] | [INTERPRETER_OR_HOST_OR_NONE] | [SETTINGS_OR_NONE] | [CWD_RULE] | [NAME_OR_NO_CLI] |

## Outcome and evidence

| Field | Result and evidence |
| --- | --- |
| Lifecycle state | [STATE] |
| installed_latest | [YES_NO_UNKNOWN_AND_OBSERVATION_TIME] |
| component_usable | [YES_NO_UNKNOWN_AND_CHECKS] |
| workflow_ready | [PER_WORKFLOW_RESULT_OR_NOT_APPLICABLE] |
| Native process exit statuses | [REAL_RESULTS_AND_LOGS] |
| Component functional artifacts | [PATHS_AND_DIGESTS] |
| Integration validation | [RECORD_REFERENCES_AND_LIMITS] |
| Fresh-process/different-directory checks | [RESULTS_AND_LIMITS] |

## Ownership, host changes, and cleanup

- Owned installation root and creation evidence: [DETAILS].
- External files referenced but not owned: [PATHS_AND_PROVIDER_OR_NONE].
- System changes, previous/new versions, authorization reference: [DETAILS_OR_NONE].
- Host dependency rollback limits: [DETAILS].
- Temporary files and their owning operation: [INVENTORY_REFERENCE].
- Runtime dependencies on temporary paths: [NONE_AFTER_VERIFICATION_OR_BLOCKER].
- Cleanup policy and persistent files to retain: [ELIGIBILITY_RULES_AND_PROTECTED_CONTENT].
- Cleanup outcome record and retained diagnostics: [STATE_OR_LOG_REFERENCE].

A verified managed installation and its published identity are immutable. The outcome reference can point to an operation record whose cleanup result is still pending when this receipt is published. Record actual cleanup results and later inspection evidence separately; changed sources, dependencies, options, or patches require a new installation key.
