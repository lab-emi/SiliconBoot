# HDL generation and language tools

Read the [common recipe](../README.md) and the selected [catalog](../../catalog/README.md) entries. These instructions define experimental checks; native support requires execution evidence.

## Installation decisions

Resolve official releases or documented source snapshots per component. Do not confuse a language frontend, an elaborator, a translator, and a synthesis plugin. Python packages need isolated environments; native frontends must retain shared libraries, headers or runtime data required by their consumers. Rust tools must match their documented toolchain and final install prefix. Record optional language features and build flags.

| Component | Dependencies or coupling to inspect | Functional acceptance |
| --- | --- | --- |
| Amaranth | Its selected synthesis/simulation backend, Python version, platform definitions | Run an official minimal design example; inspect generated HDL and simulate documented behavior |
| PyRTL | Python dependencies and selected HDL simulator | Generate HDL from an upstream example and compare simulated behavior to its reference |
| Veryl | Rust toolchain and supported emitted SystemVerilog | Build a documented project, verify elaboration diagnostics, and simulate the generated design with a recorded backend |
| slang | C++ toolchain and library consumers | Parse and elaborate official valid SystemVerilog input; verify an invalid sample produces the documented error |
| Surelog | UHDM and consumer ABI, submodule revisions | Elaborate an upstream sample and verify the produced model through its documented inspection or consumer route |
| Pyverilog | Parser/preprocessor requirements including the upstream-selected Verilog preprocessor | Parse a documented sample and inspect its AST or dataflow result with the pinned interpreter |
| Verible | Native build dependencies and public formatter/linter/parser tools | Parse a valid example, lint a known violation and format an example twice to check stability |
| svck | Verify the intended upstream identity and supported input dialect | Run its documented positive and negative checking examples; inspect diagnostics |
| vlog2verilog | Resolve the translator identity and supported input subset | Translate an upstream sample, compile the output and compare its expected behavior |
| sv2v | Supported compiler toolchain and translation limitations | Translate a documented SystemVerilog sample and verify equivalent behavior with the chosen simulator |

Use the installed tool's actual documented interface. Record executable names from its package manifest and help; do not synthesize a CLI for a library. The Yosys integrations are covered by [Yosys](../yosys/README.md).

## Verify and preserve

Keep the exact example revision, language features, expected diagnostics, generated output hashes and simulator versions with the report. Passing one sample does not establish complete language coverage. Run outside the source checkout to reveal hidden dependencies. Preserve installed schemas, runtime packages, headers required by downstream consumers and licenses; clean only owned build and download residue.
