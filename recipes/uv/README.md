# Bootstrap uv

uv is the default Python environment manager. Read its [catalog record](../../catalog/support.md#uv), [Python environment policy](../../docs/python-environments.md), and the [common recipe](../README.md). Install and check its native executable before creating Python environments or installing Python packages. Then verify its environment operations with a compatible recorded interpreter.

## Discover or install

1. Inspect the resolved uv executable, version, provider and native architecture. Record an absent, broken or unsuitable installation in the host record. Reuse a matching verified installation according to the lifecycle's identity and location rules; preserve existing installations and user settings.
2. When uv is missing or a managed installation is needed, resolve the latest official stable release from [Astral's installation documentation](https://docs.astral.sh/uv/getting-started/installation/) and [official releases](https://github.com/astral-sh/uv/releases). Freeze the release, native asset, source identity, checksums and final URL before installation. An exact restore uses the locked uv version instead.
3. Use the official standalone native distribution. uv can be bootstrapped without an existing Python environment or pip installation. Place it beneath the selected installation root at `tools/uv/<install-key>/root/`, preserving upstream license and distribution files. Inspect the actual installed executable paths rather than assuming an archive layout.
4. If using the official installer, acquire the installer for the frozen version and review its current options before execution. Use `UV_UNMANAGED_INSTALL` for the owned final executable directory; upstream documents that this suppresses shell/profile changes and disables self-updates. Record the installer URL and digest. See [official installer options](https://docs.astral.sh/uv/reference/installer/). A missing native asset requires review of an upstream-supported native source build; otherwise report the platform limitation.
5. Configure Python and cache locations under the installation root before using uv. Check the native binary first, then obtain a compatible interpreter from the frozen prerequisite plan and verify the environment operations below. Complete the uv receipt after those checks. Use that exact executable for subsequent setup. Expose verified upstream entrypoints through the candidate generation's `tools/uv` and `bin` views under the normal activation procedure.

Reusing uv outside the installation root follows the existing location-exception policy. Installing a managed copy can satisfy the root requirement while preserving the external copy. Do not upgrade uv in place or modify the user's shell startup files as part of setup.

## Verify and hand off

- Confirm version, source identity, host architecture, executable permissions and the resolved provider from a fresh process.
- Use a small official uv example to create an isolated test environment in an owned temporary directory with a recorded compatible interpreter. Resolve and install its documented package dependency, check its actual import or entrypoint location, and retain the resolution evidence.
- Recreate the test environment from those exact inputs and verify the same package versions. Check that effective Python/cache paths are within their recorded locations and that the system Python environment is unchanged.
- Record the real outcomes and any unavailable network, interpreter or native package requirements. Environment creation alone does not establish EDA workflow readiness; each Python component still needs its own recipe checks.
- Remove only owned temporary test environments and installer files after verification. Retain logs, receipts, dependency evidence and every interpreter referenced by an installation. Follow the normal [cleanup rules](../../docs/cleanup.md).

When uv cannot be installed or verified, mark dependent Python setup blocked with the reason. Preserve any working generation and continue independent components. Do not silently switch to a different environment manager.
