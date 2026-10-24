# Acceptance criteria

SiliconBoot has two distinct acceptance activities: reviewing this documentation repository and executing its instructions on a native host. A completed documentation review cannot substitute for installation evidence.

## Documentation review

- [ ] The README starts with the project name, taglines, a usable setup prompt, and the native-installation risk notice.
- [ ] Setup requires no path input: managed tools, SRAM compilers, uv and runtimes use `~/tools`, PDKs use `~/pdks` and public binary symlinks use `~/bin`, expanded against the invoking user's home. Matching macOS Homebrew tools use recorded external provider locations under the standing location exception. The existing project is derived from context, defaulting to the clone; setup creates no workspace or design scaffold. Metadata and runs remain ignored, and older recorded roots require an explicit migration.
- [ ] PATH setup detects the default login shell, selects only its bashrc, zshrc or fish configuration, honors custom configuration locations, preserves existing content and avoids duplicate entries. A fresh instance of that shell verifies command resolution.
- [ ] Setup uses no sudo or administrator-managed package changes. Scoped user-writable Homebrew changes are allowed on macOS; unwritable roots and privileged dependency requirements become explicit blockers while independent work continues.
- [ ] macOS prompts, catalog defaults, recipes and project templates require a current Homebrew check for every selected tool, including uv, against an independently resolved latest official version, native architecture and needed capabilities. Matching packages use Homebrew; fallback reasons and exact latest native inputs are recorded. Missing Homebrew, stale/unknown metadata, arbitrary taps and unsafe dependency replacement cannot silently change this policy.
- [ ] Homebrew records preserve package definitions, artifact/dependency identities, actual external locations, generation targets and retention limits. Changes respect leases and retained generations, suppress automatic cleanup and unrelated dependent upgrades, and keep exact restores on locked inputs.
- [ ] Root and project AGENTS guides direct a new agent to real files and explicit operations.
- [ ] Every file added to the repository is documentation, license metadata or Git ignore rules. There is no executable helper, script, code example, generated design source, or activation program.
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

These are prose acceptance cases for an agent on an authorized test host. Use a disposable existing project directory and isolated test-user home; do not create a workspace or alter a maintainer's real shell configuration. Keep all fixtures out of SiliconBoot commits. Record inputs, steps, actual results and evidence using the [templates](../templates/README.md).

| Scenario | Exercise | Required outcome |
| --- | --- | --- |
| Home-directory setup | Request setup while the clone is open, without supplying paths | Discover the existing project or use the clone; create no workspace or design scaffold; install managed tools and SRAM compilers under the user's ~/tools, matching macOS Homebrew tools at recorded external paths, and PDKs under ~/pdks, with individual public symlinks in ~/bin and no sudo |
| Privileged dependency | Required native dependency is absent and needs administrator-managed installation | Record the dependent components as blocked, continue independent work and perform no sudo or privileged package changes |
| macOS matching Homebrew package | Current native formula/cask matches the independently resolved latest official release and required features | Install or reuse through Homebrew; record exact package/artifact/dependency identities and concrete external paths without relocation or another location approval |
| macOS older or missing package | Homebrew trails upstream or has no matching tool | Record the comparison and reason; install the same latest official release through the best supported native binary, documented installer or source build, with managed files under ~/tools |
| macOS package identity and capability | Matching name/version hides an unrelated upstream, translated binary, missing feature, incompatible ABI, HEAD build or unversioned latest label | Do not treat it as a matching native latest package; retain evidence and choose the supported latest-version fallback or report the blocker |
| macOS Homebrew unavailable | Homebrew is absent, unsupported or not writable without elevation | Check official package metadata anyway; use official no-sudo Homebrew setup only when viable, otherwise record the reason and use the latest supported native fallback |
| macOS lookup failure | Homebrew metadata is unreachable while independent upstream discovery succeeds | Record Homebrew availability as unknown and justify a native latest-version fallback; if upstream discovery also fails, retain latest_unknown |
| macOS frozen package drift | Formula/cask or dependency inputs change after the plan is frozen | Replan affected identities before installation; do not silently install the changed package or claim equality from its version label alone |
| macOS protected dependencies | Homebrew install/upgrade would replace a keg, cask bundle or dependency referenced by a retained generation or lease | Check under the host-change gate, suppress automatic cleanup and unrelated dependent upgrades, and defer unsafe mutation; use a recorded latest-version fallback and preserve working references |
| macOS plan and exact restore | Plan without mutation, then restore an exact lock whose provider differs from current Homebrew | Plan via read-only live metadata; restore locked provider/definition/artifact/dependencies without latest substitution, reporting unavailable inputs as blockers |
| Unwritable home root | Existing tools, PDK or bin directory is not writable or resolves through an unexpected symlink | Preserve it, record the ownership or location conflict and do not retry with elevation |
| Default-shell detection | Agent runs bash while the account's default shell is zsh or fish | Select the account shell's actual configuration and verify a fresh instance of that shell; do not edit the agent shell's rc file |
| Shell configuration variants | Exercise bashrc, custom ZDOTDIR, fish with XDG_CONFIG_HOME, and missing user configuration files | Preserve content, add a bounded shell-native PATH rule only to the detected shell's effective file, create missing user configuration when needed and record backups and checks |
| Repeated PATH setup | Run setup twice and start or source the detected shell repeatedly | Exactly one effective ~/bin PATH entry and no duplicate managed sections; existing persistent rules can require no edit |
| Unknown default shell | Account lookup and SHELL fallback are unavailable or identify an unsupported shell | Preserve shell files, report PATH setup blocked and retain independently verified installations |
| Bash login startup | Existing login profile does not source bashrc | Interactive bashrc checks remain distinct; report the login PATH blocker and required follow-up without silently editing another startup file |
| Existing home binaries | ~/bin contains user files, unrelated links and names owned by another project | Preserve the directory and unrelated entries; publish only verified individual links and record explicit provider conflicts |
| Legacy roots | Existing records point to a former single installation root | Preserve that environment and report the required migration instead of silently retargeting links |
| Fresh clone and Git exclusions | Inspect the tracked tree and check representative .siliconboot records, run outputs and legacy workspace paths | No tracked workspace placeholder; generated metadata, runs and legacy workspace contents are ignored and absent from the staged set |
| Release selection | Official stable release beside draft/prerelease and non-release tags | Select the upstream-defined stable release; record why other entries were excluded |
| Source snapshot | Upstream recommends a branch other than the repository default | Use the documented branch and full immutable revision |
| Discovery failure | Network unavailable or official API rate-limited | Report `latest_unknown`; preserve working installs and avoid claiming freshness |
| Canonical source change | Official project redirects to a new location | Preserve identity evidence, original URL and canonical source; reject an unrelated namesake |
| Existing project | Existing README, AGENTS, config and user-owned files | Create only missing metadata and bounded local guidance under .siliconboot; preserve root instructions and all other content and report conflicts |
| Unusual paths | Spaces and non-ASCII characters in project/store paths | Correct literal path handling; no argument splitting, injection or escaped-name mismatch |
| Bad links | Dangling/cyclic links and links to unexpected third-party roots | Reject activation or the affected entrypoint; retain existing files and evidence |
| Name collision | Two providers export the same public name | Record a chosen default and distinct namespaced entries; never silently overwrite |
| Native identity | Wrong-architecture asset or translated execution | Reject it as native support for the selected host; report actual context |
| Missing uv | Authorized setup with no uv on the host | On macOS check Homebrew first and use a matching latest native package; otherwise install the official native uv distribution under ~/tools before Python environments or packages; record sources, provider and version |
| Existing uv | A uv executable is present before setup | Inspect identity, version, provider and native architecture; reuse only when lifecycle requirements match, preserving existing files |
| Python bootstrap failure | uv unavailable for the native host or acquisition fails | Block affected Python setup with evidence; continue independent components without silently changing managers |
| Isolation | Two Python components require conflicting dependencies | Separate uv-managed environments and fixed interpreter paths; system runtime and the other component still work |
| Python compatibility | Host Python conflicts with an EDA extension's ABI | Select and record a compatible native interpreter under ~/tools, or report the unsatisfied requirement |
| Upstream Python runtime | A host tool embeds Python or requires a managed dependency closure | Preserve the supported runtime and record an evidence-based exception to uv management |
| Fixed Python run | Ordinary invocation in a verified generation | Use its exact environment without uv synchronization, dependency resolution, lock changes or downloads |
| Clean session | New shell, different working directory, no build-session variables | Tools start and complete the relevant example using documented settings |
| AppImage mountpoint policy | On a host that restricts FUSE mountpoints, inspect a denied store-path launch and retry the same AppImage with a permitted `runs/<run-id>/tmp` inside the existing project | Record the canonical TMPDIR and actual policy evidence; verify startup and an affected function without changing installed bytes or weakening policy; if the project path is also denied, report that blocker |
| Interrupted build | Operation ends after download or during build | Record unfinished state; no broken successful entrypoints; resume rechecks inputs and ownership |
| Concurrent work | Two agents attempt the same installation or activation | Native locking serializes mutation; neither sees an incomplete installation as reusable |
| Candidate versus collection | Garbage collection overlaps a build or candidate validation | An operation lease protects new installations, reused inputs and dependencies until durable generation references replace it |
| Host change versus run admission | A run tries to start while a system package operation checks leases and mutates dependencies | The host-change gate serializes admission with that check and mutation; incompatible changes wait for existing runs |
| Activation interruption | Interruption before and after the atomic pointer change and during home binary-link publication | Current resolves to one complete generation; recovery reconciles companion records and owned ~/bin links from that generation, preserving unrelated entries |
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
