# SiliconBoot

**Agent-guided native setup for open-source IC design tools.**\
**From a prompt to a working IC design environment.**

Open the cloned SiliconBoot repository in a coding agent with file, network, and terminal access. Replace `<ABSOLUTE_INSTALL_PATH>` with the directory where you want all IC design tools, SRAM compilers, and PDKs installed, then paste this prompt:

> Find the local SiliconBoot clone and read its AGENTS.md. Create an IC design project in a folder named workspace inside the repository. Use `<ABSOLUTE_INSTALL_PATH>` as the installation root for all IC design tools, SRAM compilers and PDKs. Install the latest official versions supported natively on this host, following the catalog, recipes and lifecycle procedures. Link installations into workspace/tools/ and workspace/pdk/, and executable entrypoints into workspace/bin/. Verify components and supported workflows, record exact versions and sources, and generate workspace/AGENTS.md and workspace/ENVIRONMENT.md. Preserve existing files, report unsupported components and compatibility failures, and clean up owned temporary installers after verification. Use sudo only within my authorization and the host's approval rules. I understand this changes my machine. Use at your own risk.

The installation root is the only path you need to provide. The agent discovers the repository location and uses its `workspace/` folder for the IC project.

**Use at your own risk.** Native installation can change system packages, use substantial disk space and require sudo. Review the planned changes and grant only the permissions you intend to allow. SiliconBoot and the underlying tools are provided without warranty. You are responsible for your machine, permissions and backups. This notice does not grant sudo permission; never put passwords in prompts or records.

## What this repository provides

SiliconBoot is a set of prompts, a component catalog, installation recipes, and project record templates. Your agent performs the work using the selected tools' official instructions. There is no SiliconBoot executable, installer, service, agent SDK, or plugin dependency. A chat-only agent can explain the process but cannot install anything.

The default scope is the complete [catalog](catalog/README.md). Ask for the `analog`, `digital`, `memory`, `fpga`, or `rf` [profile](catalog/profiles.md), or name components and PDKs to narrow it. Planned and unresolved entries must appear in the result, even when they cannot be installed.

## Platform status

| Selected host | SiliconBoot validation status |
| --- | --- |
| Ubuntu 24.04, x86_64 | First validation target; no native installation evidence published |
| Linux ARM64 and other Linux distributions | Per-component evaluation required; unverified |
| macOS, Apple Silicon or Intel | Per-component evaluation required; unverified |
| Native Windows | Per-component evaluation required; unverified |

Catalog coverage is documentation coverage. No complete profile is currently verified. WSL2, virtual machines, containers, and translated execution must be identified separately; they do not establish native support for the physical host. See [platform policy](docs/platforms.md) and [acceptance criteria](docs/acceptance.md).

## The resulting project

All project paths below are relative to `workspace/` inside the local SiliconBoot clone.

| Location | Purpose |
| --- | --- |
| `AGENTS.md`, `project.md`, `ENVIRONMENT.md` | Project instructions, choices, and environment setup |
| `tools/`, `pdk/`, `bin/` | Links into one active generation of persistent installations |
| `design/`, `verification/`, `config/` | User sources, checks, and project settings |
| `ip/memory/` | Memory requests and accepted macro records |
| `runs/<run-id>/` | Generated artifacts, reports, and logs |
| `.siliconboot/` | Local receipts, generations, state, and evidence |
| `config/environment.lock.md` | Portable record of exact versions and build inputs |

Installations live under your chosen installation root in versioned tool and PDK directories. Each accepted generation records its tools, PDKs, entrypoints, and checks together. Keep the local `workspace/` contents out of SiliconBoot commits. See the [project layout](docs/project-layout.md).

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
