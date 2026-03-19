<p align="center">
  <a href="https://whileone.me">
    <img src="https://raw.githubusercontent.com/while-one/caffeine-build/main/assets/logo.png" alt="Caffeine Logo" width="50%">
  </a>
<h1 align="center">The Caffeine Framework</h1>
</p>


<p align="center">
  <img src="https://img.shields.io/badge/C-11-blue.svg?style=flat-square&logo=c" alt="C11">
  <img src="https://img.shields.io/badge/CMake-%23008FBA.svg?style=flat-square&logo=cmake&logoColor=white" alt="CMake">
  <a href="https://github.com/while-one/caffeine-template/tags">
    <img src="https://img.shields.io/github/v/tag/while-one/caffeine-template?style=flat-square&label=Release" alt="Latest Release">
  </a>
  <a href="https://github.com/while-one/caffeine-template/actions/workflows/ci.yml">
    <img src="https://img.shields.io/github/actions/workflow/status/while-one/caffeine-template/ci.yml?style=flat-square&branch=main" alt="CI Status">
  </a>
  <a href="https://github.com/while-one/caffeine-template/commits/main">
    <img src="https://img.shields.io/github/last-commit/while-one/caffeine-template.svg?style=flat-square" alt="Last Commit">
  </a>
  <a href="https://github.com/while-one/caffeine-template/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/while-one/caffeine-template?style=flat-square&color=blue" alt="License: MIT">
  </a>
</p>

# Caffeine-Template

This is the foundational template repository for all new components within the **Caffeine Framework** ecosystem (e.g., new hardware ports, middleware libraries, and application layers).

## Shared Ecosystem Standards

By instantiating a repository from this template, you inherit the framework's strict coding standards and CI infrastructure via the `caffeine-build` submodule:

*   **Formatting:** Enforces a 120-column limit, 4-space indentation, and Allman-style braces via `caffeine-build/config/coding/.clang-format`.
*   **Static Analysis:** Enforces strict C11 compliance, memory safety rules (no dynamic allocation), and best practices for embedded systems via `caffeine-build/config/coding/.clang-tidy`.
*   **Unified Build System:** A common cross-platform Docker/native build script orchestrates the build process identically to CI.

### Building Locally

To build this project locally, utilize the `caffeine-build` submodule script:

```bash
# Ensure submodules are initialized
git submodule update --init --recursive

# Build natively (Linux/Host)
./caffeine-build/scripts/build.sh native

# Build for a specific preset (e.g., STM32)
./caffeine-build/scripts/build.sh stm32f407-release

# Run formatting target
./caffeine-build/scripts/build.sh native caffeine-template-format
```

## The Caffeine Framework Layers

The framework is composed of the following distinct layers:

1.  **Generic Interface ([`caffeine-hal`](https://github.com/while-one/caffeine-hal)):** Header-only definitions of the Hardware Abstraction Layer and Virtual Method Tables (VMTs).
2.  **Hardware Ports ([`caffeine-hal-ports`](https://github.com/while-one/caffeine-hal-ports)):** The concrete implementations of the HAL for specific vendors (e.g., STM32, NXP, nRF, TI) and OS environments (Linux POSIX). It encapsulates vendor SDKs and provides modern CMake cross-compilation presets.
3.  **Middleware (TBD):** Device drivers (e.g., displays, sensors) and protocols (e.g., Modbus, USB stacks) that build strictly upon the generic `caffeine-hal` interface, remaining completely agnostic to the underlying hardware.
4.  **Application (TBD):** The top-level business logic, state machines, and system orchestration that utilize the middleware and HAL interfaces.

## Next Steps for New Components

1.  Update this `README.md` to describe the specific purpose of the new repository (e.g., "STM32 Porting Layer", "Modbus Middleware").
2.  Review and customize `.github/workflows/ci.yml` if your component requires a specific cross-compilation matrix (like ARM GCC) rather than native testing.
3.  Add the specific source files and CMake configuration (e.g., `CMakePresets.json`) as outlined in the [Caffeine-HAL Architecture Guide](https://github.com/while-one/caffeine-hal).

---

## Support

They say dealing with abstraction is a form of art, so I suppose that makes me an artist? Whether this caffeine fuels an elegant HAL or a deep debugging session, I appreciate you being part of the gallery.

If my projects helped you, buy me a brew or if the opposite open a PR!

<a href="https://www.buymeacoffee.com/whileone" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
