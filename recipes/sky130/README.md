# SKY130: sky130A

Catalog ID: `sky130`; installed variant name: `sky130A`. Recipe status: experimental; no native workflow has been validated by this repository.

## Resolve and prepare

Read the [SkyWater PDK repository](https://github.com/google/skywater-pdk), [process documentation](https://skywater-pdk.readthedocs.io/en/main/) and [open_pdks SKY130 instructions](https://github.com/fossi-foundation/open-pdks/tree/main/sky130). Follow [PDK infrastructure](../pdk-infrastructure/README.md) to resolve source data, submodule revisions, builder revision and published package provenance separately. Check current upstream maturity and known limitations; a tool installation is not a process qualification.

The checked process documentation links a [FOSSi Foundation repository](https://github.com/fossi-foundation/skywater-pdk) that identifies itself as a fork of the Google repository. Record which source each builder and library actually uses. Establish any provider change from current maintainer guidance; a documentation link alone must not silently change the requested source identity.

Select the `sky130A` process variant and the libraries required by the requested workflows. Record the standard-cell library, primitive libraries, corners and optional memory data explicitly. Avoid mixing views of one library from different revisions. A technology port's `sky130` name and the installed `sky130A` variant need an explicit mapping.

PDK text and layout data may be portable, but the builder and consuming tools must run natively on the selected OS and architecture. Establish those dependencies before treating this PDK as usable. Build with open_pdks or select a provenance-matched published package; report any unavailable requested revision.

## Install and activate

Keep all built variants and shared files in the persistent family root under `~/pdks`. Expose `pdk/sky130A` through the project generation described in [project layout](../../docs/project-layout.md). Configure `PDK_ROOT`, the variant, and each tool's documented technology path through project activation instructions. The PDK has no generic executable to add to `~/bin/`.

Check that the chosen Xschem symbols, ngspice model includes, Magic technology, Netgen setup, KLayout decks and digital library views exist before enabling their respective workflows. An absent deck limits that workflow; do not manufacture it or reuse another process's rules. Project overrides and generated outputs must remain outside the immutable PDK.

## Acceptance

1. Resolve all internal links and record the source revision of each selected library. Confirm required model corners and matching Liberty, LEF, GDS and netlist views for the selected standard cells.
2. Run a small upstream PDK transistor example through Xschem and ngspice. Record its corner and finite numeric result against the example's documented expectation or a stated engineering check.
3. Use a PDK-provided layout with a reference schematic for DRC, extraction and LVS. Record each tool, rule deck and outcome separately. Run PEX only when the selected rules support it.
4. For a digital request, run [digital-flow acceptance](../digital-flow/README.md) using these same library revisions.
5. For OpenRAM, install and validate the additional SRAM technology material in its [own recipe](../openram/README.md). A PDK-delivered memory macro is not proof that a compiler works.

Complete [records](../../docs/records.md) and [validation](../../docs/validation.md). Preserve all runtime library views and family siblings during cleanup; remove only owned staging material after the linked project view passes the checks.
