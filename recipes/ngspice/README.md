# ngspice

Catalog ID: `ngspice`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve the source and host

Start at the [official download page](https://ngspice.sourceforge.io/download.html) and [documentation](https://ngspice.sourceforge.io/docs.html). Resolve the latest stable release and its source archive there. Nightly builds and development branches are separate channels. The download page identifies SourceForge as the managed source and distinguishes third-party mirrors.

Select an official asset only when its version, OS and architecture match the request. Inspect the current platform notes: stable Linux binaries, macOS assets and development assets have different availability. A distribution package is usable only after comparing its actual version and features with the requested release. Otherwise use the selected source's installation instructions. Do not substitute a nightly asset just because it is easier to obtain.

## Install and expose

Apply [installation](../../docs/installation.md). Resolve compiler and build dependencies plus optional features from the release manual and INSTALL file. Record enabled model interfaces, XSPICE, plotting support and any shared-library build separately. A CLI executable and a shared-library installation may have different feature sets.

Install in the final persistent prefix and retain executable, runtime model data and any required shared libraries. Export the upstream `ngspice` executable. Register a shared library as a library with its path and ABI; do not invent a second CLI for it. Keep PDK model includes and startup settings in project configuration, with documented per-process activation. Avoid global model paths that silently select a different PDK.

For OSDI-dependent models, match the simulator's supported OSDI interface, target CPU and model compiler. Build model artifacts for the selected host and record their inputs; see [IHP](../ihp/README.md). File existence alone does not prove a plugin loads.

## Acceptance

1. Capture the actual version and feature information, then run a release-provided passive-circuit example in batch mode from a project run directory. Check successful analysis completion, nonempty numeric output and an expected voltage, time constant or frequency response with a recorded tolerance.
2. Run a PDK-provided MOS example using the selected model corner. Verify the simulator loaded the intended models and returned finite, physically plausible values without unresolved model names or hidden fallback models.
3. When OSDI is required, exercise a device implemented by the compiled plugin. Capture plugin loading diagnostics and compare its expected response. Mark that workflow blocked if the interface is unavailable.
4. Run the [Xschem](../xschem/README.md) netlist through the same executable. Repeat the component check in a fresh shell after installation staging is unavailable.

Store evidence under the run directory and complete [records](../../docs/records.md). Retain model binaries, supporting data and shared libraries. Clean only owned downloads and build intermediates after [validation](../../docs/validation.md).
