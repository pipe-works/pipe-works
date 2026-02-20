# pipe-works (Meta-Package)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)

> **Status: Pre-release** — This meta-package is not yet published. We are waiting for all component libraries to reach **1.0.0 Beta** before releasing the unified `pipe-works` bundle.

---

## What is This?

`pipe-works` is a **meta-package** (also called a convenience package or umbrella package) that bundles all pipe-works tools into a single installation. Instead of installing each component separately, you'll be able to:

```bash
# Future: One command to install the entire ecosystem
pip install pipe-works

# Instead of:
pip install pipeworks-name-generation
pip install pipeworks-conditional-axis
pip install pipeworks-image-generator
pip install mud-server
```

## Purpose

This repository serves as:

1. **Integration Point**: A single dependency for projects that want the full pipe-works toolkit
2. **Version Coordination**: Ensures compatible versions of all components are installed together
3. **Organization Hub**: Central documentation and issue tracking for cross-component concerns
4. **Release Management**: Coordinated releases across the ecosystem

## Current Status

**Not yet released.** We are taking a disciplined approach:

| Component                                                                                              | Current Version | Target     | Status                |
| ------------------------------------------------------------------------------------------------------ | --------------- | ---------- | --------------------- |
| [pipeworks_name_generation](https://github.com/pipe-works/pipeworks_name_generation)                   | 0.5.20          | 1.0.0-beta | 🟡 Active Development |
| [pipeworks_entity_state_generation](https://github.com/pipe-works/pipeworks_entity_state_generation)   | 0.11.1          | 1.0.0-beta | 🟡 Active Development |
| [pipeworks_axis_descriptor_lab](https://github.com/pipe-works/pipeworks_axis_descriptor_lab)            | 0.1.10          | 1.0.0-beta | 🟡 Active Development |
| [pipeworks-image-generator](https://github.com/pipe-works/pipeworks-image-generator)                   | 0.1.1           | 1.0.0-beta | 🟡 Active Development |
| [pipeworks_mud_server](https://github.com/pipe-works/pipeworks_mud_server)                             | 0.1.1           | 1.0.0-beta | 🟡 Active Development |
| [pipeworks_mud_mapper](https://github.com/pipe-works/pipeworks_mud_mapper)                             | 0.1.10          | 1.0.0-beta | 🟠 Alpha              |
| **pipe-works (meta)**                                                                                  | -               | 1.0.0-beta | ⏸️ Waiting            |

Once all components reach 1.0.0 Beta, this meta-package will be published to PyPI.

## Planned Structure

When released, the meta-package will have minimal code—primarily a `pyproject.toml` that declares dependencies:

```toml
[project]
name = "pipe-works"
version = "1.0.0-beta"
dependencies = [
    "pipeworks-name-generation>=1.0.0b1",
    "pipeworks-conditional-axis>=1.0.0b1",
    "pipeworks-image-generator>=1.0.0b1",
    "mud-server>=1.0.0b1",
]
```

### Optional Extras

```bash
# Install with all optional dependencies
pip install pipe-works[all]

# Or select specific extras
pip install pipe-works[dev]      # Development tools
pip install pipe-works[docs]     # Documentation building
pip install pipe-works[ml]       # ML models for image generation
```

## Component Libraries

### Core Generation Tools

- **[pipeworks_name_generation](https://github.com/pipe-works/pipeworks_name_generation)** - Deterministic phonetic name generator
  - Zero runtime dependencies
  - Seeded RNG for reproducibility
  - Build tools for custom corpora

- **[pipeworks_entity_state_generation](https://github.com/pipe-works/pipeworks_entity_state_generation)** - Axis-based character condition generator
  - Character physical/social conditions (6 axes: physique, age, health, wealth, demeanor, reputation)
  - Facial signals (12 signal types) and occupation axes
  - Zero runtime dependencies, weighted probability with exclusion rules

- **[pipeworks-image-generator](https://github.com/pipe-works/pipeworks-image-generator)** - Code-first image generation framework
  - Plugin architecture with lifecycle hooks
  - Workflow system (character portraits, game assets)
  - Z-Image-Turbo adapter with Gradio UI

### Development & Authoring Tools

- **[pipeworks_axis_descriptor_lab](https://github.com/pipe-works/pipeworks_axis_descriptor_lab)** - LLM descriptor testing workbench
  - Tests how small LLMs (via Ollama) produce non-authoritative descriptive text from axis payloads
  - IPC fingerprinting for descriptor comparison
  - FastAPI + vanilla JS, 561 tests / 99% coverage

- **[pipeworks_mud_mapper](https://github.com/pipe-works/pipeworks_mud_mapper)** - Interactive MUD zone editor
  - Visual map editor for creating and editing MUD zone files
  - Room management, exit system, multi-level support
  - Two-file workflow: SQLite for authoring, JSON exports for game server
  - Dash + Plotly interface

### Game Server

- **[pipeworks_mud_server](https://github.com/pipe-works/pipeworks_mud_server)** - The Undertaking MUD server
  - FastAPI backend + Gradio UI
  - Axis-based resolution system
  - Ledger/newspaper dual-layer truth
  - Integrates all generation tools

## Philosophy

All pipe-works tools follow these principles:

- **Determinism over Performance** - Same seed = same result (critical for game state)
- **Procedural over Manual** - Characters are issued, not built
- **Code-first over UI-first** - Tools are libraries, UIs are interfaces
- **GPL-3.0-or-later** - Open tools for open systems

## Development

### For Meta-Package Development

This repository will remain minimal until the 1.0.0-beta milestone. Current work focuses on:

1. Monitoring component library progress toward 1.0.0-beta
2. Maintaining organization-wide documentation
3. Coordinating cross-component features
4. Planning the initial meta-package release

### For Component Development

To contribute to a specific tool:

1. Navigate to the component repository (links above)
2. Read the component's `CONTRIBUTING.md`
3. Follow the [organization development standards](https://github.com/pipe-works/.github)

All components follow unified standards:

- Python 3.12+
- pytest with 80% coverage minimum
- black (26.1.0) / ruff / mypy for code quality
- Conventional commits for semantic versioning
- Release-please for automated releases

## Documentation

- **Organization Standards**: [pipe-works/.github](https://github.com/pipe-works/.github)
- **Philosophy & Demos**: [pipe-works.org](https://pipe-works.org)
- **Design System**: [styles/](styles/) — App tools and editorial style guides, base CSS, token maps
- **Component Docs**:
  - [pipeworks_name_generation docs](https://pipeworks-name-generation.readthedocs.io/en/latest/)
  - [pipeworks_entity_state_generation docs](https://pipeworks-entity-state-generation.readthedocs.io/en/latest/)
  - [pipeworks_axis_descriptor_lab docs](https://pipeworks-axis-descriptor-lab.readthedocs.io/en/latest/)
  - [pipeworks-image-generator docs](https://pipeworks-image-generator.readthedocs.io/en/latest/)
  - [pipeworks_mud_server docs](https://pipeworks-mud-server.readthedocs.io/en/latest/)
  - [pipeworks_mud_mapper docs](https://pipeworks-mud-mapper.readthedocs.io/en/latest/)

## Why No CI/CD Yet?

**Per audit recommendation 4.2**: This repository currently has no CI/CD pipeline because:

1. **No code to test yet** - Meta-packages are primarily dependency declarations
2. **Components have their own CI** - Each library has comprehensive testing
3. **Avoiding premature automation** - CI will be added when there's actual package structure

Once we create the `pyproject.toml` and initial package structure (targeting 1.0.0-beta), we will add:

- CI to validate package structure
- Tests to verify dependency resolution
- Documentation builds
- Release automation via release-please

This is a deliberate decision to avoid maintaining unused infrastructure.

## Roadmap

### Phase 1: Component Stabilization (Current)

- [ ] All components reach 1.0.0-beta
- [ ] APIs stabilized across libraries
- [ ] Integration testing between components

### Phase 2: Meta-Package Setup

- [ ] Create `pyproject.toml` with dependency specifications
- [ ] Add CI/CD pipeline
- [ ] Write installation and usage documentation
- [ ] Set up PyPI publishing

### Phase 3: Release

- [ ] Publish 1.0.0-beta to PyPI
- [ ] Announce unified installation path
- [ ] Gather feedback on version coordination

## Questions or Feedback?

- **For specific tool issues**: Open an issue in the relevant component repository
- **For cross-component or organization-wide concerns**: Open an issue here
- **For general discussion**: Visit [pipe-works.org](https://pipe-works.org)

## License

This meta-package and all components are licensed under **GPL-3.0-or-later**.

We chose GPL-3.0-or-later because:

1. **Derivative works stay open** - Build on pipe-works, share improvements
2. **Community ownership** - No company can privatize this work
3. **Long-term sustainability** - The ecosystem remains accessible to everyone
4. **Alignment with philosophy** - Open tools for open systems

---

**Note**: This README describes planned functionality. The meta-package does not yet exist as an installable Python package. Check back when all components reach 1.0.0-beta!
