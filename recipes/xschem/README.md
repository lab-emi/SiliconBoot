# Xschem

Catalog ID: `xschem`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve the source and host

Use the [official homepage](https://xschem.sourceforge.io/stefan/index.html) and [manual](https://xschem.sourceforge.io/stefan/xschem_man/xschem_man.html). Discover the current released source through the homepage's release link. Record the release identifier and archive digest. For an explicitly selected development snapshot, follow the homepage's current development source and record its full revision. The homepage identifies repo.hu as primary development and [Codeberg](https://codeberg.org/stef_xschem/xschem) as the replacement for the GitHub mirror; do not infer the current release from a mirror's latest commit.

Check the selected revision's installation instructions for the actual OS and CPU. A Linux source build is the first candidate. macOS needs its documented X11 and Tcl/Tk integration. Windows binaries and Cygwin builds must be distinguished; record any compatibility layer. A working window on another platform is not evidence for this host.

## Install and expose

Follow [installation](../../docs/installation.md) before changing the host. Resolve the C compiler, X11, Tcl/Tk, Xpm, parser tools and other dependencies from the chosen source. Record the Tcl/Tk and X11 providers, especially on macOS where incompatible toolkit variants can coexist.

Install the upstream executable, symbol libraries, Tcl resources and documentation together in a persistent prefix. Link only the actual public executable through the generation's `bin` view and publish its symlink in `~/bin`. Document the selected PDK's Xschem configuration and symbol search paths in the project's activation instructions. Keep project overrides under `config/tools/`; do not edit the shared PDK or the user's global Xschem startup files. Use documented upstream configuration or explicit process environment; do not create a custom launcher.

## Acceptance

1. From a fresh shell and an unrelated working directory, resolve the executable and obtain its reported version using the selected revision's documented interface.
2. Open an upstream example schematic, check symbol resolution and generate a nonempty SPICE netlist into a project run directory. If display access is unavailable, record GUI validation as not run and use documented batch netlisting where available.
3. For a selected PDK, use its own small simulation example. Confirm the expected device models, subcircuit names and model corner in the generated netlist. Run that netlist with the selected [ngspice](../ngspice/README.md), inspect convergence diagnostics, and compare measured values against the example's expected result or a stated circuit calculation and tolerance.
4. Record schematic, configuration, netlist, simulation logs and result paths. Merely displaying the schematic does not validate simulation.

Complete [validation](../../docs/validation.md) and [records](../../docs/records.md). Preserve installed libraries and runtime resources during cleanup; remove only owned staging and build material after the fresh-shell checks pass.
