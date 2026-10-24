# Installation recipes

Recipes are instructions for an agent, expressed in prose. Read the component's [catalog entry](../catalog/README.md) for identity and source policy, then the applicable recipe and [installation procedure](../docs/installation.md). Resolve exact build commands from the selected upstream revision's documentation at execution time. SiliconBoot does not provide an installer or custom launchers.

## Recipe index

| Area | Recipes |
| --- | --- |
| Python setup | [uv bootstrap](uv/README.md), [Python environment policy](../docs/python-environments.md) |
| Analog foundation | [Xschem](xschem/README.md), [ngspice](ngspice/README.md), [other analog tools and libraries](analog/README.md) |
| Layout and verification | [KLayout](klayout/README.md), [Magic](magic/README.md), [Netgen](netgen/README.md), [layout tools and plugins](layout/README.md) |
| PDKs | [ciel and open_pdks](pdk-infrastructure/README.md), [SKY130](sky130/README.md), [GF180MCU](gf180mcu/README.md), [IHP](ihp/README.md) |
| Digital | [Yosys](yosys/README.md), [HDL tools](hdl/README.md), [simulation and verification](verification/README.md), [formal tools](formal/README.md), [implementation flows](digital-flow/README.md) |
| Memory | [OpenRAM](openram/README.md), [DFFRAM](dffram/README.md) |
| Other workflows | [EM and RF](rf/README.md), [FPGA](fpga/README.md), [SoC and RISC-V](soc/README.md), [orchestration](orchestration/README.md) |

Grouped recipes supply shared procedures and per-component checks. An unresolved catalog identity or missing native path remains planned even when a group recipe exists. No recipe here constitutes native validation evidence by itself.

## Apply to every recipe

1. Confirm the catalog identity against the official homepage, repository and installation page. Recheck redirects and current maintenance status. Establish the release channel and exact immutable revision; do not assume a tag or default branch is a release.
2. Verify a native provider for the selected host, its license terms, package identity, architecture, and dependency requirements. On macOS, always check current Homebrew formulae/casks first for tools, including uv, and use a matching latest native package under [the macOS policy](../docs/installation.md#macos-check-homebrew-first). Otherwise record why and prefer an official matching binary or upstream-documented installer before a native source build. Freeze all inputs and fallback evidence in the resolution record. A package is only “latest” if its actual version matches the official selection.
3. Record dependency order, host compiler and library ABIs, needed GUI support, estimated disk/memory requirements from available evidence, and bounded build concurrency. Report unmeasured resources as unknown. Do not infer native support from a container image.
4. Build or install managed components at the final persistent prefix under `~/tools` for tools, SRAM compilers and isolated runtimes, or `~/pdks` for PDKs. Homebrew tools remain external at recorded provider-managed paths, with receipts in the tool store and concrete generation targets. Use no sudo; record missing privileged dependencies and continue independent components. Do not create a workspace or design scaffold. Preserve source and resources needed at runtime. Use uv to create and manage isolated Python environments, installing uv first if missing; follow the [Python environment policy](../docs/python-environments.md) for interpreter selection and upstream exceptions. Use component-scoped Ruby/Rust package locations as applicable. Coupled components may share an installation when upstream requires it; record that exception and every member revision.
5. Derive public entrypoints from the installed upstream package. Verify target paths, permissions, architecture, interpreter and resources. Link upstream-installed launchers when available; otherwise document a direct upstream executable/interpreter invocation and its environment. Do not write a SiliconBoot wrapper to hide missing integration.
6. Perform identity checks, a real component check and requested workflow checks. Run outside the build tree and in a fresh shell. Follow [validation](../docs/validation.md) for expected values, engineering reports and missing checks.
7. Write a [receipt](../docs/records.md), including source, license evidence, dependency and build inputs, entrypoints, verification results and owned temporary paths. Only verified entrypoints enter the candidate generation. Publish individual verified binary symlinks in `~/bin` through that generation, preserving existing entries; apply the single [default-shell PATH update](../docs/project-layout.md#default-shell-path) after activation. Follow the lifecycle activation rules; preserve failures as diagnostics.
8. Use [cleanup](../docs/cleanup.md) after successful checks. Keep runtime environments, technology data, installed package metadata, licenses, logs and upstream examples needed for future verification. Recheck operation from a clean working directory afterward.

Resolve uncertainties before the affected action. Report an unresolved source as planned, an unavailable native route as unsupported, and an unsatisfied dependency as blocked; keep unrelated components progressing. Never treat a successful import as a complete tool/PDK workflow.
