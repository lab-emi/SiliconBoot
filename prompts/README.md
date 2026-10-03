# Operation prompts

These are requests to an agent, not shell commands or a SiliconBoot CLI. Open the cloned repository in the agent and read [AGENTS.md](../AGENTS.md) first; these prompts inherit its constraints. The agent discovers the clone and uses its `workspace/` directory as the IC project.

For setup, replace only `<ABSOLUTE_INSTALL_PATH>` with the absolute directory where all IC design tools, SRAM compilers, and PDKs should be installed. Maintenance prompts reuse the installation root recorded in `workspace/.siliconboot/host.md`. Other placeholders describe a task, component selection, or record ID; repository and project paths are derived by the agent.

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

If continuing an interrupted operation, supply the operation ID. Ask the agent to inspect its frozen resolution and state, recheck completed work, and resume only missing or invalidated steps. A fresh latest-version resolution must be recorded as a new operation.
