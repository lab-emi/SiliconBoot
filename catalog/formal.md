# Synthesis and formal verification

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## yosys

- **Name / kind / aliases:** Yosys; tool; Yosys.
- **Official sources:** [Homepage](https://github.com/YosysHQ/yosys); [source repository](https://github.com/YosysHQ/yosys); [installation documentation](https://github.com/YosysHQ/yosys#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/yosys/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** yosys, yosys-config; bundled ABC path needs inventory. Dependencies to review: abc; native build dependencies.
- **Integration and validation:** Record ABC revision and synthesize a checked RTL fixture.
- **Recipe:** [yosys guidance](../recipes/yosys/README.md).

## abc

- **Name / kind / aliases:** ABC; tool; ABC.
- **Official sources:** [Homepage](https://github.com/berkeley-abc/abc); [source repository](https://github.com/berkeley-abc/abc); [installation documentation](https://github.com/berkeley-abc/abc#readme).
- **Discovery:** Review [official releases](https://github.com/berkeley-abc/abc/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** abc; Yosys may provide yosys-abc instead. Dependencies to review: Native compiler.
- **Integration and validation:** Distinguish standalone ABC from the copy coupled to a Yosys build.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## kepler-formal

- **Name / kind / aliases:** Kepler-formal; tool; Kepler-formal.
- **Official sources:** [Homepage](https://github.com/keplertech/kepler-formal); [source repository](https://github.com/keplertech/kepler-formal); [installation documentation](https://github.com/keplertech/kepler-formal#readme).
- **Discovery:** Review [official releases](https://github.com/keplertech/kepler-formal/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** kepler-formal. Dependencies to review: Native libraries; Naja data interfaces where used.
- **Integration and validation:** Prove an equivalent pair and detect an intentionally inequivalent pair.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## ghdl-yosys-plugin

- **Name / kind / aliases:** ghdl-yosys-plugin; plugin; ghdl-yosys-plugin.
- **Official sources:** [Homepage](https://github.com/ghdl/ghdl-yosys-plugin); [source repository](https://github.com/ghdl/ghdl-yosys-plugin); [installation documentation](https://github.com/ghdl/ghdl-yosys-plugin#readme).
- **Discovery:** Review [official releases](https://github.com/ghdl/ghdl-yosys-plugin/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Yosys-loaded plugin. Dependencies to review: ghdl, yosys.
- **Integration and validation:** Coupled group yosys-plugins: rebuild against both exact native APIs.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## yosys-slang

- **Name / kind / aliases:** yosys-slang; plugin; sv-elab; slang-yosys-plugin.
- **Official sources:** [Homepage](https://github.com/povik/sv-elab); [source repository](https://github.com/povik/sv-elab); [installation documentation](https://github.com/povik/sv-elab#readme).
- **Source migration:** The previously recorded [repository](https://github.com/povik/yosys-slang) redirects to the canonical source above; preserve this provenance in any installation record.
- **Discovery:** Review [official releases](https://github.com/povik/sv-elab/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Yosys-loaded plugin. Dependencies to review: yosys, slang.
- **Integration and validation:** The repository now redirects to sv-elab, integrated into Yosys from v0.67; an external plugin can override that integration. Record the actual provider and supported version range.
- **License evidence:** ISC, with embedded dependencies carrying their own notices. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## eqy

- **Name / kind / aliases:** EQY; tool; EQY.
- **Official sources:** [Homepage](https://github.com/YosysHQ/eqy); [source repository](https://github.com/YosysHQ/eqy); [installation documentation](https://github.com/YosysHQ/eqy#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/eqy/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** eqy. Dependencies to review: yosys, sby; selected solvers.
- **Integration and validation:** Check both equivalent and inequivalent RTL pairs and parse proof results.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## sby

- **Name / kind / aliases:** SBY; tool; SymbiYosys.
- **Official sources:** [Homepage](https://github.com/YosysHQ/sby); [source repository](https://github.com/YosysHQ/sby); [installation documentation](https://github.com/YosysHQ/sby#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/sby/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** sby. Dependencies to review: yosys; solver selected by proof engine.
- **Integration and validation:** Run a proof with a known result and record solver versions.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## mcy

- **Name / kind / aliases:** MCY; tool; MCY.
- **Official sources:** [Homepage](https://github.com/YosysHQ/mcy); [source repository](https://github.com/YosysHQ/mcy); [installation documentation](https://github.com/YosysHQ/mcy#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/mcy/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** mcy. Dependencies to review: yosys; selected simulator or proof engine.
- **Integration and validation:** Generate mutations and verify a known detected mutation.
- **Recipe:** [formal guidance](../recipes/formal/README.md).

## yices2

- **Name / kind / aliases:** Yices 2; tool; Yices 2.
- **Official sources:** [Homepage](https://github.com/SRI-CSL/yices2); [source repository](https://github.com/SRI-CSL/yices2); [installation documentation](https://github.com/SRI-CSL/yices2#readme).
- **Discovery:** Review [official releases](https://github.com/SRI-CSL/yices2/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** yices, yices-smt2; remaining public tools pending inventory. Dependencies to review: Native arithmetic libraries.
- **Integration and validation:** Solve both satisfiable and unsatisfiable cases and preserve solver licensing notices.
- **Recipe:** [formal guidance](../recipes/formal/README.md).
