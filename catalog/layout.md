# Layout and KLayout extensions

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

The named KLayout extensions are listed separately. The additional Productivity Suite components below come from its [own documentation](https://iic-jku.github.io/klayout-productivity-suite/doc/doc.html). They are individually versioned sources even when a collection installs them together. KLayout Salt is a distribution mechanism; the phrase “other Salt plugins” does not identify a fixed set of packages. That unnamed scope remains unresolved. Do not install every package available through a registry.

## klayout

- **Name / kind / aliases:** KLayout; tool; KLayout.
- **Official sources:** [Homepage](https://www.klayout.de/); [source repository](https://github.com/KLayout/klayout); [installation documentation](https://www.klayout.de/build.html).
- **Discovery:** Review [official releases](https://github.com/KLayout/klayout/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** klayout. Dependencies to review: Qt; optional Python/Ruby interfaces.
- **Integration and validation:** Open and round-trip a tiny layout; validate DRC/LVS using the exact PDK decks.
- **Recipe:** [klayout guidance](../recipes/klayout/README.md).

## magic

- **Name / kind / aliases:** Magic; tool; Magic.
- **Official sources:** [Homepage](http://opencircuitdesign.com/magic/); [source repository](https://github.com/RTimothyEdwards/magic); [installation documentation](http://opencircuitdesign.com/magic/install.html).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/magic/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** magic. Dependencies to review: Tcl/Tk; technology files.
- **Integration and validation:** Check layout, extraction and known DRC outcomes using the selected technology.
- **Recipe:** [magic guidance](../recipes/magic/README.md).

## netgen

- **Name / kind / aliases:** Netgen LVS; tool; Netgen LVS.
- **Official sources:** [Homepage](http://opencircuitdesign.com/netgen/); [source repository](https://github.com/RTimothyEdwards/netgen); [installation documentation](http://opencircuitdesign.com/netgen/index.html).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/netgen/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** netgen. Dependencies to review: Tcl; LVS setup for the selected PDK.
- **Integration and validation:** Identity is the LVS comparator; verify matching and deliberately mismatching netlists.
- **Recipe:** [netgen guidance](../recipes/netgen/README.md).

## cvc

- **Name / kind / aliases:** CVC circuit validity checker; tool; CVC circuit validity checker.
- **Official sources:** [Homepage](https://github.com/d-m-bailey/cvc); [source repository](https://github.com/d-m-bailey/cvc); [installation documentation](https://github.com/d-m-bailey/cvc#readme).
- **Discovery:** Review [official releases](https://github.com/d-m-bailey/cvc/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Native ERC executable; command inventory pending. Dependencies to review: Device/power rules for the selected technology.
- **Integration and validation:** Identity is circuit validity/ERC software; inspect errors from a known electrical violation.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## gds3d

- **Name / kind / aliases:** GDS3D; tool; GDS3D.
- **Official sources:** [Homepage](https://github.com/trilomix/GDS3D); [source repository](https://github.com/trilomix/GDS3D); [installation documentation](https://github.com/trilomix/GDS3D#readme).
- **Discovery:** Review [official releases](https://github.com/trilomix/GDS3D/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** GDS3D; confirm installed capitalization. Dependencies to review: Native graphics libraries and process stack.
- **Integration and validation:** Open known geometry and confirm the process-layer stack.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## gdscheck

- **Name / kind / aliases:** gdscheck; tool; gdscheck.
- **Official sources:** [Homepage](https://github.com/aesc-silicon/gdscheck); [source repository](https://github.com/aesc-silicon/gdscheck); [installation documentation](https://github.com/aesc-silicon/gdscheck#readme).
- **Discovery:** Review [official releases](https://github.com/aesc-silicon/gdscheck/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** gdscheck. Dependencies to review: Rust build dependencies; selected rule decks.
- **Integration and validation:** Inspect rule-deck coverage and expected violations; bundled rules do not prove signoff completeness.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## gdsfill

- **Name / kind / aliases:** gdsfill; tool; gdsfill.
- **Official sources:** [Homepage](https://github.com/aesc-silicon/gdsfill); [source repository](https://github.com/aesc-silicon/gdsfill); [installation documentation](https://github.com/aesc-silicon/gdsfill#readme).
- **Discovery:** Review [official releases](https://github.com/aesc-silicon/gdsfill/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Entrypoint discovery pending. Dependencies to review: Rust/Python build path and selected fill rules.
- **Integration and validation:** Measure added geometry and density while protecting existing design data.
- **License evidence:** AGPL-3.0-or-later. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## gdsfactory

- **Name / kind / aliases:** gdsfactory; library; gdsfactory.
- **Official sources:** [Homepage](https://github.com/gdsfactory/gdsfactory); [source repository](https://github.com/gdsfactory/gdsfactory); [installation documentation](https://github.com/gdsfactory/gdsfactory#readme).
- **Discovery:** Review [official releases](https://github.com/gdsfactory/gdsfactory/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library; CLI inventory pending. Dependencies to review: klayout and Python dependencies according to selected release.
- **Integration and validation:** Generate and reopen a known cell; record technology and PCell dependencies.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## gdspy

- **Name / kind / aliases:** gdspy; library; gdspy.
- **Official sources:** [Homepage](https://github.com/heitzmann/gdspy); [source repository](https://github.com/heitzmann/gdspy); [installation documentation](https://github.com/heitzmann/gdspy#readme).
- **Discovery:** Review [official releases](https://github.com/heitzmann/gdspy/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Native extension and Python ABI.
- **Integration and validation:** Generate and read back a small GDS layout with matching units and cell names.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-pex

- **Name / kind / aliases:** klayout-pex; plugin; klayout-pex.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-pex); [source repository](https://github.com/iic-jku/klayout-pex); [installation documentation](https://github.com/iic-jku/klayout-pex#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-pex/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Entrypoint discovery pending. Dependencies to review: klayout; extraction backend and selected PDK.
- **Integration and validation:** Record extractor and deck versions; inspect a known parasitic result.
- **License evidence:** GPL-3.0-or-later. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klive

- **Name / kind / aliases:** klive; plugin; klive.
- **Official sources:** [Homepage](https://github.com/gdsfactory/klive); [source repository](https://github.com/gdsfactory/klive); [installation documentation](https://github.com/gdsfactory/klive#readme).
- **Discovery:** Review [official releases](https://github.com/gdsfactory/klive/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin; no standalone executable required. Dependencies to review: klayout; gdsfactory integration when selected.
- **Integration and validation:** Check live-view updates inside the correct KLayout runtime.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## xsection

- **Name / kind / aliases:** xsection; plugin; xsection.
- **Official sources:** [Homepage](https://github.com/klayoutmatthias/xsection); [source repository](https://github.com/klayoutmatthias/xsection); [installation documentation](https://github.com/klayoutmatthias/xsection#readme).
- **Discovery:** Review [official releases](https://github.com/klayoutmatthias/xsection/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; process cross-section definition.
- **Integration and validation:** Generate a section with expected layer order and dimensions.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-productivity-suite

- **Name / kind / aliases:** KLayout Productivity Suite; plugin; KLayout Productivity Suite.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-productivity-suite); [source repository](https://github.com/iic-jku/klayout-productivity-suite); [installation documentation](https://github.com/iic-jku/klayout-productivity-suite#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-productivity-suite/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin collection. Dependencies to review: klayout; documented individual plugins.
- **Integration and validation:** Resolve each constituent separately; a collection page is not evidence of each plugin's installation.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-vector-file-export-cli

- **Name / kind / aliases:** KLayout Vector File Export CLI; tool; KLayout Vector File Export CLI.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-vector-file-export-cli); [source repository](https://github.com/iic-jku/klayout-vector-file-export-cli); [installation documentation](https://github.com/iic-jku/klayout-vector-file-export-cli#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-vector-file-export-cli/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** klayout-vector-export. Dependencies to review: klayout, klayout-vector-file-export.
- **Integration and validation:** Export a known layout and check output dimensions and selected layers.
- **License evidence:** GPL-3.0-or-later. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-align-tool

- **Name / kind / aliases:** KLayout Align Tool; plugin; KLayout Align Tool.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-align-tool); [source repository](https://github.com/iic-jku/klayout-align-tool); [installation documentation](https://github.com/iic-jku/klayout-align-tool#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-align-tool/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; plugin dependencies from upstream metadata.
- **Integration and validation:** Align a fixture and compare resulting geometry with expected coordinates.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-auto-backup

- **Name / kind / aliases:** KLayout Auto Backup; plugin; KLayout Auto Backup.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-auto-backup); [source repository](https://github.com/iic-jku/klayout-auto-backup); [installation documentation](https://github.com/iic-jku/klayout-auto-backup#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-auto-backup/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout.
- **Integration and validation:** Verify a recoverable backup in a project-owned location without changing user retention settings.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-layer-shortcuts

- **Name / kind / aliases:** KLayout Layer Shortcuts; plugin; KLayout Layer Shortcuts.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-layer-shortcuts); [source repository](https://github.com/iic-jku/klayout-layer-shortcuts); [installation documentation](https://github.com/iic-jku/klayout-layer-shortcuts#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-layer-shortcuts/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; matching process layer mapping.
- **Integration and validation:** Check selected shortcuts against the active technology layer numbers.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-library-manager

- **Name / kind / aliases:** KLayout Library Manager; plugin; KLayout Library Manager.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-library-manager); [source repository](https://github.com/iic-jku/klayout-library-manager); [installation documentation](https://github.com/iic-jku/klayout-library-manager#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-library-manager/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; configured cell libraries.
- **Integration and validation:** Load and instantiate a known library cell; keep user library configuration local to the project.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-move-tool

- **Name / kind / aliases:** KLayout Move Tool; plugin; KLayout Move Tool.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-move-tool); [source repository](https://github.com/iic-jku/klayout-move-tool); [installation documentation](https://github.com/iic-jku/klayout-move-tool#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-move-tool/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; plugin dependencies from upstream metadata.
- **Integration and validation:** Move a fixture by a known offset and check its resulting geometry.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-netlist-import

- **Name / kind / aliases:** KLayout Netlist Import; plugin; KLayout Netlist Import.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-netlist-import); [source repository](https://github.com/iic-jku/klayout-netlist-import); [installation documentation](https://github.com/iic-jku/klayout-netlist-import#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-netlist-import/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; matching PCells and process mapping.
- **Integration and validation:** Import a small netlist and check device parameters and connectivity.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-pin-tool

- **Name / kind / aliases:** KLayout Pin Tool; plugin; KLayout Pin Tool.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-pin-tool); [source repository](https://github.com/iic-jku/klayout-pin-tool); [installation documentation](https://github.com/iic-jku/klayout-pin-tool#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-pin-tool/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; process pin-layer mapping.
- **Integration and validation:** Create known pins and verify names, layers and geometry.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-plugin-utils

- **Name / kind / aliases:** KLayout Plugin Utils; library; KLayout Plugin Utils.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-plugin-utils); [source repository](https://github.com/iic-jku/klayout-plugin-utils); [installation documentation](https://github.com/iic-jku/klayout-plugin-utils#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-plugin-utils/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout-loaded utility library. Dependencies to review: klayout; embedded Python ABI.
- **Integration and validation:** Verify through each consuming plugin; no standalone executable is required.
- **Recipe:** [layout guidance](../recipes/layout/README.md).

## klayout-vector-file-export

- **Name / kind / aliases:** KLayout Vector File Export; plugin; KLayout Vector File Export.
- **Official sources:** [Homepage](https://github.com/iic-jku/klayout-vector-file-export); [source repository](https://github.com/iic-jku/klayout-vector-file-export); [installation documentation](https://github.com/iic-jku/klayout-vector-file-export#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/klayout-vector-file-export/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** KLayout plugin. Dependencies to review: klayout; selected process mapping.
- **Integration and validation:** Export a small layout and check layer selection, scale and labels.
- **Recipe:** [layout guidance](../recipes/layout/README.md).
