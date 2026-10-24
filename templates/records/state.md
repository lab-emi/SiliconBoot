# Operation and recovery state

Record version: 1\
Record type: State\
Operation ID: [OPERATION_ID]\
Project ID: [PROJECT_ID]\
Updated at: [UTC_TIME]\
Record revision: [REVISION]\
Previous record digest: [DIGEST_OR_INITIAL]\
Frozen resolution: [ABSOLUTE_PATH_AND_DIGEST]\
Operation kind: [BOOTSTRAP_UPGRADE_RESTORE_ROLLBACK_CLEANUP_OR_GC]

## Progress

| Component | Lifecycle state | Last completed step | Current input identity | Error and real exit status | Evidence | Next safe step |
| --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [STATE] | [STEP] | [IDENTITY] | [ERROR_OR_NONE] | [LOG_AND_REPORT_PATHS] | [RESUME_STEP] |

## Locks and leases

| Scope | Native mechanism | Owner host/process/start identity | Acquired at | Protected paths and references | Live/inactive evidence | Release status |
| --- | --- | --- | --- | --- | --- | --- |
| [SCOPE] | [MECHANISM] | [OWNER] | [UTC_TIME] | [PATHS_AND_IDENTITIES] | [EVIDENCE] | [STATUS] |

These rows describe native locks; they do not create locks. Uncertain owners and leases remain protected.

## Owned paths

| Canonical path | Expected type | Owning operation | Purpose | Persistent or temporary | Runtime references | Deletion eligibility |
| --- | --- | --- | --- | --- | --- | --- |
| [ABSOLUTE_PATH] | [TYPE] | [OPERATION_ID] | [PURPOSE] | [CLASSIFICATION] | [REFERENCES_OR_NONE] | [REASON_OR_NOT_ELIGIBLE] |

## Activation transaction

| Field | Value |
| --- | --- |
| Previous active generation | [ID_AND_ABSOLUTE_PATH_OR_NONE] |
| Candidate generation | [ID_AND_ABSOLUTE_PATH_OR_NONE] |
| Candidate records and link checks | [EVIDENCE_OR_PENDING] |
| Candidate operation lease and protected transitive inputs/documentation | [LEASE_ID_AND_REFERENCES] |
| Required workflow result | [EVIDENCE_OR_PENDING] |
| Registry protection established | [REVISION_AND_EVIDENCE_OR_PENDING] |
| Operation-lease protection transfer | [DURABLE_CANDIDATE_REFERENCE_EVIDENCE_OR_STILL_PROTECTED] |
| Host-change, project and registry lock evidence | [REFERENCE] |
| Atomic replacement mechanism | [MECHANISM_OR_BLOCKER] |
| Replacement attempted at | [UTC_TIME_OR_NOT_ATTEMPTED] |
| Observed current target after operation | [ABSOLUTE_PATH_AND_OBSERVATION_TIME] |
| Home binary-link publication and obsolete owned-link reconciliation | [RESULT_AND_EXACT_LINK_TARGETS_OR_PENDING] |
| Default-shell PATH setup and verification | [CONFIGURATION_BACKUP_CHECKS_OR_BLOCKER] |
| Portable lock export status | [MATCHING_DIGEST_OR_PENDING] |
| Guidance reconciliation status | [RESULT_OR_PENDING] |
| Previous generation retention | [PROTECTED_REFERENCE] |
| Recovery decision and evidence | [DECISION_OR_NOT_REQUIRED] |

## Preservation and cleanup results

- Existing project-file comparison and merge record: [EVIDENCE].
- Recoverable previous records or rendered sections: [LOCATIONS].
- Retained failure diagnostics and measured size: [DETAILS_OR_NONE].
- Deleted owned temporary paths: [PATHS_AND_RESULTS_OR_NONE].
- Unknown or unsafe paths preserved: [PATHS_AND_REASONS_OR_NONE].
- Outstanding blockers and next steps: [DETAILS_OR_NONE].
