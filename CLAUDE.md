# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

VimCode is a multi-editor configuration repository providing Vim keybindings and settings for efficient coding workflows. This is NOT a typical code project - it contains JSON configuration files that users manually copy into their editor settings.

## Supported Editors

| Editor | Status | Directory |
|--------|--------|-----------|
| VS Code | ✅ Full Support (baseline) | `config/vscode/` |
| Cursor | 🚧 Planned | `config/cursor/` |
| Windsurf (Antigravity) | 🚧 Planned | `config/antigravity/` |

## Repository Structure

```
config/
├── vscode/             # VS Code configuration (baseline)
│   ├── settings.json   # VS Code settings + Vim plugin configuration
│   └── keybindings.json# Custom keyboard shortcuts
├── cursor/             # Cursor-specific config (planned)
│   └── .gitkeep
└── antigravity/        # Windsurf/Antigravity config (planned)
    └── .gitkeep
KEYBINDINGS.md          # Quick reference cheatsheet (VS Code keybindings)
```

## Configuration Architecture

### VS Code Configuration (`config/vscode/`)

#### settings.json
Organized into clearly marked sections:
1. **PERFORMANCE** - Extension affinity for responsiveness
2. **EDITOR SETTINGS** - Visual preferences (relative line numbers, minimap, bracket colorization)
3. **VIM CORE CONFIGURATION** - Plugin settings (easymotion, sneak, clipboard, search)
4. **STATUS LINE** - Mode-specific colors
5. **KEY HANDLING** - Keys delegated to VS Code vs Vim
6. **INSERT/NORMAL/VISUAL MODE KEYBINDINGS** - Mode-specific mappings
7. **MULTI-COMMAND SEQUENCES** - Complex multi-step operations

Normal mode keybindings are further organized by function:
- Navigation, File Operations, Sidebar, Window Management, Git Operations, Search, Code Actions, Terminal

#### keybindings.json
VS Code-level keyboard shortcuts with context-aware `when` clauses. Organized into sections:
- VIM NAVIGATION SHORTCUTS
- CODE NAVIGATION AND EDITING
- SUGGESTIONS AND AUTOCOMPLETION SHORTCUTS
- SEARCH AND NAVIGATION
- FILE EXPLORER SHORTCUTS
- SPLIT MANAGEMENT
- TAB MANAGEMENT
- TERMINAL SHORTCUTS

## Key Conventions

- **Leader key**: `<space>` (set via `vim.leader`)
- **Vim-style navigation**: `ctrl+h/j/k/l` for split/panel navigation
- **Tab navigation**: `H`/`L` for previous/next tab
- **File operations**: `<leader>fs` (save), `<leader>q` (close)
- **Git operations**: `<leader>g` prefix (gb, gs, gp, gP, gh, gd)
- **Mode awareness**: Many keybindings use `vim.mode != 'Insert'` or similar conditions
- **Exit insert mode**: `jj` (double-tap j)

## Required VS Code Extensions

- Vim (`vscodevim.vim`)
- GitLens (`eamodio.gitlens`)
- Multi Command (`ryuta46.multi-command`)

## Making Changes

When modifying keybindings:
1. Follow the existing section organization with clear headers
2. Use appropriate `when` clauses for context-aware behavior
3. Group related bindings under subsection comments
4. For multi-step operations, use `multiCommand.commands` in settings.json
5. Update KEYBINDINGS.md to reflect any VS Code keybinding changes
6. When adding editor-specific configs, create a similar structure in the appropriate `config/<editor>/` directory

## Adding New Editor Support

When adding support for a new editor:
1. Create configuration files in `config/<editor>/`
2. Use VS Code config as the baseline, adapting as needed
3. Document editor-specific differences in `config/<editor>/README.md`
4. Update the root README.md "Supported Editors" table
