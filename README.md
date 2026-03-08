# VimCode — LazyVim-Style Vim Configuration for VS Code

[![Version](https://img.shields.io/badge/version-2.9.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](#)
![GitHub stars](https://img.shields.io/github/stars/wojukasz/VimCode?style=social)
![GitHub forks](https://img.shields.io/github/forks/wojukasz/VimCode?style=social)
![GitHub last commit](https://img.shields.io/github/last-commit/wojukasz/VimCode)
![GitHub issues](https://img.shields.io/github/issues/wojukasz/VimCode)

LazyVim-style keybindings for VS Code and compatible forks. Mirrors the LazyVim experience with `<space>` as leader key, full LSP integration, Git operations via GitLens, and a which-key popup menu for keybinding discovery.

Tested on Antigravity (Linux/WSL). Expected to work on any editor that supports the VSCodeVim extension — VS Code, Cursor, Windsurf, and other forks share the same config format.

## Features

- **50+ LazyVim-aligned keybindings** organized by prefix (`<leader>f*`, `<leader>s*`, `<leader>c*`, etc.)
- **which-key popup menu** — press `<space>` to see all bindings (requires `VSpaceCode.whichkey`)
- **Full Vim emulation** — modal editing with proper mode indicators
- **LSP integration** — code navigation, formatting, refactoring
- **Git operations** — integrated with GitLens for blame, history, diff
- **Window management** — `Ctrl+h/j/k/l` split navigation
- **Performance optimized** — dedicated thread prevents typing lag

## Quick Start

### 1. Install Required Extension

```bash
code --install-extension vscodevim.vim
```

### 2. Install Recommended Extensions

```bash
code --install-extension VSpaceCode.whichkey
code --install-extension eamodio.gitlens
code --install-extension hoovercj.vscode-settings-cycler
```

### 3. Apply Configuration

Copy configuration files to your editor's user directory (VS Code shown — adjust path for your editor):

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

See [SETUP.md](SETUP.md) for detailed installation instructions and troubleshooting.

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

| File | Contents |
|------|----------|
| [SETUP.md](SETUP.md) | Installation guide, validation checklist, platform notes |
| [KEYBINDINGS.md](KEYBINDINGS.md) | Complete shortcuts reference and cheat sheet |
| [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) | Workflows, plugin mastery, customization |
| [TROUBLESHOOTING.md](TROUBLESHOOTING.md) | Common issues and solutions |
| [KNOWN_ISSUES.md](KNOWN_ISSUES.md) | VSCodeVim limitations and workarounds |
| [REFERENCES.md](REFERENCES.md) | Learning resources and external links |
| [CHANGELOG.md](CHANGELOG.md) | Version history |

## Supported Editors

VimCode is built and tested on Antigravity (Linux/WSL). Any editor that uses VS Code's extension host and supports VSCodeVim should work — the `settings.json` and `keybindings.json` format is identical across VS Code, Cursor, Windsurf, and other forks. Only the config directory path and CLI command differ.

> Each editor stores config in its own directory (e.g. `~/.config/Cursor/User/`, `~/.config/Antigravity/User/`). See [SETUP.md](SETUP.md) for per-editor paths.

## Contributing

Contributions are welcome. For bugs or suggestions, open an issue or submit a pull request. For major changes, open an issue first to discuss. See [.github/CONTRIBUTING.md](.github/CONTRIBUTING.md) for contribution guidelines.

## License

MIT
