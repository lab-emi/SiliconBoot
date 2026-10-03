# PDK infrastructure and process data

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

PDK data, builder code, package-manager code and compiled device models have separate revisions. Preserve all required process-family siblings and shared files. Libraries included with a PDK are not memory compilers. The [IHP official development README](https://github.com/IHP-GmbH/IHP-Open-PDK/blob/dev/README.md) documents SG13CMOS5L; its development-channel status must remain visible.

## ciel

- **Name / kind / aliases:** ciel; tool; ciel.
- **Official sources:** [Homepage](https://github.com/fossi-foundation/ciel); [source repository](https://github.com/fossi-foundation/ciel); [installation documentation](https://github.com/fossi-foundation/ciel#readme).
- **Discovery:** Review [official releases](https://github.com/fossi-foundation/ciel/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** ciel. Dependencies to review: open-pdks when building; Python.
- **Integration and validation:** Package-manager revision and PDK data revision are separate facts.
- **License evidence:** Apache-2.0. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [pdk-infrastructure guidance](../recipes/pdk-infrastructure/README.md).

## open-pdks

- **Name / kind / aliases:** open_pdks; tool; open_pdks.
- **Official sources:** [Homepage](https://github.com/fossi-foundation/open-pdks); [source repository](https://github.com/fossi-foundation/open-pdks); [installation documentation](https://github.com/fossi-foundation/open-pdks#readme).
- **Discovery:** Review [official releases](https://github.com/fossi-foundation/open-pdks/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Build system; installed helper inventory pending. Dependencies to review: magic; selected PDK source and technology tools.
- **Integration and validation:** Record builder revision separately from every source-data revision and generated model ABI.
- **Recipe:** [pdk-infrastructure guidance](../recipes/pdk-infrastructure/README.md).

## sky130

- **Name / kind / aliases:** SKY130 / sky130A; pdk; sky130A; SkyWater 130 nm.
- **Official sources:** [Homepage](https://github.com/google/skywater-pdk); [source repository](https://github.com/google/skywater-pdk); [installation documentation](https://github.com/google/skywater-pdk#readme).
- **Discovery:** Review [official releases](https://github.com/google/skywater-pdk/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** PDK data; no executable. Dependencies to review: open-pdks or ciel provider; selected tool integrations.
- **Integration and validation:** sky130A is a processed installation variant; source data and builder must both be recorded.
- **Recipe:** [sky130 guidance](../recipes/sky130/README.md).

## gf180mcu

- **Name / kind / aliases:** GF180MCU / gf180mcuD; pdk; gf180mcuD; GlobalFoundries 180 nm.
- **Official sources:** [Homepage](https://github.com/google/gf180mcu-pdk); [source repository](https://github.com/google/gf180mcu-pdk); [installation documentation](https://github.com/google/gf180mcu-pdk#readme).
- **Discovery:** Review [official releases](https://github.com/google/gf180mcu-pdk/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** PDK data; no executable. Dependencies to review: open-pdks or ciel provider; selected tool integrations.
- **Integration and validation:** The original google/gf180mcu-pdk source was archived on 2026-09-23. Resolve maintained-source identity from official evidence before claiming latest; gf180mcuD is a processed variant. Audit all model/cell-library revisions.
- **Recipe:** [gf180mcu guidance](../recipes/gf180mcu/README.md).

## ihp-sg13g2

- **Name / kind / aliases:** IHP SG13G2; pdk; IHP SG13G2.
- **Official sources:** [Homepage](https://github.com/IHP-GmbH/IHP-Open-PDK); [source repository](https://github.com/IHP-GmbH/IHP-Open-PDK); [installation documentation](https://ihp-open-pdk-docs.readthedocs.io/en/latest/install/installation.html).
- **Discovery:** Review official release policy and process requirements. Observed default: **main**; the linked installation guide explicitly uses **dev** for its current example. Record the selected channel and full commit; no silent branch switch.
- **Interfaces / dependencies:** PDK data; no executable. Dependencies to review: Native model compiler and selected simulation/layout tools.
- **Integration and validation:** Coupled group ihp-open-pdk: preserve siblings, versions.txt and relative links.
- **Recipe:** [ihp guidance](../recipes/ihp/README.md).

## ihp-sg13cmos5l

- **Name / kind / aliases:** IHP SG13CMOS5L; pdk; IHP SG13CMOS5L.
- **Official sources:** [Homepage](https://github.com/IHP-GmbH/IHP-Open-PDK); [source repository](https://github.com/IHP-GmbH/IHP-Open-PDK); [installation documentation](https://github.com/IHP-GmbH/IHP-Open-PDK/blob/dev/README.md).
- **Discovery:** Explicit **development source snapshot**, branch **dev**, documented by upstream. Do not present it as a stable release or silently use main.
- **Interfaces / dependencies:** PDK data; no executable. Dependencies to review: Native model compiler and selected technology tools.
- **Integration and validation:** Official dev branch documents this experimental process variant; keep its channel and limitations explicit. Coupled group ihp-open-pdk.
- **Recipe:** [ihp guidance](../recipes/ihp/README.md).
