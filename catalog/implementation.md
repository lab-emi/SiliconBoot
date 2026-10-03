# ASIC implementation

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## librelane

- **Name / kind / aliases:** LibreLane; tool; LibreLane.
- **Official sources:** [Homepage](https://github.com/librelane/librelane); [source repository](https://github.com/librelane/librelane); [installation documentation](https://github.com/librelane/librelane#readme).
- **Discovery:** Review [official releases](https://github.com/librelane/librelane/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** librelane. Dependencies to review: yosys, openroad, opensta, magic, netgen, klayout; selected PDK.
- **Integration and validation:** Flow version pins are compatibility constraints; upstream latest tools may conflict.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).

## openroad

- **Name / kind / aliases:** OpenROAD; tool; OpenROAD.
- **Official sources:** [Homepage](https://github.com/The-OpenROAD-Project/OpenROAD); [source repository](https://github.com/The-OpenROAD-Project/OpenROAD); [installation documentation](https://openroad.readthedocs.io/en/latest/user/Build.html).
- **Discovery:** Review [official releases](https://github.com/The-OpenROAD-Project/OpenROAD/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** openroad. Dependencies to review: opensta integration; numerical and GUI libraries; selected PDK.
- **Integration and validation:** Current upstream build documentation prefers Bazel; retain openroad.runfiles. Record dependency commits and inspect timing, placement and routing reports.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).

## opensta

- **Name / kind / aliases:** OpenSTA; tool; OpenSTA.
- **Official sources:** [Homepage](https://github.com/parallaxsw/OpenSTA); [source repository](https://github.com/parallaxsw/OpenSTA); [installation documentation](https://github.com/parallaxsw/OpenSTA#readme).
- **Discovery:** Review [official releases](https://github.com/parallaxsw/OpenSTA/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** sta. Dependencies to review: Tcl; Liberty and timing data.
- **Integration and validation:** Parallax identifies this as the official standalone source. OpenROAD may embed its separately recorded OpenSTA provider; do not conflate their revisions. Check a small timing graph and constraints; do not claim timing closure from startup.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).

## qflow

- **Name / kind / aliases:** Qflow; tool; Qflow.
- **Official sources:** [Homepage](https://github.com/RTimothyEdwards/qflow); [source repository](https://github.com/RTimothyEdwards/qflow); [installation documentation](https://github.com/RTimothyEdwards/qflow#readme).
- **Discovery:** Review [official releases](https://github.com/RTimothyEdwards/qflow/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** qflow; conversion tools pending inventory. Dependencies to review: yosys, magic, netgen and other selected flow tools.
- **Integration and validation:** Record all implementation backend providers; vlog2verilog shares this source revision.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).

## padring

- **Name / kind / aliases:** padring; tool; padring.
- **Official sources:** [Homepage](https://github.com/YosysHQ/padring); [source repository](https://github.com/YosysHQ/padring); [installation documentation](https://github.com/YosysHQ/padring#readme).
- **Discovery:** Review [official releases](https://github.com/YosysHQ/padring/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** padring. Dependencies to review: LEF libraries and a technology-specific pad configuration.
- **Integration and validation:** Use the original YosysHQ source; flow-specific forks require their own explicit provider. Generate a small pad ring and inspect geometry and supply connectivity.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).

## fault

- **Name / kind / aliases:** Fault DFT; tool; Fault DFT.
- **Official sources:** [Homepage](https://github.com/AUCOHL/Fault); [source repository](https://github.com/AUCOHL/Fault); [installation documentation](https://fault.readthedocs.io/en/latest/installation.html).
- **Discovery:** Review [official releases](https://github.com/AUCOHL/Fault/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** fault; confirm installed launcher. Dependencies to review: yosys, iverilog and the chosen ATPG dependencies.
- **Integration and validation:** Identity is AUCOHL's DFT package, distributed on PyPI as fault-dft. Review Swift build dependencies and optional ATPG distribution terms; check scan insertion and fault-coverage reports.
- **Recipe:** [digital-flow guidance](../recipes/digital-flow/README.md).
