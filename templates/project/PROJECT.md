# Project choices

Record version: 1\
Record type: Project

| Field | Value |
| --- | --- |
| Project name | [PROJECT_NAME] |
| Stable project identifier | [PROJECT_ID] |
| Purpose | [PURPOSE] |
| Requested profile | [PROFILE] |
| Explicit component inclusions | [COMPONENT_IDS] |
| Explicit exclusions and reasons | [EXCLUSIONS_OR_NONE] |
| Native target OS and architecture | [TARGET_PLATFORM] |
| Default channel policy | [LATEST_OFFICIAL_OR_EXPLICIT_POLICY] |
| Provider exceptions accepted by user | [EXCEPTIONS_OR_NONE] |
| Selected PDK variants | [PDK_IDS] |
| Standard-cell and model libraries | [LIBRARIES_AND_CORNERS] |
| Memory compiler and technology port selections | [SELECTIONS_OR_NONE] |
| Installation root record | [HOST_RECORD_REFERENCE] |
| Persistent documentation identity | [GUIDE_REVISION_AND_DIGEST] |
| Resource/concurrency limits | [LIMITS_AND_MEASUREMENT_SOURCE] |
| Required retention | [ACTIVE_PREVIOUS_USER_RETAINED_AND_LEASED_GENERATIONS] |

The project directory is `workspace/` under the discovered SiliconBoot clone. Record the user's absolute installation root in the host record and reuse it for maintenance. This portable project record refers to that local record without embedding host-specific paths.

## Required workflows

| Workflow ID | Components, PDK, library or technology port | Required acceptance criterion | Scope exclusions |
| --- | --- | --- | --- |
| [WORKFLOW_ID] | [EXACT_COMBINATION_REQUIREMENTS] | [PASS_CRITERION] | [EXCLUSIONS_OR_NONE] |

## Public command provider choices

| Command name | Selected component/provider | Namespaced alternative | Reason |
| --- | --- | --- | --- |
| [COMMAND] | [COMPONENT_AND_PROVIDER] | [COMPONENT_COMMAND_NAME] | [SELECTION_REASON] |

## Project preservation and changes

- Existing authoritative instructions: [FILES_AND_CONSTRAINTS].
- User-owned directories and files: [OWNERSHIP_BOUNDARIES].
- Agreed generated-section boundaries: [LOCATIONS].
- Authorized host changes: [SCOPE_REFERENCE_OR_NONE].
- Version-control policy: [SOURCE_CONFIGURATION_PORTABLE_LOCK_AND_LOCAL_EXCLUSIONS].
- Open decisions or blockers: [ISSUES_OR_NONE].

## Change history

| Time | Changed choice | Reason and user-request reference |
| --- | --- | --- |
| [UTC_TIME] | [CHANGE] | [REQUEST_REFERENCE] |
