# Netgen LVS

Catalog ID: `netgen`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve the source and host

Use [Tim Edwards's Netgen repository](https://github.com/RTimothyEdwards/netgen) and [official documentation](https://opencircuitdesign.com/netgen/). This is the circuit comparison and LVS tool. Confirm the repository, provider and executable identity before installation because a mesh-generation package uses the same name.

Resolve the release or current upstream-maintained source revision using the repository and release documentation, recording the full commit when a source snapshot is needed. Read the selected revision's Linux or macOS build guidance. For another OS or architecture, report the actual native route and validation result; do not infer support from a package name.

## Install and expose

Follow [installation](../../docs/installation.md). Record compiler, Tcl/Tk libraries and build options. Match the runtime Tcl extension to the interpreter that loads it; a system Tcl replacement can invalidate an otherwise unchanged installation. macOS toolkit selection needs particular care because the upstream guide discusses an X11-based Tcl/Tk setup.

Install the upstream executable and its Tcl resources together in the persistent prefix. Export the validated LVS entrypoint, with an explicit provider if there is a name collision. Configure the exact PDK-specific setup file for each comparison. Its device equivalence and property rules are part of the validation inputs, not interchangeable defaults. Document environment needs in project instructions without adding a launcher script.

## Acceptance

1. Confirm identity and startup from a fresh shell. Use the selected upstream interface to capture its version.
2. Compare an upstream known-matching netlist pair. Check the report's final comparison result, top-cell names, pin correspondence and device counts; the process exit code alone is insufficient.
3. Run an upstream mismatch fixture when one is provided and confirm it fails for the documented reason. This detects an empty comparison or overbroad blackboxing.
4. Compare [Magic](../magic/README.md)'s extracted PDK example against its schematic using the PDK's setup. Investigate unmatched ports, devices and properties. Preserve any approved exclusions with a reason; do not suppress mismatches simply to obtain a match.

Record input hashes, setup revision, invocation, logs and the interpreted comparison outcome under [records](../../docs/records.md). Scope `workflow_ready` to the tested PDK and circuit. Keep installed Tcl packages and setup resources; remove owned temporary material only after [validation](../../docs/validation.md).
