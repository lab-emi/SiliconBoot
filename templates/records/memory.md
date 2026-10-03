# Memory macro record: [MACRO_ID]

Record version: 1\
Record type: Memory\
Project ID: [PROJECT_ID]\
Macro ID and revision: [IDENTITY]\
Created at: [UTC_TIME]\
Run ID and record: [RUN_ID_AND_REFERENCE]\
Record status: [CANDIDATE_ACCEPTED_REJECTED_OR_SUPERSEDED]\
Memory type: [SRAM_COMPILER_STANDARD_CELL_MEMORY_OR_PREBUILT_MACRO]\
Function: [RAM_ROM_OR_OTHER_SUPPORTED_FUNCTION]

## Request and supported combination

| Field | Value |
| --- | --- |
| Request source and digest | [PROJECT_RELATIVE_REQUEST_OR_IMMUTABLE_UPSTREAM_EXAMPLE_AND_DIGEST] |
| Official configuration/port support evidence | [UPSTREAM_URL_REVISION_AND_SCOPE] |
| Compiler or prebuilt macro provider | [COMPONENT_PROVIDER_CHANNEL_VERSION_AND_FULL_COMMIT] |
| Compiler installation receipt | [RECEIPT_AND_DIGEST_OR_NOT_APPLICABLE] |
| Technology port or building-block package | [SOURCE_REVISION_AND_DIGEST_OR_NOT_APPLICABLE] |
| PDK family and variant | [EXACT_IDENTITY] |
| PDK source, builder, and native model inputs | [REVISIONS_AND_DIGESTS] |
| Bitcell or standard-cell libraries | [EXACT_IDENTITIES_AND_REQUIRED_VIEWS] |
| Participating tools and runtime dependencies | [EXACT_VERSIONS_INSTALL_KEYS_AND_RECEIPTS] |
| Generation and portable lock identity | [GENERATION_ID_AND_LOCK_DIGEST] |
| Native host and architecture | [HOST_RECORD_REFERENCE] |
| Required runtime settings and paths | [RUN_RECORD_REFERENCE] |

## Dimensions and operating conditions

| Field | Requested and actually generated value |
| --- | --- |
| Words and word width | [COUNTS] |
| Banks and organization | [DETAILS] |
| Read-only, write-only, and read/write ports | [COUNTS_AND_NAMES] |
| Write-mask granularity and polarity | [DETAILS_OR_NOT_APPLICABLE] |
| Clocks, control polarity, and interface timing | [DETAILS] |
| Power and ground ports | [NAMES_AND_CONNECTION_REQUIREMENTS] |
| Process corners | [CORNERS] |
| Voltages and temperatures | [VALUES_AND_UNITS] |
| Characterization mode | [SIMULATION_ANALYTICAL_GENERATION_ONLY_OR_OTHER_MODE] |
| Requested views | [VIEW_NAMES] |
| Required functional, physical, and timing checks | [CHECKS_AND_ACCEPTANCE_CRITERIA] |

## Output views and interface consistency

| View | Required by selected mode | Actual artifact location | Content digest | Macro/ports/bus widths/power consistency | Corner and limits |
| --- | --- | --- | --- | --- | --- |
| HDL | [YES_NO_AND_REASON] | [PATH_OR_MISSING] | [ALGORITHM_AND_DIGEST_OR_NOT_APPLICABLE] | [RESULT_AND_EVIDENCE] | [DETAILS] |
| SPICE/CDL | [YES_NO_AND_REASON] | [PATH_OR_MISSING] | [ALGORITHM_AND_DIGEST_OR_NOT_APPLICABLE] | [RESULT_AND_EVIDENCE] | [DETAILS] |
| LEF | [YES_NO_AND_REASON] | [PATH_OR_MISSING] | [ALGORITHM_AND_DIGEST_OR_NOT_APPLICABLE] | [RESULT_AND_EVIDENCE] | [DETAILS] |
| GDS | [YES_NO_AND_REASON] | [PATH_OR_MISSING] | [ALGORITHM_AND_DIGEST_OR_NOT_APPLICABLE] | [RESULT_AND_EVIDENCE] | [DETAILS] |
| Liberty | [YES_NO_AND_REASON] | [PATH_OR_MISSING] | [ALGORITHM_AND_DIGEST_OR_NOT_APPLICABLE] | [RESULT_AND_EVIDENCE] | [DETAILS] |

Repeat rows for every delivered corner or view variant. Record additional promised outputs. Missing expected views remain explicit failures or blockers; a view outside the selected mode is `not applicable` with its upstream basis.

## Independent checks

Use `pass`, `fail`, `blocked`, or `not_run` for each check. Record engineering outcomes independently of native process exit statuses.

| Check | Criterion and exact tools/decks/inputs | Outcome | Real exit status | Actual metrics or report result | Evidence location and digest | Limits |
| --- | --- | --- | --- | --- | --- | --- |
| Generation | [CRITERION] | [OUTCOME] | [STATUS] | [RESULT] | [EVIDENCE] | [LIMITS] |
| View consistency | [CRITERION] | [OUTCOME] | [STATUS_OR_NOT_APPLICABLE] | [RESULT] | [EVIDENCE] | [LIMITS] |
| Functional read/write/masking | [COVERAGE_AND_CRITERION] | [OUTCOME] | [STATUS] | [RESULT] | [EVIDENCE] | [LIMITS] |
| DRC | [DECK_REVISION_AND_CRITERION] | [OUTCOME] | [STATUS] | [VIOLATION_COUNTS_AND_SCOPE] | [EVIDENCE] | [LIMITS] |
| LVS | [REFERENCE_EXTRACTION_AND_CRITERION] | [OUTCOME] | [STATUS] | [COMPARISON_RESULT] | [EVIDENCE] | [LIMITS] |
| PEX | [DECK_AND_REQUIRED_PARASITIC_SCOPE] | [OUTCOME] | [STATUS] | [RESULT] | [EVIDENCE] | [LIMITS] |
| Timing/characterization | [MODE_CORNERS_CLOCKS_AND_PATH_COVERAGE] | [OUTCOME] | [STATUS] | [SETUP_HOLD_AND_OTHER_REQUIRED_METRICS] | [EVIDENCE] | [LIMITS] |

## Acceptance and retention

- Requested acceptance gates: [GATES_AND_REQUIREMENTS_SOURCE].
- Actual acceptance decision and date: [DECISION_AND_UTC_TIME_OR_PENDING].
- User or design-process decision reference: [REFERENCE_OR_NOT_ACCEPTED].
- Explicitly accepted limitations: [LIMITATIONS_AND_ACCEPTANCE_REFERENCE_OR_NONE].
- Unresolved warnings, upstream restrictions, absent corners, and skipped checks: [DETAILS_OR_NONE].
- Accepted artifact locations and retained hashes: [PROJECT_RELATIVE_PATHS_AND_DIGESTS_OR_NOT_ACCEPTED].
- Accepted manifest destination: [IP_MEMORY_MANIFEST_PATH_OR_NOT_PROMOTED].
- Prior/superseding macro record: [REFERENCE_AND_REASON_OR_NONE].
- Retention requirements and consuming designs: [REFERENCES].

Keep candidate outputs in the run directory. Promote a record under `ip/memory/manifests` only when the requested gates pass or a documented design-process decision accepts a stated limitation. An accepted macro remains tied to these exact inputs and artifacts; a compiler upgrade creates a new candidate rather than overwriting this record. A smoke compile is not fabrication signoff.
