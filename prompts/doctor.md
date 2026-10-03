# Diagnose an environment

> Find the local SiliconBoot clone and diagnose its workspace/ project. Read AGENTS.md, workspace/AGENTS.md and docs/validation.md, and use the installation root recorded in the workspace. Keep versions and the active generation unchanged. Check records, link targets, provider identities, executable permissions, runtime dependencies and PDK resources. Use a fresh shell and another working directory, then run the recorded component and requested workflow checks in a new run directory. Report pass, fail, blocked and not_run separately, with evidence. Check whether temporary build paths are still required. Propose repairs for failures without upgrading or deleting installations.

Ordinary diagnosis may produce reports and logs. It must not silently query “latest” and rebuild the environment.
