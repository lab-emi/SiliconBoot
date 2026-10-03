# FPGA tools

Read the [common recipe](../README.md), [Yosys recipe](../yosys/README.md), and official component sources in the [catalog](../../catalog/README.md). Use the [nextpnr build and example guide](https://github.com/YosysHQ/nextpnr) to resolve current device-specific dependencies. Native validation has not been established by this document.

## Resolve and install

Treat nextpnr-ice40 and nextpnr-ecp5 as distinct capabilities even when built from one source revision. iCE40 uses the IceStorm device data; ECP5 uses Project Trellis. Record tool and database revisions, recursive submodules, selected architectures, device coverage and GUI options. Use native host build tools, and keep generated device databases in persistent runtime locations.

| Component | Required functional check |
| --- | --- |
| IceStorm | Pack and unpack a documented iCE40 example, inspect expected outputs and device identity |
| nextpnr-ice40 | Place and route an upstream-supported synthesized iCE40 example for a specific device/package; inspect timing and routing completion |
| Project Trellis | Use the installed ECP5 device database to pack/unpack the supported example; inspect device identity and outputs |
| nextpnr-ecp5 | Place and route the corresponding ECP5 example; verify device database selection, timing and routing completion |

Use a device, package and clock constraint explicitly supported by the frozen upstream example. Synthesize with the recorded Yosys, route with the selected backend, and create the expected bitstream with the matching packer. Record synthesis, route, timing and packing separately. Generate artifacts in the project run directory.

## Entrypoints and boundaries

Inventory all upstream-installed public packers, unpackers, timing utilities and programming tools; distinguish private build helpers. Record standard and namespaced aliases and their providers. Keep database directories, Python modules and licenses. Clean temporary source only if none of the tools or databases still refer to it.

Bitstream creation is a software check. Programming a physical board needs a separate user request identifying the board and interface; no catalog profile authorizes hardware programming. Missing hardware does not prevent reporting successful software stages, but hardware behavior remains untested.
