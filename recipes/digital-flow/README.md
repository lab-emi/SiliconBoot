# Digital implementation workflow

Components: Yosys, OpenROAD, OpenSTA, LibreLane, Qflow, padring and Fault, with the selected PDK and any requested frontend. Recipe status: experimental; no complete native workflow has been validated by this repository. Resolve and record each component separately.

## Official sources and native route

| Component | Official starting points | Native installation decision |
| --- | --- | --- |
| Yosys | [Recipe](../yosys/README.md) | Resolve the requested release, frontend and ABC together. |
| OpenROAD | [Source](https://github.com/The-OpenROAD-Project/OpenROAD), [build guide](https://openroad.readthedocs.io/en/latest/user/Build.html) | Use a matching official or upstream-endorsed native package, or the resolved revision's supported source build. |
| OpenSTA | [Parallax source and build guide](https://github.com/parallaxsw/OpenSTA) | Use its native build instructions and record whether the standalone executable is installed. |
| LibreLane | [Source](https://github.com/librelane/librelane), [installation guide](https://librelane.readthedocs.io/en/latest/installation/index.html) | Evaluate the documented native Nix route on Linux/macOS or a matching Linux AppImage. Record bundled dependencies. |

Resolve official releases at installation time; where none is published, verify the maintained branch from upstream documentation and record the full commit. Never assume every repository uses `main`. Apply [installation](../../docs/installation.md) to the complete dependency plan.

The current OpenROAD guide recommends Bazel for source builds and identifies `openroad.runfiles` as runtime data. Follow the chosen revision's instructions and retain its complete installed layout. For OpenSTA, record Tcl, compiler and required library dependencies from its build guide. OpenROAD's embedded timing engine and a standalone OpenSTA executable have separate identities; installing one does not prove the other is present.

LibreLane documents native Nix operation and warns that independently supplied tool versions may be incompatible. Preserve its resolved dependency closure and persistent package-manager roots. Compare every actual tool version with the user's latest request. A tested pinned flow may be offered as a named compatible environment; it cannot silently replace the independently latest tools. A Windows guide using WSL establishes a Linux environment only when the user selects it.

## Runtime and configuration

Install complete upstream runtime directories and preserve Python environments or native package closures. Expose public executables only when they work through persistent symlinks. If upstream requires an environment entry command, document it with its fixed source revision and working directory rather than inventing a launcher. Record the runtime environment for each run so temporary changes to project `current` cannot change a running flow's tool selection.

Choose an official small flow example whose PDK and standard-cell library are actually installed. Retain its upstream RTL and flow configuration in a project run area with source provenance; this repository supplies no RTL, configuration code or flow scripts. Confirm clock constraints, target period, corners, routing layers, library views and output locations before running.

### LibreLane AppImage mountpoints

Follow the official [Linux AppImage installation guide](https://librelane.readthedocs.io/en/latest/installation/appimage_installation/installation_linux.html) and [AppImage FUSE troubleshooting](https://docs.appimage.org/user-guide/troubleshooting/fuse.html). Keep the official executable in its persistent installation and use its upstream entrypoint with the bundled dependency closure.

Set `TMPDIR` to the canonical path of a private `runs/<run-id>/tmp` directory inside the existing project, following [temporary mount guidance](../../docs/project-layout.md#appimage-temporary-mounts). Verify the host permits a FUSE mount at that location. An AppArmor `fusermount3` denial reporting `failed mntpnt match` identifies a mountpoint restriction; inspect it before treating the failure as a missing FUSE dependency. A writable installation directory does not establish mount permission.

Record the effective `TMPDIR` and verify startup plus an affected functional step from a fresh process using the unchanged AppImage. Keep its runtime settings scoped to that process. Release the temporary directory only after all child processes and FUSE mounts finish. This rule applies during initial verification, design runs, and post-cleanup checks.

## Acceptance gates

1. Check each tool's identity, version and startup independently. If standalone OpenSTA is selected, run an upstream timing example and inspect a real path report.
2. Synthesize the selected example and record top module, cell statistics, mapped netlist and unresolved-cell diagnostics.
3. Run the upstream implementation flow through placement, clock construction where applicable, and routing. Check routed DEF/database and final layout files, along with tool reports. Open the resulting layout with the selected KLayout.
4. Read setup and hold results at the declared corners. Record worst slack, unconstrained paths and missing timing arcs. A report with no analyzed paths is not a timing pass.
5. Inspect routing, antenna and physical-check findings. Run the applicable PDK DRC and LVS checks and record actual counts and match status. Missing decks or skipped checks stay explicit.
6. Verify a fresh-shell rerun using installed runtime data, then compare hashes and reports where reproducibility is expected. Record nondeterministic outputs without promising bitwise identity.

Store each tool receipt and the complete workflow dependency set under [records](../../docs/records.md). Mark individual components usable even if the integration is blocked, but set `workflow_ready` only after its required gates pass. Preserve previous installations on upgrade failure; clean only owned transient data after [validation](../../docs/validation.md).

## Additional implementation components

These components have their own acceptance criteria. Installing LibreLane or OpenROAD does not validate them. Apply the same source freezing, native-host assessment, fresh-shell verification and persistent-runtime rules above to each one.

### Qflow

Read the [official repository](https://github.com/RTimothyEdwards/qflow) and [Qflow documentation](https://opencircuitdesign.com/qflow/). Resolve its release or documented maintained source revision independently. Read that revision's native build requirements and configure the final install prefix plus explicit paths to its toolchain. Upstream identifies Yosys, GrayWolf, Qrouter, Magic and Netgen as external tools; add missing backends to the dependency plan and record their own official sources and revisions. A different router is not an automatic replacement.

Preserve the installed technology directory and upstream flow resources alongside the executable. Inventory public conversion utilities, including the catalog's `vlog2verilog` capability, under the same Qflow source receipt. A version change affecting those shared utilities invalidates their dependent checks as well.

For acceptance, run a small upstream example with a supported technology. Confirm synthesis, placement and routing actually invoked the recorded backends. Inspect the mapped netlist, DEF/layout, timing report and applicable DRC/LVS outcomes. Record stopped stages individually. Check the conversion utility on an upstream supported input and pass its output to the documented consumer. Keep installed resources and technology data during cleanup.

### padring

Use the [YosysHQ upstream repository](https://github.com/YosysHQ/padring) and its build and example instructions. The [donn repository](https://github.com/donn/padring) is a fork through ax3ghazy; any required fork must have a separate provider identity and reason. Resolve the selected provider's release policy and commit, then assess its C++ toolchain, CMake and Ninja requirements for the native host.

Install the actual public executable at a persistent location with required runtime resources. Run the revision's example using its LEF and placement configuration, writing requested DEF, GDS or SVG outputs to the project run directory. Check die dimensions, units, pad count/order, corner orientation, filler placement and cell names against the inputs. Detect duplicate cell names across input LEFs before they can overwrite one another.

Open the physical output with the selected layout viewer and inspect expected geometry. If the project needs electrical connectivity, verify power continuity and signal mapping with the applicable downstream rules; a geometric ring image does not establish connectivity or physical signoff. Preserve the input library provenance and all generated reports.

### Fault DFT

Use [AUCOHL/Fault](https://github.com/AUCOHL/Fault), its [installation guide](https://fault.readthedocs.io/en/latest/installation.html) and [usage example](https://fault.readthedocs.io/en/latest/usage.html). Resolve the release or maintained source revision before choosing a native Linux/macOS Nix package or an upstream wheel/source build. The documented Python distribution is `fault-dft`; confirm the installed `fault` command belongs to that package. Record Python and native wheel compatibility, or Swift and build dependencies when compiling from source.

Resolve Yosys, Icarus Verilog and the chosen ATPG backend individually. The checked installation guide requires an Icarus development version for its IHP integration; if this still applies, report the stable-channel workflow incompatibility and present the development channel explicitly. Keep optional Atalanta and PODEM separate: the upstream README identifies distribution/use restrictions, so do not silently include them in an open-source-only dependency set. Record the selected backend and its license evidence.

Run the official `s27` tutorial or its revision-equivalent example through the requested synthesis, netlist cutting, fault simulation and scan-chain steps. Record the library and cell models, clock/reset and bypass signals, fault model, tested fault counts, achieved coverage and any vector limit that stopped the run. Check scan integrity and simulate the resulting netlist with the intended cell models. Exercise JTAG insertion only when that capability is requested, and report it separately.

Retain the installed upstream entrypoints, Python package, native libraries and any Nix roots. Store generated vectors, netlists, coverage results and logs in the project run directory. A working version command or a produced scan netlist alone does not satisfy DFT acceptance.
