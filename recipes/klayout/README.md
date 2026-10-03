# KLayout

Catalog ID: `klayout`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve the source and host

Use the [official download and build page](https://www.klayout.de/build.html), [manual](https://www.klayout.de/doc.html) and [source](https://github.com/KLayout/klayout). Resolve the current release and an asset for the exact OS and CPU; verify the signatures or checksums actually published for that asset. Record an independently computed digest separately from upstream verification.

Native Linux, macOS and Windows distributions must be evaluated individually. On Apple Silicon, verify the executable architecture; a translated Intel build does not establish ARM64 support. Read the selected release's build instructions when no suitable asset exists. The Python package and the desktop application are distinct providers with different capabilities.

## Install and expose

Follow [installation](../../docs/installation.md). A source build must record Qt, Ruby, Python and compiler choices. Match any installed extension to the interpreter embedded in that application; the project's general Python environment does not determine KLayout's Python ABI.

Preserve the application bundle or installed directory, shared resources and libraries. Link its documented public executable only if that entrypoint works through a symlink; otherwise document the official launch method and limitation. Keep PDK technology files, layer maps, libraries and rule decks in their installed PDK layout. Put project-specific configuration in `config/tools/`. Do not copy a whole user plugin directory into a shared installation or install unrelated plugins implicitly.

Each requested plugin needs its own official source, revision, compatible host version and acceptance result. Loading an extension successfully is weaker evidence than exercising its requested operation.

## Acceptance

1. Open an upstream or PDK example layout. Confirm the expected top cell, hierarchy, database unit and layer interpretation. Save a copy into the run directory and reopen it.
2. Run a documented PDK DRC example with its exact rule deck. Parse the report database and record total findings by rule, the design's expected result and any documented exclusions. Include an upstream known-failing fixture where supplied to prove the checker is active.
3. If the PDK supplies a KLayout LVS workflow, compare the example's extracted connectivity to its schematic. Record compared top cells, device counts and final match status. If it has no applicable LVS or PEX deck, mark that check unavailable rather than borrowing rules from another process.
4. Check GUI and batch execution separately from a fresh shell. Keep rule invocation details, report databases and screenshots when useful.

Use [validation](../../docs/validation.md) and [records](../../docs/records.md). Preserve installed packages, technology resources and licenses; discard only owned staging files after the installed application has passed these checks.
