# Changelog

All notable changes to this configuration will be documented in this file.

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
