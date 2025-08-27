# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Merge Combinator Custom Template** - A Typst template project for creating branded documents for Merge Combinator, LLC. This template provides professional document formatting with the company's branding and design standards.

### Key Assets
- **Company Logo**: `arrows.png` - The Merge Combinator logo used in documents
- **Template System**: Built on the MDPI journal template foundation, customized for Merge Combinator's needs

## Development Commands

### Essential Commands
```bash
# Run the test suite
just test

# Generate documentation PDF
just doc

# Install package locally for development (uses @local prefix)
just install

# Package for distribution
just package local  # or preview/release

# Run full CI suite (tests + docs)
just ci

# Update test reference outputs
just update

# Uninstall local package
just uninstall
```

### Testing Workflow
- Tests use the `typst-test` framework with reference-based image comparison
- Test files are located in `tests/` directory
- Run `just update` after making intentional output changes to update reference images

## Architecture & Structure

### Core Components
- **`src/lib.typ`** - Main package entry point, exports the template function
- **`src/impl.typ`** - Template implementation containing layout logic and styling
- **`typst.toml`** - Package manifest defining metadata, version, and entry points
- **`arrows.png`** - Merge Combinator logo for brand identity

### Template Function
The main template function will be customized to accept configuration for Merge Combinator documents:
- Document title and subtitle
- Author information
- Custom branding with Merge Combinator logo
- Professional formatting standards

### Package Distribution
- Local development uses `@local` namespace prefix
- Preview releases use `@preview` namespace prefix
- Production releases published to Typst package registry
- `.typstignore` controls which files are included in distribution

## Development Guidelines

### Making Changes
1. Modify template logic in `src/impl.typ`
2. Test changes with `just test`
3. Update documentation if needed with `just doc`
4. Test locally with `just install` before committing

### Adding Features
- New template parameters should be added to the main template function signature
- Maintain backward compatibility when possible
- Document new features in the manual (`docs/manual.typ`)

### Version Management
- Version defined in `typst.toml`
- Follow semantic versioning
- Update version before packaging for release