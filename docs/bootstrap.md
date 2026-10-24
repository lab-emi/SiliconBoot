# Bootstrap an IC project

SiliconBoot is a set of instructions for an agent with filesystem, network, and native process access. The agent performs the work using the host's facilities and the selected components' official installation procedures. A text-only assistant can explain the steps but cannot claim to have installed or verified an environment.

Start with the [repository guide](../AGENTS.md), [catalog](../catalog/README.md), and [bootstrap prompt](../prompts/bootstrap.md). Follow the [installation procedure](installation.md) for every selected component. All generated guidance and records use English.

## 1. Inspect the request and host

- Discover the local SiliconBoot clone from the current working directory, open files, or attached repository context. Confirm it contains the root AGENTS.md, catalog, and recipes. Ask which clone to use only when the available context cannot identify it; do not request a path the agent can already determine.
- Use the existing design project identified by context, or the clone itself when no separate project is selected. Record its canonical path. Do not create a workspace, add a placeholder, or scaffold design directories. Preserve any existing workspace. A persistent documentation snapshot is guidance, not a project to initialize.
- Expand `~/tools`, `~/pdks` and `~/bin` using the invoking user's actual home directory. Tools, SRAM compilers, uv and isolated runtimes belong under `~/tools`; PDKs belong under `~/pdks`; public executable symlinks belong under `~/bin`. Record their absolute and canonical locations without asking for an installation root. Never redefine HOME or use root's home through sudo.
- Honor the user's requested components, profile, PDK, provider, and permissions. The default scope is the `all` profile, including uv; JupyterLab is optional. Every selected entry needs a disposition, including entries that have no implemented recipe.
- Read existing project instructions, configuration, and environment records. Inventory files before creating anything. Existing user files remain authoritative; an ambiguous ownership or conflicting configuration blocks only the affected mutation.
- Record the native operating system, release, CPU architecture, process architecture, available storage and memory, compiler availability, GUI/display access, package manager, relevant existing installations, default login shell and its configuration path in the [host record](../templates/records/host.md). Follow [shell detection and PATH setup](project-layout.md#default-shell-path).
- Identify network restrictions and source access. Establish which native filesystem facilities can provide exclusive locks, symbolic links, and atomic replacement. See [platforms](platforms.md).
- When selecting an AppImage, inspect FUSE access and the policy governing its temporary mountpoint. Use a private `runs/<run-id>/tmp` directory inside the existing project with a verified canonical path as described in [project layout](project-layout.md#appimage-temporary-mounts). A writable installation store does not establish permission to mount beneath it.
- Inventory existing commands by their resolved provider and actual version. A matching executable name alone does not establish component identity or suitability.
- Check whether uv is available, recording its path, version and provider. If missing, plan its official native installation before any Python environment or package setup. Review compatible Python versions and upstream runtime exceptions using [Python environments](python-environments.md).

Present a compact plan: selected and excluded components, known blockers, official source locations, missing system dependencies, expected large downloads or builds, measured resource constraints, user-owned installation paths, binary collisions and the one shell configuration to update. Do not invent time or space estimates. Apply build concurrency limits appropriate to the host.

Setup uses no sudo or system package changes. Prefer an upstream-supported user installation for missing dependencies; if a dependency still needs administrator action, record the affected components as blocked and continue independent work. A later explicit request and the host's approval rules govern any separate privileged action. Passwords must never enter project files, prompts, receipts or logs.

## 2. Initialize without replacing user content

Follow [project layout](project-layout.md). Put generated guidance, choices, locks and local state inside the existing directory's `.siliconboot/`; leave its root README and AGENTS authoritative. Create only missing metadata, installation and binary-link directories. Create run directories when checks or design tasks need them, not an empty design scaffold. The committed root `.gitignore` excludes these local records and runs as well as legacy workspaces; do not force-add generated files. Render [project templates](../templates/README.md) under `.siliconboot/` with actual paths and selected settings. Merge only clearly bounded SiliconBoot sections into existing generated guidance, preserving all other content and a recoverable previous copy.

Use `~/tools` as the tool store and `~/pdks` as the separate PDK root; do not produce `~/tools/tools` or `~/tools/pdks`. Store shared bookkeeping beneath `~/tools/.siliconboot/`. Record both roots and `~/bin` in `.siliconboot/host.md` and reuse them for maintenance. If existing records use different roots, preserve that environment and report the migration needed before reconnecting links. Inspect existing directories, symlinks, ownership and write access before mutation. An unwritable path is a blocker, not a reason to retry with sudo.

Install managed components using the versioned tool and PDK layouts. Existing system dependencies retain their native package-manager locations. If a component provider requires managed files elsewhere or proposes reusing an external installation, disclose the actual locations and record an explicit accepted exception before using that provider.

Keep a persistent, read-only documentation snapshot under `~/tools/.siliconboot/guides`. Identify it by the repository revision and, for local modifications or a checkout without Git history, a digest of its Markdown content. Copy the relevant root guidance, repository LICENSE, catalog, recipes, docs, prompts, and templates while preserving their relative paths. Record the source checkout and digest. Project guidance must point to this existing snapshot. If the clone itself holds the local project records, preserve those records while its environment is in use. This snapshot contains documentation and its license only.

Register the project with its stable project identifier, canonical path, retained generations and both installation roots. Registration and initial filesystem changes must follow the lock rules in [installation](installation.md). Do not register an incomplete or unverified installation as usable.

## 3. Resolve, install, and verify

1. Read each selected catalog entry and its recipe, including official source identity and platform limits.
2. Resolve latest versions from official upstream information and freeze a dated [resolution plan](../templates/records/resolution.md). Ordinary inspection and design runs do not refresh this plan.
3. Install in dependency order, beginning with the [uv prerequisite](../recipes/uv/README.md) when missing, then compatible interpreters and isolated Python environments. Include coupled tool, PDK, and model requirements. Complete independent components even when another component fails. Mark dependent components blocked with the actual cause.
4. Build a persistent installation, write its receipt, and run the required component checks. Run the selected integration checks with evidence and explicit limitations.
5. Create a new candidate generation with complete links, manifest, portable lock, and validation records. Verify it from a fresh process with the documented environment and working directory.
6. Activate according to the [generation transaction](installation.md#activate-one-generation). On a first installation, a verified subset may be activated as `partial` with its missing components and workflows listed. An existing environment remains active until its replacement passes the required upgrade checks.
7. Publish verified binary symlinks in `~/bin` without replacing unrelated entries. Configure PATH only in the detected default shell's startup file, then verify command resolution in a fresh instance of that shell. Export the activated portable lock to `.siliconboot/environment.lock.md`, reconcile project guidance, and perform [owned temporary-file cleanup](cleanup.md).

## 4. Finish with an evidence-based summary

Report the existing project directory, tool and PDK roots, binary directory, detected shell and edited configuration file, active generation, selected profile, exact component versions and providers, entrypoint locations, and how to read `.siliconboot/ENVIRONMENT.md`. Separate latest-version status, component usability, and workflow readiness. Link the resolution, manifest, lock, validation, and failure records.

List unsupported or planned entries, unresolved latest versions, failures, skipped checks, missing GUI checks, incompatible combinations, and any host package changes. Report successful cleanup and retained diagnostic files with measured size where available. Provide the next resumable step for each unfinished component.

An installation is complete only to the scope supported by its recorded evidence. Follow [validation](validation.md) and the [acceptance checklist](acceptance.md); a repository document or a successful version query alone is not native installation evidence.
