# Layout libraries, viewers and extensions

Apply the [common recipe](../README.md) and component sources in the [catalog](../../catalog/README.md). [KLayout](../klayout/README.md), [Magic](../magic/README.md), and [Netgen](../netgen/README.md) have dedicated recipes. All checks below need host-specific evidence.

## Installation and identity

Distinguish geometry libraries, viewers, design-rule tools, electrical-rule tools and extraction integrations. Each checks a different property. Match plugins to the host tool's runtime, Qt, Python or Ruby ABI. Keep project technology settings and plugin search paths scoped to the project or dedicated installed environment; preserve an existing user's plugin configuration.

| Component | Installation concern | Functional acceptance |
| --- | --- | --- |
| CVC | Confirm the circuit-validity/ERC tool and its netlist, power and device models | Run upstream valid and invalid circuit cases; inspect actual electrical-rule violations |
| GDS3D | Preserve configuration, technology mapping, shaders and GUI resources | Open an upstream layout with its layer map and inspect visible geometry and layer heights |
| gdscheck | Confirm intended upstream checker and the exact properties it checks | Run upstream accepted and rejected GDS inputs; inspect diagnostic differences |
| gdsfill | Record geometry engine, layer selection, density goals and keepouts | Fill an official sample, inspect fill count/density and confirm exclusion regions remain clear |
| gdsfactory | Isolate Python and record its PDK/technology plugin separately | Generate a documented cell, round-trip its layout and inspect geometry, ports and units |
| gdspy | Match Python/native extension and numerical dependencies | Generate and round-trip an upstream geometry example, checking area, units and hierarchy |
| klayout-pex | Match KLayout, PDK extraction inputs and selected solver | Extract a supported reference layout; inspect parasitic nets, units and numeric values |
| klive | Resolve both the sender package and KLayout receiver integration | Send a supported layout to the running viewer and verify the actual displayed cell |
| xsection | Match the upstream KLayout package and process description | Reproduce a documented cross-section and inspect its layer/process sequence |
| klayout-productivity-suite | Enumerate and freeze the exact official member plugins | Load each selected member in the recorded KLayout and exercise its documented minimal function |
| klayout-vector-file-export-cli | Confirm host/runtime integration and supported output formats | Export an upstream sample and inspect dimensions, layers and the resulting vector file |

For any named plugin member expanded by the catalog, apply the suite row's install isolation and require that member's own functional check. Unknown or unnamed extensions remain explicit unresolved scope; do not bulk-install all packages found in a public registry.

## Acceptance and cleanup

Keep known-good and known-bad geometry separate. A parse check is not DRC; an extraction is not LVS; a rendered image is not proof of either. When claiming physical-verification readiness, use the selected PDK's actual decks and [workflow acceptance](../../docs/validation.md), including declared limits of the open decks.

Preserve installed macros, scripts supplied by the upstream package, libraries, runtime source, technology resources and licenses. SiliconBoot adds no code of its own. Clean only owned temporary acquisition/build files after a fresh-session check of each plugin's actual host path.
