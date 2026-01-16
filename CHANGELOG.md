# Changelog

All notable changes to this configuration will be documented in this file.

## [4.0.0] - 2026-01-16

### BREAKING CHANGE
- The multi-editor support has been removed in favor of a single, unified configuration. The `config/vscode`, `config/cursor`, and `config/antigravity` directories have been removed, and the configuration files now reside in the root `config` directory.

### Added
- `EDITOR_COMPARISON.md` has been added to provide a detailed analysis of the compatibility and potential issues with each editor.

### Changed
- Keybindings have been updated to better align with LazyVim conventions, using `<space>` as the primary leader key.
  - **File Explorer Toggle:** `<space>e` (was `ctrl+shift+e`)
  - **Workspace Search:** `<space>/` (was `ctrl+shift+f`)
  - **Format Document:** `<space>f` (was `ctrl+space f`)
  - **Navigate Back:** `ctrl+o` (was `ctrl+t`)
- The `README.md` file has been updated to reflect the simplified file structure.

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

## [2.0.0] - 2025-01-16

### Added
- Quick reference cheatsheet (`KEYBINDINGS.md`)
- Performance optimization via `extensions.experimental.affinity`
- Tab navigation with `H`/`L` keys
- Git operations: blame, stage, pull, push, history, diff (`<leader>g` prefix)
- Workspace search: `<leader>sw`
- Rename symbol: `<leader>rn`
- New terminal: `<leader>tn`

### Changed
- Reorganized `settings.json` with clear section headers
- File operations moved to cleaner namespace:
  - Save: `<leader>fs` (was `<leader>ww`)
  - Close: `<leader>q` (was `<leader>wc`)
- Updated `CLAUDE.md` with new architecture documentation

### Removed
- Experimental `#TODO` comments cleaned up
- Redundant/conflicting keybindings removed

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
