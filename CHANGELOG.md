# Changelog

All notable changes to this configuration will be documented in this file.

## [4.0.0] - 2026-01-17

### Added
- Comprehensive documentation overhaul:
  - `SETUP.md` - Detailed installation and configuration guide
  - `TIPS_AND_TRICKS.md` - Advanced usage patterns and workflows
  - `TROUBLESHOOTING.md` - Common issues and solutions
  - `REFERENCES.md` - Additional resources and learning materials
- Significantly expanded `EDITOR_COMPARISON.md` with detailed compatibility analysis
- Enhanced `KEYBINDINGS.md` with more comprehensive key mapping documentation

### Changed
- Major improvements to configuration files with better organization and documentation
- Updated `README.md` with improved structure and clarity
- Refined keybindings for better usability and consistency

## [3.2.0] - 2026-01-16

### BREAKING CHANGE
- Multi-editor support has been removed in favor of a single, unified configuration
- The `config/vscode`, `config/cursor`, and `config/antigravity` directories have been removed
- Configuration files now reside in the root `config` directory

### Added
- `EDITOR_COMPARISON.md` to provide analysis of editor compatibility and potential issues

### Changed
- Keybindings updated to align with LazyVim conventions, using `<space>` as the primary leader key:
  - **File Explorer Toggle:** `<space>e` (was `ctrl+shift+e`)
  - **Workspace Search:** `<space>/` (was `ctrl+shift+f`)
  - **Format Document:** `<space>f` (was `ctrl+space f`)
  - **Navigate Back:** `ctrl+o` (was `ctrl+t`)
- Consolidated configuration from multi-editor structure back to unified setup
- Updated documentation to reflect simplified structure

### Removed
- `CLAUDE.md` (content integrated into other documentation)
- Multi-editor scaffolding directories

## [3.1.0] - 2026-01-16

### Added
- Official support for Windsurf (Antigravity) editor.
- Populated `config/antigravity/` with `settings.json` and `keybindings.json` based on the VS Code configuration.

### Changed
- Updated `README.md` to reflect full support for Antigravity.

## [3.0.0] - 2026-01-16

### BREAKING CHANGE
- Configuration files moved from `config/` to `config/vscode/`
- Users must update their installation paths

### Added
- Multi-editor repository structure
- Scaffolding for Cursor editor support (`config/cursor/`)
- Scaffolding for Windsurf/Antigravity editor support (`config/antigravity/`)
- "Supported Editors" table in README.md
- Editor-specific README files in each config directory
- Guidelines for adding new editor support in CLAUDE.md

### Changed
- VS Code configuration now lives in `config/vscode/` subdirectory
- Updated all documentation to reflect new structure
- KEYBINDINGS.md now notes it is VS Code-specific
- CLAUDE.md rewritten for multi-editor architecture

## [2.0.0] - 2026-01-16

### Added
- `KEYBINDINGS.md` - Quick reference cheatsheet for all keybindings
- `CLAUDE.md` - Documentation for working with Claude Code on this repository

### Changed
- Minor updates to `CHANGELOG.md` formatting and organization

**Note:** This release focused on documentation. All configuration features were part of v1.0.0.

## [1.0.0] - 2025-01-22

Initial release with comprehensive Vim keybindings for VS Code.

### Added
- Custom status line integration with mode-specific colors
- Enhanced editor settings
  - Bracket pair colorization
  - Improved minimap configuration
  - Better bracket guides
- Visual mode features
  - Line sorting: `<leader>ss`
  - Case transformation: `<leader>u`, `<leader>l`
  - Select all occurrences: `<leader>a`
- Improved Vim experience
  - Yank highlighting
  - Better fold handling
  - Custom search highlighting
  - EasyMotion and Sneak plugins enabled
- Navigation shortcuts
  - Split navigation: `ctrl+h/j/k/l`
  - Tab navigation: `alt+[`, `alt+]`
  - Definition jumping: `ctrl+]`, `ctrl+t`
- Split management
  - Resize shortcuts: `alt+h`, `alt+l`
  - Maximize toggle: `ctrl+w m`
- Terminal integration
  - Toggle terminal: `ctrl+;`
  - Maximize terminal: `ctrl+shift+;`
- File explorer integration
  - Toggle sidebar: `<leader>e`
  - Reveal in explorer: `<leader>f`
- Basic operations
  - Exit insert mode: `jj`
  - Toggle comment: `<leader>c`
  - Clear search: `ctrl+n`
