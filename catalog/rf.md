# EM and RF

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

## openems

- **Name / kind / aliases:** openEMS; tool; openEMS.
- **Official sources:** [Homepage](https://www.openems.de/); [source repository](https://github.com/thliebig/openEMS); [installation documentation](https://docs.openems.de/).
- **Discovery:** Review [official releases](https://github.com/thliebig/openEMS/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** openEMS; Python/Octave interfaces. Dependencies to review: csxcad; native numerical libraries.
- **Integration and validation:** Run a small EM model and inspect convergence and a numerical reference.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## csxcad

- **Name / kind / aliases:** CSXCAD; library; CSXCAD.
- **Official sources:** [Homepage](https://github.com/thliebig/CSXCAD); [source repository](https://github.com/thliebig/CSXCAD); [installation documentation](https://github.com/thliebig/CSXCAD#readme).
- **Discovery:** Review [official releases](https://github.com/thliebig/CSXCAD/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Native library; Python/Octave interfaces. Dependencies to review: Native geometry libraries.
- **Integration and validation:** Coupled group openems-family: native library and scripting ABI must match.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## qcsxcad

- **Name / kind / aliases:** QCSXCAD; library; QCSXCAD.
- **Official sources:** [Homepage](https://github.com/thliebig/QCSXCAD); [source repository](https://github.com/thliebig/QCSXCAD); [installation documentation](https://github.com/thliebig/QCSXCAD#readme).
- **Discovery:** Review [official releases](https://github.com/thliebig/QCSXCAD/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Qt geometry library. Dependencies to review: csxcad; Qt.
- **Integration and validation:** Coupled group openems-family; check rendering through AppCSXCAD.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## appcsxcad

- **Name / kind / aliases:** AppCSXCAD; tool; AppCSXCAD.
- **Official sources:** [Homepage](https://github.com/thliebig/AppCSXCAD); [source repository](https://github.com/thliebig/AppCSXCAD); [installation documentation](https://github.com/thliebig/AppCSXCAD#readme).
- **Discovery:** Review [official releases](https://github.com/thliebig/AppCSXCAD/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** AppCSXCAD. Dependencies to review: csxcad, qcsxcad; Qt.
- **Integration and validation:** Load a geometry file and confirm dimensions before launching simulation.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## palace

- **Name / kind / aliases:** Palace; tool; Palace.
- **Official sources:** [Homepage](https://github.com/awslabs/palace); [source repository](https://github.com/awslabs/palace); [installation documentation](https://github.com/awslabs/palace#readme).
- **Discovery:** Review [official releases](https://github.com/awslabs/palace/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** palace. Dependencies to review: MPI and numerical solver libraries; mesh data.
- **Integration and validation:** Record the numerical-library/MPI ABI and inspect a small reference simulation.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## gmsh

- **Name / kind / aliases:** Gmsh; tool; Gmsh.
- **Official sources:** [Homepage](https://gmsh.info/); [source repository](https://gitlab.onelab.info/gmsh/gmsh); [installation documentation](https://gmsh.info/doc/texinfo/).
- **Discovery:** Review the linked upstream release/download documentation. Release policy and maintained branch **unknown**; resolve them before selecting a snapshot.
- **Interfaces / dependencies:** gmsh; library interface. Dependencies to review: Native geometry/graphics libraries.
- **Integration and validation:** Generate a small mesh and inspect element counts and geometric validity.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## fasthenry2

- **Name / kind / aliases:** FastHenry2; tool; FastHenry2.
- **Official sources:** [Homepage](https://github.com/ediloren/FastHenry2); [source repository](https://github.com/ediloren/FastHenry2); [installation documentation](https://github.com/ediloren/FastHenry2#readme).
- **Discovery:** Review [official releases](https://github.com/ediloren/FastHenry2/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** fasthenry; confirm upstream build output. Dependencies to review: Native compiler.
- **Integration and validation:** Compute resistance/inductance for a known conductor and inspect units and signs.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## fastercap

- **Name / kind / aliases:** FasterCap; tool; FasterCap.
- **Official sources:** [Homepage](https://github.com/ediloren/FasterCap); [source repository](https://github.com/ediloren/FasterCap); [installation documentation](https://github.com/ediloren/FasterCap#readme).
- **Discovery:** Review [official releases](https://github.com/ediloren/FasterCap/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** FasterCap; confirm upstream build output. Dependencies to review: Native numerical and GUI libraries.
- **Integration and validation:** Compute a small capacitance matrix and check symmetry and physical plausibility.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## scikit-rf

- **Name / kind / aliases:** scikit-rf; library; scikit-rf.
- **Official sources:** [Homepage](https://github.com/scikit-rf/scikit-rf); [source repository](https://github.com/scikit-rf/scikit-rf); [installation documentation](https://github.com/scikit-rf/scikit-rf#readme).
- **Discovery:** Review [official releases](https://github.com/scikit-rf/scikit-rf/releases) and upstream tag policy. Observed default branch: **master**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library. Dependencies to review: Python numerical libraries.
- **Integration and validation:** Read a Touchstone fixture and validate network conversions and frequency units.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## gds2palace

- **Name / kind / aliases:** gds2palace; library; gds2palace.
- **Official sources:** [Homepage](https://github.com/VolkerMuehlhaus/gds2palace_ihp_sg13g2); [source repository](https://github.com/VolkerMuehlhaus/gds2palace_ihp_sg13g2); [installation documentation](https://github.com/VolkerMuehlhaus/gds2palace_ihp_sg13g2#readme).
- **Discovery:** Review [official releases](https://github.com/VolkerMuehlhaus/gds2palace_ihp_sg13g2/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Python library; CLI inventory pending. Dependencies to review: palace, gmsh; selected layer stack/PDK.
- **Integration and validation:** Confirm the process stack and compare generated mesh and ports with the source layout.
- **License evidence:** GPL-3.0-or-later. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## setupem

- **Name / kind / aliases:** setupEM; tool; setupEM.
- **Official sources:** [Homepage](https://github.com/VolkerMuehlhaus/setupEM); [source repository](https://github.com/VolkerMuehlhaus/setupEM); [installation documentation](https://github.com/VolkerMuehlhaus/setupEM#readme).
- **Discovery:** Review [official releases](https://github.com/VolkerMuehlhaus/setupEM/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** Entrypoint discovery pending. Dependencies to review: gds2palace, palace, gmsh; GUI runtime.
- **Integration and validation:** Create and solve one small model; inspect port definitions and solver outputs.
- **License evidence:** GPL-3.0-or-later. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [rf guidance](../recipes/rf/README.md).

## snp2le

- **Name / kind / aliases:** snp2le; tool; snp2le.
- **Official sources:** [Homepage](https://github.com/iic-jku/snp2le); [source repository](https://github.com/iic-jku/snp2le); [installation documentation](https://github.com/iic-jku/snp2le#readme).
- **Discovery:** Review [official releases](https://github.com/iic-jku/snp2le/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** snp2le; confirm installed launcher. Dependencies to review: scikit-rf; ngspice or vacask for validation.
- **Integration and validation:** Compare the fitted circuit frequency response with its source S-parameters.
- **License evidence:** Apache-2.0. Retain the selected revision’s own license and dependency notices.
- **Recipe:** [rf guidance](../recipes/rf/README.md).
