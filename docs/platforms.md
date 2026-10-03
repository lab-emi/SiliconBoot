# Native platform policy and evidence

This repository provides installation guidance. **No native installation or workflow has been verified as part of this documentation release.** A catalog entry or recipe is not proof that a component runs on a platform. Record support per component, version, provider, OS, architecture, and workflow using [validation evidence](validation.md).

## Validation priorities

| Host | Current repository evidence | Required treatment |
| --- | --- | --- |
| Ubuntu 24.04, x86_64 | Unverified; first native validation target | Confirm each upstream's requirements and execute component and workflow checks on this host. |
| Linux, ARM64 | Unverified | Require native assets or native source builds and recompile architecture-dependent models. |
| Other Linux distributions/releases | Unverified | Reassess package names, library ABI, compiler versions, and filesystem facilities. |
| macOS, Apple silicon or Intel | Unverified | Confirm each component's native support, toolchain, frameworks, and model ABI; do not assume Linux recipes transfer. |
| Native Windows | Unverified and component-dependent | Use only upstream-supported native procedures; confirm the required symlink, locking, and atomic activation semantics. |
| WSL2 | Separate Linux execution environment, unverified | Use only when the user explicitly selects it; record its Linux guest and Windows host context. |

Container, virtual-machine, subsystem, translation-layer, and remote-host execution must be identified accurately. A successful run there does not verify direct native support on a different host. Do not silently substitute one environment for another when native installation was requested.

## Support vocabulary

| Level | Required interpretation |
| --- | --- |
| `planned` | Cataloged scope; the applicable install or verification procedure is incomplete. |
| `experimental` | An applicable procedure exists, but the documented native checks have not established the claimed capability. |
| `verified` | Retained evidence names the exact native host, inputs, checks, outcomes, and limitations. |
| `unsupported` | Upstream or observed constraints rule out this component or combination for the requested environment. |

Use `unknown` as an unresolved observation in records, not a positive support claim. Verification of one component's version query does not promote all its workflows to verified. Headless functional checks and GUI checks have separate outcomes. A passing profile on one host does not promote the whole catalog or another architecture.

## Preflight evidence

Record native OS/release, CPU and process architecture, filesystem type for project and store, available resources, upstream platform requirements, package ownership, compiler/runtime versions, GUI access, and network access. Establish these capabilities before filesystem mutation:

- Persistent installations with an accessible final prefix and suitable filesystem permissions.
- Native symbolic links with known resolution semantics and executable permissions.
- Exclusive locks whose owner and lifetime can be observed reliably.
- Atomic replacement of the project `current` symlink on its filesystem.
- Safe inspection and deletion that will not follow an unowned link or race a concurrent mutation.

If an essential capability is absent or uncertain, record the blocker and stop the affected mutation. A network or removable filesystem may behave differently from a local filesystem; do not assume locking and rename guarantees from the operating system name alone.

Use [installation records](records.md) to distinguish upstream support assertions from observed native results. Update this platform table only when reviewable evidence warrants a narrower, precise claim. Do not mark a platform verified from the presence of documentation.
