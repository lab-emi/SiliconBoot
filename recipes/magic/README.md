# Magic

Catalog ID: `magic`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve the source and host

Read the [official source](https://github.com/RTimothyEdwards/magic), its INSTALL document and [Magic documentation](https://opencircuitdesign.com/magic/). Determine whether upstream identifies a current release or a maintained source snapshot; record the actual tag or complete commit. Do not use a historical major-version heading in the README as a latest-release resolver.

Use the selected revision's native installation instructions. Linux and the repository's macOS guide are candidates for validation. Any other host needs an explicit upstream-supported route and a successful local check before claiming support. GUI support also depends on the display and toolkit configuration.

## Install and expose

Apply [installation](../../docs/installation.md). Record the C build toolchain, Tcl/Tk ABI, display backend and optional dependencies. Ensure the PDK's technology-file requirements match the installed Magic revision. If building a PDK requires Magic, validate Magic first, build the PDK next, then run the combined checks.

Install Magic's executable, Tcl files, technology resources and supporting libraries in a persistent prefix. Register every public executable actually provided by that installation; do not infer extra commands from another version. Use the PDK's documented startup file by an explicit project setting and keep user overrides under `config/tools/`. A custom shell wrapper must not be introduced to hide missing runtime configuration.

## Acceptance

1. Obtain version information and open an upstream example with its intended technology. Record GUI validation separately if only batch execution is available.
2. Load a small PDK-provided layout and run its documented DRC. Record the technology revision, units, enabled rules and final violation counts. Use a known-failing upstream fixture when available to verify that checks are actually running.
3. Extract the same layout and produce the appropriate SPICE representation in the run directory. Check the top cell, ports, device model names and nonempty connectivity; zero extracted devices is a failure for a transistor test cell.
4. Send the extracted netlist and the reference schematic netlist to [Netgen](../netgen/README.md) with that PDK's setup. Record extraction and LVS separately.
5. If parasitic extraction is required and supported by that PDK, run its documented extraction mode, inspect nonzero expected parasitics and simulate the extracted circuit. A plain connectivity extraction does not establish PEX readiness.

Complete the fresh-shell checks in [validation](../../docs/validation.md) and the [receipt](../../docs/records.md). Retain Tcl resources and technology data during cleanup. All generated layout, extraction and report files belong under project `runs/`, never in the shared PDK.
