# Reactivate a retained generation

> Find the local SiliconBoot clone and roll back its workspace/ project to `<GENERATION_ID>`. Read AGENTS.md, workspace/AGENTS.md and docs/upgrade.md, and inspect the retained generation, its receipts, links, environment settings, and validation evidence. Check that its installations and current host dependencies still work. Preserve leases for running jobs. If required checks pass, switch the project's current pointer under the documented locks and update the documented active state and portable lock from that generation. Report exactly what changed and any system package changes that this rollback cannot reverse. Do not delete the newer generation as part of rollback.

A retained directory whose dependencies have disappeared is not a usable rollback target.
