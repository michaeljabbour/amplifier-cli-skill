# This front door has moved

Use [Build with Amplifier](https://michaeljabbour.github.io/amplifier-skill-build-amplifier/) for the current guide, downloadable portable method and evidence scopes. The [maintained source](https://github.com/michaeljabbour/amplifier-skill-build-amplifier) combines the developer topics behind one independently installable entry.

This historical repository and its original method files are retained for existing installs, pinned references and Git history. The payload below has not been replaced.

To install the maintained method, clone the current source and run its installer into your host’s skills-parent directory (shown here as `~/.agents/skills`):

```sh
git clone https://github.com/michaeljabbour/amplifier-skill-build-amplifier.git
cd amplifier-skill-build-amplifier
python3 scripts/capability.py install --dest ~/.agents/skills
```

The portable install includes its references and license; it starts no service and requires no Amplifier runtime or Memory installation. Native execution has separate prerequisites and evidence limits.

---

# Amplifier CLI Skill

A Claude Code skill that teaches how to build CLI applications using [Amplifier](https://github.com/microsoft/amplifier) foundation patterns.

## What This Skill Provides

This skill teaches:
- **Bundle composition** - Load, compose, prepare, and execute sessions
- **Module ecosystem** - Using 36+ available Amplifier modules
- **Session orchestration** - Loop-streaming, context management, and hooks
- **Production patterns** - Memory systems, safety hooks, and debugging
- **Foundation patterns** - Source-of-truth workflows from amplifier-foundation

## Installation

**Quick install:**
```bash
/plugin install https://github.com/michaeljabbour/amplifier-cli-skill
```

**OpenAI Codex CLI (local):**
```bash
# from the repo root
CODEX_HOME="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$CODEX_HOME/skills"
ln -s "$(pwd)/skills/amplifier-cli-skill" "$CODEX_HOME/skills/amplifier-cli-skill"
# restart Codex to pick up new skills
```

**For detailed installation instructions, troubleshooting, and alternative methods, see [INSTALLATION.md](INSTALLATION.md).**

Once installed, Claude Code will automatically use this skill when you:
- Ask about building CLI applications
- Work with Amplifier bundles or modules
- Need help with session orchestration
- Request guidance on production patterns

## Repository Structure

```
amplifier-cli-skill/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata
├── skills/
│   └── amplifier-cli-skill/
│       ├── SKILL.md             # Main skill definition
│       └── references/          # Deep-dive documentation
│           ├── ARCHITECTURE.md
│           ├── ARCHITECTURE_FLOWS.md
│           ├── BUILD_PATTERNS.md
│           ├── CONTRIBUTING.md
│           ├── CUSTOM_EXTENSIONS.md
│           ├── EXAMPLES.md
│           ├── HOOKS.md
│           ├── MEMORY.md
│           ├── REFERENCE_IMPLEMENTATION_HISTORY.md
│           ├── TROUBLESHOOTING.md
│           └── README.md
├── .github/
│   └── AUDIT_PROMPT.md          # Maintainer tools
├── LICENSE                       # MIT License
└── README.md                     # This file
```

## Amplifier Ecosystem

This skill is part of the broader Amplifier ecosystem:

### Core Repositories
- **[amplifier](https://github.com/microsoft/amplifier)** - Main framework repository
- **[amplifier-core](https://github.com/microsoft/amplifier-core)** - Core library (execution engine)
- **[amplifier-foundation](https://github.com/microsoft/amplifier-foundation)** - Foundation library (configuration/composition layer)
- **[Amplifier Modules](https://github.com/microsoft/amplifier/blob/main/docs/MODULES.md)** - Module catalog (36+ available modules)

### Related Skills
- **[amplifier-modulebuilder-skill](https://github.com/michaeljabbour/amplifier-modulebuilder-skill)** - Agent Skill for building amplifier-foundation modules
  - Learn to create custom tools, hooks, providers, contexts, and orchestrators
  - "Bricks and studs" architecture patterns
  - Testing strategies and best practices

### Reference Implementations
- **[amplifier-simplecli](https://github.com/michaeljabbour/amplifier-simplecli)** - Production terminal UI implementation
  - Complete CLI application built with amplifier-foundation
  - Example of bundle composition and module usage
  - Memory system and hooks integration

**Learning Path**: Build modules with amplifier-modulebuilder-skill → Compose them into apps with this skill → See them in action in amplifier-simplecli

## Quick Start Example

```python
from amplifier_foundation import load_bundle

async def main():
    # 1. Load bundles
    base = await load_bundle("./bundles/base.md")
    provider = await load_bundle("./providers/opus.yaml")

    # 2. Compose bundles
    composed = base.compose(provider)

    # 3. Prepare (downloads modules)
    prepared = await composed.prepare()

    # 4. Create session and execute
    async with await prepared.create_session() as session:
        response = await session.execute("Hello!")
        print(response)
```

## Documentation

- **[SKILL.md](skills/amplifier-cli-skill/SKILL.md)** - Main skill documentation with quick start patterns
- **[references/](skills/amplifier-cli-skill/references/)** - Deep-dive guides on architecture, hooks, memory, and more
- **[EXAMPLES.md](skills/amplifier-cli-skill/references/EXAMPLES.md)** - Complete bundle examples ready to copy

## Contributing

See [CONTRIBUTING.md](skills/amplifier-cli-skill/references/CONTRIBUTING.md) for repository structure and guidelines.

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Version

**2.0.0** - Plugin-enabled skill with comprehensive documentation and production patterns.
