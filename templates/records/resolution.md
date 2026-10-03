# Frozen resolution plan

Record version: 1\
Record type: Resolution\
Operation ID: [OPERATION_ID]\
Frozen at: [UTC_TIME]\
Plan revision and content digest: [IDENTITY]\
Project ID: [PROJECT_ID]\
Requested profile and scope: [SCOPE]\
Target native platform: [OS_ARCHITECTURE]\
Guidance and catalog revision: [REVISION_AND_DIGEST]

## Scope disposition

| Catalog ID | Selected or excluded | Recipe/support status | Planned action or blocker | Required workflow impact |
| --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [DISPOSITION] | [STATUS] | [ACTION_OR_BLOCKER] | [WORKFLOWS] |

## Official discovery evidence

| Component | Provider/channel | Checked at | Official evidence URL | Release/tag or maintained branch | Full commit | Selected version | Latest status and reason |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [PROVIDER_AND_CHANNEL] | [UTC_TIME] | [URL] | [UPSTREAM_LABEL] | [FULL_COMMIT_OR_NOT_APPLICABLE] | [VERSION] | [STATUS] |

## Source and asset identities

| Component/input | Official repository or asset URL | Canonical redirect/final download URL | OS/architecture | Digest and origin | Signature result | Allowed host evidence |
| --- | --- | --- | --- | --- | --- | --- |
| [INPUT_ID] | [URL] | [URL_OR_NONE] | [TARGET_OR_SOURCE] | [ALGORITHM_DIGEST_AND_UPSTREAM_OR_LOCAL] | [RESULT_OR_NOT_PROVIDED] | [UPSTREAM_EVIDENCE] |

## Dependency and build plan

| Component | Exact dependencies and edge types | ABI constraints | Coupled group | Compiler/runtime/build options | Planned install identity | Install order |
| --- | --- | --- | --- | --- | --- | --- |
| [COMPONENT_ID] | [DEPENDENCY_IDS_AND_TYPES] | [CONSTRAINTS_OR_NONE] | [GROUP_OR_NONE] | [BUILD_INPUTS] | [NORMALIZED_IDENTITY_AND_DIGEST] | [ORDER_OR_BLOCKER] |

Record transitive sources and submodules, PDK source data separately from builder and model revisions, memory technology ports, and upstream-provided patch inputs. Explain any cycle and its documented staged resolution. Document provider or channel exceptions, unpinned dependencies, planned system changes, resource limits, and their authorization references.

## Acceptance and resumption

- Required component checks: [CHECKS_AND_RECIPE_REFERENCES].
- Required affected workflows: [WORKFLOW_IDS_AND_CRITERIA].
- Existing capabilities to preserve: [CAPABILITIES].
- Latest incompatibilities or unknowns: [ISSUES_OR_NONE].
- Resume using this frozen plan: [RESUME_RULE_AND_CURRENT_STATE_LINK].
- Superseded plan, if any: [IDENTITY_AND_REASON_OR_NONE].

Discovery is frozen at the time above. A changed source, dependency, provider, or build choice requires a new plan revision and an explicit downstream rebuild assessment.
