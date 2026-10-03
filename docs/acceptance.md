# Acceptance criteria

SiliconBoot has two distinct acceptance activities: reviewing this documentation repository and executing its instructions on a native host. A completed documentation review cannot substitute for installation evidence.

## Documentation review

- [ ] The README starts with the project name, taglines, a usable setup prompt, and the native-installation risk notice.
- [ ] Setup asks for only the absolute installation root. The agent discovers the clone, initializes its existing `workspace/` project, and reuses the recorded root for maintenance. A fresh clone contains the empty tracked `.gitkeep`; all other workspace contents and `workspace2/` are ignored.
- [ ] Root and project AGENTS guides direct a new agent to real files and explicit operations.
- [ ] Every file added to the repository is documentation, license metadata, Git ignore rules, or the empty `workspace/.gitkeep`. There is no executable helper, script, code example, generated design source, or activation program.
- [ ] All prose and commit messages are English. Sources come from component maintainers and their documented providers.
- [ ] Every named catalog component has a unique ID, explicit identity or unresolved status, source policy, recipe route, and functional acceptance requirement.
- [ ] Catalog inheritance is explicit. Platforms, providers, dependencies, coupling, entrypoints, runtime layout, license/status evidence, allowed download sources and cleanup rules can be resolved without inventing facts.
- [ ] Profiles have deterministic membership, include dependency closure, and list planned/unresolved items instead of hiding them.
- [ ] Local links resolve. Recipe paths and component names agree with the catalog and templates.
- [ ] Latest stable, source snapshots, prereleases, forks and published PDK snapshots are distinguished. Network failure cannot become a latest-version claim.
- [ ] Lifecycle docs cover native inspection, permissions, fixed resolution, dependency order, isolation, resume, locking, activation, portable restore, rollback, cleanup and explicit garbage collection.
- [ ] uv is the default Python environment manager in prompts, profiles, recipes and project templates. Missing uv is installed first during setup; planning and ordinary runs do not install it implicitly. Interpreter locations, exact dependency records and upstream runtime exceptions are explicit.
- [ ] Records distinguish component state, latest discovery, engineering check outcomes, and overall completeness. Unknown, failed and skipped results cannot be mistaken for success.
- [ ] Templates contain all mandatory record fields and explain placeholders. Local absolute paths and portable reproduction inputs have distinct homes.
- [ ] AppImage guidance places temporary mountpoints in a private project run directory, verifies the canonical path against host policy, records TMPDIR, and checks for remaining mounts before cleanup.
- [ ] No support claim exceeds actual evidence. Published platform status states what has and has not been run.

## Native execution scenarios

These are prose acceptance cases for an agent on an authorized test host. Create fixtures in a disposable clone's local `workspace/` and keep them out of SiliconBoot commits. Record inputs, steps, actual results and evidence using the [templates](../templates/README.md).

| Scenario | Exercise | Required outcome |
| --- | --- | --- |
| Single-path setup | Supply only an absolute installation root while the clone is open | Discover the clone, initialize or preserve its existing `workspace/`, and place managed tools, SRAM compilers, and PDKs under the supplied root |
| Fresh clone and Git exclusions | Check a fresh clone, then add representative visible, hidden and nested workspace files plus a workspace2 file | The empty `workspace/.gitkeep` exists and is the only tracked workspace path; every generated file and workspace2 file is ignored and absent from the staged set |
| Release selection | Official stable release beside draft/prerelease and non-release tags | Select the upstream-defined stable release; record why other entries were excluded |
| Source snapshot | Upstream recommends a branch other than the repository default | Use the documented branch and full immutable revision |
| Discovery failure | Network unavailable or official API rate-limited | Report `latest_unknown`; preserve working installs and avoid claiming freshness |
| Canonical source change | Official project redirects to a new location | Preserve identity evidence, original URL and canonical source; reject an unrelated namesake |
| Existing project | Existing README, AGENTS, config and user-owned files | Create only missing structure and bounded managed sections; preserve other content and report conflicts |
| Unusual paths | Spaces and non-ASCII characters in project/store paths | Correct literal path handling; no argument splitting, injection or escaped-name mismatch |
| Bad links | Dangling/cyclic links and links to unexpected third-party roots | Reject activation or the affected entrypoint; retain existing files and evidence |
| Name collision | Two providers export the same public name | Record a chosen default and distinct namespaced entries; never silently overwrite |
| Native identity | Wrong-architecture asset or translated execution | Reject it as native support for the selected host; report actual context |
| Missing uv | Authorized setup with no uv on the host | Install and verify the official native uv distribution under the chosen root before Python environments or packages; record sources and version |
| Existing uv | A uv executable is present before setup | Inspect identity, version, provider and native architecture; reuse only when lifecycle requirements match, preserving existing files |
| Python bootstrap failure | uv unavailable for the native host or acquisition fails | Block affected Python setup with evidence; continue independent components without silently changing managers |
| Isolation | Two Python components require conflicting dependencies | Separate uv-managed environments and fixed interpreter paths; system runtime and the other component still work |
| Python compatibility | Host Python conflicts with an EDA extension's ABI | Select and record a compatible native interpreter under the root, or report the unsatisfied requirement |
| Upstream Python runtime | A host tool embeds Python or requires a managed dependency closure | Preserve the supported runtime and record an evidence-based exception to uv management |
| Fixed Python run | Ordinary invocation in a verified generation | Use its exact environment without uv synchronization, dependency resolution, lock changes or downloads |
| Clean session | New shell, different working directory, no build-session variables | Tools start and complete the relevant example using documented settings |
| AppImage mountpoint policy | On a host that restricts FUSE mountpoints, inspect a denied store-path launch and retry the same AppImage with a permitted `workspace/runs/<run-id>/tmp` | Record the canonical TMPDIR and actual policy evidence; verify startup and an affected function without changing installed bytes or weakening policy; if the project path is also denied, report that blocker |
| Interrupted build | Operation ends after download or during build | Record unfinished state; no broken successful entrypoints; resume rechecks inputs and ownership |
| Concurrent work | Two agents attempt the same installation or activation | Native locking serializes mutation; neither sees an incomplete installation as reusable |
| Candidate versus collection | Garbage collection overlaps a build or candidate validation | An operation lease protects new installations, reused inputs and dependencies until durable generation references replace it |
| Host change versus run admission | A run tries to start while a system package operation checks leases and mutates dependencies | The host-change gate serializes admission with that check and mutation; incompatible changes wait for existing runs |
| Activation interruption | Interruption before and after the atomic pointer change | Current resolves to one complete generation; recovery reconciles companion records from that generation |
| Latest incompatibility | New plugin or tool breaks a previously working flow | Keep prior generation active and record `blocked_latest_incompatible` |
| First partial bootstrap | Independent component passes while another fails | Activate only the verified subset if appropriate; show `partial` and every omitted item |
| Long-running job | Upgrade or rollback while a run is active | Job retains its original absolute paths and lease; future jobs use the newly selected generation |
| Shared installations | Two projects reference one install; one upgrades | Both projects retain valid versions and links; no referenced install is removed |
| Temporary cleanup | A runtime source tree is adjacent to build residue and a user symlink | Delete only owned temporary data, preserve runtime and third-party targets, recheck startup |
| Mounted temporary directory | Cleanup encounters an active or unresolved AppImage mount beneath a run's tmp directory | Preserve the directory until all owning processes and mounts finish; retain reports and artifacts after exact owned cleanup |
| Python retention | Several environments reference one uv-managed interpreter | Preserve the interpreter and all live environment references during cleanup and collection; handle shared caches separately |
| Garbage collection | Unregistered/unknown projects, retained generations, dependencies or uncertain leases | Retain anything whose lack of references cannot be established; honor dry-run vs explicit removal scope |
| Exact restore | Lock references an unavailable source, dependency or patch | Block exact restore with precise missing inputs; no silent latest substitution |
| Rollback | Retained generation with changed system dependency | Validate before selection; report system rollback limitations and keep working state if invalid |
| PDK layout | IHP siblings, shared files, relative links and generated native models | Preserve the complete supported upstream layout and resolve every selected model dependency |
| Memory combination | Supported compiler/port plus unsupported PDK combination | Run the supported case; label unsupported combinations and missing views/checks accurately |
| Engineering failure | Process exits successfully but timing, DRC, LVS or assertions fail | Preserve the real exit status and report the engineering failure separately |
| New agent handoff | Fresh session with only project instructions and recorded references | Locate exact tools, inspect capabilities, run a check and find maintenance procedures |

## Promotion to verified

A maintainer may promote only the exact OS/architecture/component or workflow combination supported by evidence. Record date, source and recipe revisions, native context, build inputs, environment integrity, real function checks and report locations. Redact secrets and private paths before publishing evidence. Update [platforms](platforms.md), the catalog entry and affected profile together.

Full-profile verification requires accounting for every selected component and dependency, with no hidden planned entries. An unsupported item may be honestly reported, but it does not become a passing capability. Do not promise installation time, disk usage or resource requirements without measurements and conditions.
