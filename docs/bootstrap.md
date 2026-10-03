# Bootstrap an IC project

SiliconBoot is a set of instructions for an agent with filesystem, network, and native process access. The agent performs the work using the host's facilities and the selected components' official installation procedures. A text-only assistant can explain the steps but cannot claim to have installed or verified an environment.

Start with the [repository guide](../AGENTS.md), [catalog](../catalog/README.md), and [bootstrap prompt](../prompts/bootstrap.md). Follow the [installation procedure](installation.md) for every selected component. All generated guidance and records use English.

## 1. Inspect the request and host

- Discover the local SiliconBoot clone from the current working directory, open files, or attached repository context. Confirm it contains the root AGENTS.md, catalog, and recipes. If working inside its `workspace/`, resolve the parent clone. Ask which clone to use only when the available context cannot identify it; do not request a path the agent can already determine.
- Derive the IC project path as `workspace/` directly under that clone. Create it if missing or inspect and preserve it if it already exists. A persistent documentation snapshot is guidance, not another clone in which to create a workspace.
- Use the user's absolute installation path as the persistent store root for all tools, SRAM compilers, and PDKs. Normalize the repository, workspace, and installation root internally and record their absolute locations. The installation root is the only path the user supplies. Never change the meaning of the user's home directory.
- Honor the user's requested components, profile, PDK, provider, and permissions. The default scope is the full catalog; every selected entry needs a disposition, including entries that have no implemented recipe.
- Read existing project instructions, configuration, and environment records. Inventory files before creating anything. Existing user files remain authoritative; an ambiguous ownership or conflicting configuration blocks only the affected mutation.
- Record the native operating system, release, CPU architecture, process architecture, available storage and memory, compiler availability, GUI/display access, package manager, and relevant existing installations in the [host record](../templates/records/host.md).
- Identify network restrictions and source access. Establish which native filesystem facilities can provide exclusive locks, symbolic links, and atomic replacement. See [platforms](platforms.md).
- Inventory existing commands by their resolved provider and actual version. A matching executable name alone does not establish component identity or suitability.

Present a compact plan: selected and excluded components, known blockers, official source locations, proposed system dependencies, expected large downloads or builds, measured resource constraints, and the exact scope of privileged changes. Do not invent time or space estimates. Apply build concurrency limits appropriate to the host.

Use elevated privileges only within the user's existing authorization and the host's approval rules. A risk notice is not authorization. Passwords belong only in a controlled interactive prompt and must never enter project files, prompts, receipts, or logs. If privileged work is unavailable, continue independent work that needs no elevation and record the blocker.

## 2. Initialize without replacing user content

Follow [project layout](project-layout.md). Create only missing directories under the clone's `workspace/`. Keep workspace contents out of SiliconBoot commits using the clone's local Git exclusions, preserving existing exclusions. Render [project templates](../templates/README.md) there with actual paths and selected settings. Merge a clearly bounded SiliconBoot section into an existing README, AGENTS, or environment guide only when its meaning does not conflict with existing instructions. Keep all text outside that section. Preserve a recoverable copy before replacing a previously generated section.

Use the supplied installation directory directly as the store root; do not append another `siliconboot` directory or replace it with a home-directory or environment-variable default. Record it in `workspace/.siliconboot/host.md` and reuse that recorded root for maintenance. For first setup, ask for the installation path only if it is missing. A disagreement with an existing workspace's recorded root requires a documented migration; do not silently reconnect its links. Validate that the root can hold the persistent store without overwriting project or repository files.

Install all managed tools, SRAM compilers, and PDKs beneath that root using the versioned layout. System dependencies retain their native package-manager locations. If a component provider requires files elsewhere or proposes reusing an external installation, disclose the actual locations and obtain an explicit exception before using that provider.

Keep a persistent, read-only documentation snapshot under the store's `guides` directory. Identify it by the repository revision and, for local modifications or a checkout without Git history, a digest of its Markdown content. Copy the relevant root guidance, repository LICENSE, catalog, recipes, docs, prompts, and templates while preserving their relative paths. Record the source checkout and digest. Project guidance must point to this existing snapshot so a removed source checkout does not strand the project. This snapshot contains documentation and its license only.

Register the project with its stable project identifier, canonical path, retained generations, and selected store. Registration and initial filesystem changes must follow the lock rules in [installation](installation.md). Do not register an incomplete or unverified installation as usable.

## 3. Resolve, install, and verify

1. Read each selected catalog entry and its recipe, including official source identity and platform limits.
2. Resolve latest versions from official upstream information and freeze a dated [resolution plan](../templates/records/resolution.md). Ordinary inspection and design runs do not refresh this plan.
3. Install in dependency order, including coupled tool, PDK, and model requirements. Complete independent components even when another component fails. Mark dependent components blocked with the actual cause.
4. Build a persistent installation, write its receipt, and run the required component checks. Run the selected integration checks with evidence and explicit limitations.
5. Create a new candidate generation with complete links, manifest, portable lock, and validation records. Verify it from a fresh process with the documented environment and working directory.
6. Activate according to the [generation transaction](installation.md#activate-one-generation). On a first installation, a verified subset may be activated as `partial` with its missing components and workflows listed. An existing environment remains active until its replacement passes the required upgrade checks.
7. Export the activated portable lock to `config/environment.lock.md`, reconcile project guidance, and perform [owned temporary-file cleanup](cleanup.md).

## 4. Finish with an evidence-based summary

Report the project and store locations, active generation, selected profile, exact component versions and providers, entrypoint locations, and how to read `ENVIRONMENT.md`. Separate latest-version status, component usability, and workflow readiness. Link the resolution, manifest, lock, validation, and failure records.

List unsupported or planned entries, unresolved latest versions, failures, skipped checks, missing GUI checks, incompatible combinations, and any host package changes. Report successful cleanup and retained diagnostic files with measured size where available. Provide the next resumable step for each unfinished component.

An installation is complete only to the scope supported by its recorded evidence. Follow [validation](validation.md) and the [acceptance checklist](acceptance.md); a repository document or a successful version query alone is not native installation evidence.
