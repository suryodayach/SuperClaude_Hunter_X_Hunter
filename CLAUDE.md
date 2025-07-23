# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

### Development Commands
```bash
# Install SuperClaude package and dependencies
pip install -e .  # Development installation
pip install SuperClaude  # From PyPI

# Run SuperClaude installer
python3 -m SuperClaude install  # Module approach
SuperClaude install  # Direct command
superclaude install  # Lowercase alias

# Installation profiles
SuperClaude install --minimal      # Core framework only
SuperClaude install --interactive  # Choose components
SuperClaude install --profile developer  # Full installation

# Other operations
SuperClaude update    # Update existing installation
SuperClaude uninstall # Remove SuperClaude
SuperClaude status    # Check installation status
```

### Testing & Quality
Currently, the project lacks formal test suites and linting configuration. When implementing tests or quality checks:
- Check for test framework setup in setup.py or pyproject.toml first
- Look for existing test patterns in the codebase
- Consider adding pytest for Python testing
- Consider adding ruff or flake8 for linting

## Architecture

### Project Structure
SuperClaude is a Python framework that extends Claude Code with specialized commands, personas, and MCP server integration. It uses a documentation-driven approach where markdown files define behavior.

### Core Components

1. **Framework Documentation** (`SuperClaude/Core/`)
   - Entry point: `CLAUDE.md` - Loads all framework components
   - `COMMANDS.md` - 16 slash commands for development tasks
   - `FLAGS.md` - Command flags and auto-activation rules
   - `PERSONAS.md` - 11 AI specialists with domain expertise
   - `MCP.md` - External tool integration (Context7, Sequential, Magic, Playwright)
   - `ORCHESTRATOR.md` - Intelligent routing and decision system
   - `PRINCIPLES.md` - Core development principles
   - `RULES.md` - Operational rules and security guidelines
   - `MODES.md` - Operational modes (Task Management, Introspection, Token Efficiency)

2. **Slash Commands** (`SuperClaude/Commands/`)
   - Development: `/sc:implement`, `/sc:build`, `/sc:design`
   - Analysis: `/sc:analyze`, `/sc:troubleshoot`, `/sc:explain`
   - Quality: `/sc:improve`, `/sc:test`, `/sc:cleanup`
   - Others: `/sc:document`, `/sc:git`, `/sc:estimate`, `/sc:task`, `/sc:index`, `/sc:load`, `/sc:spawn`

3. **Installation System** (`setup/`)
   - Modular component-based installation
   - Profile support (minimal, quick, developer)
   - Cross-platform compatibility
   - MCP server integration

### Key Design Patterns

1. **Documentation-Driven**: Commands and behavior defined in markdown files
2. **Persona System**: Auto-activating AI specialists based on context
3. **MCP Integration**: External tools for docs, UI, testing, and analysis
4. **Wave Orchestration**: Multi-stage execution for complex operations
5. **Token Optimization**: Intelligent compression and resource management

### Integration Points

1. **Claude Code**: Extends via `~/.claude/` directory structure
2. **MCP Servers**: Integrated via Claude Code's MCP protocol
3. **Python Package**: Standard setuptools/hatchling packaging
4. **CLI Entry Points**: `SuperClaude`, `superclaude` commands

### Security Considerations

- Always use absolute paths (security requirement)
- Read before Write/Edit operations (mandatory)
- No automatic commits without user permission
- Path traversal prevention in file operations
- Sensitive data protection in logs and commits

### Development Workflow

When modifying SuperClaude:
1. Changes to commands → Edit markdown files in `SuperClaude/Commands/`
2. Framework behavior → Modify Core documentation files
3. Installation logic → Update `setup/` components
4. New features → Consider impacts on personas, MCP servers, and orchestration
5. Version updates → Update VERSION file and setup.py/pyproject.toml

### Important Notes

- Framework uses Python 3.8+ features
- Minimal external dependencies (only setuptools)
- Hooks system removed in v3 (planned for v4)
- Commands prefix changed from `/` to `/sc:` in v3
- Installation creates files in `~/.claude/` directory