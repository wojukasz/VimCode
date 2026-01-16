# VimCode - Modern Vim Experience for Code Editors

Enhanced configuration with Vim keybindings for efficient coding workflows. This setup combines the power of Vim motions with modern editor features.

*IMPORTANT:* Some of the shortcuts are experimental and I am trying things on the go so they might not work at all or as intended! Please leave a comment and feel free to adjust and fix!

## Supported Editors

This configuration is primarily targeted at **VS Code** but should be compatible with other VS Code-based editors like **Cursor** and **Antigravity (Windsurf)**. The `EDITOR_COMPARISON.md` file contains a more detailed analysis of the compatibility and potential issues with each editor.

## Repository Structure

```
config/
├── settings.json   # VS Code settings + Vim plugin configuration
└── keybindings.json# Custom keyboard shortcuts
KEYBINDINGS.md      # Quick reference cheatsheet
```

## Installation

1. Open VS Code settings.json:
   - Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "settings json"
   - Click "Preferences: Open User Settings (JSON)"
   - Clear the file and paste the content from `config/settings.json`

2. Open VS Code keybindings.json:
   - Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "keyboard json"
   - Click "Preferences: Open Keyboard Shortcuts (JSON)"
   - Clear the file and paste the content from `config/keybindings.json`

3. Install required extensions from VS Code Marketplace
4. Restart VS Code

Alternative ways to open configuration files:
- Settings:
  - Mac: `Cmd+,` then click the "Open Settings (JSON)" icon in the top right
  - Windows/Linux: `Ctrl+,` then click the "Open Settings (JSON)" icon in the top right
- Keybindings:
  - Mac: `Cmd+K Cmd+S` then click the "Open Keyboard Shortcuts (JSON)" icon
  - Windows/Linux: `Ctrl+K Ctrl+S` then click the "Open Keyboard Shortcuts (JSON)" icon


## Required Extensions

- [Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
  - **Core of the setup.** Provides the Vim emulation layer, including modes, motions, and the `<leader>` key functionality.
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
  - **Powers all Git integration.** Enables features like blame annotations, file history, and staging, which are mapped to the `<leader>g` keybindings.
- [Multi Command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)
  - **Enables complex key sequences.** Used to chain multiple VS Code commands together into a single keybinding, such as maximizing the terminal and focusing it with one keypress.

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
