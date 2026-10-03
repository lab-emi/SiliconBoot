# FPGA

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## icestorm

- **Name / kind / aliases:** Project IceStorm; tool; Project IceStorm.
- **Official sources:** [Homepage](https://github.com/YosysHQ/icestorm); [source repository](https://github.com/YosysHQ/icestorm); [installation documentation](https://github.com/YosysHQ/icestorm#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/icestorm/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** icepack, iceunpack, icebox_vlog, iceprog; remaining tools pending inventory. Dependencies to review: USB libraries where programming is enabled.
- **Integration and validation:** Record device database revision; avoid hardware programming during installation checks.
- **Recipe:** [fpga guidance](../recipes/fpga/README.md).

## nextpnr-ice40

- **Name / kind / aliases:** nextpnr iCE40; tool; nextpnr iCE40.
- **Official sources:** [Homepage](https://github.com/YosysHQ/nextpnr); [source repository](https://github.com/YosysHQ/nextpnr); [installation documentation](https://github.com/YosysHQ/nextpnr#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/nextpnr/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** nextpnr-ice40. Dependencies to review: yosys, icestorm.
- **Integration and validation:** Shares nextpnr source revision with nextpnr-ecp5; validate the iCE40 architecture separately.
- **Recipe:** [fpga guidance](../recipes/fpga/README.md).

## nextpnr-ecp5

- **Name / kind / aliases:** nextpnr ECP5; tool; nextpnr ECP5.
- **Official sources:** [Homepage](https://github.com/YosysHQ/nextpnr); [source repository](https://github.com/YosysHQ/nextpnr); [installation documentation](https://github.com/YosysHQ/nextpnr#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/nextpnr/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** nextpnr-ecp5. Dependencies to review: yosys, prjtrellis.
- **Integration and validation:** Shares nextpnr source revision with nextpnr-ice40; validate the ECP5 architecture separately.
- **Recipe:** [fpga guidance](../recipes/fpga/README.md).

## prjtrellis

- **Name / kind / aliases:** Project Trellis; tool; Project Trellis; Trellis.
- **Official sources:** [Homepage](https://github.com/YosysHQ/prjtrellis); [source repository](https://github.com/YosysHQ/prjtrellis); [installation documentation](https://github.com/YosysHQ/prjtrellis#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/prjtrellis/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** ecppack, ecpunpack; remaining tools pending inventory. Dependencies to review: Device database; native/Python libraries.
- **Integration and validation:** Record bitstream database revisions and check a pack/unpack round trip.
- **Recipe:** [fpga guidance](../recipes/fpga/README.md).
