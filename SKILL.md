# Caffeine Template - Agent Guidelines & Skill Definition

<instructions>
You are acting as an expert systems engineer and project architect contributing to the `caffeine-template` repository. When you are invoked to work on this repository, you MUST strictly adhere to the architectural rules, coding standards, and workflows defined in this document.
</instructions>

## 1. Project Context
`caffeine-template` is the foundational boilerplate for all new components within the **Caffeine Framework** ecosystem. It provides a standardized structure for new hardware ports, middleware, and applications, ensuring they are "born" with the framework's strict quality and build standards.

### Core Philosophy
*   **Centralized Infrastructure:** All build logic (toolchains, base presets, scripts) is inherited from the **`caffeine-build`** submodule. 
*   **Minimalist Core:** The template provides only the essential files (`CMakeLists.txt`, `CMakePresets.json`, and basic CI) to avoid bloat while enforcing consistency.
*   **Developer Experience:** It is designed to be fully functional immediately after a `git clone --recursive`, allowing developers to focus on implementation rather than environment setup.

## 2. Agent Workflow Rules

### A. Submodule Mandate
*   **Reference Paths:** All build-related includes and preset inheritances MUST point to the `caffeine-build/` subdirectory.
*   **No Duplication:** Never copy toolchain files or base presets from `caffeine-build` into the template's local directories.

### B. Coding Standards (BARR-C:2018 / Allman)
All code generated for the template or its derivatives MUST follow these strict rules:
*   **Strict C11:** No C++ features, GNU statement expressions, or compiler-specific attributes unless wrapped in framework-standard macros.
*   **Memory Safety:** No dynamic memory allocation (`malloc`, `free`, `realloc`). All state must be static or passed via context pointers.
*   **Formatting:** 120-column limit, 4-space indentation, and **Allman-style braces** (braces on new lines).
*   **Naming:** Lowercase with underscores for functions and variables; `UPPER_CASE` for macros and enums.

### C. Build System Usage
Always use the centralized orchestrator for testing and documentation:
```bash
# Build natively (Host)
./caffeine-build/scripts/build.sh native

# Build for a specific architecture (e.g., ARM)
./caffeine-build/scripts/build.sh stm32f407-release
```

## 3. Documentation Mandate
*   **Standard Header:** Every `README.md` must maintain the standardized Caffeine logo and status badges at the top.
*   **Badge Accuracy:** When creating a new repository from this template, badges MUST be updated to point to the new repository's URL.

## 4. CI/CD Standards
*   **Containerized Builds:** All CI jobs must run inside the pre-built Docker containers provided by the `caffeine-build` registry.
*   **Submodule Checkouts:** Ensure `.github/workflows/ci.yml` always uses `submodules: recursive` in the checkout step.
