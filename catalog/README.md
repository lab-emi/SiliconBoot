# Component catalog

This catalog records the intended component coverage and the upstream sources an agent must review. It is documentation, not an installer. Resolved components with a linked procedure have **experimental** SiliconBoot support: a procedure is documented, while native installation, component checks and integrated workflows are **unverified**. Unresolved identities, scope or procedures remain **planned**. An official upstream repository or working upstream build does not establish SiliconBoot support.

Source review date: **2026-10-03**. Repository moves and observed default branches are recorded where checked. These observations are not version locks or promises that a branch is a stable maintenance channel. Resolve sources again when installation or upgrade is requested.

## Read the catalog

- [Analog and schematic tools](analog.md)
- [HDL languages and frontends](hdl.md)
- [Simulation and verification](verification.md)
- [Synthesis and formal verification](formal.md)
- [ASIC implementation](implementation.md)
- [Layout and KLayout extensions](layout.md)
- [EM and RF](rf.md)
- [FPGA](fpga.md)
- [SoC, RISC-V and RgGen](soc.md)
- [Orchestration and libraries](orchestration.md)
- [PDK infrastructure and process data](pdks.md)
- [Memory compilers](memory.md)
- [Optional support tools](support.md)
- [Profiles and unresolved scope](profiles.md)

Each component subsection is one record. Its heading starts with its unique canonical ID. Fields in that record override the inherited defaults below. A name, package name, repository name and installed command can differ; none is a substitute for the others. Dependencies describe the integration that needs review, not a complete, executable package dependency graph.

## Field definitions and inherited values

| Field | Meaning and inherited value |
| --- | --- |
| id | Unique lowercase component identity, as written in its heading. IDs remain stable across upstream renames. |
| kind | Tool, library, plugin, compiler or PDK. A collection is a scope record which must be expanded into constituent components. |
| aliases | The displayed upstream name plus any aliases explicitly listed in the record. Case changes alone do not create another component. |
| homepage | The project's own homepage. Where no separate homepage is listed, the linked official source repository is the project homepage. Unresolved identities have no approved homepage. |
| source_repository | Maintainer-controlled source location; record canonical redirects and identify forks. No approved repository is implied for an unresolved identity. |
| installation_docs | The linked upstream documentation or README landing page, followed by the relevant installation/build section for the selected version. A landing-page link does not mean its installation procedure has been verified. |
| latest_resolver | Apply the release and branch review rules below. The repository's official release page is a discovery starting point, not evidence that every tag or asset is a stable release. |
| channel | Official stable release preferred. Source snapshot, development, nightly and latest-published are separate explicit channels. Channel remains unresolved until an upstream policy and exact revision are recorded. |
| maintained_branch | Unknown unless a record names an upstream-documented maintenance branch. An observed default branch is recorded separately and does not fill this field automatically. |
| platforms | Native Ubuntu 24.04 x86_64 is the first intended validation target. Linux ARM64, other Linux systems, macOS Intel/ARM64 and Windows are unverified; review each component separately. WSL and emulated execution must be identified as such. |
| support_level | Experimental for resolved entries with a documented procedure; native execution remains unverified. Planned applies when identity, scope or procedure is unresolved. Verified requires recorded native component and workflow evidence; no record currently claims it. Unsupported applies to a specific incompatible platform or workflow, not merely missing tests. |
| providers | Candidate upstream source build. Upstream binary/package providers are eligible only after documentation establishes their identity, selected revision and native host compatibility. System package reuse must be recorded as external, with exact version and owner. |
| dependencies | Component IDs and system/runtime requirements named in the record. Complete the version-specific list before installation; an absent dependency is unknown, not proof that none exists. |
| abi_constraints | Native OS/architecture, compiler, C/C++ libraries and interpreter ABI must match. Plugins additionally match the exact host-tool API; model plugins match simulator and model-compiler ABI. |
| coupled_group | None declared unless noted. Absence does not waive dependency compatibility checks. |
| recipe | Linked Markdown guidance in recipes. Shared recipes cover several components and require reviewing each component's own upstream instructions. |
| recipe_revision | Documentation revision 1, reviewed 2026-10-03. Capture the repository commit or content digest used for an actual setup. |
| entrypoints | Candidate public command names or library/plugin interfaces. Relative installation paths and a complete executable inventory are pending. Publish only entrypoints inspected in the final persistent installation. |
| runtime_layout | Preserve the upstream runtime tree beneath the persistent component root, including shared data, libraries, licenses, interpreter environments and required source. Do not link to temporary build trees. PDK layout and shared family files remain intact. |
| smoke_checks | Pending. Confirm version/source identity, native architecture, executable or import availability, and operation from a fresh shell and different working directory. |
| workflow_checks | Pending. The record's validation expectation and recipe define the minimum real task; inspect numerical values, reports and artifacts. Version output or import success alone never establishes workflow readiness. |
| license | Not audited unless explicitly stated. Inspect the selected upstream revision's license files, dependency notices and model/data licenses; retain them. An unreviewed license is unknown, not unrestricted. |
| upstream_status | Maintenance status unassessed unless noted. A reachable repository does not establish ongoing maintenance. Preserve archive, migration, experimental and deprecation notices from the selected source. |
| download_hosts | Initially only the exact homepage/source/documentation hosts in the record. GitHub source records also permit github.com, api.github.com, raw.githubusercontent.com and codeload.github.com for that identified project. Additional asset, registry and redirect hosts require an explicit upstream link and recorded final URL before use. |
| cleanup_rules | Remove only owned temporary downloads and build intermediates after successful verification. Preserve runtime source, environments, model data, licenses, receipts, logs, active installations and versions referenced by any retained project generation. Do not traverse user symlinks or remove system packages/caches. |

## Release and branch review

1. Start from the component's own release and installation documentation. Select the latest official non-draft, non-prerelease release using upstream ordering. A moving branch, a nightly asset and a stable release are different channels.
2. For tag-only projects, confirm which tags upstream treats as releases. Do not sort tag strings lexicographically or treat every tag as a release.
3. If upstream offers no formal release, obtain evidence of the maintained branch from its documentation. Record the branch and full resolved commit. A default-branch observation below is only a lead for that review.
4. On an API error, rate limit, unreachable source or ambiguous release policy, record **latest_unknown**. A failed release query never authorizes silently falling back to a branch or an older package.
5. Record the discovery time, official page, canonical source URL, release/tag, full commit, submodule revisions, selected asset URL, checksum and any upstream signature evidence. A locally calculated hash is a content identifier; label it separately from an upstream-published checksum.
6. Record installed-latest status, component usability and workflow readiness independently. Incompatible latest versions remain visible as **blocked_latest_incompatible**; preserve an existing working environment. A compatible older selection needs its own named environment and explicit version differences.
7. For a PDK, compare source data, builder and model revisions separately. A new package-manager release does not update PDK data by itself. A published prebuilt snapshot must match the requested data revision or be reported under the distinct latest-published channel.

## Cross-component identities

- **netgen** identifies the netlist/LVS comparator maintained by Tim Edwards.
- **cvc** identifies circuit validity and electrical-rule checking.
- **fault** identifies AUCOHL's design-for-test package.
- **yosys-slang** retains its catalog ID after upstream's move to **sv-elab**. Review whether the selected Yosys already integrates it before adding a plugin.
- **vlog2verilog** is a separately visible Qflow entrypoint with the same source revision; do not build a second unrelated package.
- **nextpnr-ice40** and **nextpnr-ecp5** are separate architecture capabilities from one source repository. Record both when one installation supplies both.
- **sky130** and **gf180mcu** identify source families; **sky130A** and **gf180mcuD** identify the requested processed variants.
- **openram**, **dffram** and pre-generated memory libraries are different capabilities. No PDK presence implies that either compiler supports it.

## Evidence needed before support changes

A support update must name the host OS and architecture, exact component and dependency revisions, provider, recipe revision, native execution method, checks performed, outputs inspected and limitations. Tool startup, another project's published results and an untested recipe are insufficient. This documentation contains no measured installation time, disk requirement or completed native validation claim.
