# Clean temporary installation files

> Find the local SiliconBoot clone and clean up temporary installation files for its workspace/ project using docs/cleanup.md. Read AGENTS.md and workspace/AGENTS.md, and use the installation root recorded in the workspace. Inspect ownership records and validation before selecting temporary downloads, archives, extraction directories and build intermediates. Resolve paths without following user symlinks into third-party directories. Preserve runtime source trees, environments, PDK resources, licenses, receipts, logs, active and retained generations, installations shared with other projects, and running jobs. Remove only proven owned temporary items within the recorded operation scope. Report removed items, retained failures and space recovered. Do not garbage-collect installations or clear shared package-manager caches.

If ownership or runtime use is uncertain, retain the item and explain what evidence is missing.
