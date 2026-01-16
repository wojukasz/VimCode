# VimCode - Modern Vim Experience for Code Editors

Enhanced configuration with Vim keybindings for efficient coding workflows. This setup combines the power of Vim motions with modern editor features.

*IMPORTANT:* Some of the shortcuts are experimental and I am trying things on the go so they might not work at all or as intended! Please leave a comment and feel free to adjust and fix!

## Supported Editors

| Editor | Status | Config Path |
|--------|--------|-------------|
| VS Code | ✅ Full Support | `config/vscode/` |
| Cursor | 🚧 Planned | `config/cursor/` |
| Windsurf (Antigravity) | 🚧 Planned | `config/antigravity/` |

## Repository Structure

```
config/
├── vscode/             # VS Code configuration (baseline)
│   ├── settings.json   # VS Code settings + Vim plugin configuration
│   └── keybindings.json# Custom keyboard shortcuts
├── cursor/             # Cursor-specific config (planned)
└── antigravity/        # Windsurf/Antigravity config (planned)
KEYBINDINGS.md          # Quick reference cheatsheet (VS Code)
```

## Features

### 💻 Editor Navigation
- Vim-style split navigation (`ctrl+h/j/k/l`)
- Quick file switching with `alt+[` and `alt+]`
- Efficient split management with `alt+h/l` for resizing
- Enhanced bracket navigation with colorization
- Improved minimap visibility

### 📁 File Explorer
- Toggle sidebar: `<leader>e`
- File navigation with Vim keys
- Quick file operations (rename, create, delete)

### 🔍 Search and Replace
- Enhanced workspace search with `<leader>s w`
- Find in files: `ctrl+shift+f`
- Navigate results: `F4/Shift+F4`
- Custom search highlighting

### ⚡ Quick Actions
- Format document: `ctrl+space f`
- Go to definition: `ctrl+]`
- Navigate back: `ctrl+t`

### 🔧 Git Integration
- Toggle blame: `<leader>g b`
- Quick stage: `<leader>g s`
- Pull: `<leader>g p`
- Push: `<leader>g P`
- View history: `<leader>g h`

### 🖥️ Terminal Integration
- Toggle terminal: `ctrl+;`
- Maximize terminal: `ctrl+shift+;`
- Create new terminal: `<leader>t n`

### ✨ Visual Mode Enhancements
- Sort lines: `<leader>s s`
- Transform to uppercase: `<leader>u`
- Transform to lowercase: `<leader>l`
- Select all occurrences: `<leader>a`

### 🎨 Status Line Integration
- Mode-specific colors
- Visual mode indicators
- Clear status feedback
- Custom color schemes for each mode

## Installation

### VS Code

1. Open VS Code settings.json:
   - Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "settings json"
   - Click "Preferences: Open User Settings (JSON)"
   - Clear the file and paste the content from `config/vscode/settings.json`

2. Open VS Code keybindings.json:
   - Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "keyboard json"
   - Click "Preferences: Open Keyboard Shortcuts (JSON)"
   - Clear the file and paste the content from `config/vscode/keybindings.json`

3. Install required extensions from VS Code Marketplace
4. Restart VS Code

### Cursor / Windsurf

Editor-specific configurations are planned. In the meantime, the VS Code configuration should work as a baseline for these VS Code-based editors.

Alternative ways to open configuration files:
- Settings:
  - Mac: `Cmd+,` then click the "Open Settings (JSON)" icon in the top right
  - Windows/Linux: `Ctrl+,` then click the "Open Settings (JSON)" icon in the top right
- Keybindings:
  - Mac: `Cmd+K Cmd+S` then click the "Open Keyboard Shortcuts (JSON)" icon
  - Windows/Linux: `Ctrl+K Ctrl+S` then click the "Open Keyboard Shortcuts (JSON)" icon

## Required Extensions

- [Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Multi Command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)

## Key Concepts

- Leader key is set to `<space>`
- Consistent use of Vim navigation patterns
- Integration with VS Code's native features
- Enhanced terminal and git workflows
- Visual feedback through status line colors

## Common Workflows

### File Navigation
1. Open sidebar: `<leader>e`
2. Navigate files: `j/k`
3. Expand/collapse: `l/h`
4. Open in split: `ctrl+shift+1/2`

### Git Operations
1. Stage changes: `<leader>g s`
2. View changes: `<leader>g d`
3. Push changes: `<leader>g P`

### Code Navigation
1. Go to definition: `ctrl+]`
2. Return from definition: `ctrl+t`
3. Find in workspace: `<leader>s w`

### Text Manipulation
1. Sort lines: Select lines + `<leader>s s`
2. Transform case: Select text + `<leader>u/l`
3. Multi-line editing: Select lines + `<leader>a`

## Editor Settings

Key settings include:
- Bracket pair colorization
- Enhanced minimap configuration
- Improved fold handling
- Yank highlighting
- Custom search highlighting
- Mode-specific status line colors

## Customization

Edit the following files to customize the configuration:
- `config/vscode/settings.json`: VS Code and Vim settings
- `config/vscode/keybindings.json`: Custom keyboard shortcuts

### Status Line Colors
You can customize mode colors in `config/vscode/settings.json`:
```json
"vim.statusBarColors.normal": "#519aba",
"vim.statusBarColors.insert": "#98c379",
"vim.statusBarColors.visual": "#c678dd"
```

## Contributing

Feel free to submit issues and enhancement requests!
