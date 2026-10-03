# Orchestration and libraries

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## edalize

- **Name / kind / aliases:** Edalize; library; Edalize.
- **Official sources:** [Homepage](https://github.com/olofk/edalize); [source repository](https://github.com/olofk/edalize); [installation documentation](https://github.com/olofk/edalize#readme).
- **Discovery:** Review [official releases](https://github.com/olofk/edalize/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Selected EDA backend tools.
- **Integration and validation:** Generate a backend build description and execute a small checked design.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## fusesoc

- **Name / kind / aliases:** FuseSoC; tool; FuseSoC.
- **Official sources:** [Homepage](https://github.com/olofk/fusesoc); [source repository](https://github.com/olofk/fusesoc); [installation documentation](https://github.com/olofk/fusesoc#readme).
- **Discovery:** Review [official releases](https://github.com/olofk/fusesoc/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** fusesoc. Dependencies to review: edalize; selected EDA tools.
- **Integration and validation:** Resolve a small core and run the selected backend with pinned dependencies.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## siliconcompiler

- **Name / kind / aliases:** SiliconCompiler; tool; SiliconCompiler.
- **Official sources:** [Homepage](https://github.com/siliconcompiler/siliconcompiler); [source repository](https://github.com/siliconcompiler/siliconcompiler); [installation documentation](https://github.com/siliconcompiler/siliconcompiler#readme).
- **Discovery:** Review [official releases](https://github.com/siliconcompiler/siliconcompiler/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** sc; remaining public tools pending inventory. Dependencies to review: Selected EDA backend tools; Python.
- **Integration and validation:** Inspect the task graph and verify a small flow's artifacts and reports.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## libman

- **Name / kind / aliases:** LibMan; tool; LibMan.
- **Official sources:** [Homepage](https://github.com/IHP-GmbH/LibMan); [source repository](https://github.com/IHP-GmbH/LibMan); [installation documentation](https://github.com/IHP-GmbH/LibMan#readme).
- **Discovery:** Review [official releases](https://github.com/IHP-GmbH/LibMan/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** GUI launcher inventory pending. Dependencies to review: Qt; design-library format; selected view editors.
- **Integration and validation:** Official IC design-library manager from IHP; open and save a fixture library and check view-editor integration.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## najaeda

- **Name / kind / aliases:** najaeda; library; najaeda.
- **Official sources:** [Homepage](https://github.com/najaeda/naja); [source repository](https://github.com/najaeda/naja); [installation documentation](https://github.com/najaeda/naja#readme).
- **Discovery:** Review [official releases](https://github.com/najaeda/naja/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python/native library. Dependencies to review: Native Naja and Python ABI.
- **Integration and validation:** Load and transform a netlist; confirm connectivity and serialization round trip.
- **License evidence:** Apache-2.0. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## vlsirtools

- **Name / kind / aliases:** vlsirtools; library; vlsirtools.
- **Official sources:** [Homepage](https://github.com/Vlsir/Vlsir); [source repository](https://github.com/Vlsir/Vlsir); [installation documentation](https://github.com/Vlsir/Vlsir#readme).
- **Discovery:** Review [official releases](https://github.com/Vlsir/Vlsir/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Vlsir schemas; selected simulator backend.
- **Integration and validation:** Record schema revisions and test serialization plus a backend simulation.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## osic-multitool

- **Name / kind / aliases:** OSIC Multitool; tool; OSIC Multitool.
- **Official sources:** [Homepage](https://github.com/iic-jku/osic-multitool); [source repository](https://github.com/iic-jku/osic-multitool); [installation documentation](https://github.com/iic-jku/osic-multitool#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/osic-multitool/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Inventory pending; do not export every source file. Dependencies to review: Depends on the selected utility and design flow.
- **Integration and validation:** Review each utility's paths and external tool assumptions before any native use.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).
