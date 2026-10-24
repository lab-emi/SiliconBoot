# [PROJECT_NAME]

[PROJECT_PURPOSE]

## SiliconBoot managed section begins

Read [project choices]([PROJECT_ABSOLUTE_PATH]/.siliconboot/project.md), [agent guidance]([PROJECT_ABSOLUTE_PATH]/.siliconboot/AGENTS.md), and [environment instructions]([PROJECT_ABSOLUTE_PATH]/.siliconboot/ENVIRONMENT.md) before using this environment.

Tools live under [TOOLS_ABSOLUTE_PATH] and PDKs under [PDKS_ABSOLUTE_PATH]. The generation's `tools` and `pdk` views identify exact installations. Public executable symlinks live in [BIN_ABSOLUTE_PATH], expanded from `~/bin`, with PATH configured for the detected default login shell. The active [manifest]([PROJECT_ABSOLUTE_PATH]/.siliconboot/current/manifest.md) records versions, providers, invocation requirements, and capabilities. The [validation record]([PROJECT_ABSOLUTE_PATH]/.siliconboot/current/validation.md) reports checks and limitations. These views all select one generation through `.siliconboot/current`.

Setup creates no workspace or design scaffold and preserves root project instructions. During design work, keep design inputs in `design` and `verification`, project overrides in `config`, memory requests in `ip/memory/configs`, and generated outputs in a unique `runs` directory. Shared tools and PDKs are immutable. Pin a concrete generation and create a run lease for long workflows, following the [run instructions]([GUIDE_ABSOLUTE_PATH]/prompts/run.md).

Current requested scope: [PROFILE_AND_COMPONENT_SCOPE]. Selected PDK and libraries: [PDK_AND_LIBRARY_SELECTION]. Environment status and limitations: [STATUS_AND_LINK_TO_EVIDENCE].

For maintenance, use the persistent [SiliconBoot guide]([GUIDE_ABSOLUTE_PATH]/README.md) and [operational prompts]([GUIDE_ABSOLUTE_PATH]/prompts/README.md). Upgrades are explicit. Restore another host from `.siliconboot/environment.lock.md`; local absolute links are not portable.

Native installation is at the user's own risk and changes user-owned installations and shell PATH configuration. Setup uses no sudo; privileged dependency blockers are recorded for separate administrator action. Keep passwords out of all project records.

## SiliconBoot managed section ends
