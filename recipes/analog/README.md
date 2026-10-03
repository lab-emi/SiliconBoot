# Analog tools and libraries

Apply the [common recipe](../README.md) and each component's [catalog](../../catalog/README.md) sources. [Xschem](../xschem/README.md) and [ngspice](../ngspice/README.md) have dedicated recipes. The instructions below are experimental until validated on a recorded native host.

## Resolve and install

Resolve each selected component independently. Keep simulator engines, model compilers, Python bindings, and characterization tools distinct in the receipts. Build native numerical libraries and simulator plugins for the actual host ABI. A binding may need a shared-library build of its simulator; a working simulator executable alone does not prove that interface works.

For Python packages, use the maintainer-linked distribution and an isolated interpreter at the final prefix. Check supported interpreter and scientific-library versions before selecting dependencies. Keep example data and model files needed by runtime operations. GUI applications require a working display session for GUI verification; headless checks and GUI checks have separate results.

## Component checks

| Component | Installation decision | Required real check |
| --- | --- | --- |
| XCircuit | Preserve Tcl/Tk resources and fonts; discover the actual GUI entrypoint | Open an upstream schematic example, inspect connectivity, and export it into the run directory |
| Schemdraw | Record the Python interpreter and supported rendering backend | Render a small upstream circuit example and inspect the resulting image/vector file |
| Xyce | Follow official native build requirements and record numerical libraries and parallel configuration | Run an official circuit with an expected operating point or transient response; inspect convergence and values |
| VacasK | Confirm supported model/compiler interface and runtime data from its own docs | Run a documented circuit; verify model loading, convergence and numerical results |
| Qucs-S | Record the GUI and selected external simulator separately | Simulate an upstream schematic with the recorded backend and verify plotted data |
| OpenVAF-ReLoaded | Verify this fork's identity, release channel, host architecture and supported model format | Compile a supported Verilog-A example and load the resulting model in the intended simulator for a numerical check |
| ADMS | Retain templates needed by the selected simulator's model integration | Process an upstream model with the matching template; validate the generated model through the target simulator's documented flow |
| CACE | Resolve characterization backend tools and PDK/model dependencies | Characterize one upstream-supported cell or circuit and inspect expected measured parameters and pass/fail limits |
| CharLib | Record simulator, cell netlist, models, corners, and timing setup | Characterize one supported cell and validate the Liberty structure, units, tables, and values |
| Chipify | Confirm source identity and current upstream workflow before choosing dependencies | Reproduce its documented minimal characterization example and inspect its declared outputs |
| lctime | Verify the supported simulator and library-generation inputs | Run the upstream smallest timing example; check declared timing arcs and numerical tables |
| Hdl21 | Record generator dependencies, netlisting path, and chosen simulator backend | Generate an upstream example netlist, inspect connectivity and simulate it if that integration is claimed |
| pygmid | Preserve device lookup data and record its provenance and PDK | Reproduce a documented lookup calculation and compare units and values to its source data |
| PyOPUS | Resolve simulator interface and native extension requirements | Run a documented numerical/simulation example and check expected values and simulator invocation |
| PySpice | Verify the selected ngspice shared library and its ABI | Simulate an upstream small circuit through Python, checking vectors and actual loaded library path |
| ngspyce | Confirm package identity and its own supported ngspice interface | Run a documented circuit through its API; check library loading and numerical output |
| spicebind | Establish the upstream binding and backend identity before installation | Exercise its documented simulator integration and inspect returned circuit results |
| spicelib | Record which simulator is selected and whether it is present natively | Read and modify an upstream sample netlist; run a supported backend only if available and verify results |
| spyci | Confirm the intended project and simulator dependency | Use the upstream example to invoke the simulator and inspect its parsed results |
| gaw3-xschem | Preserve wave-viewer integration resources and discover the official executable | Open data produced by the selected Xschem/ngspice example and confirm expected signal names and units |

Before a check, identify the exact upstream example path/revision and expected result in the validation record. If the catalog has not resolved a component's official identity, stop that component at planning and report the evidence needed; do not install a similarly named package.

## Workflow acceptance and cleanup

For schematic-to-simulation readiness, use the [Xschem recipe](../xschem/README.md) with the selected PDK, simulator, model compiler and corner. For characterization readiness, require the actual generated library and measured reports. Keep model-compiler output tied to the simulator ABI in the install key.

Remove only owned downloads and build intermediates after clean-session checks. Preserve simulator shared libraries, installed Python sources, model templates, fonts, characterization inputs needed at runtime, and all licenses. Record missing GUI access or unavailable reference data as untested capabilities.
