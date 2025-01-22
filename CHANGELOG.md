# Changelog

All notable changes to this configuration will be documented in this file.

## [1.1.0] - 2025-01-22

### Added
- Custom status line integration with mode-specific colors
- Enhanced editor settings
  - Bracket pair colorization
  - Improved minimap configuration
  - Better bracket guides
- New visual mode features
  - Line sorting
  - Case transformation
  - Multi-line editing
- Improved Vim experience
  - Yank highlighting
  - Better fold handling
  - Custom search highlighting

## [1.0.0] - 2025-01-22

### Added
- Enhanced Git integration
  - Pull command: `<leader>g p`
  - Push command: `<leader>g P`
  - File history: `<leader>g h`
- New navigation shortcuts
  - Method boundaries: `[m`, `]m`
  - Error navigation: `[d`, `]d`
  - Definition jumping: `ctrl+]`, `ctrl+t`
- Split management
  - Resize shortcuts: `alt+h`, `alt+l`
  - Maximize toggle: `ctrl+w m`
  - Equal sizing: `<C-w>=`
- Code folding commands
  - Fold: `<leader>z`
  - Unfold: `<leader>Z`
- Tab navigation
  - Previous/Next: `alt+[`, `alt+]`
- Workspace management
  - Close workspace: `ctrl+shift+w`
  - Copy file path: `ctrl+k p`
- Enhanced panel navigation
  - Consistent ctrl+j/k in all panels
  - Improved terminal focus controls

### Changed
- Standardized sidebar toggling to use `<leader>e`
- Improved comments and documentation
- Reorganized keybindings into logical groups

### Fixed
- Removed redundant keybindings
- Standardized leader key usage
- Improved context awareness for shortcuts

## [0.1.0] - Initial Release

### Added
- Basic Vim keybindings
- File explorer integration
- Terminal shortcuts
- Basic Git commands
- Split navigation
