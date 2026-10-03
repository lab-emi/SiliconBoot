# Memory compilers and macro acceptance

Memory readiness belongs to a specific compiler, technology port, PDK, library, tool set and requested configuration. Installing a compiler or opening a memory layout does not prove that combination works.

## Three distinct component types

| Type | What it provides | Evidence required |
| --- | --- | --- |
| [OpenRAM](../recipes/openram/README.md) | SRAM generation using a technology port and memory-specific cells | A real compile for a supported port, consistent output views, functional checks and the requested physical/timing checks. |
| [DFFRAM](../recipes/dffram/README.md) | Memory built from latch or flip-flop standard cells | A supported building-block configuration, complete implementation, functional checks and actual setup/hold results. |
| Prebuilt memory macro library | Existing fixed configurations and their views | Source and revision, matching views and corners, and the checks required by the consuming project. It supplies no compiler capability. |

Preserve these distinctions in the catalog, installation summary and project manifest. SRAM generation and ROM generation also need separate capabilities.

## Documented combinations to investigate

This table records upstream guidance checked on 2026-10-03. It is not a local validation matrix; no combination below has been executed by this repository. Recheck the exact chosen revisions during each installation or upgrade.

| Compiler | PDK/technology | Starting assessment | Next acceptance step |
| --- | --- | --- | --- |
| OpenRAM | SKY130 technology with the `sky130A` installation | Upstream lists a SKY130 port; additional SRAM technology material is required. | Resolve all cell and PDK revisions, then compile an upstream supported example. |
| OpenRAM | `gf180mcuD` SRAM | Upstream setup explicitly states SRAM generation is unsupported; experimental ROM is a separate feature. | Record SRAM as unsupported unless newer official port documentation changes this. |
| OpenRAM | `ihp-sg13g2` or `ihp-sg13cmos5l` | No port established by the checked supported-technology list. | Record the requested SRAM combination as unsupported until an official port is identified and validated. |
| DFFRAM | `sky130A` | Upstream lists latch and DFF configurations, with differing silicon-history claims. | Validate the actual size, port arrangement, building blocks and tool set. |
| DFFRAM | `gf180mcuD` | Upstream reports hold violations. | Allow only a clearly limited generation result until required timing checks pass. |
| DFFRAM | Either IHP variant | No support established by the checked platform table. | Report unsupported instead of substituting SKY130 building blocks. |

Sources: [OpenRAM technologies](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/index.md), [OpenRAM setup](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/basic_setup.md), [DFFRAM platform table](https://github.com/AUCOHL/DFFRAM#platform-support-status). A source revision becoming available does not change any local result to verified automatically.

## Plan a compile

1. Resolve the compiler, its technology or building-block package, selected PDK variant, standard-cell or bitcell libraries, model compiler and every simulation/implementation/checking dependency. Record the complete versions, revisions and native host identity.
2. Select an official example that the chosen port supports. Preserve its source and configuration provenance in the downstream project. SiliconBoot supplies instructions only; it does not bundle generator code, RTL or executable configuration templates.
3. Record dimensions, banks, read/write ports, write masks, operating conditions and requested output views. Determine which checks are required before launching the run. Select realistic small upstream examples for installation validation rather than inventing unsupported minimum dimensions.
4. Place outputs in `runs/<run-id>/artifacts/memory/`, with reports and logs in the same run. Keep source requests under `ip/memory/configs/` according to [project layout](project-layout.md). Do not generate into shared tool or PDK directories.

## Inspect outputs and outcomes

Check expected views against the compiler's selected mode, including HDL, SPICE/CDL, LEF, GDS and Liberty when promised. Record absent views explicitly; a compiler need not produce every format in every mode. Verify matching macro names, port names/order, bus widths, power connections, geometry and operating corners. Preserve output hashes and the configuration needed to reproduce the run.

Functional validation should exercise the official example's write/read behavior, address coverage and masking where applicable. Physical validation must identify the rule decks, extracted/reference circuits and report outcomes. Timing validation must identify the simulator or analyzer, characterization mode, clocks, corners, path coverage and setup/hold findings. Analytical timing models, skipped checks and generation-only modes must be visible in the result.

Use separate conclusions for installation, generation, functional verification, DRC, LVS, PEX and timing. A skipped step is `not_run`; a missing integration is unavailable or unsupported; an actual failing check is failed. Apply the overall status rules from [validation](validation.md). A smoke result is evidence for one configuration and cannot substitute for the project's full integration and signoff requirements.

## Record and retain

Use the [memory record template](../templates/records/memory.md). It supplements [installation records](records.md) with:

- Compiler and port/building-block identities; PDK variant, library and every participating tool revision.
- Host OS/architecture, native provider, persistent runtime paths and relevant environment choices.
- Request dimensions, ports, banks, masks, corners, voltages, temperatures and characterization mode.
- Exact upstream example/configuration provenance, run directory, invocation details, exit status and log paths.
- Output views and hashes, each check's result, parsed timing/physical metrics and unresolved warnings.
- Acceptance status, reviewer or design-process decision, accepted artifact locations and limitations.

Propose an entry under `ip/memory/manifests/` only after the requested acceptance gates pass or the design process explicitly accepts a documented limitation. A compiler upgrade does not overwrite a previously accepted macro. Retain its prior inputs and artifacts until the project's retention rules permit removal. Cleanup must preserve compiler source, technology cells, PDK siblings, package-manager roots and all accepted or referenced macro views.
