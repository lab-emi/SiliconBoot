# Validation and capability reporting

Validation answers three separate questions: which exact component is installed, whether it performs a real task, and whether the selected combination supports a requested workflow. Read the [record contract](records.md) before reporting results.

## Three layers

| Layer | Required evidence | What it establishes |
| --- | --- | --- |
| Identity and startup | Actual provider path, version/revision evidence, architecture, executable or import location, runtime dependencies | The intended component can be located and started |
| Component function | Upstream-supported example, expected result, actual outputs and engineering checks | One stated component capability works on this host |
| Workflow | Exact tools, PDK/technology/corner, source inputs, reports and acceptance criteria | One stated combination performs the tested workflow |

Do not assume every program supports the same version option. Derive the identity check from upstream documentation. For libraries, use the recorded interpreter and inspect the loaded package location. For plugins, load them through the actual host tool. For PDKs, verify resources and consumers; a directory listing is not a functional check.

## Before execution

1. Record the host and native execution context, candidate or active generation, exact component revisions and dependencies.
2. Select an example from the frozen upstream revision or an authorized project input. Record its source, immutable revision and input hashes. Keep original user sources unchanged.
3. Define expected artifacts, report fields, acceptable numerical tolerances, and failure conditions before running. Identify which checks are required for activation and which are optional.
4. Create a run directory with artifacts, reports and logs. Record the generation lease and the absolute runtime paths used for the entire run.
5. Record the actual executable/interpreter, argument list, working directory and relevant environment overrides as evidence. Do not record credentials or unrelated secret environment values.

Generated test inputs and upstream examples live in the user's project or persistent installation as appropriate. This repository contains prose scenarios only.

## Cross-tool acceptance

| Workflow | Minimum real check | Required interpretation |
| --- | --- | --- |
| Xschem → ngspice | Netlist a small supported PDK schematic and simulate a declared corner | Check pin connectivity, model includes, convergence, expected vectors and numerical values |
| Yosys → OpenROAD or LibreLane | Synthesize and implement a small supported RTL example using one selected library/platform | Inspect mapped cells, netlist, constraints, placement/routing outputs and timing reports; state which stages actually ran |
| KLayout / Magic / Netgen | Use one known design with the chosen PDK's supported decks | Report DRC, LVS and PEX independently; inspect violation counts, comparison outcome and extracted data |
| IHP model integration | Simulate a circuit that loads the native OSDI or Xyce model plugin being claimed | Identify the loaded binary and ABI; check models, corners, convergence and expected electrical results |
| OpenRAM | Compile the smallest configuration supported by the actual technology port | Inspect all required views and their interfaces; report characterization, DRC and LVS separately |
| DFFRAM | Generate a small supported standard-cell memory with the actual platform/flow | Inspect views, functional behavior and timing/physical reports; retain upstream limitations |
| HDL simulation | Compile/elaborate and run a self-checking upstream design | Count executed tests and assertions; detect empty or prematurely terminated regressions |
| Formal | Run a known proof and counterexample case | Record assumptions, bounds, engines, solver status and trace; do not promote bounded results to unbounded proofs |
| FPGA | Synthesize, route and pack a supported device example | Inspect target identity, routing completion, timing and bitstream; physical hardware remains a separate check |
| EM/RF | Run a documented numerical example through the selected native solver | Check units, mesh/boundary settings, convergence and a reference observable with declared tolerance |

For physical verification, an open deck may have incomplete coverage. Record the deck revision and its documented scope. A clean report establishes only the checks that deck actually ran. If a deliberately invalid upstream fixture exists, verify that it triggers the expected error so an unloaded or empty deck cannot appear successful.

## Environment integrity

Before activation, inspect every exported entrypoint and installation link. Detect missing or circular links, unexpected targets, non-executables, wrong architectures, interpreter paths in temporary directories, and command-name collisions. Validate relative links from the actual generation directory, not just through the current view. After activation, also verify each owned `~/bin` symlink through the selected generation and confirm that unrelated existing entries were preserved.

Repeat a representative component check in a fresh instance of the detected default login shell and a different working directory, using only the documented environment. Verify the recorded bashrc, zshrc or fish configuration adds `~/bin` from a baseline PATH, preserves other entries and remains free of duplicates across repeated startup or sourcing. Check interactive and applicable login behavior separately. Record unsupported shells, aliases, functions and startup overrides as limitations. Follow [default-shell PATH setup](project-layout.md#default-shell-path). Do not inherit the build session's PATH, library paths or active language environment. Confirm GUI resources when GUI readiness is claimed. Verify all PDK internal links, shared files, selected device models, standard-cell views and required corners.

For Python components, check the recorded uv identity, environment path, actual interpreter build and provider, imported package locations, and native binding compatibility. Confirm that each environment matches its frozen dependencies and that normal tool invocation leaves the environment and lock unchanged. Verify upstream-managed runtime exceptions through their actual host tool. Include the uv prerequisite's environment creation and recreation evidence from its [recipe](../recipes/uv/README.md).

After removing owned temporary files, repeat startup and the relevant functional check to detect accidental dependence on cleaned source or build files. Keep installed runtime source when upstream needs it.

## Results and activation

Use `pass`, `fail`, `blocked`, and `not_run` for individual checks, with a reason for every non-pass. A missing log or a skipped check is not a pass. Record real exit status even when a report shows an engineering failure after successful process completion.

Report these claims independently:

- `installed_latest`: `yes` only relative to a successful, dated official resolution and the selected channel. Use `unknown` when discovery failed. It does not imply future freshness.
- `component_usable`: `yes` only for the named component capabilities actually exercised on this host.
- `workflow_ready`: `yes` only for each explicitly tested combination and its stated limits.

For a first bootstrap, a verified independent subset can become a `partial` generation with all omissions listed. During upgrade, keep the old generation until required affected workflows pass. If latest components cannot work together, record `blocked_latest_incompatible` and preserve the prior working environment. A separately requested compatible environment must identify every component that is older than the latest official selection.

## Final handoff

Summarize the existing project directory, canonical tool and PDK roots, public binary directory, default shell and startup configuration, active generation, selected scope, versions, per-component outcomes, per-workflow outcomes, skipped checks, system changes, temporary-file cleanup and remaining blockers. Link the reports. Do not describe native installation as verified based only on this repository's documentation review. Verification here is engineering evidence for a tested setup, not fabrication signoff.
