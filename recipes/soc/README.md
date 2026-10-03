# SoC integration and RISC-V

Apply the [common recipe](../README.md) and component identities in the [catalog](../../catalog/README.md). Freeze target architecture and ABI separately from the machine executing the toolchain. A native compiler executable can produce code for a different target; report both.

## Resolve and install

| Component | Resolution and runtime requirements | Functional acceptance |
| --- | --- | --- |
| Kactus2 | Native GUI, plugins, IP-XACT version and example library | Open and validate an upstream example design; inspect resolved bus interfaces and generated documentation or supported design export |
| PULP tools | Resolve the catalog's exact named subprojects and official sources; the umbrella name alone is not installable | Run each selected member's own upstream minimal example and record its distinct capability |
| bender | Rust toolchain, package sources and dependency lock behavior | Resolve an upstream HDL example, inspect ordered sources and execute its documented consumer flow |
| RgGen | Isolated Ruby packages, core plugins, input formats, and exact selected backends | Generate registers from an upstream specification with every selected backend; verify addresses, widths, resets, access modes and downstream parsing |
| RISC-V GNU toolchain | Target ISA, ABI, C library, multilib choices, submodules and host compiler | Build an upstream test program for the selected target; inspect binary architecture and run it in the documented target environment |
| riscv-pk | Target ABI and compatible compiler/sysroot; target runtime, not a host executable | Load the generated proxy-kernel payload through the recorded simulator and inspect expected program behavior |
| Spike | Supported ISA extensions, native dependencies and target runtime | Run the supported upstream test/payload and check expected termination and observable output |

The [RgGen project](https://github.com/rggen/rggen) documents separate plugins and output backends. Expand the catalog's members explicitly and retain compatible dependency versions. Do not claim all backends based on one HDL output. Inspect each declared output with an appropriate parser, simulator, or document reader.

## Validation and handoff

Keep the host OS/architecture, target triple, ISA extensions, ABI, library/sysroot, payload and simulator versions in the records. A RISC-V target binary should not be placed in the host's executable map as if the host could run it directly. Locate target runtimes through their installed roots and document the simulator invocation instead.

Use the complete toolchain prefix so headers, linker scripts, libraries and compiler support programs remain available. Export public cross-tool entrypoints under their upstream names without shadowing the system compiler. Clean only owned downloads/build files after compiling and running outside the build tree. Do not alter existing IP repositories or send hardware programs to a device during setup.
