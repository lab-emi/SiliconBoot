# Generation-pinned run

Record version: 1\
Record type: Run\
Run ID: [RUN_ID]\
Project ID: [PROJECT_ID]\
Purpose: [DESIGN_OR_VERIFICATION_TASK]\
Started at: [UTC_TIME]\
Finished at: [UTC_TIME_OR_RUNNING]\
Status: [RUNNING_SUCCEEDED_FAILED_INTERRUPTED_OR_BLOCKED]

## Fixed environment and lease

| Field | Value |
| --- | --- |
| Concrete generation ID and absolute path | [ID_AND_PATH_WITHOUT_CURRENT] |
| Manifest and lock digests | [DIGESTS] |
| Native host and process architecture | [PLATFORM] |
| Lease identity and registry reference | [LEASE_ID_AND_REFERENCE] |
| Owner host/process/start identity | [OWNER] |
| Generation and transitive installation references protected | [IDENTITIES] |
| Host-change, project, and registry lock evidence when registering lease | [EVIDENCE] |
| Owned temporary directory and effective TMPDIR, if required | [CANONICAL_PATH_OWNERSHIP_AND_SETTING_OR_NOT_APPLICABLE] |
| FUSE mountpoint policy and native check, if required | [EVIDENCE_OR_NOT_APPLICABLE] |
| Complete process tree finished | [EVIDENCE_OR_NOT_YET] |
| Temporary mounts released and owned cleanup outcome | [EVIDENCE_OR_PENDING_OR_NOT_APPLICABLE] |
| Lease release status and time | [STATUS_AND_TIME_OR_STILL_PROTECTED] |

## Inputs and execution conditions

| Step | Component and receipt | Upstream entrypoint/interpreter | Task arguments described in prose | Exact working directory | Environment settings | Input identities |
| --- | --- | --- | --- | --- | --- | --- |
| [STEP_ID] | [IDENTITIES] | [PERSISTENT_TARGET] | [TASK_INPUTS_AND_OPTIONS] | [ABSOLUTE_CWD] | [EXACT_NONSECRET_VALUES] | [PATHS_COMMITS_AND_DIGESTS] |

Use concrete generation and installation paths for all child processes and later stages. Record the design-source revision and uncommitted-input digests, PDK variant, library, model, corner, memory technology, and relevant seeds where applicable.

## Results and evidence

| Step/check | Expected result | Real process exit status | Actual parsed result | Artifact/report/log location | Content digest |
| --- | --- | --- | --- | --- | --- |
| [STEP_OR_CHECK] | [CRITERION] | [STATUS] | [RESULT] | [PROJECT_RELATIVE_PATH] | [ALGORITHM_AND_DIGEST] |

- Memory request and required output views, if applicable: [DETAILS_OR_NOT_APPLICABLE].
- Missing outputs, checks, or corners: [DETAILS_OR_NONE].
- Timing/DRC/LVS/PEX or numeric interpretation: [RESULTS_AND_LIMITATIONS].
- Upstream limitations affecting this run: [DETAILS_OR_NONE].
- User or design-process acceptance reference for promoted artifacts: [REFERENCE_OR_NOT_ACCEPTED].
- Follow-up or resume action: [ACTION_OR_NONE].

Run artifacts remain in this run's project directory. Promoting a memory macro to `ip/memory/manifests` requires its acceptance and provenance record; merely producing files does not establish acceptance.
