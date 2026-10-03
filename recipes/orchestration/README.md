# Build orchestration and library management

Follow the [common recipe](../README.md) and official [catalog](../../catalog/README.md) entries. An orchestration framework and its backends are separate installed components; importing the framework does not prove a backend workflow works.

Use [uv](../uv/README.md) for the Python environments below, installing it first if missing. Follow the [Python environment policy](../../docs/python-environments.md) for isolation, exact dependencies and native bindings.

## Installation decisions and checks

| Component | Installation decision | Functional acceptance |
| --- | --- | --- |
| Edalize | Isolated Python, selected backend and its tool versions | Run a documented small backend example; inspect generated invocation and the actual backend output |
| FuseSoC | Isolated Python and explicit project library/configuration locations | Resolve and simulate an upstream example core, checking dependency records, test results and run output paths |
| SiliconCompiler | Isolated runtime, selected target/PDK and flow tool requirements | Run a small official flow locally with recorded native tools; inspect task statuses, tool reports and expected artifacts |
| LibMan | Confirm library manager identity and its storage model | Register and retrieve an upstream sample library without altering a user's existing library database |
| najaeda | Python/native library coupling, supported netlist formats | Load a documented netlist, inspect hierarchy/connectivity, and validate its exported result with a supported consumer |
| vlsirtools | Schema/runtime compatibility and selected simulator dependencies | Exercise upstream serialization/netlisting and a supported simulator example; check actual returned results |
| osic-multitool | Use only this component's own catalog source and documented native dependencies | Exercise each selected documented utility on upstream sample data and inspect its declared output |

Follow [FuseSoC's official installation guide](https://fusesoc.readthedocs.io/en/latest/user/installation.html) for its package identity, adapting runtime placement to SiliconBoot's isolated persistent prefix. Keep its [library configuration](https://fusesoc.readthedocs.io/en/stable/user/package_manager/) project-scoped so setup does not unexpectedly modify the user's global libraries. Resolve the selected release's behavior before choosing configuration paths.

For [SiliconCompiler](https://github.com/siliconcompiler/siliconcompiler), inspect the selected flow's actual execution backend. A remote job, container, or independently downloaded binary must not be reported as using the recorded native project tools. Preserve native execution provenance through the orchestration layer.

## Optional support tools

If the `support` profile is requested, add JupyterLab from its official source in its own uv-managed environment. uv is already a default setup dependency for every profile. Verify the requested support capability without treating it as an EDA workflow. Notebook servers must follow the user's chosen exposure and authentication settings; do not start a persistent public service during setup.

For JupyterLab, open a temporary local session using the selected interpreter kernel, run an upstream introductory notebook, confirm the kernel's actual environment, and shut the session down after the check. Keep each kernel associated with its intended IC environment; retain its interpreter and dependencies according to the normal lifecycle rules.

## Activation and cleanup

Record which backend executables were actually invoked, the resolved generation, library source revisions, working directories and generated configuration. Keep project-specific settings in the project and caches under recorded ownership. Preserve installed runtime sources and schemas. Do not delete shared library repositories or package-manager caches as routine cleanup.
