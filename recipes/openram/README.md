# OpenRAM

Catalog ID: `openram`. Kind: SRAM compiler. Recipe status: experimental; no native compilation has been validated by this repository. Read [memory compilers](../../docs/memory-compilers.md) before installation.

## Resolve compiler, technology and channel

Start with the [official repository](https://github.com/VLSIDA/OpenRAM), [setup guide](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/basic_setup.md), [usage guide](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/basic_usage.md) and [porting guide](https://github.com/VLSIDA/OpenRAM/blob/stable/PORTING.md). Inspect official releases first. When upstream publishes no formal release, resolve the documented `stable` branch to a full commit; the branch name alone is not a fixed version. Read documentation at that same revision. A release that fails the requested workflow is an incompatibility to report, not permission to switch channels silently.

Check the technology port before accepting a requested compiler/PDK combination. The [technology list](https://github.com/VLSIDA/OpenRAM/blob/stable/docs/source/index.md) includes SKY130. The setup guide currently states that GF180MCU SRAM generation is unsupported and distinguishes experimental ROM work. Do not infer an IHP SRAM port from the presence of prebuilt SRAMs in its PDK. Report missing ports as unsupported rather than attempting a port during setup.

## Native installation and persistent runtime

Apply [installation](../../docs/installation.md). The current setup guide uses Nix to provide external tools and describes Python dependencies plus additional SKY130 SRAM technology material. Inspect its dependency closure and actual versions. Native execution still requires matching host architecture throughout; a container route does not meet a native request.

Keep the compiler source, technology directories, required cell views and Python environment at stable absolute paths in the persistent installation. Preserve any Nix roots needed to keep the tool closure available. A release that relies on Nix-managed pinned tools must record them individually and disclose differences from latest versions. Do not replace those tools ad hoc and assume compatibility.

Install SKY130 technology material using that revision's documented procedure into the candidate installation. Record the SRAM cell source independently of the general PDK. Document `OPENRAM_HOME`, `OPENRAM_TECH` and any interpreter-specific paths only for the OpenRAM process. Keep them out of global Python configuration.

Export an upstream-provided console entrypoint if available. Otherwise record the persistent interpreter and upstream compiler entry file as a two-part invocation; do not invent an executable or write a wrapper. Source needed at runtime is installation content, not cleanup residue.

## Acceptance

1. Confirm interpreter, compiler identity, technology discovery and external-tool resolution in a fresh shell.
2. Select the smallest currently supported upstream example for the actual technology. Record words, width, ports, banks, bitcell type, corners, voltages and temperatures. OpenRAM configuration is Python-based; retain the upstream configuration with its provenance in the downstream run, without adding configuration code to this repository.
3. Run full physical generation with the requested validation and characterization modes. Record explicitly whether timing is simulated or analytically estimated and whether DRC/LVS/PEX were performed.
4. Inspect the expected GDS, SPICE, Verilog, LEF, Liberty, log and configuration outputs against the selected mode. Check consistent macro names, pin ordering, dimensions, power pins and corners across views; a nonempty directory is insufficient.
5. Parse DRC/LVS results, inspect timing data and run the upstream functional memory verification available for that configuration. Failed, skipped and unavailable checks remain distinct.

Keep results in `runs/<run-id>/artifacts/memory/`. Complete [records](../../docs/records.md) and the memory acceptance record before proposing an `ip/memory/manifests/` entry. Cleanup retains technology cells, compiler sources, package roots and runtime dependencies. A passed small compile validates that exact combination only.
