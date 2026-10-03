# Project and persistent-store layout

The IC design project lives in `workspace/` directly under the cloned SiliconBoot repository. Its tracked empty `.gitkeep` makes the directory available immediately after cloning. The agent discovers the clone's location and derives this project path. The user supplies only the absolute installation root for tools, SRAM compilers, and PDKs, called the store in these documents.

The generated project contains Markdown guidance and records, directories, and native symbolic links. SiliconBoot does not generate activation scripts, wrappers, installer code, or design-source examples. The user's design work may later add its own source files inside the local workspace. Render the [templates](../templates/README.md) with the derived project path and chosen installation root.

## Project locations

Every location in this table is relative to the clone's `workspace/` directory. Preserve an existing workspace and its user files when repeating setup.

| Location | Purpose and ownership |
| --- | --- |
| `.gitkeep` | Empty repository-owned placeholder; preserve it and keep generated project files untracked. |
| `README.md` | Project introduction and a bounded SiliconBoot orientation section. |
| `AGENTS.md` | Existing project rules plus a bounded guide to this project's active tools, records, and lifecycle. |
| `project.md` | Human-readable desired scope, profiles, PDK selection, command providers, installation-root record reference, and workflow requirements. |
| `ENVIRONMENT.md` | Session and per-tool environment instructions, with the actual persistent documentation location. |
| `tools` | Symlink to `.siliconboot/current/tools`; each child references one persistent tool installation. |
| `pdk` | Symlink to `.siliconboot/current/pdk`; family views preserve upstream shared resources and relative links. |
| `bin` | Symlink to `.siliconboot/current/bin`; each child references an actual upstream public entrypoint. |
| `design/rtl`, `design/schematics`, `design/layout`, `design/constraints` | User-owned design sources. |
| `verification/digital`, `verification/analog`, `verification/formal`, `verification/drc`, `verification/lvs` | User-owned verification inputs and requirements. |
| `config/tools`, `config/flows` | Project overrides; never edit shared installations for project-specific configuration. |
| `config/environment.lock.md` | Portable exact environment record intended for version control. |
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

An existing real directory or user symlink at `tools`, `pdk`, or `bin` is a preservation conflict. Inventory it, document the proposed migration, and follow the user's authorization; do not replace it on the assumption that its name implies SiliconBoot ownership. Existing project files and user changes inside a generated section also require a three-way comparison with the prior rendered section before updating.

## Persistent store

Use the absolute installation root supplied by the user, as described in [bootstrap](bootstrap.md). All paths below are relative to that root. Tools and SRAM compilers use `tools/`; PDK families use `pdks/`. Reuse the root recorded in the workspace's host record for later operations, and use the same canonical store identity across projects that share it.

| Store-relative location | Contents |
| --- | --- |
| `guides/<guide-revision>/` | Read-only Markdown snapshot of the guidance, catalog, and recipes used by the project. |
| `tools/<component>/<install-key>/root/` | Complete persistent runtime installation with its upstream layout. |
| `tools/<component>/<install-key>/receipt.md` | Installation identity, exact sources, dependencies, and evidence. |
| `runtimes/python/<runtime-key>/root/` | Persistent uv-managed Python distribution and its owned executable directory. |
| `runtimes/python/<runtime-key>/receipt.md` | Exact interpreter build, provider, asset digest, native ABI and references. |
| `cache/uv/` | Shared uv dependency cache with recorded ownership; outside routine temporary cleanup. |
| `pdks/<family>/<install-key>/root/` | Complete PDK family, shared data, and native model products. |
| `pdks/<family>/<install-key>/receipt.md` | Data, builder, toolchain, model, and patch provenance. |
| `downloads/<operation-id>/` | Owned temporary downloads. |
| `work/<operation-id>/` | Owned extraction, clone, and build intermediates that are not runtime dependencies. |
| `logs/<operation-id>/` | Retained installation diagnostics and verification reports. |
| `locks/`, `leases/` | Native-lock-associated ownership records and active-use protection records. |
| `registry.md` | Registered projects, retained generations, installations, and references. |

Runtime source can remain part of a persistent installation. A Python component may need both source and its private interpreter environment; neither is disposable merely because a build has finished. Install at the final prefix and retain required upstream files. An external system installation remains at its provider's location and is recorded as external.

Install uv under `tools/uv/`. Create each uv-managed environment inside its component's final runtime tree, recording its exact path. Derive a Python runtime key from the canonical build identity, including the exact interpreter implementation, version, provider build and asset digest. Register runtime receipts and dependency references using the same locks and leases as tool installations. These runtime dependencies do not add catalog scope records. Follow [Python environments](python-environments.md) to keep downloads, interpreter entrypoints and caches under the selected root.

## Entrypoints and environment

The generation manifest maps every exported name to its component, receipt, upstream executable, interpreter if needed, and runtime requirements. Export only public entrypoints. Keep private build helpers, unrelated package executables, and whole system binary directories out of the project's binary view.

Use a standard executable name only when its provider is unambiguous or explicitly selected in `project.md`. Provide a disambiguating `<component>--<command>` symlink where appropriate. A collision blocks that name until the provider selection is recorded. Never silently allow the last installed component to win.

Libraries, PDKs, and host-tool plugins may have no public executable. Expose them through the installation views and record their actual use. For tools with special runtime requirements, follow the per-tool environment and working-directory instructions; use upstream-provided entrypoints without creating wrappers.

`ENVIRONMENT.md` describes how to place the selected generation's `bin` directory at the front of a session's search path without duplicate entries, and how to select supported PDK variables and tool settings. Set a model/configuration path only if that path exists and the recipe requires it. Do not globally combine virtual environments or set broad library search paths without a specific verified requirement. Record the original session values when a session needs restoration.

For long or reproducible runs, resolve the generation and every environment path to fixed absolute locations before starting and create a lease. Do not pass paths containing `current` into a long-running workflow. The top-level links are convenient discovery views and can change during an upgrade; [generation-pinned runs](installation.md#lock-operations-and-preserve-running-work) keep one coherent environment.

### AppImage temporary mounts

For LibreLane AppImage, create a real, private `workspace/runs/<run-id>/tmp` directory during run admission, using owner-only permissions where supported. Resolve its canonical absolute path and set `TMPDIR` to that path for the AppImage process and its children. The upstream runtime creates and releases its FUSE mount below this directory. Keep the AppImage itself under the selected persistent installation root. Record the actual temporary path, ownership, environment, and checks in the run record and describe the rule in the manifest and generated project guidance.

Verify the mount policy against the real path. On hosts with a restricted AppArmor `fusermount3` profile, a directory below the user's home may be allowed while `/eda/work` is denied. A workspace symlink into a denied location does not establish permission, and a clone outside the home directory needs its own policy check. If the derived project directory is denied, record the precise blocker and preserve the environment; do not weaken the policy or silently relocate the project.

For a mount failure, inspect the actual `TMPDIR`, `/dev/fuse`, the installed FUSE helper, and accessible kernel or audit diagnostics. A mountpoint-policy denial does not establish that FUSE is missing. Recheck startup and an affected function with the same installed AppImage and a verified project temporary directory before changing capability claims. Follow the [LibreLane recipe](../recipes/digital-flow/README.md#librelane-appimage-mountpoints).

Wait for the entire process tree to exit and confirm that no mount remains before applying [owned temporary cleanup](cleanup.md). Preserve the run's inputs, reports, and artifacts. An abandoned mount or uncertain owner blocks deletion of that directory.

## Version control and portability

The root `.gitignore` ignores `/workspace/*` and makes one exception for `/workspace/.gitkeep`. Git tracks that empty file so a fresh clone has a workspace; every generated file, link, nested directory, and hidden state directory remains local. `/workspace2/` is also ignored. Check the staged file list before committing and never force-add generated workspace contents. Preserve unrelated exclusion rules when replacing an older local `/workspace/` exclusion with the committed policy.

If the user wants version control for the IC design, follow their chosen project repository policy and track its sources, configuration, memory requests, accepted manifests, guidance, and portable lock there. Portable records use component identities and project-relative paths; they do not contain host-specific installation prefixes, private credentials, or local usernames.

Exclude machine-local links, `.siliconboot` state, installation caches, native lock files, and large generated outputs from any design repository according to the user's existing policy. Preserve existing exclusion settings. The host-specific environment guide can be kept local; a portable checked-in guide must avoid rendered absolute host paths.

Move a project to another host by [restoring its portable lock](upgrade.md#restore-an-exact-lock). Copying an old absolute symlink does not rebuild the environment. Keep [records](records.md) explicit about this distinction.
