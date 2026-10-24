# Project and persistent-store layout

Setup uses an existing project directory identified from the working context, defaulting to the local SiliconBoot clone. It does not create a workspace or scaffold a design project. Generated guidance and records live under that directory's `.siliconboot/`. Existing workspace directories and user sources remain intact.

Managed EDA tools, SRAM compilers, uv and isolated runtimes live under `~/tools`; PDKs live under `~/pdks`; public executable symlinks live under `~/bin`. Matching macOS Homebrew tools remain at their provider-managed locations under the [Homebrew exception](installation.md#macos-check-homebrew-first), with receipts in the tool store. Expand home paths against the invoking user's actual home directory, record their canonical identities and use them without sudo. SiliconBoot generates Markdown guidance and records, directories and native symbolic links. It does not generate activation scripts, wrappers, installer code or design-source examples. Render the [templates](../templates/README.md) with the existing project path and both installation roots.

## Project locations

Every location in this table is relative to the existing project directory. Only metadata is initialized during setup; design, configuration, memory and run directories are used or created when the corresponding task requires them. Preserve existing user files when repeating setup.

| Location | Purpose and ownership |
| --- | --- |
| `.siliconboot/README.md` | Local orientation and links to environment guidance; the project's root README remains authoritative. |
| `.siliconboot/AGENTS.md` | Guide to this project's active tools, records and lifecycle, used together with existing project rules. |
| `.siliconboot/project.md` | Desired scope, profiles, PDK selection, command providers, installation-root record references and workflow requirements. |
| `.siliconboot/ENVIRONMENT.md` | Session and per-tool environment instructions, with the actual persistent documentation location. |
| `design/rtl`, `design/schematics`, `design/layout`, `design/constraints` | User-owned design sources. |
| `verification/digital`, `verification/analog`, `verification/formal`, `verification/drc`, `verification/lvs` | User-owned verification inputs and requirements. |
| `config/tools`, `config/flows` | Project overrides; never edit shared installations for project-specific configuration. |
| `.siliconboot/environment.lock.md` | Portable exact environment export; copy to a user-selected tracked location when requested. |
| `ip/memory/configs`, `ip/memory/manifests` | User memory requests and accepted macro provenance records. |
| `docs` | Project-specific design documentation. |
| `runs/<run-id>/artifacts`, `reports`, `logs` | Outputs for one independently recorded design or validation run. |
| `runs/<run-id>/tmp` | Private temporary directory owned by this run, including its AppImage mountpoints; remove only after all processes and mounts finish. |
| `runs/<run-id>/run.md` | Generation, inputs, invocation conditions, checks, and artifact identities for that run. |
| `.siliconboot/current` | The single symlink selecting one complete immutable generation. |
| `.siliconboot/generations/<generation-id>/tools`, `pdk`, `bin` | Consistent installation and executable views for that generation. |
| `.siliconboot/generations/<generation-id>/manifest.md` | Host-specific component, provider, entrypoint, and runtime map. |
| `.siliconboot/generations/<generation-id>/lock.md` | Portable exact resolution belonging to this generation. |
| `.siliconboot/generations/<generation-id>/validation.md` | Evidence for this generation's component and workflow claims. |
| `.siliconboot/host.md`, `.siliconboot/state.md` | Host observations and resumable operation state. |
| `.siliconboot/resolutions`, `.siliconboot/logs` | Frozen discovery plans, activation evidence, diagnostics, and provenance records. |
| `.siliconboot/leases` | Human-readable descriptions of active operation and run protection, backed by native locking. |

Angle-bracketed path parts denote values chosen during initialization. They are not literal directory names. Never create placeholder paths or leave an unresolved template in the active environment.

Do not create project-root `tools`, `pdk` or `bin` links. Keep installation views inside the generation and publish individual executable symlinks in `~/bin`. Inventory existing home-directory roots and links before adding anything; their names do not establish SiliconBoot ownership. Existing guidance and user changes inside a generated section require a three-way comparison with the prior rendered section before updating.

## Persistent store

Use the home-directory roots described in [bootstrap](bootstrap.md). In these documents, the shared store comprises the tool root `~/tools`, PDK root `~/pdks` and bookkeeping under `~/tools/.siliconboot`. Reuse both canonical roots recorded in the project's host record for maintenance, with one registry protecting their shared references. Older records with a single root require an explicit migration; preserve their paths until that migration is resolved.

| Location | Contents |
| --- | --- |
| `~/tools/.siliconboot/guides/<guide-revision>/` | Read-only Markdown snapshot of the guidance, catalog and recipes used by the project. |
| `~/tools/<component>/<install-key>/root/` | Complete persistent runtime installation with its upstream layout. |
| `~/tools/<component>/<install-key>/receipt.md` | Installation identity, exact sources, dependencies and evidence. |
| Recorded Homebrew prefix, keg/Caskroom and application paths | External macOS tools; generation views reference verified concrete runtime targets, with receipts in the tool store. |
| `~/tools/.siliconboot/runtimes/python/<runtime-key>/root/` | Persistent uv-managed Python distribution and its owned executable directory. |
| `~/tools/.siliconboot/runtimes/python/<runtime-key>/receipt.md` | Exact interpreter build, provider, asset digest, native ABI and references. |
| `~/tools/.siliconboot/cache/uv/` | Shared uv dependency cache with recorded ownership; outside routine temporary cleanup. |
| `~/pdks/<family>/<install-key>/root/` | Complete PDK family, shared data and native model products. |
| `~/pdks/<family>/<install-key>/receipt.md` | Data, builder, toolchain, model and patch provenance. |
| `~/tools/.siliconboot/downloads/<operation-id>/` | Owned temporary downloads. |
| `~/tools/.siliconboot/work/<operation-id>/` | Owned extraction, clone and build intermediates that are not runtime dependencies. |
| `~/tools/.siliconboot/logs/<operation-id>/` | Retained installation diagnostics and verification reports. |
| `~/tools/.siliconboot/locks/`, `leases/` | Native-lock-associated ownership records and active-use protection records, both under the store's `.siliconboot/`. |
| `~/tools/.siliconboot/registry.md` | Registered projects, retained generations, installations, home binary links and references. |

Runtime source can remain part of a persistent installation. A Python component may need both source and its private interpreter environment; neither is disposable merely because a build has finished. Install at the final prefix and retain required upstream files. An external system installation remains at its provider's location and is recorded as external.

Install managed uv under `~/tools/uv/`, or record its external native Homebrew location on macOS when that provider matches the latest official release. Create each uv-managed environment inside its component's final runtime tree, recording its exact path. Derive a Python runtime key from the canonical build identity, including the exact interpreter implementation, version, provider build and asset digest. Register runtime receipts and dependency references using the same locks and leases as tool installations. These runtime dependencies do not add catalog scope records. Follow [Python environments](python-environments.md) to keep managed downloads, interpreter entrypoints and caches under `~/tools`, and record provider-managed runtime exceptions.

## Entrypoints and environment

The generation manifest maps every exported name to its component, receipt, upstream executable, interpreter if needed, and runtime requirements. Export only public entrypoints. Keep private build helpers, unrelated package executables and whole system binary directories out of the generation's binary view.

Use a standard executable name only when its provider is unambiguous or explicitly selected in `.siliconboot/project.md`. Provide a disambiguating `<component>--<command>` symlink where appropriate. A collision blocks that name until the provider selection is recorded. Never silently allow the last installed component to win.

Preserve `~/bin` as a directory and add individual symlinks; never replace the directory with a generation link. Each managed public name points through this project's `.siliconboot/current/bin/<name>` to its upstream executable. Record the owning project, link text and final provider in the shared registry. Existing files or unrelated symlinks, including links owned by another project, block that name until an explicit provider choice resolves the conflict. Publication and reconciliation follow the activation locks. Repeated setup reuses matching links and preserves unrelated entries.

Libraries, PDKs, and host-tool plugins may have no public executable. Expose them through the installation views and record their actual use. For tools with special runtime requirements, follow the per-tool environment and working-directory instructions; use upstream-provided entrypoints without creating wrappers.

`.siliconboot/ENVIRONMENT.md` records the home binary directory, detected default shell, startup file, PATH change and checks, along with per-tool PDK variables and runtime settings. Set a model/configuration path only if that path exists and the recipe requires it. Do not globally combine virtual environments or set broad library search paths without a specific verified requirement. Record the original session values when a session needs restoration.

For long or reproducible runs, resolve the generation and every environment path to fixed absolute locations before starting and create a lease. Put that concrete generation's `bin` first in the run's process PATH. Do not pass paths containing `current` into a long-running workflow. Home binary links are convenient discovery views and can change during an upgrade; [generation-pinned runs](installation.md#lock-operations-and-preserve-running-work) keep one coherent environment.

### Default shell PATH

Detect the invoking user's configured login shell from the host account database using native facilities. The shell running the agent may be different; use SHELL only as a recorded fallback when the account lookup is unavailable and the value identifies a supported shell. Do not guess bash from the agent's process. Record the detected executable, detection evidence and effective user configuration location before editing. An unknown or unsupported shell blocks only automatic PATH setup; report it without editing another shell's files.

| Default shell | Configuration location | PATH behavior |
| --- | --- | --- |
| bash | `~/.bashrc` | Add the user's absolute `~/bin` directory only when absent, exporting PATH and preserving all other entries. Use bash syntax. |
| zsh | `.zshrc` under the effective ZDOTDIR, or `~/.zshrc` when ZDOTDIR is unset | Add the user's absolute `~/bin` directory only when absent from zsh's path array, preserving other entries. Use zsh syntax. |
| fish | `config.fish` under the effective fish configuration directory, normally `~/.config/fish/config.fish`; honor XDG_CONFIG_HOME | Use fish's `fish_add_path` with PATH scope so the startup file provides persistence without changing universal variables; preserve other entries and avoid duplicates. |

These locations follow the official [bash startup rules](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files), [zsh startup rules](https://zsh.sourceforge.io/Doc/Release/Files.html), [fish configuration rules](https://fishshell.com/docs/current/language.html#configuration-files) and [fish PATH interface](https://fishshell.com/docs/current/cmds/fish_add_path.html). Inspect the installed shell's behavior and existing startup files, including ZDOTDIR established during zsh startup. Bash login shells may need an existing user login profile to source `.bashrc`; if that connection is missing, report it and document the required follow-up rather than silently editing additional files.

Create `~/bin` before PATH verification. Inspect and preserve the selected configuration file, make a recoverable copy, and merge one clearly bounded SiliconBoot PATH section using that shell's native syntax. Create the selected file and its missing user configuration directories when needed. If existing configuration already supplies the required PATH entry persistently, keep it and record that no edit was needed. Do not modify other shells or system-wide startup files. Guard against duplicate entries when a shell starts repeatedly or the file is sourced again, and quote paths with spaces correctly.

Verify syntax and command resolution from a fresh interactive instance of the detected default shell, in another working directory and with a baseline PATH that does not inherit the setup session's added entry. Also check the default shell's login behavior where applicable. Record the effective PATH, selected symlink targets and any alias, function or startup override that prevents the intended provider from resolving. A passing check in the agent's own shell is insufficient.

### AppImage temporary mounts

For LibreLane AppImage, create a real, private `runs/<run-id>/tmp` directory inside the existing project during run admission, using owner-only permissions where supported. Resolve its canonical absolute path and set `TMPDIR` to that path for the AppImage process and its children. The upstream runtime creates and releases its FUSE mount below this directory. Keep the AppImage itself under `~/tools`. Record the actual temporary path, ownership, environment and checks in the run record and describe the rule in the manifest and generated project guidance.

Verify the mount policy against the real path. On hosts with a restricted AppArmor `fusermount3` profile, a directory below the user's home may be allowed while another writable path is denied. A project symlink into a denied location does not establish permission, and a project outside the home directory needs its own policy check. If the existing project directory is denied, record the precise blocker and preserve the environment; do not weaken the policy or silently relocate the project.

For a mount failure, inspect the actual `TMPDIR`, `/dev/fuse`, the installed FUSE helper, and accessible kernel or audit diagnostics. A mountpoint-policy denial does not establish that FUSE is missing. Recheck startup and an affected function with the same installed AppImage and a verified project temporary directory before changing capability claims. Follow the [LibreLane recipe](../recipes/digital-flow/README.md#librelane-appimage-mountpoints).

Wait for the entire process tree to exit and confirm that no mount remains before applying [owned temporary cleanup](cleanup.md). Preserve the run's inputs, reports, and artifacts. An abandoned mount or uncertain owner blocks deletion of that directory.

## Version control and portability

The root `.gitignore` excludes `/.siliconboot/`, `/runs/`, `/workspace/` and `/workspace2/`. Fresh clones contain no workspace placeholder, and setup creates no workspace. Preserve legacy workspace contents without tracking them. Check the staged file list before committing and never force-add generated records or run outputs. Preserve unrelated exclusion rules.

If the user wants version control for the IC design, follow their existing project repository policy and track its sources, configuration, memory requests, accepted manifests, guidance and a copy of the portable lock at their chosen location. Portable records use component identities and project-relative paths; they do not contain host-specific installation prefixes, private credentials or local usernames.

Exclude machine-local links, `.siliconboot` state, installation caches, native lock files, and large generated outputs from any design repository according to the user's existing policy. Preserve existing exclusion settings. The host-specific environment guide can be kept local; a portable checked-in guide must avoid rendered absolute host paths.

Move a project to another host by [restoring its portable lock](upgrade.md#restore-an-exact-lock). Copying an old absolute symlink does not rebuild the environment. Keep [records](records.md) explicit about this distinction.
