# Changelog

All notable changes to this configuration will be documented in this file.

## [2.0.0] - 2026-01-17

Major update with comprehensive documentation, community health files, and refined keybindings.

### Added
- **GitHub Community Health Files:**
  - `.github/CONTRIBUTING.md` - Contribution guidelines following LazyVim conventions
  - `.github/ISSUE_TEMPLATE/` - Bug report, feature request, and keybinding conflict templates
  - `.github/PULL_REQUEST_TEMPLATE.md` - Structured PR template
- **Package Metadata:**
  - `package.json` - npm/GitHub package metadata with keywords for discoverability
  - Install scripts for VS Code and Cursor
- **Comprehensive Documentation:**
  - `SETUP.md` - Detailed installation and configuration guide
  - `TIPS_AND_TRICKS.md` - Advanced usage patterns and workflows
  - `TROUBLESHOOTING.md` - Common issues and solutions
  - `REFERENCES.md` - Additional resources and learning materials
  - `EDITOR_COMPARISON.md` - Detailed compatibility analysis for VS Code, Cursor, and Windsurf
- **Enhanced Keybindings Documentation:**
  - Significantly expanded `KEYBINDINGS.md` with comprehensive key mapping documentation
  - Quick reference cheatsheet
  - Organized by LazyVim conventions

### Changed
- **Keybindings aligned with LazyVim conventions:**
  - Primary leader key: `<space>` (space)
  - Organized by prefix: `<leader>f*` (files), `<leader>s*` (search), `<leader>c*` (code), etc.
  - File Explorer Toggle: `<space>e`
  - Workspace Search: `<space>/`
  - Better consistency with LazyVim muscle memory
- **Configuration Structure:**
  - Unified configuration in `config/` directory
  - Single `settings.json` and `keybindings.json` for all compatible editors
  - Multi-editor support for VS Code, Cursor, and Windsurf
- **Documentation Improvements:**
  - Updated `README.md` with improved structure and clarity
  - Better organization of all documentation files
  - Enhanced contribution guidelines

### Fixed
- Corrected changelog entries and version history
- Improved keybinding consistency
- Fixed documentation references

### Removed
- Promotional marketing content
- Redundant documentation files
- Multi-editor scaffolding (consolidated to single config)

## [1.0.0] - 2025-01-22

Initial release with comprehensive Vim keybindings for VS Code.

### Added
- **Custom Status Line Integration:**
  - Mode-specific colors
  - Visual feedback for Vim modes
- **Enhanced Editor Settings:**
  - Bracket pair colorization
  - Improved minimap configuration
  - Better bracket guides
- **Visual Mode Features:**
  - Line sorting: `<leader>ss`
  - Case transformation: `<leader>u`, `<leader>l`
  - Select all occurrences: `<leader>a`
- **Vim Experience Improvements:**
  - Yank highlighting
  - Better fold handling
  - Custom search highlighting
  - EasyMotion and Sneak plugins enabled
- **Navigation Shortcuts:**
  - Split navigation: `ctrl+h/j/k/l`
  - Tab navigation: `alt+[`, `alt+]`
  - Definition jumping: `ctrl+]`, `ctrl+t`
- **Split Management:**
  - Resize shortcuts: `alt+h`, `alt+l`
  - Maximize toggle: `ctrl+w m`
- **Terminal Integration:**
  - Toggle terminal: `ctrl+;`
  - Maximize terminal: `ctrl+shift+;`
- **File Explorer Integration:**
  - Toggle sidebar: `<leader>e`
  - Reveal in explorer: `<leader>f`
- **Basic Operations:**
  - Exit insert mode: `jj`
  - Toggle comment: `<leader>c`
  - Clear search: `ctrl+n`
