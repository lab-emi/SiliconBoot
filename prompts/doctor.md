# Diagnose an environment

> Find the local SiliconBoot clone and the existing project directory from context, defaulting to the clone. Diagnose its environment using AGENTS.md, .siliconboot/AGENTS.md and docs/validation.md, reusing the recorded tool and PDK roots. Keep versions and the active generation unchanged. Check records, ~/bin symlink targets, provider identities, executable permissions, runtime dependencies, PDK resources, detected default shell and its PATH configuration. Use a fresh instance of that shell and another working directory, then run the recorded component and requested workflow checks in a new run directory. Report pass, fail, blocked and not_run separately, with evidence. Check whether temporary build paths are still required. Propose repairs for failures without creating a workspace, using sudo, upgrading or deleting installations.

Ordinary diagnosis may produce reports and logs. It must not silently query “latest” and rebuild the environment.
