# Memory compilers

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

Compiler installation is only one part of memory support. A usable combination requires a documented technology port, compatible PDK/tool revisions, the requested geometry and ports, and inspected output views. Neither compiler is validated by this repository.

## openram

- **Name / kind / aliases:** OpenRAM; compiler; OpenRAM.
- **Official sources:** [Homepage](https://openram.org/); [source repository](https://github.com/VLSIDA/OpenRAM); [installation documentation](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/basic_setup.md).
- **Discovery:** Review official releases first. Upstream-documented maintenance branch: **stable**; a source selection records its full commit. See the linked setup document.
- **Interfaces / dependencies:** Python compiler interface; installed launcher inventory pending. Dependencies to review: Supported technology port; ngspice, magic, netgen according to port.
- **Integration and validation:** Official maintained branch stable. The linked setup document states GF180 SRAM is unsupported, with an experimental ROM path; no IHP SRAM port was established. Verify a documented compiler/technology/tool tuple and all promised views.
- **Recipe:** [openram guidance](../recipes/openram/README.md).

## dffram

- **Name / kind / aliases:** DFFRAM; compiler; DFFRAM.
- **Official sources:** [Homepage](https://github.com/AUCOHL/DFFRAM); [source repository](https://github.com/AUCOHL/DFFRAM); [installation documentation](https://github.com/AUCOHL/DFFRAM#readme).
- **Discovery:** Review [official releases](https://github.com/AUCOHL/DFFRAM/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Documented Python/LibreLane plugin interface; launcher inventory pending. Dependencies to review: librelane, yosys, openroad; supported standard-cell platform.
- **Integration and validation:** Uses standard cells; upstream GF180 platform has hold-violation warnings and discourages 1RW1R configurations.
- **Recipe:** [dffram guidance](../recipes/dffram/README.md).
