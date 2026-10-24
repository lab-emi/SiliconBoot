# Persistent store registry

Record version: 1\
Record type: Registry\
Store canonical absolute path: [TOOLS_CANONICAL_PATH]\
PDK canonical absolute path: [PDKS_CANONICAL_PATH]\
Shared bookkeeping directory: [STORE_METADATA_ABSOLUTE_PATH]\
Updated at: [UTC_TIME]\
Record revision: [REVISION]\
Previous revision digest: [DIGEST_OR_INITIAL]\
Native registry lock evidence for this update: [EVIDENCE]

## Registered projects

| Stable project ID | Canonical project path | Last verified accessible | Current generation | Previous valid generation | User-retained generations | Registration/migration/retirement state |
| --- | --- | --- | --- | --- | --- | --- |
| [PROJECT_ID] | [ABSOLUTE_PATH] | [TIME_AND_RESULT] | [GENERATION_ID] | [GENERATION_ID_OR_NONE] | [IDS_OR_NONE] | [STATE_AND_EVIDENCE] |

## Protected generation references

| Project/generation | Reason retained | Manifest and lock identity | Direct and transitive installation identities | Documentation snapshot | Reference checked at |
| --- | --- | --- | --- | --- | --- |
| [PROJECT_AND_GENERATION] | [CURRENT_PREVIOUS_USER_LEASE_OR_RECOVERY] | [PATHS_AND_DIGESTS] | [IDENTITIES] | [GUIDE_IDENTITY] | [UTC_TIME] |

## Installations and ownership

| Component/installation key | Managed or external | Canonical root and receipt | Owning creation operation | Referring projects/generations and dependencies | State | Deletion protection |
| --- | --- | --- | --- | --- | --- | --- |
| [IDENTITY] | [OWNERSHIP] | [PATHS_AND_DIGEST] | [OPERATION_ID_OR_EXTERNAL] | [REFERENCES] | [STATE] | [REASON_OR_CANDIDATE_PENDING_RECHECK] |

## Home binary-link ownership

| Public symlink path | Owning project | Recorded link text through current/bin | Selected upstream provider | Last observed target and status |
| --- | --- | --- | --- | --- |
| [BIN_ABSOLUTE_PATH_AND_NAME] | [PROJECT_ID] | [LINK_TEXT] | [COMPONENT_AND_RECEIPT] | [OBSERVATION_AND_EVIDENCE] |

Existing files, unrelated symlinks and names owned by other projects remain preserved until a provider conflict is explicitly resolved. Published links protect their referenced installations and generations during collection.

## Run and operation leases

| Lease ID | Project/operation/run | Host/process/start identity | Protected generation/installations | Acquired at | Liveness evidence | Release or unresolved status |
| --- | --- | --- | --- | --- | --- | --- |
| [LEASE_ID] | [IDENTITY] | [OWNER] | [REFERENCES] | [UTC_TIME] | [OBSERVED_EVIDENCE] | [STATUS] |

## Reconciliation and garbage collection

- Inaccessible projects or uncertain references: [DETAILS_OR_NONE].
- Conflicting or unregistered paths preserved: [DETAILS_OR_NONE].
- Latest comparison with accessible generation manifests: [TIME_AND_EVIDENCE].
- Explicit retirement or migration requests: [REQUEST_REFERENCES_OR_NONE].
- Garbage-collection candidate report and user-authorized scope: [REFERENCE_OR_NONE].
- Rechecks under component/project/registry locks: [EVIDENCE_OR_NOT_PERFORMED].
- Deleted installation identities and retained deletion evidence: [DETAILS_OR_NONE].

Do not infer deletion eligibility from a missing reference, expired timestamp, inaccessible project, or absent process ID alone. Keep every uncertain installation protected until ownership, liveness, and references have been resolved.
