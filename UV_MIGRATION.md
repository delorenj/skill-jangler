# UV Migration Guide

This project has been migrated to use **uv** as the primary Python package manager.

## What Changed?

### Before (Old Way - Still Works)
```bash
# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install requests beautifulsoup4 pytest

# Run commands
python3 cli/doc_scraper.py --config configs/godot.json
python3 cli/package_skill.py output/godot/
```

### After (New Way - Recommended)
```bash
# One-time setup: Install dependencies
uv sync

# Run commands (no venv activation needed!)
uv run skill-seekers --config configs/godot.json
uv run skill-seeker-package output/godot/
```

## Benefits of UV

✅ **Faster** - 10-100x faster than pip
✅ **Simpler** - No manual venv management
✅ **Reliable** - Lockfile ensures consistent installs
✅ **Modern** - Latest Python packaging best practices

## Installation

### Install UV

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows:**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**With pip:**
```bash
pip install uv
```

### Install Project Dependencies

```bash
# Clone repository
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers

# Install all dependencies (creates .venv automatically)
uv sync

# That's it! You're ready to go.
```

## Command Reference

### Core Commands

| Old Command | New Command |
|------------|-------------|
| `python3 cli/doc_scraper.py` | `uv run skill-seekers` or `uv run skill-seeker-scrape` |
| `python3 cli/estimate_pages.py` | `uv run skill-seeker-estimate` |
| `python3 cli/enhance_skill.py` | `uv run skill-seeker-enhance` |
| `python3 cli/enhance_skill_local.py` | `uv run skill-seeker-enhance-local` |
| `python3 cli/package_skill.py` | `uv run skill-seeker-package` |
| `python3 cli/upload_skill.py` | `uv run skill-seeker-upload` |
| `python3 cli/pdf_scraper.py` | `uv run skill-seeker-pdf` |
| `python3 cli/generate_router.py` | `uv run skill-seeker-router` |
| `python3 cli/split_config.py` | `uv run skill-seeker-split` |
| `python3 cli/run_tests.py` | `uv run skill-seeker-test` |

### Optional Dependencies

```bash
# Install with PDF support
uv sync --extra pdf

# Install with MCP server support
uv sync --extra mcp

# Install with API enhancement support
uv sync --extra enhance

# Install development tools
uv sync --extra dev

# Install everything
uv sync --all-extras
```

## Examples

### Basic Workflow

```bash
# Install dependencies
uv sync

# Scrape documentation
uv run skill-seekers --config configs/react.json

# Package the skill
uv run skill-seeker-package output/react/
```

### With PDF Support

```bash
# Install with PDF dependencies
uv sync --extra pdf

# Scrape a PDF
uv run skill-seeker-pdf --pdf docs/manual.pdf --name myskill
```

### With Local Enhancement

```bash
# Scrape and enhance
uv run skill-seekers --config configs/godot.json --enhance-local

# Or enhance separately
uv run skill-seeker-enhance-local output/godot/
```

## Running Tests

```bash
# Install dev dependencies
uv sync --extra dev

# Run tests
uv run pytest

# Or use the test command
uv run skill-seeker-test
```

## Troubleshooting

### "uv: command not found"

Install uv first:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### "No module named 'cli'"

Run `uv sync` to install the project:
```bash
uv sync
```

### Old venv Still Active

Deactivate the old virtual environment:
```bash
deactivate
```

Then use `uv run` commands - no activation needed!

### Want to Use Old Way?

The old commands still work:
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 cli/doc_scraper.py --config configs/godot.json
```

## For Contributors

### Development Setup

```bash
# Clone and install with all dev tools
git clone https://github.com/yusufkaraaslan/Skill_Seekers.git
cd Skill_Seekers
uv sync --all-extras

# Run tests
uv run pytest

# Format code
uv run ruff format .

# Lint code
uv run ruff check .
```

### Adding Dependencies

**Don't edit requirements.txt!** Use pyproject.toml instead:

```bash
# Add a regular dependency
uv add requests

# Add an optional dependency
uv add --extra pdf PyMuPDF

# Add a dev dependency
uv add --dev pytest
```

### Lock File

The `uv.lock` file ensures everyone gets the same dependency versions. Commit it to git:

```bash
git add uv.lock
git commit -m "Update dependencies"
```

## Migration Checklist

- [x] Created pyproject.toml with all dependencies
- [x] Added CLI entry points for all commands
- [x] Made cli/ and mcp/ proper Python packages
- [x] Updated .gitignore for uv files
- [x] Tested uv sync
- [x] Tested all CLI commands
- [ ] Updated README.md
- [ ] Updated CLAUDE.md
- [ ] Updated QUICKSTART.md
- [ ] Updated BULLETPROOF_QUICKSTART.md
- [ ] Updated docs/*.md

## Questions?

- **UV Documentation**: https://docs.astral.sh/uv/
- **Project Issues**: https://github.com/yusufkaraaslan/Skill_Seekers/issues
- **UV vs pip**: https://docs.astral.sh/uv/pip/compatibility/

---

**Happy coding with UV!** 🚀
