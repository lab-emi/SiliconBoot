# Python environments for IC design

Use uv by default to create and manage Python environments. It is a setup dependency for every profile. Inspect its availability first and follow the [uv recipe](../recipes/uv/README.md) to install it when missing and verify its native executable before creating Python environments or installing packages. A planning-only request records this step without executing it.

Apply the [installation lifecycle](installation.md), including frozen inputs, locks, receipts and activation. An explicit user choice can override the default. A missing or unusable uv blocks the Python setup that needs it; record the cause and continue independent components.

## Choose and preserve the interpreter

Resolve the component's Python constraints and native extension ABI before choosing an interpreter. Select an exact stable Python version compatible with that release and its tool bindings. Record implementation, version, build, architecture, provider, source URL and digest. A newer host Python does not establish compatibility.

Prefer a uv-managed interpreter beneath `~/tools`. uv obtains its managed CPython builds from Astral's python-build-standalone project; record that provider rather than describing the binary as a python.org release asset. An existing native system interpreter can be a recorded external runtime dependency when compatible. Inspect the selected uv version's [Python support and discovery rules](https://docs.astral.sh/uv/concepts/python-versions/).

Before downloading Python, assign its final versioned runtime location and receipt as described in [project layout](project-layout.md). Set `UV_PYTHON_INSTALL_DIR` to that runtime's root and `UV_PYTHON_BIN_DIR` to its owned executable directory. Set `UV_CACHE_DIR` to `~/tools/.siliconboot/cache/uv`. These are process settings recorded in the manifest; keep them out of shell startup files. The shared `~/bin` PATH entry follows [default-shell setup](project-layout.md#default-shell-path). Confirm the effective paths against uv's [storage reference](https://docs.astral.sh/uv/reference/storage/) and [environment reference](https://docs.astral.sh/uv/reference/environment/). Keep the exact interpreter location stable for every environment that references it.

## Create isolated environments

Give each Python component an independent environment at its final persistent installation prefix. Use uv's environment creation interface with an explicit destination and exact interpreter path. Direct package operations to that environment's interpreter so an inherited active environment or nearby `.venv` cannot select the target accidentally. See [uv environments](https://docs.astral.sh/uv/pip/environments/).

Use uv's pip interface for upstream requirements or packaged distributions. When upstream already supplies a uv project and lock, preserve them and select the candidate environment explicitly through `UV_PROJECT_ENVIRONMENT`. Keep it separate from other components. Follow upstream's [project environment configuration](https://docs.astral.sh/uv/concepts/projects/config/). A design-specific Python environment also belongs under `~/tools` and is linked through the generation's `tools` view.

Freeze package versions, sources, extras, indexes, build requirements and native dependencies before populating the candidate. Preserve a retrievable dependency lock or resolved requirements asset with its digest and provenance. Reference it from the Markdown receipt and portable lock. If resolution needs uv and Python first, install those from a frozen prerequisite plan, then freeze the dependent plan before building. Review [uv dependency locking](https://docs.astral.sh/uv/pip/compile/); report any unresolved inputs instead of claiming exact restoration.

Keep OS-managed Python packages unchanged. Do not share unrelated dependencies through a global environment or `PYTHONPATH`. A tested coupled group can share an environment when its recipe requires it; record its complete membership and constraints. Preserve runtime source for editable installs in the permanent installation tree.

## Respect upstream runtime requirements

On macOS, apply [Homebrew-first tool selection](installation.md#macos-check-homebrew-first) to uv and packaged Python tools. A matching Homebrew tool can include a provider-managed Python runtime; record its exact interpreter and dependency closure as an external runtime exception and let Homebrew maintain that package. Do not use uv to alter Homebrew's environment or copy it into `~/tools`. Independently created IC environments still use uv at their final managed locations. Reuse any external interpreter only with its recorded identity, compatible ABI and retention limits.

An embedded interpreter, required Conda environment, Nix dependency closure or incompatible package installation feature can require an upstream-managed runtime. Preserve that runtime when official evidence establishes the requirement. Record the reason, upstream source, manager, interpreter, exact dependencies and verification limits. Do not silently replace it with uv or fall back from uv on an unexplained error. A routine upstream pip example alone does not require a different manager; check compatibility with uv's pip interface.

Existing environments remain intact until a separately built candidate passes the relevant checks. Adopting uv is an installation or maintenance action; it does not authorize migrating a working environment during an ordinary run.

## Run, maintain and clean up

Run verified tools through their recorded upstream entrypoints or the fixed environment interpreter. When an upstream workflow requires `uv run`, document a verified invocation that disables synchronization, lock updates and downloads and selects the recorded environment. Plain `uv run` can lock and sync automatically; `--locked` or `--frozen` alone does not disable syncing. Review uv's [locking and syncing behavior](https://docs.astral.sh/uv/concepts/projects/sync/) before publishing run instructions. Do not use transient `uvx` environments as persistent IC tool installations.

Record uv as a build dependency and the interpreter as a runtime dependency, including their exact identities. uv is also a runtime dependency when the workflow invokes it. Preserve interpreter installations, environments, persistent sources and dependency records while any retained generation or lease references them. Shared uv caches follow the separate cache policy in [cleanup](cleanup.md). Upgrades build new environments and runtime locations; exact restore uses the recorded inputs rather than resolving latest versions.
