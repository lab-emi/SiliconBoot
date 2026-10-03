# Profiles and coverage

Profiles describe a selection to review. They do not certify a compatible environment or an installed workflow. Apply the [catalog defaults](README.md) and the linked recipes, resolve exact dependency versions, and report every selected component's status.

Include uv as a default setup dependency in every profile and custom component selection. Install it first when missing, before Python environment or package setup. An explicit user choice can override this default; record the choice and affected scope. Upstream runtime exceptions follow the [Python environment policy](../docs/python-environments.md).

## Selections

| Profile | Selected records | Selection notes |
| --- | --- | --- |
| all | Every category record except optional JupyterLab: 135 unique IDs, including uv | Includes named extensions, PDK families and memory compilers. Report the unresolved PULP umbrella explicitly and review its identified constituents individually. Experimental or planned entries must remain visible. |
| analog | All analog and layout records; PDK infrastructure and each requested process variant | Review simulator/model ABI, schematic-to-simulation and layout verification as separate capabilities. |
| digital | All HDL, verification, formal, implementation, SoC and orchestration records; KLayout, Magic, Netgen; PDK infrastructure and requested process variants | FPGA architecture tools remain in fpga unless requested. Select solver and language backends explicitly; no latest-version compatibility is presumed. |
| memory | OpenRAM and DFFRAM; their documented compiler/technology/tool dependencies | Select each compiler's supported PDK port independently. A source PDK or pre-generated macro does not establish a compiler port. |
| fpga | All FPGA records; Yosys, ABC and the HDL/simulation frontend needed by the design | iCE40 and ECP5 have separate device databases and validation results. Hardware programming requires a separate requested design action. |
| rf | All RF records; Qucs-S, ngspice, Xyce, VacasK, OpenVAF-ReLoaded and the selected layout/PDK dependencies | Record solver, mesh, material stack, model and port definitions. A solver executable does not prove a process-specific EM flow. |
| support | JupyterLab, plus the default uv dependency | Optional notebook capability; JupyterLab is excluded from all and the domain profiles unless explicitly requested. |

A profile's dependencies are reviewed recursively and deduplicated by canonical ID. System libraries, runtime package dependencies and upstream submodules are recorded with their parent component. Shared-source capabilities such as nextpnr architecture builds and Qflow conversion tools retain separate capability records while sharing their actual source/install identity.

## Component counts

| Category | Records |
| --- | ---: |
| [Analog and schematic tools](analog.md) | 22 |
| [HDL languages and frontends](hdl.md) | 10 |
| [Simulation and verification](verification.md) | 11 |
| [Synthesis and formal verification](formal.md) | 9 |
| [ASIC implementation](implementation.md) | 6 |
| [Layout and KLayout extensions](layout.md) | 23 |
| [EM and RF](rf.md) | 12 |
| [FPGA](fpga.md) | 4 |
| [SoC, RISC-V and RgGen](soc.md) | 22 |
| [Orchestration and libraries](orchestration.md) | 7 |
| [PDK infrastructure and process data](pdks.md) | 6 |
| [Memory compilers](memory.md) | 2 |
| [Python environment manager and optional support](support.md) | 2 |
| Total | 136 |

The total includes the PULP umbrella scope record. It does not count unnamed extensions, aliases, bundled system libraries or pre-generated memory macros as separate components. There are no verified native installations or workflows in these counts.

## Explicit scope and discovery gaps

- **PULP tools:** no single authoritative package or fixed tool bundle is established by that name. The catalog identifies Bender and the upstream-linked PULP toolchain, SDK and runtime. Resolve the requested PULP target before treating the collection as complete. Verible and sv2v already have their own records.
- **Unnamed Salt plugins:** the independently documented KLayout extensions are enumerated in the layout catalog. Additional unnamed plugins have no approved identity or installation selection. Keep the gap in a full-coverage report until concrete upstream names and sources are established.
- **GF180 latest source:** the original Google source repository is archived. Identify any maintained successor from official evidence before claiming an up-to-date source installation. A fork or builder snapshot must identify its provider explicitly.
- **Release and branch policies:** many records have a checked repository default branch but no reviewed maintenance-channel policy. Report latest_unknown until the official policy and exact revision are established.
- **Installation inventories:** several upstream tools export more commands than the catalog currently names. Inspect the persistent installation, classify public entrypoints and record their relative paths before making a complete binary-coverage claim.
- **License and platform review:** inherited unknown values must be resolved for the selected versions. Native checks, resource measurements, model compilation and memory workflows remain unverified.

## Minimum profile evidence

Record component usability and profile workflow readiness separately. Analog requires a checked schematic-to-simulation result and the selected layout checks. Digital requires a checked RTL-to-implementation flow with interpreted reports. Memory requires supported generated views and the compiler's stated verification steps. FPGA requires a correct architecture-specific implementation and bitstream-generation result. RF requires a checked numerical example with documented convergence or reference behavior.

Partial results can be useful, but they must list missing, incompatible, unresolved and untested components. The word all describes scope; it never means all-ready without the corresponding evidence.
