```markdown
# OptiScaler Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides a comprehensive guide to contributing to the OptiScaler project, a Python-based codebase (with some C++ components) focused on advanced upscaling and frame generation technologies for games. It covers coding conventions, common development workflows, and testing patterns, enabling both new and experienced contributors to work efficiently and consistently within the repository.

## Coding Conventions

**File Naming**
- Use `snake_case` for Python files and directories.
  - Example: `framegen_feature.py`, `menu_common.py`

**Import Style**
- Prefer **relative imports** within modules.
  - Example:
    ```python
    from .utils import calculate_scale
    ```

**Export Style**
- Use **named exports**; explicitly define what is exported from a module.
  - Example:
    ```python
    __all__ = ['FrameGenFeature', 'Upscaler']
    ```

**Commit Messages**
- Freeform style, no strict prefixes.
- Average commit message length: ~39 characters.
- Reference the feature or file changed when possible.
  - Example: `Add FSR3 framegen support for DX12`

## Workflows

### Update README or Documentation
**Trigger:** When updating documentation or adding information to the README.  
**Command:** `/update-docs`

1. Edit `README.md` to add or update content.
2. Commit the changes with a message referencing the update.

_Example commit message:_  
`Update README with new FG backend info`

---

### Add or Update Quirk
**Trigger:** When adding or adjusting a workaround for a specific game or hardware issue.  
**Command:** `/add-quirk`

1. Edit `OptiScaler/misc/Quirks.h` to add or modify a quirk.
2. Optionally update related files:
   - `OptiScaler/dllmain.cpp`
   - `OptiScaler/inputs/FG/DLSSG_Mod.h`
3. Commit with a message referencing the quirk or game.

_Example commit message:_  
`Add quirk for GameX to fix resolution bug`

---

### Menu or UI Feature Tweak
**Trigger:** When adding, adjusting, or fixing menu/UI features.  
**Command:** `/menu-update`

1. Edit `OptiScaler/menu/menu_common.cpp` to implement the change.
2. Commit with a message describing the menu/UI update.

_Example commit message:_  
`Improve UI scaling for 4K displays`

---

### Add or Update FrameGen Feature
**Trigger:** When implementing or modifying a Frame Generation (FG) feature for a backend (DLSSG, FSRFG, XeFG, etc.).  
**Command:** `/add-fg-feature`

1. Edit or add files under `OptiScaler/framegen/<backend>/` (e.g., `DLSSG_Dx12.cpp`).
2. Optionally update related hooks or input files.
3. Commit with a message referencing the FG feature.

_Example commit message:_  
`Add XeFG framegen support for DX12`

---

### Fix or Improve FG Swapchain Release
**Trigger:** When fixing or optimizing swapchain release logic for FG features.  
**Command:** `/fix-fg-swapchain`

1. Edit `OptiScaler/hooks/FG_Hooks.cpp` and/or related FG input files:
   - `OptiScaler/inputs/FG/FSR3_Dx12_FG.cpp`
   - `OptiScaler/inputs/FG/FfxApi_Dx12_FG.cpp`
2. Commit with a message referencing swapchain release improvements.

_Example commit message:_  
`Fix swapchain release bug in FSR3 FG`

---

### Multi-file Feature Integration
**Trigger:** When adding a major feature or refactor that touches multiple subsystems.  
**Command:** `/integrate-feature`

1. Edit or add multiple files across hooks, inputs, menu, upscalers, and config.
2. Update project files if new files are added:
   - `OptiScaler/Config.cpp`
   - `OptiScaler/State.h`
   - `OptiScaler/menu/menu_common.cpp`
   - `OptiScaler/hooks/FG_Hooks.cpp`
   - `OptiScaler/inputs/FG/DLSSG_Mod.h`
   - `OptiScaler/upscalers/FeatureProvider_Dx12.cpp`
   - `OptiScaler/upscalers/FeatureProvider_Dx11.cpp`
   - `OptiScaler/upscalers/FeatureProvider_Vk.cpp`
   - `OptiScaler/OptiScaler.vcxproj`
   - `OptiScaler/OptiScaler.vcxproj.filters`
3. Commit with a message referencing the feature or refactor.

_Example commit message:_  
`Integrate HDR support across all upscalers`

---

## Testing Patterns

- **Framework:** Unknown (no explicit testing framework detected).
- **Test File Pattern:** Files matching `*.test.*`
  - Example: `framegen_feature.test.py`
- **Best Practice:** Place tests alongside implementation files or in a dedicated `tests/` directory, using the `.test.` naming convention.

_Example test file:_
```python
# framegen_feature.test.py

from .framegen_feature import FrameGenFeature

def test_framegen_basic():
    fg = FrameGenFeature()
    assert fg.is_enabled() is True
```

## Commands

| Command            | Purpose                                               |
|--------------------|-------------------------------------------------------|
| /update-docs       | Update README or documentation                        |
| /add-quirk         | Add or update a quirk for a specific game/hardware    |
| /menu-update       | Add or tweak menu or UI features                      |
| /add-fg-feature    | Implement or modify a FrameGen backend feature        |
| /fix-fg-swapchain  | Fix or improve swapchain release logic for FG         |
| /integrate-feature | Integrate a major feature or perform a large refactor |

```