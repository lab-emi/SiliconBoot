# Optional support tools

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

These general development tools are optional and excluded from the default all profile. Their presence does not provide an EDA workflow by itself.

## jupyter

- **Name / kind / aliases:** JupyterLab; tool; Jupyter; JupyterLab.
- **Official sources:** [Homepage](https://jupyter.org/); [source repository](https://github.com/jupyterlab/jupyterlab); [installation documentation](https://github.com/jupyterlab/jupyterlab#readme).
- **Discovery:** Review [official releases](https://github.com/jupyterlab/jupyterlab/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** jupyter-lab; related Jupyter commands depend on selected packages. Dependencies to review: Isolated Python environment; chosen kernels.
- **Integration and validation:** Optional notebook support; bind services according to user-selected access policy.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## uv

- **Name / kind / aliases:** uv; tool; uv.
- **Official sources:** [Homepage](https://docs.astral.sh/uv/); [source repository](https://github.com/astral-sh/uv); [installation documentation](https://docs.astral.sh/uv/getting-started/installation/).
- **Discovery:** Review [official releases](https://github.com/astral-sh/uv/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** uv, uvx. Dependencies to review: Native binary for host OS/architecture.
- **Integration and validation:** Optional environment manager; each EDA component still needs isolated dependencies.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).
