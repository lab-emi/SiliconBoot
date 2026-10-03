# [PROJECT_NAME]

[PROJECT_PURPOSE]

## SiliconBoot managed section begins

Read [project choices]([PROJECT_ABSOLUTE_PATH]/project.md), [agent guidance]([PROJECT_ABSOLUTE_PATH]/AGENTS.md), and [environment instructions]([PROJECT_ABSOLUTE_PATH]/ENVIRONMENT.md) before using this environment.

Tools are linked through `tools`, PDKs through `pdk`, and actual public executables through `bin`. The active [manifest]([PROJECT_ABSOLUTE_PATH]/.siliconboot/current/manifest.md) records versions, providers, invocation requirements, and capabilities. The [validation record]([PROJECT_ABSOLUTE_PATH]/.siliconboot/current/validation.md) reports checks and limitations. These views all select one generation through `.siliconboot/current`.

Keep design inputs in `design` and `verification`, project overrides in `config`, memory requests in `ip/memory/configs`, and generated outputs in a unique `runs` directory. Shared tools and PDKs are immutable. Pin a concrete generation and create a run lease for long workflows, following the [run instructions]([GUIDE_ABSOLUTE_PATH]/prompts/run.md).

Current requested scope: [PROFILE_AND_COMPONENT_SCOPE]. Selected PDK and libraries: [PDK_AND_LIBRARY_SELECTION]. Environment status and limitations: [STATUS_AND_LINK_TO_EVIDENCE].

For maintenance, use the persistent [SiliconBoot guide]([GUIDE_ABSOLUTE_PATH]/README.md) and [operational prompts]([GUIDE_ABSOLUTE_PATH]/prompts/README.md). Upgrades are explicit. Restore another host from `config/environment.lock.md`; local absolute links are not portable.

Native installation is at the user's own risk and can alter host dependencies. Privileged operations require the user's authorization under the host's approval rules. Keep passwords out of all project records.

## SiliconBoot managed section ends
