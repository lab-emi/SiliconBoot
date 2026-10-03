# Electromagnetics and RF

Apply the [common recipe](../README.md) and official [catalog](../../catalog/README.md) sources. Resolve all native numerical libraries, interpreter interfaces and GUI dependencies before building. This recipe is experimental.

## Dependency groups

Treat CSXCAD, openEMS and their bindings as a compatible group; QCSXCAD and AppCSXCAD add the viewer stack. The current [official Python installation guide](https://docs.openems.de/en/latest/install/manual_install.html) requires a shared native prefix for CSXCAD and openEMS. Record each member's exact revision under that group prefix and verify bindings outside the source directories. The [native C++ guide](https://docs.openems.de/en/latest/development/cpp.html) describes the library and viewer dependency order. Resolve current requirements from the selected release before installation.

For Palace, use the [official project](https://github.com/awslabs/palace) and its linked build documentation. Record solver libraries, compiler, MPI implementation, enabled CPU/GPU features and mesh format. A runtime compiled against one MPI implementation must not silently load another.

## Component checks

| Component | Required check |
| --- | --- |
| openEMS | Run a small upstream EM example with the recorded interface; inspect convergence, ports, units and numerical outputs |
| CSXCAD | Build and serialize the upstream example geometry with the selected binding; load it in the actual solver |
| QCSXCAD | Load the library through its documented viewer consumer and verify geometry rendering |
| AppCSXCAD | Open the recorded geometry and inspect its mesh, materials and coordinate scale |
| Palace | Run a small upstream example at a bounded mesh size and process count; check convergence and its reference observable |
| Gmsh | Mesh a documented geometry, inspect physical groups and element quality, and load the mesh in the intended solver |
| FastHenry2 | Run an upstream conductor example and check inductance/resistance values and units |
| FasterCap | Run an upstream capacitor example, inspect solver convergence and the capacitance matrix |
| scikit-rf | Read upstream reference network data and reproduce a documented RF calculation with expected units and values |
| gds2palace | Convert a supported layout to the documented solver inputs and complete the associated small solver example |
| setupEM | Confirm upstream identity, supported backend and process stack, then reproduce its smallest documented EM setup |
| snp2le | Confirm identity and supported network-to-model conversion; compare converted-model response with the source network data |

For every numerical check, define the comparison values and tolerances before the run. A plausible plot or a nonempty output matrix is insufficient. Mesh choice, units, frequency range and boundary conditions belong in the validation record.

## Runtime and cleanup

Python wrappers need their own recorded interpreter and matching native libraries. Preserve geometry data, material databases, installed libraries and bindings. When multiple components share an upstream-required prefix, cleanup and garbage collection operate on the whole group. Headless computation and GUI viewing have separate results. Record missing optional GPU or display support without implying the CPU solver failed.
