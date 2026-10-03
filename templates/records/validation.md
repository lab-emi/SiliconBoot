# Generation validation

Record version: 1\
Record type: Validation\
Project ID: [PROJECT_ID]\
Generation ID: [GENERATION_ID]\
Validated at: [UTC_TIME]\
Native host: [HOST_RECORD_AND_PLATFORM]\
Resolution identity: [RESOLUTION_ID_AND_DIGEST]\
Requested scope: [COMPONENTS_AND_WORKFLOWS]\
Overall status: [READY_PARTIAL_OR_BLOCKED]

## Structural and runtime checks

| Check | Expected criterion | Actual outcome | Real exit status where applicable | Evidence/artifact location and digest | Limits |
| --- | --- | --- | --- | --- | --- |
| [LINK_PERMISSION_COLLISION_RESOURCE_ENVIRONMENT_OR_ISOLATION_CHECK] | [CRITERION] | [PASS_FAIL_NOT_RUN_OR_BLOCKED] | [STATUS_OR_NOT_APPLICABLE] | [EVIDENCE] | [LIMITS_OR_NONE] |

## Component functional checks

| Component and exact identity | Check and input fixture identity | Expected criterion | Actual result | Native process exit status | Reports/artifacts and digests | Scope limitations |
| --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_IDENTITY] | [CHECK_AND_INPUT] | [CRITERION] | [RESULT] | [EXIT_STATUS] | [EVIDENCE] | [LIMITS] |

## Workflow checks

| Workflow | Exact tools/PDK/technology/corner | Input provenance | Expected artifacts and report criteria | Actual report result | Native exit statuses | Artifact/report identities | Missing views or checks |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [WORKFLOW_ID] | [COMBINATION] | [INPUTS] | [CRITERIA] | [RESULT] | [STATUSES] | [PATHS_AND_DIGESTS] | [LIMITATIONS_OR_NONE] |

## Capability statement

| Component or named workflow | installed_latest and observation time | component_usable | workflow_ready | Evidence and reason |
| --- | --- | --- | --- | --- |
| [ID] | [YES_NO_UNKNOWN_AND_TIME] | [YES_NO_UNKNOWN] | [YES_NO_UNKNOWN_OR_NOT_APPLICABLE] | [EVIDENCE] |

- Selected entries without complete evidence: [IDS_AND_REASONS_OR_NONE].
- Latest incompatibilities: [DETAILS_OR_NONE].
- Fresh-process and different-working-directory results: [EVIDENCE].
- GUI checks: [EVIDENCE_OR_NOT_RUN_WITH_REASON].
- Numeric/timing/DRC/LVS/PEX/memory interpretation: [ACTUAL_PARSED_RESULTS_AND_LIMITS].
- Upstream restrictions and untested configurations: [DETAILS].
- Activation recommendation for the recorded scope: [RECOMMENDATION_AND_REASON].

An exit status of zero is not itself proof of correct design behavior, clean rule checks, timing closure, or fabrication readiness. Record these claims only when the actual reports and stated acceptance criteria support them.
