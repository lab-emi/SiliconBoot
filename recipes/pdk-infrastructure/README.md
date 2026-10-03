# PDK infrastructure: Ciel and open_pdks

Catalog IDs: `ciel`, `open-pdks`. Recipe status: experimental; no native installation has been validated by this repository. Use this recipe with [SKY130](../sky130/README.md), [GF180MCU](../gf180mcu/README.md) or [IHP](../ihp/README.md).

## Resolve the right layer

[Ciel](https://github.com/fossi-foundation/ciel) manages versioned PDK builds. [open_pdks](https://github.com/fossi-foundation/open-pdks) transforms foundry data into tool-specific installations. Their own revisions, a published PDK package identifier and the underlying process-data revisions are separate facts. The open_pdks documentation explains that IHP already supplies a usable directory structure, so an open_pdks build is not generally required for it.

Resolve Ciel's latest official release using its repository and linked package metadata. Resolve open_pdks through its releases or documented maintained branch, currently `main`, and record the exact commit. Then resolve every requested PDK's original sources, submodules and build recipe independently. Apply [installation](../../docs/installation.md) to each layer.

For a latest-source request, compare the complete source revision set with published package metadata. A package identified by an open_pdks commit does not by itself prove that all foundry sources are current. If provenance cannot establish equivalence, build from resolved sources or report the latest-source request as unmet. A user-selected `latest-published` channel may choose the newest published package, with the source differences recorded.

## Native installation and runtime

Read current Ciel requirements for the host. Install its Python package into a persistent isolated environment using upstream packaging; export only the console entrypoints actually provided. Preserve that environment's absolute location. Resolve open_pdks' build dependencies from each family guide, including the required layout-processing tools. Build one large family at a time when memory or disk is constrained.

Use a candidate installation area for Ciel operations. Its own active-version selection must not change another project's PDK view or the project's active generation during preparation. Record package-manager ownership and persistent cache dependencies. Use upstream supported storage options rather than relocating an environment with absolute paths.

## Layout and acceptance

Preserve the entire family root, siblings, common data, licenses and internal relative links. `PDK_ROOT` names the directory containing variants; `PDK` names the selected variant. Register the actual case-sensitive installed name, such as `sky130A`, separately from the catalog ID. This contract follows the [open_pdks layout documentation](https://github.com/fossi-foundation/open-pdks#open-pdks-format).

1. Confirm the manager's actual version and inventory without altering the active project.
2. Inspect each installed variant's device models, technology files, library views, corners and link targets. Detect missing submodules, dangling links and files that still depend on a temporary checkout.
3. Run the selected PDK recipe's real simulation and physical-check examples. A successful download establishes availability, not workflow readiness.
4. Repeat discovery and one workflow from the candidate project view in a fresh shell. Confirm outputs stay in `runs/` and source data remains unchanged.

Store source, builder and package receipts under [records](../../docs/records.md). Retain runtime data and any referenced manager objects. Cleanup may remove owned archives and disposable processing trees only after [validation](../../docs/validation.md); it must not garbage-collect shared PDK versions.
