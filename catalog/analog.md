# Analog and schematic tools

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## xschem

- **Name / kind / aliases:** Xschem; tool; Xschem.
- **Official sources:** [Homepage](https://xschem.sourceforge.io/stefan/index.html); [source repository](https://codeberg.org/stef_xschem/xschem); [installation documentation](https://xschem.sourceforge.io/stefan/xschem_man/xschem_man.html).
- **Discovery:** The official homepage identifies primary development in repo.hu SVN and a Codeberg mirror. Review that migration before selecting a release or snapshot. Maintained branch and SVN-to-Git revision mapping remain unknown.
- **Interfaces / dependencies:** xschem. Dependencies to review: ngspice (optional simulator).
- **Integration and validation:** Schematic capture; confirm the current official source migration before resolution.
- **Recipe:** [xschem guidance](../recipes/xschem/README.md).

## xcircuit

- **Name / kind / aliases:** XCircuit; tool; XCircuit.
- **Official sources:** [Homepage](http://opencircuitdesign.com/xcircuit/); [source repository](https://github.com/RTimothyEdwards/XCircuit); [installation documentation](https://github.com/RTimothyEdwards/XCircuit#readme).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/XCircuit/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** xcircuit. Dependencies to review: Tcl/Tk and display libraries.
- **Integration and validation:** Draw and reopen a schematic with labels and net connectivity.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## schemdraw

- **Name / kind / aliases:** Schemdraw; library; Schemdraw.
- **Official sources:** [Homepage](https://github.com/cdelker/schemdraw); [source repository](https://github.com/cdelker/schemdraw); [installation documentation](https://github.com/cdelker/schemdraw#readme).
- **Discovery:** Review [official releases](https://github.com/cdelker/schemdraw/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library; no executable required. Dependencies to review: Python and drawing backend.
- **Integration and validation:** Render a small circuit and check its image dimensions and connectivity labels.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## ngspice

- **Name / kind / aliases:** ngspice; tool; ngspice.
- **Official sources:** [Homepage](https://ngspice.sourceforge.io/); [source repository](https://sourceforge.net/p/ngspice/ngspice/); [installation documentation](https://ngspice.sourceforge.io/download.html).
- **Discovery:** Use the official stable-release downloads page; nightly and development snapshots are separate channels. Maintained source branch is unknown. Official Linux binary availability must be reviewed independently from Windows assets.
- **Interfaces / dependencies:** ngspice. Dependencies to review: OSDI model compiler only when a selected model requires it.
- **Integration and validation:** Check circuit values and model loading; stable and development snapshots are distinct channels.
- **Recipe:** [ngspice guidance](../recipes/ngspice/README.md).

## xyce

- **Name / kind / aliases:** Xyce; tool; Xyce.
- **Official sources:** [Homepage](https://xyce.sandia.gov/); [source repository](https://github.com/Xyce/Xyce); [installation documentation](https://xyce.sandia.gov/documentation-tutorials/).
- **Discovery:** Review [official releases](https://github.com/Xyce/Xyce/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Xyce. Dependencies to review: Native numerical libraries; optional MPI; adms when required for device generation.
- **Integration and validation:** Numerical-library, MPI and compiled-device ABI must match the native host.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## vacask

- **Name / kind / aliases:** VacasK; tool; VacasK.
- **Official sources:** [Homepage](https://codeberg.org/arpadbuermen/VACASK); [source repository](https://codeberg.org/arpadbuermen/VACASK); [installation documentation](https://codeberg.org/arpadbuermen/VACASK#readme).
- **Discovery:** Review the linked upstream release/download documentation. Release policy and maintained branch **unknown**; resolve them before selecting a snapshot.
- **Interfaces / dependencies:** vacask. Dependencies to review: openvaf-reloaded; native numerical libraries.
- **Integration and validation:** Keep device libraries with the simulator and record the OSDI interface revision.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## qucs-s

- **Name / kind / aliases:** Qucs-S; tool; Qucs-S.
- **Official sources:** [Homepage](https://github.com/ra3xdh/qucs_s); [source repository](https://github.com/ra3xdh/qucs_s); [installation documentation](https://github.com/ra3xdh/qucs_s#readme).
- **Discovery:** Review [official releases](https://github.com/ra3xdh/qucs_s/releases) and upstream tag policy. Observed default branch: **current**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** qucs-s. Dependencies to review: ngspice or xyce; Qt.
- **Integration and validation:** Check the selected backend independently from schematic-editor startup.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## openvaf-reloaded

- **Name / kind / aliases:** OpenVAF-ReLoaded; compiler; OpenVAF-ReLoaded.
- **Official sources:** [Homepage](https://github.com/OpenVAF/OpenVAF-Reloaded); [source repository](https://github.com/OpenVAF/OpenVAF-Reloaded); [installation documentation](https://github.com/OpenVAF/OpenVAF-Reloaded#readme).
- **Discovery:** Review [official releases](https://github.com/OpenVAF/OpenVAF-Reloaded/releases) and upstream tag policy. Observed default branch: **mob**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** openvaf. Dependencies to review: Rust/LLVM build dependencies.
- **Integration and validation:** Compile a model for the native simulator ABI and load it in a numerical test.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## adms

- **Name / kind / aliases:** ADMS; compiler; ADMS.
- **Official sources:** [Homepage](https://github.com/Qucs/ADMS); [source repository](https://github.com/Qucs/ADMS); [installation documentation](https://github.com/Qucs/ADMS#readme).
- **Discovery:** Review [official releases](https://github.com/Qucs/ADMS/releases) and upstream tag policy. Observed default branch: **develop**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** admsXml. Dependencies to review: XML/template build dependencies.
- **Integration and validation:** Generated device code must be rebuilt with its target simulator.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## cace

- **Name / kind / aliases:** CACE; tool; CACE.
- **Official sources:** [Homepage](https://github.com/fossi-foundation/cace); [source repository](https://github.com/fossi-foundation/cace); [installation documentation](https://github.com/fossi-foundation/cace#readme).
- **Discovery:** Review [official releases](https://github.com/fossi-foundation/cace/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** cace. Dependencies to review: xschem, ngspice; magic, netgen and klayout according to checks.
- **Integration and validation:** Run one characterized circuit; inspect measurement limits and completion status.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## charlib

- **Name / kind / aliases:** CharLib; tool; CharLib.
- **Official sources:** [Homepage](https://github.com/stineje/CharLib); [source repository](https://github.com/stineje/CharLib); [installation documentation](https://github.com/stineje/CharLib#readme).
- **Discovery:** Review [official releases](https://github.com/stineje/CharLib/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Entrypoint discovery pending. Dependencies to review: ngspice; Python.
- **Integration and validation:** Characterize one supported cell and inspect the Liberty tables and units.
- **License evidence:** GPL-2.0 (package metadata; check selected source revision). Retain the selected revision’s own license and dependency notices.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## chipify

- **Name / kind / aliases:** Chipify; tool; Chipify.
- **Official sources:** [Homepage](https://github.com/santihofi/chipify); [source repository](https://github.com/santihofi/chipify); [installation documentation](https://github.com/santihofi/chipify#readme).
- **Discovery:** Review [official releases](https://github.com/santihofi/chipify/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** chipify, chipify-cli. Dependencies to review: xschem, ngspice; selected PDK; optional GUI libraries.
- **Integration and validation:** Upstream describes work in progress and IHP-focused support; validate each requested process separately.
- **License evidence:** Apache-2.0. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## lctime

- **Name / kind / aliases:** lctime; tool; lctime.
- **Official sources:** [Homepage](https://codeberg.org/librecell/lctime); [source repository](https://codeberg.org/librecell/lctime); [installation documentation](https://codeberg.org/librecell/lctime#readme).
- **Discovery:** Review the linked upstream release/download documentation. Release policy and maintained branch **unknown**; resolve them before selecting a snapshot.
- **Interfaces / dependencies:** Entrypoint discovery pending. Dependencies to review: ngspice; Python.
- **Integration and validation:** Characterize a small supported cell and parse generated timing tables.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## hdl21

- **Name / kind / aliases:** Hdl21; library; Hdl21.
- **Official sources:** [Homepage](https://github.com/dan-fritchman/Hdl21); [source repository](https://github.com/dan-fritchman/Hdl21); [installation documentation](https://github.com/dan-fritchman/Hdl21#readme).
- **Discovery:** Review [official releases](https://github.com/dan-fritchman/Hdl21/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: vlsirtools; simulator selected by the design.
- **Integration and validation:** Elaborate and simulate a small analog design; import alone is insufficient.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## pygmid

- **Name / kind / aliases:** pygmid; library; pygmid.
- **Official sources:** [Homepage](https://github.com/dreoilin/pygmid); [source repository](https://github.com/dreoilin/pygmid); [installation documentation](https://github.com/dreoilin/pygmid#readme).
- **Source migration:** The previously recorded [repository](https://github.com/madrasalach/pygmid) redirects to the canonical source above; preserve this provenance in any installation record.
- **Discovery:** Review [official releases](https://github.com/dreoilin/pygmid/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Python scientific libraries; device characterization data.
- **Integration and validation:** Validate a lookup against the matching technology data and units.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## pyopus

- **Name / kind / aliases:** PyOPUS; library; PyOPUS.
- **Official sources:** [Homepage](https://fides.fe.uni-lj.si/pyopus/); [source repository](https://codeberg.org/arpadbuermen/PyOPUS); [installation documentation](https://codeberg.org/arpadbuermen/PyOPUS#readme).
- **Discovery:** Review the linked upstream release/download documentation. Release policy and maintained branch **unknown**; resolve them before selecting a snapshot.
- **Interfaces / dependencies:** Python library; GUI entrypoints pending. Dependencies to review: Native Python extensions; selected simulator.
- **Integration and validation:** Record Python and numerical-library ABI and run an optimization with inspected results.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## pyspice

- **Name / kind / aliases:** PySpice; library; PySpice.
- **Official sources:** [Homepage](https://github.com/PySpice-org/PySpice); [source repository](https://github.com/PySpice-org/PySpice); [installation documentation](https://github.com/PySpice-org/PySpice#readme).
- **Discovery:** Review [official releases](https://github.com/PySpice-org/PySpice/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: ngspice or xyce; native shared-library interface.
- **Integration and validation:** Verify shared-library resolution and compare a numerical result to the circuit expectation.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## ngspyce

- **Name / kind / aliases:** ngspyce; library; ngspyce.
- **Official sources:** [Homepage](https://github.com/ignamv/ngspyce); [source repository](https://github.com/ignamv/ngspyce); [installation documentation](https://github.com/ignamv/ngspyce#readme).
- **Discovery:** Review [official releases](https://github.com/ignamv/ngspyce/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: ngspice shared library; Python.
- **Integration and validation:** Check native library ABI and a real circuit evaluation.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## spicebind

- **Name / kind / aliases:** spicebind; library; spicebind.
- **Official sources:** [Homepage](https://github.com/themperek/spicebind); [source repository](https://github.com/themperek/spicebind); [installation documentation](https://github.com/themperek/spicebind#readme).
- **Discovery:** Review [official releases](https://github.com/themperek/spicebind/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Simulator-loaded bridge; exported names pending. Dependencies to review: ngspice; VPI-capable HDL simulator.
- **Integration and validation:** Couple the HDL VPI and ngspice ABIs and verify bidirectional signal exchange.
- **License evidence:** BSD-3-Clause. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## spicelib

- **Name / kind / aliases:** spicelib; library; spicelib.
- **Official sources:** [Homepage](https://github.com/nunobrum/spicelib); [source repository](https://github.com/nunobrum/spicelib); [installation documentation](https://github.com/nunobrum/spicelib#readme).
- **Discovery:** Review [official releases](https://github.com/nunobrum/spicelib/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library; utility names pending. Dependencies to review: A selected supported SPICE simulator.
- **Integration and validation:** Read, modify and simulate a supported netlist and inspect its outputs.
- **License evidence:** GPL-3.0 (package metadata; confirm license version in source). Retain the selected revision’s own license and dependency notices.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## spyci

- **Name / kind / aliases:** spyci; library; spyci.
- **Official sources:** [Homepage](https://github.com/gmagno/spyci); [source repository](https://github.com/gmagno/spyci); [installation documentation](https://github.com/gmagno/spyci#readme).
- **Discovery:** Review [official releases](https://github.com/gmagno/spyci/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: ngspice or xyce output data; plotting dependencies.
- **Integration and validation:** Check waveform parsing, units and numeric samples.
- **License evidence:** MIT. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [analog guidance](../recipes/analog/README.md).

## gaw3-xschem

- **Name / kind / aliases:** gaw3-xschem; tool; xschem-gaw.
- **Official sources:** [Homepage](https://github.com/StefanSchippers/xschem-gaw); [source repository](https://github.com/StefanSchippers/xschem-gaw); [installation documentation](https://github.com/StefanSchippers/xschem-gaw#readme).
- **Discovery:** Review [official releases](https://github.com/StefanSchippers/xschem-gaw/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** gaw. Dependencies to review: xschem for remote-control integration; GTK.
- **Integration and validation:** This is the Xschem maintainer's Gaw fork; record provider identity explicitly.
- **Recipe:** [analog guidance](../recipes/analog/README.md).
