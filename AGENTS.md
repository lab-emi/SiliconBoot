# SiliconBoot agent guide

SiliconBoot guides an agent through native IC environment setup. Read [bootstrap](docs/bootstrap.md), the selected [catalog](catalog/README.md) entries, and their [recipes](recipes/README.md) before installation. Use the [operation prompts](prompts/README.md) and [record contract](docs/records.md) for later work.

## Working on this repository

- Keep all prose and commit messages in English.
- Keep the repository entirely prompt and documentation based: Markdown instructions, catalogs, recipes, examples, and templates, plus license metadata, Git ignore rules, and the empty `workspace/.gitkeep` placeholder. Do not add application code, scripts, executable wrappers, generated design sources, CI programs, or installer implementations. Describe checks and procedures in prose.
- Use component maintainers' official documentation and repositories. Track source identity and canonical redirects. Do not derive installation instructions from unrelated tool bundles.
- Keep links, component IDs, recipe references, and templates consistent. Review changes with [documentation acceptance](docs/acceptance.md). Claim native verification only with recorded execution evidence.

## Setting up or maintaining a user's project

- Discover the local SiliconBoot clone from the current working context and use its `workspace/` directory as the IC project. The tracked `workspace/.gitkeep` makes this directory available in a fresh clone; create it only if missing and preserve existing contents. The user supplies only the absolute installation root for tools, SRAM compilers, and PDKs; record it and reuse it for later operations. Do not ask for repository or project paths that can be derived from context. Preserve the root `.gitignore`: only the empty placeholder is tracked inside `workspace/`; generated contents and `workspace2/` stay out of SiliconBoot commits.
- Honor the user's scope and existing authorization. Inspect the host and preserve existing files before changing anything. Only merge clearly bounded SiliconBoot sections into existing documentation; report conflicting instructions for resolution.
- Resolve the latest official stable release when installing or upgrading. When none exists, establish the upstream maintenance branch and record its exact revision. Freeze the resolution before building. Report `latest_unknown` if discovery fails; never silently substitute an older release, architecture, provider, or execution environment.
- Install into persistent versioned locations and isolate language runtimes. Preserve upstream PDK layouts, resources, and licenses. Follow [installation](docs/installation.md) for dependency order, locking, retries, and generation activation.
- Use uv by default to create and manage Python environments for IC design. Check for uv during host inspection; if it is missing, install it from its official source and verify its native executable before creating Python environments or installing Python packages. Follow the [uv recipe](recipes/uv/README.md) and [Python environment policy](docs/python-environments.md), including recorded exceptions for upstream-managed runtimes.
- Expose installation roots through `tools/` and `pdk/`, and verified upstream executable entrypoints through `bin/`. Record every provider and resolve name collisions explicitly. Libraries and plugins can require an interpreter or host tool; do not invent a CLI or a custom launcher.
- Follow [validation](docs/validation.md). Record sources, versions, build inputs, patches, capabilities, failures, and evidence before activation. Keep `installed_latest`, `component_usable`, and `workflow_ready` distinct. Do not advertise a partial environment as complete.
- Pin the resolved generation for each design run. Write generated results into its run directory, keeping shared installations immutable. Upgrade only when requested and retain the working generation until affected checks pass.
- For LibreLane AppImage, create a private `workspace/runs/<run-id>/tmp` directory and scope `TMPDIR` to its canonical absolute path. Verify that the host permits FUSE mounts there; a store path such as `/eda/work` may be denied by AppArmor. Inspect mountpoint denials and retry with the verified project directory before declaring FUSE unavailable. Follow [temporary mount guidance](docs/project-layout.md#appimage-temporary-mounts) and retain the directory until all processes and mounts finish.
- Use sudo only within the user's authorization and the host's approval rules. Never store passwords or suggest persistent unrestricted passwordless sudo. This risk notice does not itself grant permission.
- After successful checks, use the [cleanup procedure](docs/cleanup.md) to remove owned temporary files. Preserve runtime sources, shared installations, retained generations, and active runs. Garbage collection is a separate explicit operation.

Generate project instructions from [the project templates](templates/README.md), replacing placeholders with real persistent paths. A new agent must be able to locate and run the environment from those documents alone. Native installation is at the user's own risk.
