# Yosys

Catalog ID: `yosys`. Recipe status: experimental; no native installation has been validated by this repository.

## Resolve source and dependencies

Use the [official repository and releases](https://github.com/YosysHQ/yosys) and [installation documentation](https://yosyshq.readthedocs.io/projects/yosys/en/latest/getting_started/installation.html). Resolve the newest official non-prerelease release and read build instructions from that exact revision. Development documentation may describe a newer build system and dependency minimums than the chosen release.

On macOS, check Homebrew first under [the macOS policy](../../docs/installation.md#macos-check-homebrew-first), including the required plugins, ABC and runtime features. Use a matching native package when eligible; otherwise prefer an official matching binary or documented installer, then evaluate a native source build. Linux source builds are a candidate when no suitable asset exists. Other hosts need a matching native provider and explicit local validation. A distribution package must be compared with the resolved version. An upstream-endorsed binary bundle is a separate provider: inventory the actual bundled component revisions and report any version mismatch.

Follow [installation](../../docs/installation.md). Resolve compiler, parser generators, build system, Python and optional Tcl/readline dependencies from the selected revision. Record the bundled ABC and other submodule revisions; the Yosys release name does not identify an independently installed ABC. Preserve release-provided submodule content or fetch exactly its recorded revisions.

## ABI and runtime

Install the executable, technology mapping files, share data and documented supporting executables in one persistent prefix. Register only entrypoints actually installed. Select the intended ABC provider explicitly if a second ABC installation exists.

Treat native Yosys plugins and their frontends as a coupled build group. Record the Yosys revision, plugin revision, compiler ABI and any external frontend/library versions. Rebuild or revalidate plugins after a host Yosys change. A plugin that loads is not yet proven to synthesize its supported language. Keep plugin paths in project configuration and activation instructions, without generating a custom launcher.

## Acceptance

1. Obtain actual version information and synthesize a small official example into a project run directory. Check its selected top, nonempty netlist, cell statistics and diagnostic report; unexpected black boxes or unresolved cells fail this check.
2. If an optional frontend is selected, use its official example requiring that frontend, then synthesize it. Record the language feature and actual plugin loaded.
3. For ASIC use, map an upstream example to the selected PDK's Liberty data. Check that mapped cells belong to that library and that the mapped netlist can be read with the corresponding library models.
4. Pass that mapped design to [digital-flow acceptance](../digital-flow/README.md). A synthesis result alone cannot establish place-and-route or timing readiness.
5. Repeat a synthesis from a fresh shell and another working directory using only installed resources.

Complete [records](../../docs/records.md) and [validation](../../docs/validation.md). Preserve installed share data, plugins and ABC runtime files; remove only owned build staging. When latest Yosys breaks a required plugin, record `blocked_latest_incompatible` and preserve the prior environment.
