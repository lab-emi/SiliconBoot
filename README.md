# SiliconBoot

**Agent-guided native setup for open-source IC design tools.**\
**From a prompt to a working IC design environment.**

Open the cloned SiliconBoot repository in a coding agent with file, network, and terminal access, then paste this prompt:

> Find the local SiliconBoot clone and read its AGENTS.md. Install managed EDA tools, SRAM compilers, uv and isolated runtimes under `~/tools`, and PDKs under `~/pdks`, using persistent versioned locations without sudo. On macOS, always check Homebrew first for every tool, including uv: compare its current formula/cask with the latest official upstream version and native host requirements. If it matches, install through Homebrew and record its actual provider-managed paths as an exception to `~/tools`; otherwise record the reason and install the same latest version using the best upstream-supported native method, preferring an official binary or documented installer before a source build. Follow docs/installation.md for Homebrew availability, permissions, dependencies and generation retention. Do not create a workspace or scaffold a design project. Use the existing project directory from context, or the clone itself, for local `.siliconboot/` guidance and records. Use uv to manage Python environments; if uv is missing, install and verify it first through the selected provider. Install the latest official versions supported natively on this host, following the catalog, recipes and lifecycle procedures. Put symbolic links to verified upstream public binaries in `~/bin`, preserving existing files and resolving name collisions. Detect my default login shell and add `~/bin` to PATH once in its bashrc, zshrc or fish configuration, respecting custom configuration locations. Verify components and supported workflows, record exact versions and sources, and generate `.siliconboot/AGENTS.md` and `.siliconboot/ENVIRONMENT.md`. Report unsupported components, compatibility failures and dependencies that require administrator action; continue independent work without elevation. Clean up owned temporary installers after verification. I understand this changes my machine. Use at your own risk.

No installation path is required. The agent expands these paths against your home directory and discovers the repository and any existing project from context. Setup creates no workspace. Existing workspace contents remain untouched.

**Use at your own risk.** Native installation uses disk space and changes user-owned installations, binary links and the detected shell's PATH configuration. Setup uses no sudo; missing privileged dependencies are reported as blockers. SiliconBoot and the underlying tools are provided without warranty. You are responsible for your machine, permissions and backups. Never put passwords in prompts or records.

## What this repository provides

SiliconBoot is a set of prompts, a component catalog, installation recipes, and project record templates. Your agent performs the work using the selected tools' official instructions. There is no SiliconBoot executable, installer, service, agent SDK, or plugin dependency. A chat-only agent can explain the process but cannot install anything.

The default scope is the `all` [profile](catalog/profiles.md), including uv as the default Python environment manager; JupyterLab remains optional. Ask for the `analog`, `digital`, `memory`, `fpga`, or `rf` profile, or name components and PDKs to narrow it. Planned and unresolved entries must appear in the result, even when they cannot be installed. See [Python environments](docs/python-environments.md) for isolation, interpreter selection, and upstream runtime exceptions.

## Platform status

| Selected host | SiliconBoot validation status |
| --- | --- |
| Ubuntu 24.04, x86_64 | First validation target; no native installation evidence published |
| Linux ARM64 and other Linux distributions | Per-component evaluation required; unverified |
| macOS, Apple Silicon or Intel | Per-component evaluation required; unverified |
| Native Windows | Per-component evaluation required; unverified |

Catalog coverage is documentation coverage. No complete profile is currently verified. WSL2, virtual machines, containers, and translated execution must be identified separately; they do not establish native support for the physical host. See [platform policy](docs/platforms.md) and [acceptance criteria](docs/acceptance.md).

## Installation locations

Setup uses the following locations and preserves existing content. Project-relative paths refer to the existing directory selected from context, defaulting to the local clone.

| Location | Purpose |
| --- | --- |
| `~/tools/<component>/<install-key>/` | Persistent EDA tools, SRAM compilers and isolated component runtimes |
| Recorded Homebrew-managed paths on macOS | Matching latest tools installed through Homebrew; external packages with receipts under `~/tools` |
| `~/pdks/<family>/<install-key>/` | Persistent PDK families, resources and receipts |
| `~/bin/` | Symbolic links to verified upstream public executable entrypoints |
| `.siliconboot/AGENTS.md`, `.siliconboot/project.md`, `.siliconboot/ENVIRONMENT.md` | Local instructions, choices and environment setup |
| `.siliconboot/` | Local receipt references, generations, state and evidence |
| `.siliconboot/environment.lock.md` | Portable record of exact versions and build inputs |
| `runs/<run-id>/` | Generated artifacts, reports, and logs |
| `runs/<run-id>/tmp/` | Private temporary files and AppImage mountpoints for that run |

Each accepted generation records its tools, PDKs, entrypoints and checks together. Shell setup selects `~/.bashrc`, the effective zshrc, or fish's configuration according to the default login shell. Runs are created only when needed; setup does not create design-source directories. The root `.gitignore` keeps generated records, runs and legacy workspace contents local. See the [project layout](docs/project-layout.md), [shell setup](docs/project-layout.md#default-shell-path) and [AppImage temporary mount guidance](docs/project-layout.md#appimage-temporary-mounts).

## Start, inspect, or maintain an environment

- [Bootstrap guide](docs/bootstrap.md): host inspection through verified activation.
- [Operation prompts](prompts/README.md): plan, inventory, diagnose, run, upgrade, restore, rollback, and clean up.
- [Recipes](recipes/README.md): component-specific decisions and acceptance checks.
- [Memory compilers](docs/memory-compilers.md): compiler, technology port, and PDK compatibility.
- [Examples](examples/README.md): walkthroughs with explicit expected outcomes.
- [Contributing](CONTRIBUTING.md): add sources, recipes, and measured validation evidence.

For an upgrade, use the [upgrade prompt](prompts/upgrade.md). Ordinary design runs and diagnosis keep the selected versions fixed. Latest official releases and workflow compatibility are reported separately.

## License

SiliconBoot is licensed under [Apache License 2.0](LICENSE). Installed tools, PDKs, models, and generated artifacts retain their own license terms, which the agent records from their sources.
