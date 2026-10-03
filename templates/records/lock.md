# Portable environment lock

Record version: 1\
Record type: Lock\
Resolution identity: [PORTABLE_RESOLUTION_ID]\
Created at: [UTC_TIME]\
Requested profile and complete scope: [SCOPE]\
Target OS/architecture and ABI constraints: [CONSTRAINTS]\
Guidance/catalog/recipe identity: [REVISION_AND_CONTENT_DIGEST]\
Generation policy: [LATEST_OFFICIAL_EXACT_RESTORE_OR_NAMED_COMPATIBLE_POLICY]

This record contains portable exact input identities. Host paths, local usernames, machine-specific interpreter locations, process owners, and credentials belong elsewhere.

## Locked components and sources

| Catalog ID/kind | Provider/channel | Official source URL | Release/tag and maintained branch | Full commit | Asset or source digest | Latest observation and status |
| --- | --- | --- | --- | --- | --- | --- |
| [ID_AND_KIND] | [PROVIDER_CHANNEL] | [URL] | [LABELS_OR_NOT_APPLICABLE] | [COMMIT_OR_NOT_APPLICABLE] | [ALGORITHM_AND_DIGEST] | [UTC_TIME_RESULT_AND_EVIDENCE] |

## Locked dependencies and build choices

| Component/input | Exact dependency identities and edge types | Compiler/runtime requirements | Build options | ABI constraints | Coupled group | Patch source, digest and modification status |
| --- | --- | --- | --- | --- | --- | --- |
| [ID] | [TRANSITIVE_IDENTITIES] | [EXACT_REQUIREMENTS] | [CHOICES] | [CONSTRAINTS] | [GROUP_OR_NONE] | [IDENTITY_OR_NONE] |

## PDK and memory inputs

| PDK/compiler | Data source revisions and submodules | Builder/model revisions | Technology port | Selected variants/libraries/corners | Model ABI inputs |
| --- | --- | --- | --- | --- | --- |
| [ID_OR_NOT_APPLICABLE] | [IDENTITIES] | [IDENTITIES] | [EXACT_PORT_OR_NOT_APPLICABLE] | [SELECTIONS] | [INPUTS] |

## Python environment inputs

| Component or coupled group | Manager version and source identity | Interpreter implementation/version/build/provider and asset digest | Dependency lock or resolved requirements identity | Extras, indexes and build dependencies | Upstream runtime exception |
| --- | --- | --- | --- | --- | --- |
| [ID_OR_NOT_APPLICABLE] | [UV_IDENTITY_OR_RECORDED_MANAGER] | [EXACT_INPUTS] | [RETRIEVABLE_SOURCE_OR_PORTABLE_ASSET_REFERENCE_AND_DIGEST] | [EXACT_CHOICES] | [REASON_AND_OFFICIAL_EVIDENCE_OR_NONE] |

Preserve the dependency resolution asset needed to recreate each environment. Keep local interpreter paths in the manifest and receipts. Restore these inputs exactly; an older lock using a different manager requires a separate maintenance change to adopt uv.

## Entrypoint and workflow policy

| Public command | Selected component/provider | Namespaced alternative |
| --- | --- | --- |
| [COMMAND] | [PROVIDER] | [ALTERNATIVE_OR_NOT_APPLICABLE] |

| Required workflow | Exact component/PDK/technology combination | Project-relative input or official fixture identity | Acceptance criterion |
| --- | --- | --- | --- |
| [WORKFLOW_ID] | [COMBINATION] | [INPUT_IDENTITY] | [CRITERION] |

## Integrity and restoration limits

- Official checksum/signature evidence: [PUBLIC_REFERENCES_AND_RESULTS_OR_NOT_PROVIDED].
- Known unresolved or unpinned transitive inputs: [DETAILS_OR_NONE].
- External system package requirements and reproducibility limits: [DETAILS].
- Modified sources and exact upstream patch inputs, including retrievable URL or preserved portable asset reference and digest: [DETAILS_OR_NONE].
- Excluded, unsupported, failed, or unverified selected entries: [IDS_AND_REASONS_OR_NONE].
- Verified restoration scope, if a restore was performed: [EXACT_INPUTS_WORKFLOW_EQUIVALENCE_OR_HASH_MATCH_WITH_EVIDENCE_OR_NOT_PERFORMED].

Restore these exact inputs without latest discovery. An unavailable locked input is a blocker; a substituted version requires a separate lock. Matching sources alone do not establish bit-for-bit build reproducibility.
