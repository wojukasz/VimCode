# VimCode - LazyVim-Style Configuration for VS Code

> Bring the power and efficiency of LazyVim to VS Code with 50+ carefully crafted keybindings.

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](#)
![GitHub stars](https://img.shields.io/github/stars/wojukasz/VimCode?style=social)
![GitHub forks](https://img.shields.io/github/forks/wojukasz/VimCode?style=social)
![GitHub last commit](https://img.shields.io/github/last-commit/wojukasz/VimCode)
![GitHub issues](https://img.shields.io/github/issues/wojukasz/VimCode)

A comprehensive **Vim configuration for VS Code** that mirrors the LazyVim experience with `<space>` as the leader key. Perfect for developers who want **Neovim muscle memory in VS Code** with full LSP integration, Git operations, and modern editor features. Compatible with **VSCodeVim, Cursor, and Windsurf** editors.

## Features

- **50+ LazyVim-aligned keybindings** - Organized by prefix (`<leader>f*`, `<leader>s*`, `<leader>c*`, etc.)
- **Full Vim emulation** - Modal editing with proper mode indicators
- **LSP integration** - Code navigation, formatting, refactoring
- **Git operations** - Integrated with GitLens for blame, history, diff
- **Window management** - `Ctrl+h/j/k/l` split navigation
- **Performance optimized** - Dedicated thread prevents typing lag
- **Multi-editor support** - Works with VS Code, Cursor, and Antigravity (Windsurf)

## Quick Start

### 1. Install Required Extension

```bash
code --install-extension vscodevim.vim
```

### 2. Install Recommended Extensions

```bash
code --install-extension eamodio.gitlens
code --install-extension hoovercj.vscode-settings-cycler
```

### 3. Apply Configuration

Copy configuration files to your VS Code user directory:

**macOS:**
```bash
cp config/settings.json ~/Library/Application\ Support/Code/User/
cp config/keybindings.json ~/Library/Application\ Support/Code/User/
```

**Linux:**
```bash
cp config/settings.json ~/.config/Code/User/
cp config/keybindings.json ~/.config/Code/User/
```

**Windows (PowerShell):**
```powershell
Copy-Item config\settings.json $env:APPDATA\Code\User\
Copy-Item config\keybindings.json $env:APPDATA\Code\User\
```

### 4. Restart VS Code

That's it! See [SETUP.md](SETUP.md) for detailed installation instructions and troubleshooting.

## Essential Keybindings

| Keybinding | Action | Category |
|------------|--------|----------|
| `<leader>ff` | Find files | File |
| `<leader>/` | Search in workspace | Search |
| `<leader>e` | Toggle sidebar | File |
| `<leader>ca` | Code action | LSP |
| `gd` | Go to definition | LSP |
| `Shift+H/L` | Previous/next buffer | Buffer |
| `Ctrl+h/j/k/l` | Navigate splits | Window |
| `<leader>gg` | Git status | Git |
| `[d` / `]d` | Previous/next diagnostic | Diagnostic |

**Leader key:** `<space>`

See [KEYBINDINGS.md](KEYBINDINGS.md) for complete shortcuts reference.

## Documentation

- **[SETUP.md](SETUP.md)** - Complete installation guide and configuration details
- **[KEYBINDINGS.md](KEYBINDINGS.md)** - Comprehensive shortcuts guide and cheat sheet
- **[TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md)** - Power user features, workflows, and best practices
- **[TROUBLESHOOTING.md](TROUBLESHOOTING.md)** - Common issues and solutions
- **[EDITOR_COMPARISON.md](EDITOR_COMPARISON.md)** - VS Code vs Cursor vs Antigravity compatibility
- **[REFERENCES.md](REFERENCES.md)** - Learning resources and external links
- **[CHANGELOG.md](CHANGELOG.md)** - Version history and breaking changes

## Configuration Structure

```
VimCode/
├── config/
│   ├── settings.json      # VS Code settings + all <leader> bindings
│   └── keybindings.json   # Modifier keys (Ctrl/Alt/Shift) bindings
├── SETUP.md               # Installation and configuration guide
├── KEYBINDINGS.md         # Shortcuts reference and cheat sheet
├── TIPS_AND_TRICKS.md     # Power user guide
└── TROUBLESHOOTING.md     # Common issues and solutions
```

## Keybinding Organization

VimCode uses the LazyVim convention of organizing keybindings by prefix:

- **`<leader>f*`** - File operations (find, recent, new, buffer list)
- **`<leader>s*`** - Search operations (grep, workspace symbols, replace)
- **`<leader>c*`** - Code actions (format, rename, quick fix)
- **`<leader>b*`** - Buffer management (close, switch, pin/unpin)
- **`<leader>g*`** - Git operations (blame, status, history, diff)
- **`<leader>w*`** - Window management (split, close, maximize)
- **`<leader>x*`** - Diagnostics (problems panel, navigation)
- **`<leader>u*`** - UI toggles (word wrap, zen mode, line numbers)

## Supported Editors

- **VS Code** - Full support (primary target)
- **Cursor** - Compatible (AI-powered editor)
- **Antigravity (Windsurf)** - Compatible (VS Code fork)

See [EDITOR_COMPARISON.md](EDITOR_COMPARISON.md) for details on multi-editor support.

## Philosophy

VimCode follows these principles:

1. **Consistency** - Same keybindings between Neovim and VS Code
2. **Discoverability** - Organized by prefix for easy learning
3. **Efficiency** - Common operations accessible with minimal keystrokes
4. **Integration** - Work with VS Code's native features, not against them
5. **Performance** - Optimized configuration for responsive editing

## Validation Checklist

After installation, test these essential bindings:

- [ ] `Space` in Normal mode doesn't move cursor
- [ ] `<leader>ff` (Space, f, f) opens file picker
- [ ] `<leader>/` (Space, /) opens workspace search
- [ ] `gd` jumps to definition
- [ ] `Shift+H` / `Shift+L` switches buffers
- [ ] `Ctrl+h/j/k/l` navigates between splits

See [SETUP.md](SETUP.md#validation) for complete validation checklist.

## Why VimCode?

If you love Vim but need the power of VS Code's ecosystem, VimCode gives you the best of both worlds:

- **Familiar muscle memory** from LazyVim
- **Modern LSP features** with VS Code's IntelliSense
- **Rich extension ecosystem** (GitLens, debuggers, formatters)
- **Visual feedback** with status bar mode indicators
- **Cross-platform** works on macOS, Linux, and Windows

## Contributing

Contributions are welcome! Found a bug or have a suggestion? Feel free to open an issue or submit a pull request.

For major changes, please open an issue first to discuss what you would like to change. See [.github/CONTRIBUTING.md](.github/CONTRIBUTING.md) for detailed contribution guidelines.

## Note

Some keybindings are experimental and may require adjustments based on your workflow. Feel free to customize the configuration files to suit your needs.

## License

MIT

---

**Get Started:** [SETUP.md](SETUP.md) | **Quick Reference:** [KEYBINDINGS.md](KEYBINDINGS.md) | **Learn More:** [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md)
