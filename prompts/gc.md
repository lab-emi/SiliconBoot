# Review unreferenced installations

> Find the local SiliconBoot clone and assess garbage collection in the installation root recorded in workspace/.siliconboot/host.md. Read AGENTS.md, workspace/AGENTS.md and docs/cleanup.md. This request is for a dry run. Reconcile registered projects, every retained generation, active run leases, and installation dependencies under the documented locks. List only installations proven unreferenced, with their receipts and reasons, and list uncertain cases separately. Do not delete anything. Provide a concrete candidate list that I can explicitly select for removal.

For an already reviewed candidate list, the user can authorize removal with this follow-up:

> Remove the garbage-collection candidates `<CANDIDATE_IDS>` from the recorded dry run `<REVIEW_ID>`. Recheck references, leases, dependencies, ownership and paths immediately before removal under the appropriate locks. Retain any candidate whose status changed or cannot be proven safe. Report actual removals and retained items.

Ordinary cleanup and an upgrade do not authorize removing old installations. Existing explicit removal authorization remains valid for the specified scope, subject to the reference recheck.
