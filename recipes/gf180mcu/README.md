# GF180MCU: gf180mcuD

Catalog ID: `gf180mcu`; installed variant name: `gf180mcuD`. Recipe status: experimental; no native workflow has been validated by this repository.

## Resolve and prepare

Use the [official GF180MCU repository](https://github.com/google/gf180mcu-pdk), [process documentation](https://gf180mcu-pdk.readthedocs.io/en/latest/) and [open_pdks family guide](https://github.com/fossi-foundation/open-pdks/tree/main/gf180mcu). Resolve upstream data and submodules, builder revision and package provenance according to [PDK infrastructure](../pdk-infrastructure/README.md).

The Google repository reported an archive date of 2026-09-23 when checked for this recipe. Recheck its status and any maintainer-documented successor. An archived tip can identify the newest content in that source, but must not be described as an actively maintained branch. Record a successor or community provider separately and establish its provenance before selecting it.

The requested variant is `gf180mcuD`. The [open_pdks variant description](https://github.com/fossi-foundation/open-pdks#example-usage) identifies its five-metal stack with 1.1 micrometre top metal. Preserve the variant identity through layout rules, extraction, technology LEF and tool configuration; another GF180MCU variant is not an interchangeable fallback.

Select the standard-cell library and required voltage/process/temperature corners from the actual installed data. Record these choices before a digital or memory run. Native tool support is independent of portable PDK data; resolve the builder and consuming tools for the host and record any missing native dependency.

## Install and activate

Build the selected resolved sources or obtain a matching published package. Preserve the family root and all linked siblings. Expose the exact `gf180mcuD` directory under project `pdk/` and document its configuration without changing the shared installation. Add no executable for the PDK itself.

Inspect required primitive models, Xschem symbols, Magic technology, Netgen setup, KLayout rules, library netlists and timing/physical views. Mark absent tool integrations individually. Do not infer that a successful SKY130 workflow also supports GF180MCU.

## Acceptance

1. Validate links, selected metal-stack identity, library views and all requested corners.
2. Run a small GF180MCU device simulation from upstream examples. Check loaded model names, corner selection, expected bias and numeric behavior. Keep a record of convergence and model warnings.
3. Run DRC, extraction and LVS on a matching upstream layout/schematic example using GF180MCU-specific rules. Record report counts and final comparisons independently.
4. For a digital request, perform [digital-flow acceptance](../digital-flow/README.md) with this exact variant and standard-cell library.
5. Keep memory capabilities separate. [OpenRAM's setup documentation](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/basic_setup.md) currently excludes GF180MCU SRAM compilation while describing experimental ROM work. [DFFRAM](../dffram/README.md) lists GF180MCU with a timing limitation; generating its files does not establish a timing-clean result. Recheck those upstream statements at installation time.

Store source revisions, builder settings, selected views and outcomes in [records](../../docs/records.md). Apply [validation](../../docs/validation.md) from the project view, retain runtime data and remove only owned temporary build inputs after successful checks.
