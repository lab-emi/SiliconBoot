# IHP PDK family

Catalog IDs: `ihp-sg13g2`, `ihp-sg13cmos5l`. Coupled group: the complete IHP PDK checkout and its host-built models. Recipe status: experimental; no native workflow has been validated by this repository.

## Resolve source and channel explicitly

Use the [IHP-owned repository](https://github.com/IHP-GmbH/IHP-Open-PDK) and [installation guide](https://ihp-open-pdk-docs.readthedocs.io/en/latest/install/installation.html). Inspect releases, branch documentation and the tree of the exact resolved commit. The checked guide selects `dev` for its simulation example because the example and `main` models differ. Record this as a development source snapshot, including full commit and submodule revisions, rather than relabeling it a stable release.

The [official dev README](https://github.com/IHP-GmbH/IHP-Open-PDK/blob/dev/README.md) describes both SG13G2 and SG13CMOS5L and treats the open PDK as a preview. It distinguishes CMOS5L's reduced metal stack and devices. Availability on this branch does not establish availability in an older release or on `main`. Check each requested variant at resolution time. If absent, report that source/channel combination as unavailable and retain the user's selected channel.

## Native dependencies and complete layout

The upstream guide is based on Ubuntu Linux LTS. Establish native support for every consuming tool on other hosts; PDK data availability alone is insufficient. Follow [installation](../../docs/installation.md) and [PDK infrastructure](../pdk-infrastructure/README.md).

Keep the entire checkout, both present variant directories, `versions.txt`, submodules and shared files under one persistent family installation. Preserve relative links. Expose only variants that actually exist, while retaining common files at their original relative location. Record one coupled source identity so an upgrade cannot combine mismatched variant trees.

Read tool configuration and model compilation instructions at that commit. The upstream guide associates ngspice with OpenVAF/OSDI and Xyce with ADMS-based model compilation. Inspect each tool's current required interface and compiler compatibility; build models for the exact OS, architecture and simulator ABI. A bundled shared object is not presumed portable. Record model sources, compiler, simulator, flags and artifact hashes as part of the installation identity.

Create derived model artifacts only in a new candidate family installation, retaining the pristine source identity and modification record. Match KLayout's embedded Python dependencies to its actual interpreter. Describe required PDK and tool paths in project activation instructions; do not create wrapper scripts or change global startup files.

## Acceptance

1. Check all links, common metadata, variant-specific technology files, model includes and requested library corners. Treat upstream `versions.txt` as compatibility evidence and compare it with actual installed versions.
2. For each selected variant, run its own small device example with the correct configuration. For SG13G2, include a device that requires its compiled model plugin when testing that interface. For CMOS5L, use an example and rules documented for CMOS5L; do not substitute SG13G2 layers or unavailable devices.
3. Exercise ngspice OSDI loading and, if requested, Xyce plugin loading separately. Record finite expected results and loading diagnostics, not merely successful compilation.
4. Run the available variant-specific DRC and LVS examples and inspect reports. Mark any absent extraction or digital integration unavailable. Prebuilt SRAM library views do not establish OpenRAM support.
5. Repeat one simulation from a fresh shell through the candidate project view, with build staging unavailable.

Record separate variant outcomes and the shared installation receipt under [records](../../docs/records.md). Keep the previous complete family installation until affected workflows pass [validation](../../docs/validation.md). Cleanup must preserve siblings, common metadata, model plugins, technology sources and all referenced versions.
