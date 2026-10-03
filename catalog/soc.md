# SoC, RISC-V and RgGen

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

The [RgGen upstream README](https://github.com/rggen/rggen#readme) identifies its core packages and SystemVerilog, Verilog, VHDL and Veryl backends. Their own repositories below provide component-specific evidence. Supporting RTL libraries are data dependencies, not host programs. Use one isolated Ruby environment with a recorded compatible dependency set.

The [PULP platform README](https://github.com/pulp-platform/pulp#readme) points to Bender, its toolchain, SDK and runtime. These explicit dependencies are listed below. “PULP tools” remains an umbrella whose target and scope must be selected; Bender, Verible and sv2v retain their own independent catalog identities.

## kactus2

- **Name / kind / aliases:** Kactus2; tool; Kactus2.
- **Official sources:** [Homepage](https://github.com/kactus2/kactus2dev); [source repository](https://github.com/kactus2/kactus2dev); [installation documentation](https://github.com/kactus2/kactus2dev#readme).
- **Discovery:** Review [official releases](https://github.com/kactus2/kactus2dev/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** kactus2; confirm installed capitalization. Dependencies to review: Qt and IP-XACT schemas.
- **Integration and validation:** Open, validate and save a small IP-XACT component without schema loss.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## pulp-tools

- **Support exception:** Planned; aggregate scope is unresolved.
- **Name / kind / aliases:** PULP tools; collection; PULP tools.
- **Official sources:** [Homepage](https://github.com/pulp-platform/pulp); [source repository](https://github.com/pulp-platform/pulp); [installation documentation](https://github.com/pulp-platform/pulp#readme).
- **Discovery:** Not a release-bearing aggregate package. Resolve each selected constituent; the PULP platform source is an upstream scope reference.
- **Interfaces / dependencies:** No aggregate executable. Dependencies to review: bender; select SDK/toolchain for the chosen PULP target.
- **Integration and validation:** Umbrella scope unresolved: this ID is a selection record, not an installable package.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## bender

- **Name / kind / aliases:** Bender; tool; Bender.
- **Official sources:** [Homepage](https://pulp-platform.github.io/bender/); [source repository](https://github.com/pulp-platform/bender); [installation documentation](https://pulp-platform.github.io/bender/).
- **Discovery:** Review [official releases](https://github.com/pulp-platform/bender/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** bender. Dependencies to review: Rust build dependencies; Git.
- **Integration and validation:** Resolve a small HDL dependency graph and preserve its lock and source order.
- **License evidence:** Apache-2.0 OR MIT. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen

- **Name / kind / aliases:** RgGen; tool; RgGen.
- **Official sources:** [Homepage](https://github.com/rggen/rggen); [source repository](https://github.com/rggen/rggen); [installation documentation](https://github.com/rggen/rggen#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** rggen. Dependencies to review: Ruby; rggen-core, rggen-default-register-map, rggen-systemverilog, rggen-c-header, rggen-markdown, rggen-spreadsheet-loader.
- **Integration and validation:** Generate a register map and validate outputs through the selected backend.
- **License evidence:** MIT. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## riscv-gnu-toolchain

- **Name / kind / aliases:** RISC-V GNU toolchain; compiler; RISC-V GNU toolchain.
- **Official sources:** [Homepage](https://github.com/riscv-collab/riscv-gnu-toolchain); [source repository](https://github.com/riscv-collab/riscv-gnu-toolchain); [installation documentation](https://github.com/riscv-collab/riscv-gnu-toolchain#readme).
- **Discovery:** Review [official releases](https://github.com/riscv-collab/riscv-gnu-toolchain/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Target-prefixed GCC/binutils; names depend on ISA, ABI and target OS. Dependencies to review: Native compiler and upstream submodules.
- **Integration and validation:** Record target triple, ISA, ABI, multilib choices and every source submodule revision.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## riscv-pk

- **Name / kind / aliases:** RISC-V proxy kernel; tool; RISC-V proxy kernel.
- **Official sources:** [Homepage](https://github.com/riscv-software-src/riscv-pk); [source repository](https://github.com/riscv-software-src/riscv-pk); [installation documentation](https://github.com/riscv-software-src/riscv-pk#readme).
- **Discovery:** Review [official releases](https://github.com/riscv-software-src/riscv-pk/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** pk target program; not a native host CLI. Dependencies to review: riscv-gnu-toolchain; spike for a selected validation target.
- **Integration and validation:** Build for the target ISA/ABI and execute under the selected RISC-V simulator.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## spike

- **Name / kind / aliases:** Spike; tool; Spike.
- **Official sources:** [Homepage](https://github.com/riscv-software-src/riscv-isa-sim); [source repository](https://github.com/riscv-software-src/riscv-isa-sim); [installation documentation](https://github.com/riscv-software-src/riscv-isa-sim#readme).
- **Discovery:** Review [official releases](https://github.com/riscv-software-src/riscv-isa-sim/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** spike. Dependencies to review: Native build dependencies; compatible target program.
- **Integration and validation:** Run a small known program and inspect completion and simulated output.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-core

- **Name / kind / aliases:** RgGen core; library; RgGen core.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-core); [source repository](https://github.com/rggen/rggen-core); [installation documentation](https://github.com/rggen/rggen-core#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-core/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Ruby library loaded by rggen. Dependencies to review: Isolated Ruby dependencies.
- **Integration and validation:** Resolve as a dependency of RgGen; test through register generation.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-default-register-map

- **Name / kind / aliases:** RgGen default register map; plugin; RgGen default register map.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-default-register-map); [source repository](https://github.com/rggen/rggen-default-register-map); [installation documentation](https://github.com/rggen/rggen-default-register-map#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-default-register-map/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen-core.
- **Integration and validation:** Validate register-map loading and reject a deliberately invalid field definition.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-systemverilog

- **Name / kind / aliases:** RgGen SystemVerilog backend; plugin; RgGen SystemVerilog backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-systemverilog); [source repository](https://github.com/rggen/rggen-systemverilog); [installation documentation](https://github.com/rggen/rggen-systemverilog#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-systemverilog/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen-core.
- **Integration and validation:** Generate SystemVerilog RTL and UVM register models; compile with a compatible downstream tool.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-verilog

- **Name / kind / aliases:** RgGen Verilog backend; plugin; RgGen Verilog backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-verilog); [source repository](https://github.com/rggen/rggen-verilog); [installation documentation](https://github.com/rggen/rggen-verilog#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-verilog/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen; rggen-verilog-rtl.
- **Integration and validation:** Generate Verilog and simulate register accesses with its matching support RTL.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-vhdl

- **Name / kind / aliases:** RgGen VHDL backend; plugin; RgGen VHDL backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-vhdl); [source repository](https://github.com/rggen/rggen-vhdl); [installation documentation](https://github.com/rggen/rggen-vhdl#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-vhdl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen; rggen-vhdl-rtl.
- **Integration and validation:** Generate VHDL and simulate register accesses with its matching support RTL.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-veryl

- **Name / kind / aliases:** RgGen Veryl backend; plugin; RgGen Veryl backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-veryl); [source repository](https://github.com/rggen/rggen-veryl); [installation documentation](https://github.com/rggen/rggen-veryl#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-veryl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen; veryl.
- **Integration and validation:** Generate Veryl and validate the emitted downstream RTL.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-c-header

- **Name / kind / aliases:** RgGen C header backend; plugin; RgGen C header backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-c-header); [source repository](https://github.com/rggen/rggen-c-header); [installation documentation](https://github.com/rggen/rggen-c-header#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-c-header/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen-core.
- **Integration and validation:** Compare generated register offsets and masks with the input specification.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-markdown

- **Name / kind / aliases:** RgGen Markdown backend; plugin; RgGen Markdown backend.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-markdown); [source repository](https://github.com/rggen/rggen-markdown); [installation documentation](https://github.com/rggen/rggen-markdown#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-markdown/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen-core.
- **Integration and validation:** Check generated tables against the same register-map data used for RTL.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-spreadsheet-loader

- **Name / kind / aliases:** RgGen spreadsheet loader; plugin; RgGen spreadsheet loader.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-spreadsheet-loader); [source repository](https://github.com/rggen/rggen-spreadsheet-loader); [installation documentation](https://github.com/rggen/rggen-spreadsheet-loader#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-spreadsheet-loader/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen-core; spreadsheet parser dependencies.
- **Integration and validation:** Load a small supported workbook and verify field widths and reset values.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-systemrdl

- **Name / kind / aliases:** RgGen SystemRDL loader; plugin; RgGen SystemRDL loader.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-systemrdl); [source repository](https://github.com/rggen/rggen-systemrdl); [installation documentation](https://github.com/rggen/rggen-systemrdl#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-systemrdl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** RgGen plugin. Dependencies to review: rggen; SystemRDL parser dependencies.
- **Integration and validation:** Compare the loaded register model with the original SystemRDL description.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-verilog-rtl

- **Name / kind / aliases:** RgGen Verilog support RTL; library; RgGen Verilog support RTL.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-verilog-rtl); [source repository](https://github.com/rggen/rggen-verilog-rtl); [installation documentation](https://github.com/rggen/rggen-verilog-rtl#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-verilog-rtl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** HDL source library; no host executable. Dependencies to review: Compatible rggen-verilog output; HDL simulator.
- **Integration and validation:** Preserve the library revision used to compile the generated register block.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## rggen-vhdl-rtl

- **Name / kind / aliases:** RgGen VHDL support RTL; library; RgGen VHDL support RTL.
- **Official sources:** [Homepage](https://github.com/rggen/rggen-vhdl-rtl); [source repository](https://github.com/rggen/rggen-vhdl-rtl); [installation documentation](https://github.com/rggen/rggen-vhdl-rtl#readme).
- **Discovery:** Review [official releases](https://github.com/rggen/rggen-vhdl-rtl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** HDL source library; no host executable. Dependencies to review: Compatible rggen-vhdl output; VHDL simulator.
- **Integration and validation:** Preserve the library revision used to compile the generated register block.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## pulp-riscv-gnu-toolchain

- **Name / kind / aliases:** PULP RISC-V GNU toolchain; compiler; PULP RISC-V GNU toolchain.
- **Official sources:** [Homepage](https://github.com/pulp-platform/pulp-riscv-gnu-toolchain); [source repository](https://github.com/pulp-platform/pulp-riscv-gnu-toolchain); [installation documentation](https://github.com/pulp-platform/pulp-riscv-gnu-toolchain#readme).
- **Discovery:** Review [official releases](https://github.com/pulp-platform/pulp-riscv-gnu-toolchain/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Target-prefixed compiler tools; inventory depends on chosen target. Dependencies to review: Native toolchain and upstream submodules.
- **Integration and validation:** Distinct provider from the general RISC-V toolchain; select the PULP target and ISA extensions explicitly.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## pulp-sdk

- **Name / kind / aliases:** PULP SDK; tool; PULP SDK.
- **Official sources:** [Homepage](https://github.com/pulp-platform/pulp-sdk); [source repository](https://github.com/pulp-platform/pulp-sdk); [installation documentation](https://github.com/pulp-platform/pulp-sdk#readme).
- **Discovery:** Review [official releases](https://github.com/pulp-platform/pulp-sdk/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Target-dependent SDK interfaces; inventory pending. Dependencies to review: pulp-riscv-gnu-toolchain; target simulator/runtime.
- **Integration and validation:** Officially linked by PULP; SDK scope and target choice must be resolved before installation.
- **Recipe:** [soc guidance](../recipes/soc/README.md).

## pulp-runtime

- **Name / kind / aliases:** PULP runtime; library; PULP runtime.
- **Official sources:** [Homepage](https://github.com/pulp-platform/pulp-runtime); [source repository](https://github.com/pulp-platform/pulp-runtime); [installation documentation](https://github.com/pulp-platform/pulp-runtime#readme).
- **Discovery:** Review [official releases](https://github.com/pulp-platform/pulp-runtime/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Target runtime library; no native host executable. Dependencies to review: pulp-riscv-gnu-toolchain; selected PULP target.
- **Integration and validation:** Compile a runtime regression for the requested target and record its exact configuration.
- **Recipe:** [soc guidance](../recipes/soc/README.md).
