# Operation prompts

These are requests to an agent, not shell commands or a SiliconBoot CLI. Open the cloned repository in the agent and read [AGENTS.md](../AGENTS.md) first; these prompts inherit its constraints. The agent discovers the clone and any existing design project from context, using the clone itself when no separate project is selected. It does not create a workspace or scaffold design directories.

Setup needs no path placeholder: EDA tools, SRAM compilers, uv and isolated runtimes go under `~/tools`, PDKs under `~/pdks`, and verified public binary symlinks under `~/bin`, without sudo. Setup detects the default login shell and adds `~/bin` to PATH in its bashrc, zshrc or fish configuration. Maintenance reuses the canonical roots and shell settings recorded in the existing project's `.siliconboot/host.md`; it does not silently move older installations. Other placeholders describe a task, component selection or record ID; repository and project paths are derived by the agent.

| Prompt | Result |
| --- | --- |
| [Bootstrap](bootstrap.md) | Install the requested scope and create project guidance |
| [Plan](plan.md) | Inspect and resolve the proposed environment without installing |
| [Inventory](inventory.md) | Locate versions, entrypoints, libraries, and verified capabilities |
| [Doctor](doctor.md) | Check the current environment without changing versions |
| [Run](run.md) | Run one design task against a fixed generation |
| [Upgrade](upgrade.md) | Discover latest upstream versions and validate a new generation |
| [Restore](restore.md) | Rebuild the exact inputs in a portable lock |
| [Rollback](rollback.md) | Reactivate a retained generation |
| [Cleanup](cleanup.md) | Remove owned temporary installation files |
| [Garbage collection](gc.md) | Review or remove unreferenced installations when explicitly requested |

Default installation scope is `all`. Optional scope phrases include “Use the analog profile with sky130A,” “Set up only Yosys and Verilator,” and “Plan memory compilation for this PDK and report supported compiler ports.” Profiles select components, not permission to substitute versions or deployment environments.

Use uv by default for Python environments in every selection, installing and verifying it first during setup if missing. Planning records this prerequisite without executing it. Ordinary runs use the recorded environments; exact restore preserves locked manager and interpreter identities. Follow [Python environments](../docs/python-environments.md).

If continuing an interrupted operation, supply the operation ID. Ask the agent to inspect its frozen resolution and state, recheck completed work, and resume only missing or invalidated steps. A fresh latest-version resolution must be recorded as a new operation.
