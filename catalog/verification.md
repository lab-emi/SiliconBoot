# Simulation and verification

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## iverilog

- **Name / kind / aliases:** Icarus Verilog; tool; Icarus Verilog.
- **Official sources:** [Homepage](https://github.com/steveicarus/iverilog); [source repository](https://github.com/steveicarus/iverilog); [installation documentation](https://github.com/steveicarus/iverilog#readme).
- **Discovery:** Review [official releases](https://github.com/steveicarus/iverilog/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** iverilog, vvp, iverilog-vpi. Dependencies to review: Native compiler/runtime.
- **Integration and validation:** Compile and run an assertion-bearing RTL test; VPI extensions use the same build ABI.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## verilator

- **Name / kind / aliases:** Verilator; tool; Verilator.
- **Official sources:** [Homepage](https://github.com/verilator/verilator); [source repository](https://github.com/verilator/verilator); [installation documentation](https://github.com/verilator/verilator#readme).
- **Discovery:** Review [official releases](https://github.com/verilator/verilator/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** verilator; remaining public tools pending inventory. Dependencies to review: Native C++ compiler and build tools.
- **Integration and validation:** Build and execute a testbench, then inspect assertions and output values.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## ghdl

- **Name / kind / aliases:** GHDL; tool; GHDL.
- **Official sources:** [Homepage](https://github.com/ghdl/ghdl); [source repository](https://github.com/ghdl/ghdl); [installation documentation](https://github.com/ghdl/ghdl#readme).
- **Discovery:** Review [official releases](https://github.com/ghdl/ghdl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** ghdl. Dependencies to review: Ada toolchain; backend-dependent LLVM or GCC libraries.
- **Integration and validation:** Record the selected backend and simulate a VHDL testbench.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## nvc

- **Name / kind / aliases:** NVC; tool; NVC.
- **Official sources:** [Homepage](https://github.com/nickg/nvc); [source repository](https://github.com/nickg/nvc); [installation documentation](https://github.com/nickg/nvc#readme).
- **Discovery:** Review [official releases](https://github.com/nickg/nvc/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** nvc. Dependencies to review: LLVM/native build dependencies.
- **Integration and validation:** Analyze, elaborate and run a VHDL design with assertions.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## irsim

- **Name / kind / aliases:** IRSIM; tool; IRSIM.
- **Official sources:** [Homepage](https://github.com/RTimothyEdwards/irsim); [source repository](https://github.com/RTimothyEdwards/irsim); [installation documentation](https://github.com/RTimothyEdwards/irsim#readme).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/irsim/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** irsim. Dependencies to review: Tcl/Tk; process parameter files.
- **Integration and validation:** Run a switch-level example with a known transition sequence.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## cocotb

- **Name / kind / aliases:** cocotb; library; cocotb.
- **Official sources:** [Homepage](https://github.com/cocotb/cocotb); [source repository](https://github.com/cocotb/cocotb); [installation documentation](https://github.com/cocotb/cocotb#readme).
- **Discovery:** Review [official releases](https://github.com/cocotb/cocotb/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library and simulator integration. Dependencies to review: A supported HDL simulator; Python and native interface.
- **Integration and validation:** Run one test through the selected simulator and inspect the test-result report.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## cocotbext-ams

- **Name / kind / aliases:** cocotbext-ams; library; cocotbext-ams.
- **Official sources:** [Homepage](https://github.com/VLSIDA/cocotbext-ams); [source repository](https://github.com/VLSIDA/cocotbext-ams); [installation documentation](https://github.com/VLSIDA/cocotbext-ams#readme).
- **Discovery:** Review [official releases](https://github.com/VLSIDA/cocotbext-ams/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python extension; no standalone executable required. Dependencies to review: cocotb; ngspice or xyce shared interface.
- **Integration and validation:** Verify analog and digital event exchange with the selected simulator versions.
- **License evidence:** BSD-3-Clause. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## pyuvm

- **Name / kind / aliases:** pyuvm; library; pyuvm.
- **Official sources:** [Homepage](https://github.com/pyuvm/pyuvm); [source repository](https://github.com/pyuvm/pyuvm); [installation documentation](https://github.com/pyuvm/pyuvm#readme).
- **Discovery:** Review [official releases](https://github.com/pyuvm/pyuvm/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: cocotb; supported HDL simulator.
- **Integration and validation:** Resolve a compatible cocotb release and run a UVM test with checked assertions.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## covered

- **Name / kind / aliases:** Covered; tool; Covered.
- **Official sources:** [Homepage](https://github.com/chiphackers/covered); [source repository](https://github.com/chiphackers/covered); [installation documentation](https://github.com/chiphackers/covered#readme).
- **Discovery:** Review [official releases](https://github.com/chiphackers/covered/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** covered. Dependencies to review: HDL waveform/simulation input; Tcl/Tk for GUI.
- **Integration and validation:** Generate coverage from a small design and inspect the expected exercised branches.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## gtkwave

- **Name / kind / aliases:** GTKWave; tool; GTKWave.
- **Official sources:** [Homepage](https://github.com/gtkwave/gtkwave); [source repository](https://github.com/gtkwave/gtkwave); [installation documentation](https://github.com/gtkwave/gtkwave#readme).
- **Discovery:** Review [official releases](https://github.com/gtkwave/gtkwave/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** gtkwave; converter tools pending inventory. Dependencies to review: GTK and waveform readers.
- **Integration and validation:** Open a generated waveform and verify signal names and transitions.
- **Recipe:** [verification guidance](../recipes/verification/README.md).

## surfer

- **Name / kind / aliases:** Surfer; tool; Surfer.
- **Official sources:** [Homepage](https://gitlab.com/surfer-project/surfer); [source repository](https://gitlab.com/surfer-project/surfer); [installation documentation](https://gitlab.com/surfer-project/surfer#readme).
- **Discovery:** Review the linked upstream release/download documentation. Release policy and maintained branch **unknown**; resolve them before selecting a snapshot.
- **Interfaces / dependencies:** surfer. Dependencies to review: Rust/native graphics dependencies.
- **Integration and validation:** Load a waveform with known transitions and verify native GUI behavior.
- **Recipe:** [verification guidance](../recipes/verification/README.md).
