# HDL languages and frontends

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## amaranth

- **Name / kind / aliases:** Amaranth; library; Amaranth.
- **Official sources:** [Homepage](https://github.com/amaranth-lang/amaranth); [source repository](https://github.com/amaranth-lang/amaranth); [installation documentation](https://github.com/amaranth-lang/amaranth#readme).
- **Discovery:** Review [official releases](https://github.com/amaranth-lang/amaranth/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: yosys and a backend as required by the selected workflow.
- **Integration and validation:** Elaborate a circuit and compare simulated behavior with the emitted RTL.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## pyrtl

- **Name / kind / aliases:** PyRTL; library; PyRTL.
- **Official sources:** [Homepage](https://github.com/UCSBarchlab/PyRTL); [source repository](https://github.com/UCSBarchlab/PyRTL); [installation documentation](https://github.com/UCSBarchlab/PyRTL#readme).
- **Discovery:** Review [official releases](https://github.com/UCSBarchlab/PyRTL/releases) and upstream tag policy. Observed default branch: **development**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Python.
- **Integration and validation:** Generate and simulate a small design with a known expected result.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## veryl

- **Name / kind / aliases:** Veryl; compiler; Veryl.
- **Official sources:** [Homepage](https://github.com/veryl-lang/veryl); [source repository](https://github.com/veryl-lang/veryl); [installation documentation](https://github.com/veryl-lang/veryl#readme).
- **Discovery:** Review [official releases](https://github.com/veryl-lang/veryl/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** veryl. Dependencies to review: Rust build/runtime requirements.
- **Integration and validation:** Translate a small design and validate emitted SystemVerilog with a chosen simulator.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## slang

- **Name / kind / aliases:** slang; compiler; slang.
- **Official sources:** [Homepage](https://github.com/MikePopoloski/slang); [source repository](https://github.com/MikePopoloski/slang); [installation documentation](https://github.com/MikePopoloski/slang#readme).
- **Discovery:** Review [official releases](https://github.com/MikePopoloski/slang/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** slang. Dependencies to review: Native C++ runtime.
- **Integration and validation:** Parse and elaborate valid and deliberately invalid SystemVerilog inputs.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## surelog

- **Name / kind / aliases:** Surelog; compiler; Surelog.
- **Official sources:** [Homepage](https://github.com/chipsalliance/Surelog); [source repository](https://github.com/chipsalliance/Surelog); [installation documentation](https://github.com/chipsalliance/Surelog#readme).
- **Discovery:** Review [official releases](https://github.com/chipsalliance/Surelog/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** surelog. Dependencies to review: UHDM and native build dependencies.
- **Integration and validation:** Preserve UHDM dependency revisions and check elaborated design structure.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## pyverilog

- **Name / kind / aliases:** Pyverilog; library; Pyverilog.
- **Official sources:** [Homepage](https://github.com/PyHDI/Pyverilog); [source repository](https://github.com/PyHDI/Pyverilog); [installation documentation](https://github.com/PyHDI/Pyverilog#readme).
- **Discovery:** Review [official releases](https://github.com/PyHDI/Pyverilog/releases) and upstream tag policy. Observed default branch: **develop**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: iverilog for preprocessing where required.
- **Integration and validation:** Parse a preprocessed design and inspect its syntax tree.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## verible

- **Name / kind / aliases:** Verible; tool; Verible.
- **Official sources:** [Homepage](https://github.com/chipsalliance/verible); [source repository](https://github.com/chipsalliance/verible); [installation documentation](https://github.com/chipsalliance/verible#readme).
- **Discovery:** Review [official releases](https://github.com/chipsalliance/verible/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** verible-verilog-lint, verible-verilog-format; remaining public tools pending inventory. Dependencies to review: Native build dependencies.
- **Integration and validation:** Run lint and formatting checks on known valid and invalid fixtures.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## svck

- **Name / kind / aliases:** svck; tool; svck.
- **Official sources:** [Homepage](https://github.com/AsFigo/svck); [source repository](https://github.com/AsFigo/svck); [installation documentation](https://github.com/AsFigo/svck#readme).
- **Discovery:** Review [official releases](https://github.com/AsFigo/svck/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** svck.py through its isolated Python environment. Dependencies to review: verible.
- **Integration and validation:** Use the documented Python entrypoint and verify a known lint violation.
- **License evidence:** MIT. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## vlog2verilog

- **Name / kind / aliases:** vlog2verilog; tool; vlog2verilog.
- **Official sources:** [Homepage](https://github.com/RTimothyEdwards/qflow); [source repository](https://github.com/RTimothyEdwards/qflow); [installation documentation](https://github.com/RTimothyEdwards/qflow#readme).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/qflow/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** vlog2Verilog; confirm installed capitalization. Dependencies to review: qflow conversion resources.
- **Integration and validation:** Part of the Qflow source tree; share its revision and avoid duplicate installation.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).

## sv2v

- **Name / kind / aliases:** sv2v; compiler; sv2v.
- **Official sources:** [Homepage](https://github.com/zachjs/sv2v); [source repository](https://github.com/zachjs/sv2v); [installation documentation](https://github.com/zachjs/sv2v#readme).
- **Discovery:** Review [official releases](https://github.com/zachjs/sv2v/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** sv2v. Dependencies to review: Haskell build dependencies.
- **Integration and validation:** Translate SystemVerilog and compare simulation with the original design.
- **Recipe:** [hdl guidance](../recipes/hdl/README.md).
