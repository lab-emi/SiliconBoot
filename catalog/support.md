# Python environment manager and optional support

Every record inherits the [catalog field definitions and defaults](README.md). Resolved entries with a linked procedure have **experimental** SiliconBoot support; native installation and workflow checks are **unverified**. Explicit unresolved scope remains **planned**. Command names describe interfaces, not runnable instructions or a completed installation inventory.

uv is a default setup dependency for every profile. JupyterLab is optional. Neither component's presence establishes an EDA workflow by itself.

## jupyter

- **Name / kind / aliases:** JupyterLab; tool; Jupyter; JupyterLab.
- **Official sources:** [Homepage](https://jupyter.org/); [source repository](https://github.com/jupyterlab/jupyterlab); [installation documentation](https://github.com/jupyterlab/jupyterlab#readme).
- **Discovery:** Review [official releases](https://github.com/jupyterlab/jupyterlab/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** jupyter-lab; related Jupyter commands depend on selected packages. Dependencies to review: uv-managed isolated Python environment; chosen kernels.
- **Integration and validation:** Optional notebook support; bind services according to user-selected access policy.
- **Recipe:** [orchestration guidance](../recipes/orchestration/README.md).

## uv

- **Name / kind / aliases:** uv; tool; uv.
- **Official sources:** [Homepage](https://docs.astral.sh/uv/); [source repository](https://github.com/astral-sh/uv); [installation documentation](https://docs.astral.sh/uv/getting-started/installation/).
- **Discovery:** Review [official releases](https://github.com/astral-sh/uv/releases) and upstream tag policy. Observed default branch: **main**; maintained branch **unknown**. No automatic branch fallback.
- **Interfaces / dependencies:** uv, uvx. Dependencies to review: Native binary for host OS/architecture.
- **Integration and validation:** Default Python environment manager. Install and verify uv first when missing, then create isolated environments with recorded interpreters and dependencies. Validate environment creation and recreation before relying on it for Python components.
- **Recipe:** [uv bootstrap](../recipes/uv/README.md) and [Python environment policy](../docs/python-environments.md).
