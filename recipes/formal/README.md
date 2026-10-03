# Logic optimization and formal verification

Follow the [common recipe](../README.md) and each component's official [catalog](../../catalog/README.md) sources. Pair this recipe with [Yosys](../yosys/README.md) for Yosys-dependent tools. Native status remains unverified until evidence is recorded.

## Resolve the complete chain

Resolve the frontend, synthesis engine, formal runner, solver, and plugins as separate inputs. Inspect their documented compatibility and included dependency revisions. A standalone latest ABC and the ABC revision expected by a particular Yosys build can differ; record each provider and route names explicitly. Do not overwrite bundled dependencies or silently relabel them latest.

The catalog retains `yosys-slang` as a stable identity for the upstream project now called sv-elab. Inspect the selected Yosys release for an integrated frontend before installing a separate plugin. Record the integrated or external provider and its actual revision; a newer plugin must not silently override the integrated implementation. Apply the frontend check to whichever provider is selected.

| Component | Installation and coupling | Functional acceptance |
| --- | --- | --- |
| ABC | Native toolchain and any caller's expected revision/interface | Optimize an upstream circuit and use the documented equivalence check to validate the result |
| Kepler-formal | Resolve the exact upstream identity, solver and synthesis integration first | Run official passing and failing formal examples; inspect proof/counterexample reports |
| ghdl-yosys-plugin | Match GHDL backend and Yosys plugin ABI | Load the plugin in the recorded Yosys and synthesize an upstream VHDL example |
| yosys-slang / sv-elab | Resolve the integrated or external provider; match slang and any Yosys plugin ABI | Load the frontend and synthesize a supported SystemVerilog example, checking the resulting hierarchy and cells |
| eqy | Yosys, solvers and partitioning dependencies documented by the selected release | Check one equivalent pair and one intentionally different upstream pair; inspect partition results |
| sby | Yosys and the selected engines/solvers | Run a bounded or unbounded upstream proof plus a counterexample case; preserve engine status and traces |
| mcy | Tool dependencies and mutation-testing example configuration | Run a small upstream mutation example; verify executed, detected, surviving and failed classifications |
| Yices2 | Native libraries and the supported solver interface | Run documented satisfiable and unsatisfiable problems; inspect results and exit status |

## Acceptance and retention

Record proof mode, assumptions, bounds, engine and solver versions, expected result and actual result. A bounded pass must retain its bound. `unknown`, timeout, an unexecuted engine, and proof failure are different outcomes; none establishes an unbounded proof. Keep the report and counterexample artifacts in the run directory.

Rebuild ABI-dependent plugins when their host changes and validate them before replacing the generation. Preserve plugin modules, solvers, installed Python sources, runtime libraries and licenses. Unavailable optional solvers block only the workflows that need them. Retain the old working combination if latest dependencies are incompatible.
