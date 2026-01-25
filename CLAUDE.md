# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Organization Guide

This is the **canonical pipe-works organization guide** - the authoritative reference for development patterns, standards, and architectural decisions across all pipe-works repositories.

**Core Philosophy**: Create open-source tools for interactive fiction that emphasize determinism, procedural generation, and player agency through issued characters and axis-based resolution systems.

## Repository Ecosystem

The pipe-works organization maintains **7 interconnected projects**, each with its own CLAUDE.md file for detailed guidance:

```
pipe-works (GitHub Organization)
├── pipe-works/                      # This repo - Organization guide and README
├── pipe-works-org/                  # Static website (HTML/CSS/JS)
├── pipeworks_mud_server/            # The Undertaking MUD server (Python/FastAPI/Gradio)
├── pipeworks-image-generator/       # Image generation framework (Python/Z-Image-Turbo/Gradio)
├── pipeworks_entity_state_generation/ # Character/facial condition generator (Python)
├── pipeworks_name_generation/       # Phonetic name generator (Python)
└── pipeworks_character_sheet_generator/ # Character sheet generation (Python) [Coming soon]
```

## Repository Summaries

### 1. pipe-works
**Purpose**: Organization guide and documentation hub
**Tech Stack**: Markdown documentation
**Status**: Active documentation

This repository serves as the "front door" for the pipe-works ecosystem, providing the canonical README and this organizational CLAUDE.md.

### 2. pipe-works-org
**Purpose**: Static promotional website for pipe-works.org
**Tech Stack**: HTML, CSS (no build system), vanilla JavaScript
**Status**: Active development

A print-workshop aesthetic website with "goblin laws" themed content, shared typography system (6 font families), and interactive story game (Crooked Pipe).

**Repository**: https://github.com/pipe-works/pipe-works-org
**CLAUDE.md**: See repo for detailed guidance

### 3. pipeworks_mud_server
**Purpose**: The Undertaking - procedural, ledger-driven MUD server
**Tech Stack**: Python 3.12+, FastAPI, Gradio, SQLite
**Status**: Proof-of-concept (implements foundation, designs full vision)

A multiplayer interactive fiction system where:
- **Characters are issued, not built** - procedural goblin generation
- **Failure is recorded as data** - axis-based resolution (6 axes)
- **Ledgers are truth, newspapers are stories** - dual-layer truth system
- **Optimization is resisted** - no "best builds"
- **Players become creators** - Gradio authoring toolkit

**Repository**: https://github.com/pipe-works/pipeworks_mud_server
**CLAUDE.md**: See repo for detailed guidance

### 4. pipeworks-image-generator
**Purpose**: Image generation framework for Z-Image-Turbo
**Tech Stack**: Python 3.12+, HuggingFace Diffusers, Gradio 5.0+, PyTorch
**Status**: Active development

Code-first image generation with plugin architecture, workflow system, prompt builder, multi-model adapter registry, and Gradio web UI.

**Repository**: https://github.com/pipe-works/pipeworks-image-generator
**CLAUDE.md**: See repo for detailed guidance

### 5. pipeworks_entity_state_generation
**Purpose**: Procedural character condition and facial signal generator
**Tech Stack**: Python 3.12+ (zero runtime dependencies)
**Status**: Active development

Axis-based condition generation with weighted probabilities and exclusion rules for coherence. Conditions exist on axes (e.g., "Stable ↔ Precarious"), not binary flags.

**Repository**: https://github.com/pipe-works/pipeworks_entity_state_generation
**CLAUDE.md**: See repo for detailed guidance

### 6. pipeworks_name_generation
**Purpose**: Phonetic name generator (context-free, deterministic)
**Tech Stack**: Python 3.12+ (zero runtime dependencies)
**Status**: Phase 1 complete (simple pattern), build tools active

Deterministic name generation with syllable extraction (Pyphen/NLTK), feature annotation, structural candidate generation, and policy-based filtering.

**Repository**: https://github.com/pipe-works/pipeworks_name_generation
**CLAUDE.md**: See repo for detailed guidance

### 7. pipeworks_character_sheet_generator
**Status**: Not yet created
**Purpose**: Generate character sheets for issued goblins (planned integration with MUD server)

## Cross-Project Integration

These projects are designed to work together:

```
┌─────────────────────────────────────────────────────────────────┐
│                    pipeworks_mud_server                         │
│              (The Undertaking - Main Game Server)               │
│                                                                 │
│  Integrates:                                                    │
│  • pipeworks_name_generation → Character name issuance          │
│  • pipeworks_entity_state_generation → Character quirks/failing │
│  • pipeworks-image-generator → Character portraits              │
│  • pipeworks_character_sheet_generator → Sheet generation       │
└─────────────────────────────────────────────────────────────────┘
                              ▲
                              │
                    ┌─────────┴─────────┐
                    │                   │
        ┌───────────▼──────┐  ┌────────▼─────────┐
        │ pipeworks_       │  │ pipeworks-       │
        │ name_generation  │  │ image-generator  │
        │                  │  │                  │
        │ Phonetic names   │  │ AI portraits     │
        └──────────────────┘  └──────────────────┘
                    │
        ┌───────────▼──────────────────┐
        │ pipeworks_entity_state_      │
        │ generation                   │
        │                              │
        │ Character conditions,        │
        │ facial signals, occupations  │
        └──────────────────────────────┘
```

**Integration Patterns**:
1. **Name Generation**: MUD server calls name generator with seed (deterministic)
2. **Condition Generation**: Character issuance pulls from condition axes
3. **Image Generation**: Portrait workflow uses character conditions in prompts
4. **Website**: pipe-works-org promotes the ecosystem

## Organization Standards

### Python Development Standards

**Python Version**: 3.12+ minimum
- Best CUDA/PyTorch compatibility across ML libraries
- Mature and stable with all major libraries tested
- Supported until October 2028
- **CI Strategy**: Test on both 3.12 and 3.13 for forward compatibility

**Virtual Environments**: pyenv virtualenvs (one per repository)
```bash
# Create virtualenv for a repo
pyenv virtualenv 3.12.x <repo-name>

# Examples
pyenv virtualenv 3.12 pipeworks_name_generation
pyenv virtualenv 3.12 pipeworks_audio_processing
```

**Code Quality Standards**:
- **Line Length**: 100 characters (black/ruff)
- **Type Hints**: Required for all public APIs
- **Testing**: pytest with coverage reports (>85% overall, >90% core)
- **CI/CD**: GitHub Actions (test, lint, coverage)
- **Pre-commit Hooks**: black, ruff, mypy

### Determinism Requirements

All generator projects (name, entity state) prioritize determinism:
```python
# ALWAYS use Random(seed), NOT random.seed()
rng = random.Random(seed)  # Isolated RNG instance
```

**Critical Rule**: Same seed MUST produce same result. This is essential for:
- Game entity ID mapping
- Reproducible character generation
- Debugging and testing
- Player experience consistency

### Configuration Patterns

- **Environment-based**: Use Pydantic Settings with `PIPEWORKS_*` prefix
- **YAML-based**: For policy configurations and content libraries
- **JSON-based**: For world/data definitions

### Documentation Standards

Each repository maintains:
- **CLAUDE.md**: AI-assisted development guide referencing this org guide
- **README.md**: User-facing documentation
- **docs/**: Detailed design docs (for complex projects)
- **Sphinx/MkDocs**: Auto-generated API docs (where applicable)

**Repository CLAUDE.md Pattern**:
```markdown
## pipe-works Organization Standards

This repository follows pipe-works organization standards.
See https://github.com/pipe-works/pipe-works/blob/main/CLAUDE.md for full details.

- Python 3.12+, pyenv virtualenvs
- pytest >85% coverage
- black/ruff/mypy code quality
- Conventional commits (where using release-please)
- GPL-3.0-or-later license
```

### Testing Standards

**Test Structure**:
```
tests/
├── unit/                    # Fast, isolated tests
├── integration/             # Tests with real dependencies
├── e2e/                     # End-to-end workflows
├── fixtures/                # Shared test data
└── conftest.py              # Shared fixtures
```

**Coverage Standards**:
| Type | Minimum | Target |
|------|---------|--------|
| Unit | 90% | 95% |
| Integration | 70% | 80% |
| Overall | 85% | 90% |

## Important Constraints Across Projects

### Zero Runtime Dependencies (Where Applicable)

Core generator libraries maintain zero runtime dependencies:
- **pipeworks_name_generation**: Pure Python at runtime
- **pipeworks_entity_state_generation**: Pure Python at runtime
- **Build tools** can have dependencies, but runtime code must be minimal

**Rationale**: Minimize supply chain risk, maximize portability, ensure long-term maintainability.

### GPL-3.0 Licensing

All projects are GPL-3.0 licensed. When adding dependencies:
- Check license compatibility (must be GPL-compatible)
- Document in requirements.txt/pyproject.toml
- Avoid proprietary or restrictive licenses

### Determinism Over Performance

For game-critical code (name generation, character issuance):
- **Determinism is paramount** (same seed = same result)
- Performance is secondary
- Use seeded RNG instances, not global random state
- All randomness must be reproducible

### Programmatic vs. LLM Responsibilities

**Programmatic systems are AUTHORITATIVE**:
- Character names, attributes, quirks
- Resolution math and axis calculations
- Ledger truth and game state
- All game mechanics

**LLMs are NON-AUTHORITATIVE**:
- Descriptions and flavor text
- Newspaper interpretations
- Help text and explanations
- Narrative generation

This separation prevents hallucinated mechanics, balance drift, and schema corruption.

## Version Control Patterns

### Conventional Commits

Projects using release-please (pipeworks_name_generation, future projects) require conventional commits:
```
feat(scope): Add new feature
fix(scope): Fix bug
docs: Update documentation
refactor: Restructure code
chore: Maintenance tasks
```

**Types**:
- `feat:` - New feature (triggers minor version bump in 0.x, major in 1.x+)
- `fix:` - Bug fix (triggers patch version bump)
- `docs:` - Documentation only changes
- `refactor:` - Code refactoring with no functionality change
- `chore:` - Maintenance tasks (hidden in changelog)

### Branch Strategies

- **main**: Stable releases
- **develop**: Active development (where applicable)
- **feature/***: Feature branches

### Versioning Strategy (Semantic Versioning)

While in **0.x (Alpha)**:
- `0.x.0` - New features, capabilities, or breaking changes
- `0.x.y` - Bug fixes, documentation, internal refactoring

Move to **1.0.0 (Stable)** when:
- Core features complete and tested
- API stable and production-ready
- External users exist
- Documentation comprehensive

## Common Questions

**Q: Which project should I contribute to first?**
A: Depends on your interest! Start with README.md files to understand each project.

**Q: Where is the canonical organization guide?**
A: You're reading it! This file (pipe-works/CLAUDE.md) is the canonical source.

**Q: How do I reference org standards in my repo's CLAUDE.md?**
A: Include a section linking to this file (see Documentation Standards above).

**Q: Which project handles name generation?**
A: pipeworks_name_generation - deterministic phonetic names

**Q: Which project generates character conditions?**
A: pipeworks_entity_state_generation - axis-based conditions

**Q: Which project is the main game server?**
A: pipeworks_mud_server - The Undertaking MUD server

**Q: Which project generates images?**
A: pipeworks-image-generator - Z-Image-Turbo framework

**Q: Where is the website code?**
A: pipe-works-org - Static HTML/CSS website

## Project Status Summary

| Project | Status | Current Version | Test Coverage | CI/CD |
|---------|--------|----------------|---------------|-------|
| pipe-works | Documentation | N/A | N/A | No |
| pipe-works-org | Active | N/A | N/A | No |
| pipeworks_mud_server | Proof-of-Concept | N/A | High | ✅ |
| pipeworks-image-generator | Active | N/A | 50%+ (core: 93-100%) | ✅ |
| pipeworks_entity_state_generation | Active | N/A | High | ✅ |
| pipeworks_name_generation | Phase 1 | 0.2.0 (Alpha) | High | ✅ |

## Future Development

### Short-term (Phase 1)
- ✅ Name generator foundation (complete)
- ✅ Entity state generator foundation (complete)
- ✅ Image generator framework (complete)
- ⏳ MUD server proof-of-concept (active)
- ⏳ Website polish (active)

### Medium-term (Phase 2)
- Character issuance system in MUD server
- Axis-based resolution engine
- Ledger and newspaper systems
- Integration of all generators into MUD server
- Character sheet generator project

### Long-term (Phase 3+)
- Creator's toolkit (Gradio authoring environment)
- Player-created content pipeline
- Multi-server federation
- Advanced procedural systems (items, rooms, NPCs)

## License

All projects in the pipe-works organization are licensed under **GPL-3.0-or-later**.

See individual project LICENSE files for details.

---

**pipe-works Organization** - Building tools for accountable, procedural interactive fiction.

For implementation guidance specific to a repository, see that repository's CLAUDE.md file.
