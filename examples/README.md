# Guided examples

These examples are walkthrough specifications for an agent. They contain no circuit source, RTL, executable test, or installation program. Obtain test inputs from the selected component's official, revision-pinned examples and keep generated work in the user's project. Read [validation](../docs/validation.md) and the relevant recipes first.

## Analog setup with a PDK

**Request:** Set up the analog profile for a chosen native host and sky130A, then verify a small PDK circuit.

1. Inspect the host and project. Resolve Xschem, ngspice, physical-verification tools, PDK builder/package manager, raw PDK data and model dependencies independently.
2. Record which selected components have a usable native path and which remain blocked. Freeze exact inputs before building.
3. Install at persistent prefixes, preserving the PDK's technology setup and models. Netlist an upstream-supported schematic into a new run directory.
4. Simulate a stated corner and compare expected values with explicit tolerances. If requested, perform the corresponding DRC, LVS or PEX checks with the supported decks and inspect each result.
5. Activate the verified subset, record any missing analog-profile items, produce project instructions and clean up owned temporary files.

**Acceptance:** Recorded model and corner actually load; numerical checks pass; advertised physical checks have their own reports; the same example works from a new shell after cleanup. If only this small workflow is tested, do not label the entire analog profile verified.

## Digital implementation

**Request:** Set up the digital profile and implement a small official example with a selected PDK/library.

Resolve Yosys, the needed frontend, OpenSTA, OpenROAD or LibreLane, and all platform data as one workflow plan. Compare latest versions with documented compatibility requirements. Synthesize and implement the recorded example and inspect mapped cells, constraints, routing completion and timing. Store generated netlists, physical views and reports in the run directory.

**Acceptance:** Each claimed stage has valid artifacts and parsed results. Unmet timing remains a failed engineering check even if all tools exit successfully. Latest-version incompatibility preserves any existing working generation.

## Compile a memory

**Request:** Determine whether a specific memory size, port arrangement and PDK are supported, then compile the smallest supported validation configuration.

Use the [memory guide](../docs/memory-compilers.md) to choose a real compiler and technology port. Resolve the compiler, PDK, port and backend versions before building. Use the compiler's current supported example; inspect every required view and report characterization, DRC, LVS and timing independently.

**Acceptance:** A compiler ran with a documented technology port and produced the expected views. A pre-generated macro library or Python import cannot satisfy this request. Keep results under the run; add a macro manifest only after the user or design process accepts the macro.

## Upgrade, recover and hand off

**Request:** Upgrade one component, preserve a usable environment, then verify another agent can find it.

Use the [upgrade prompt](../prompts/upgrade.md). Resolve affected dependencies and create a separate installation and candidate generation. If a required check fails, keep the previous generation and retain diagnostic records. If the candidate passes, activate it and retain the previous generation. Use the [rollback prompt](../prompts/rollback.md) when a rollback is explicitly requested.

**Acceptance:** One generation is selected consistently across tools, PDKs and binary providers. Existing runs keep their original generation. A new agent can read the project's existing AGENTS.md together with .siliconboot/AGENTS.md and .siliconboot/ENVIRONMENT.md, locate exact installations and rerun the documented checks without access to the previous session's environment.
