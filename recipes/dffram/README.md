# DFFRAM

Catalog ID: `dffram`. Kind: standard-cell memory compiler. Recipe status: experimental; no native compilation has been validated by this repository. Read [memory compilers](../../docs/memory-compilers.md).

## Resolve source and supported configuration

Use the [official repository and platform table](https://github.com/AUCOHL/DFFRAM) and [usage guide](https://github.com/AUCOHL/DFFRAM/blob/main/docs/Usage.md). Resolve an official release when available, otherwise verify the maintained branch, currently `main`, and freeze its full commit. Read implementation, dependencies and documentation at that revision together: the checked tree contains a LibreLane plugin while parts of the usage text retain older flow naming.

DFFRAM builds memory from flip-flop or latch standard cells. Record the exact PDK, standard-cell library and building-block set. The current platform table reports a GF180MCU hold-timing problem, and the README discourages the 1RW1R configuration. Recheck both restrictions at resolution time and retain them in the receipt unless newer upstream evidence and local validation resolve them. A listed platform is not a guarantee for every size or port arrangement.

## Native installation and dependencies

Follow [installation](../../docs/installation.md). The usage guide describes Linux/macOS with Nix. Confirm a native dependency closure for the actual CPU and retain its package-manager roots. Inventory the flow, Yosys, OpenROAD, Python interfaces, PDK and library versions; a latest DFFRAM checkout can still contain pinned dependencies that are older than their latest releases.

Preserve the source, platform building blocks, upstream flow resources, Python environment and installed dependency closure in persistent locations. OpenROAD's Python interface and the placer/flow integration must be compatible. A separately upgraded OpenROAD binary does not prove that its Python API will work with this compiler.

Use an upstream-provided entrypoint where available. If the compiler uses an upstream Python entry file, document its persistent interpreter, file path and upstream environment-entry method. Do not create a custom launcher. Keep user configuration and all generation output in the project, without altering shared building blocks.

## Acceptance

1. Check compiler startup and dependency resolution from a fresh shell using the fixed source and environment.
2. Choose a currently supported upstream example with a listed size and building-block set. Record width, depth, ports, latch/DFF choice, PDK, library and corners. Do not enable an override that bypasses supported-size validation.
3. Run the complete upstream generation and hardening flow. Inspect expected HDL model/netlist, LEF, GDS and timing views for matching macro identity and pins; record any missing view.
4. Run its available functional verification and inspect placement, routing, DRC and LVS reports. Check real setup and hold reports with analyzed paths and the requested corners. A generated GDS or a process exit of zero is insufficient.
5. For GF180MCU, preserve the upstream timing caveat and local slack results. A remaining hold violation prevents timing readiness even when generation and physical checks pass.

Store artifacts under `runs/<run-id>/artifacts/memory/` and complete the [memory acceptance record](../../docs/memory-compilers.md). Register accepted results under `ip/memory/manifests/` only through the project's acceptance process. Apply [records](../../docs/records.md) and [validation](../../docs/validation.md); retain runtime sources and package roots while removing only owned disposable files.
