# VimCode Setup Guide

Complete installation and configuration guide for VimCode - LazyVim-style keybindings for VS Code.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Quick Installation](#quick-installation)
- [Detailed Installation](#detailed-installation)
  - [Step 1: Install Extensions](#step-1-install-extensions)
  - [Step 2: Locate User Directory](#step-2-locate-user-directory)
  - [Step 3: Backup Configuration](#step-3-backup-existing-configuration)
  - [Step 4: Apply Configuration](#step-4-apply-configuration)
  - [Step 5: Platform-Specific Setup](#step-5-platform-specific-setup)
  - [Step 6: Restart VS Code](#step-6-restart-vs-code)
- [Configuration Files Explained](#configuration-files-explained)
- [Validation](#validation)
- [Optional Features](#optional-features)
- [Platform-Specific Notes](#platform-specific-notes)
- [Next Steps](#next-steps)

## Prerequisites

- **VS Code** (or compatible editor: Cursor, Antigravity)
- **Basic Vim knowledge** (modes, motions, commands)
- **Git** (for Git integration features)

## Quick Installation

For experienced users who want to get started quickly:

```bash
# 1. Install core extension
code --install-extension vscodevim.vim

# 2. Install recommended extensions
code --install-extension eamodio.gitlens
code --install-extension hoovercj.vscode-settings-cycler

# 3. Copy configuration files (macOS/Linux)
cp config/settings.json ~/.config/Code/User/      # Linux
cp config/keybindings.json ~/.config/Code/User/  # Linux

# Or for macOS:
cp config/settings.json ~/Library/Application\ Support/Code/User/
cp config/keybindings.json ~/Library/Application\ Support/Code/User/

# 4. Restart VS Code
```

See [Detailed Installation](#detailed-installation) for step-by-step instructions.

## Detailed Installation

### Step 1: Install Extensions

#### Required Extension

**VSCode Vim** - Provides modal editing and Vim emulation:
```bash
code --install-extension vscodevim.vim
```

#### Highly Recommended Extensions

**GitLens** - Powers all Git integration features (`<leader>g*` bindings):
```bash
code --install-extension eamodio.gitlens
```

**Settings Cycler** - Enables line number toggling (`<leader>ul`):
```bash
code --install-extension hoovercj.vscode-settings-cycler
```

#### Optional Extensions

**Which Key** - Keybinding discovery menu (LazyVim-style):
```bash
code --install-extension VSpaceCode.whichkey
```

**Error Lens** - Inline diagnostics display:
```bash
code --install-extension usernamehw.errorlens
```

**Multi Command** - Enables complex key sequences:
```bash
code --install-extension ryuta46.multi-command
```

### Step 2: Locate User Directory

VS Code stores user configuration in the following locations:

| Platform | Path |
|----------|------|
| **macOS** | `~/Library/Application Support/Code/User/` |
| **Linux** | `~/.config/Code/User/` |
| **Windows** | `%APPDATA%\Code\User\` |

**For Cursor:**
- macOS: `~/Library/Application Support/Cursor/User/`
- Linux: `~/.config/Cursor/User/`
- Windows: `%APPDATA%\Cursor\User\`

**For Antigravity (Windsurf):**
- macOS: `~/Library/Application Support/Windsurf/User/`
- Linux: `~/.config/Windsurf/User/`
- Windows: `%APPDATA%\Windsurf\User\`

### Step 3: Backup Existing Configuration

**Important:** Always backup your existing configuration before applying VimCode.

**macOS/Linux:**
```bash
# For VS Code
cp ~/Library/Application\ Support/Code/User/settings.json ~/Library/Application\ Support/Code/User/settings.json.backup
cp ~/Library/Application\ Support/Code/User/keybindings.json ~/Library/Application\ Support/Code/User/keybindings.json.backup

# Or Linux
cp ~/.config/Code/User/settings.json ~/.config/Code/User/settings.json.backup
cp ~/.config/Code/User/keybindings.json ~/.config/Code/User/keybindings.json.backup
```

**Windows (PowerShell):**
```powershell
Copy-Item $env:APPDATA\Code\User\settings.json $env:APPDATA\Code\User\settings.json.backup
Copy-Item $env:APPDATA\Code\User\keybindings.json $env:APPDATA\Code\User\keybindings.json.backup
```

### Step 4: Apply Configuration

Copy the VimCode configuration files to your user directory.

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

**Alternative: Manual Copy via VS Code**

1. **For settings.json:**
   - Press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "settings json"
   - Select "Preferences: Open User Settings (JSON)"
   - Copy content from `config/settings.json` and paste

2. **For keybindings.json:**
   - Press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
   - Type "keyboard json"
   - Select "Preferences: Open Keyboard Shortcuts (JSON)"
   - Copy content from `config/keybindings.json` and paste

### Step 5: Platform-Specific Setup

#### macOS

**Enable key repeat** (prevents typing lag with Vim):
```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```

For Cursor:
```bash
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false
```

**Note:** You may need to restart your Mac for this to take effect.

#### Windows

No additional setup required. The configuration works out of the box.

#### Linux

No additional setup required. The configuration works out of the box.

#### Non-US Keyboards

If you have a non-US keyboard layout, you may need to adjust bracket navigation keys:

In `keybindings.json`, replace:
- `oem_4` with `[BracketLeft]`
- `oem_6` with `[BracketRight]`
- `oem_2` with `[Slash]`

### Step 6: Restart VS Code

Close and reopen VS Code for all changes to take effect.

## Configuration Files Explained

VimCode uses two configuration files with specific purposes:

### settings.json

**Location:** `config/settings.json`

**Contains:**
- All `<leader>` keybindings (space as leader)
- Vim plugin configuration
- Editor settings (line numbers, scrolling, colors)
- Mode-specific status bar colors
- Extension integration settings

**Key Sections:**
```json
{
  // Vim Core Settings
  "vim.leader": "<space>",
  "vim.useSystemClipboard": true,

  // Leader Keybindings
  "vim.normalModeKeyBindingsNonRecursive": [
    // File operations (<leader>f*)
    // Search operations (<leader>s*)
    // Code actions (<leader>c*)
    // Buffer management (<leader>b*)
    // Git operations (<leader>g*)
    // Window management (<leader>w*)
    // Diagnostics (<leader>x*)
    // UI toggles (<leader>u*)
  ]
}
```

### keybindings.json

**Location:** `config/keybindings.json`

**Contains:**
- Modifier key bindings (`Ctrl`, `Alt`, `Shift`)
- Window navigation (`Ctrl+h/j/k/l`)
- Buffer navigation (`Shift+H/L`, `[b`, `]b`)
- Diagnostic navigation (`[d`, `]d`, `[e`, `]e`)
- Context-specific bindings (explorer, terminal, suggestions)

**Key Features:**
- Smart `when` clauses prevent conflicts
- Context-aware navigation (suggestions, quick open, explorer)
- Proper handling of special keys

## Validation

After installation, run through this checklist to verify your setup:

### Core Functionality

- [ ] Press `Space` in Normal mode - cursor should NOT move
- [ ] Press `i` to enter Insert mode - status bar turns green
- [ ] Press `Esc` or `jk` to return to Normal mode - status bar turns blue
- [ ] Press `v` to enter Visual mode - status bar turns purple

### File Operations (`<leader>f*`)

- [ ] `<leader>ff` - Opens file picker (Quick Open)
- [ ] `<leader>fr` - Shows recent files
- [ ] `<leader>fn` - Creates new file
- [ ] `<leader>fb` - Lists open buffers
- [ ] `<leader>e` - Toggles sidebar

### Search Operations (`<leader>s*`)

- [ ] `<leader>/` - Opens workspace search
- [ ] `<leader>sg` - Opens search/grep
- [ ] `<leader>ss` - Shows document symbols
- [ ] `<leader>sk` - Opens keyboard shortcuts

### Code Actions (`<leader>c*`)

- [ ] `<leader>ca` - Shows code actions (on a code symbol)
- [ ] `<leader>cf` - Formats document
- [ ] `<leader>cr` - Renames symbol (on a code symbol)

### LSP Navigation

- [ ] `gd` - Jumps to definition (on a code symbol)
- [ ] `gr` - Shows references (on a code symbol)
- [ ] `K` - Shows hover documentation (on a code symbol)
- [ ] `Ctrl+o` - Navigates back after `gd`

### Buffer Management

- [ ] `Shift+H` - Switches to previous buffer/tab
- [ ] `Shift+L` - Switches to next buffer/tab
- [ ] `<leader>bd` - Closes current buffer
- [ ] `[b` / `]b` - Navigate buffers (alternative)

### Window Navigation

- [ ] `Ctrl+h` - Focuses left split
- [ ] `Ctrl+j` - Focuses split below
- [ ] `Ctrl+k` - Focuses split above
- [ ] `Ctrl+l` - Focuses right split
- [ ] `<leader>-` - Splits window horizontally
- [ ] `<leader>|` - Splits window vertically

### Diagnostics

- [ ] `[d` - Jumps to previous diagnostic
- [ ] `]d` - Jumps to next diagnostic
- [ ] `<leader>xx` - Opens problems panel

### Git Operations (requires GitLens)

- [ ] `<leader>gg` - Opens Git status (Source Control)
- [ ] `<leader>gb` - Toggles Git blame
- [ ] `<leader>gd` - Shows Git diff
- [ ] `[h` / `]h` - Navigate Git hunks (if changes exist)

### Other Features

- [ ] `jk` or `jj` - Exits Insert mode (same as `Esc`)
- [ ] `Alt+j` / `Alt+k` - Moves lines up/down
- [ ] `<` / `>` in Visual mode - Indents and reselects
- [ ] `Ctrl+/` - Toggles terminal
- [ ] No typing lag in Insert mode

If all checks pass, your setup is complete!

## Optional Features

### Settings Cycler (Line Number Toggle)

To enable line number toggling with `<leader>ul`:

1. Install Settings Cycler extension (see [Step 1](#step-1-install-extensions))

2. Uncomment the `settings.cycle` section at the bottom of `settings.json`:
   ```json
   "settings.cycle": [
     {
       "id": "lineNumbers",
       "values": [
         { "editor.lineNumbers": "on" },
         { "editor.lineNumbers": "relative" },
         { "editor.lineNumbers": "off" }
       ]
     }
   ]
   ```

3. Restart VS Code

### Which Key (Keybinding Discovery)

To enable LazyVim-style keybinding menus:

1. Install Which Key extension (see [Step 1](#step-1-install-extensions))

2. Configure in `settings.json` (optional customization):
   ```json
   "whichkey.bindings": [
     {
       "key": "f",
       "name": "File operations",
       "type": "bindings",
       "bindings": [
         {"key": "f", "name": "Find files", "type": "command", "command": "workbench.action.quickOpen"}
       ]
     }
   ]
   ```

## Platform-Specific Notes

### macOS

**Key repeat is essential:**
- Without key repeat enabled, holding `j` or `k` in Normal mode may show accent menus
- Run: `defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false`
- Restart your Mac after running this command

**Terminal considerations:**
- `Ctrl+h` may conflict with terminal delete
- Use `<leader>ft` to toggle terminal instead of `Ctrl+/` if conflicts arise

### Windows

**PowerShell vs Command Prompt:**
- Use PowerShell for copy commands (supports `Copy-Item`)
- Command Prompt requires different syntax: `copy` instead of `Copy-Item`

**Path separators:**
- Use backslashes in Windows paths: `config\settings.json`
- PowerShell accepts forward slashes: `config/settings.json`

### Linux

**X11 vs Wayland:**
- Both display servers work with VimCode
- No specific configuration needed

**Clipboard integration:**
- Requires `xclip` or `xsel` on X11
- Install with: `sudo apt install xclip` (Debian/Ubuntu)

## Next Steps

After completing the setup:

1. **Learn the keybindings:** Review [KEYBINDINGS.md](KEYBINDINGS.md) for complete reference
2. **Explore workflows:** Read [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) for power user features
3. **Customize:** Modify `config/settings.json` and `config/keybindings.json` to fit your workflow
4. **Get help:** See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) if you encounter issues

## Configuration Architecture

### Why Two Files?

VimCode splits configuration into two files for technical reasons:

**settings.json** - Handled by Vim extension:
- All `<leader>` bindings must be in Vim's configuration
- Vim processes these internally before VS Code
- Allows for Vim-specific features (modes, motions)

**keybindings.json** - Handled by VS Code:
- Modifier keys (`Ctrl`, `Alt`, `Shift`) work better in VS Code
- Better integration with VS Code's when clause system
- More granular context control (suggestions, quick open, etc.)

### Keybinding Prefix Organization

VimCode follows LazyVim's prefix convention for discoverability:

| Prefix | Category | Example Bindings |
|--------|----------|------------------|
| `<leader>f*` | File operations | `ff` find, `fr` recent, `fn` new |
| `<leader>s*` | Search | `sg` grep, `ss` symbols, `sk` keys |
| `<leader>c*` | Code actions | `ca` action, `cf` format, `cr` rename |
| `<leader>b*` | Buffers | `bd` delete, `bp` pin, `bb` switch |
| `<leader>g*` | Git | `gg` status, `gb` blame, `gd` diff |
| `<leader>w*` | Windows | `wd` close, `ww` switch, `wm` maximize |
| `<leader>x*` | Diagnostics | `xx` problems, (also `[d`, `]d`) |
| `<leader>u*` | UI toggles | `uw` wrap, `uz` zen, `ul` line numbers |

This organization makes keybindings easy to remember and discover.

### Performance Optimization

VimCode includes critical performance settings:

**Dedicated Thread Execution:**
```json
"extensions.experimental.affinity": {
  "vscodevim.vim": 1
}
```

This runs the Vim extension in a separate thread, preventing typing lag.

**Disable Unused Extensions:**
- Each active extension consumes resources
- Use VS Code Profiles to maintain minimal extension sets
- Disable extensions you don't need for Vim editing

**Status Bar Colors:**
```json
"vim.statusBarColors.normal": "#519aba",  // Blue
"vim.statusBarColors.insert": "#98c379",  // Green
"vim.statusBarColors.visual": "#c678dd",  // Purple
"vim.statusBarColors.replace": "#e06c75"  // Red
```

These provide instant visual feedback for your current mode.

## Understanding the Configuration

### Editor Settings

VimCode includes carefully chosen editor settings:

**Line Numbers:**
```json
"editor.lineNumbers": "relative",
"vim.smartRelativeLine": true
```
- Relative numbers in Normal/Visual modes (for motions like `10j`)
- Absolute numbers in Insert mode (for debugging)

**Scrolling:**
```json
"editor.smoothScrolling": true,
"editor.cursorSurroundingLines": 8
```
- Smooth scrolling for better visual tracking
- 8 lines of context above/below cursor (like `scrolloff` in Vim)

**Visual Feedback:**
```json
"editor.bracketPairColorization.enabled": true,
"vim.highlightedyank.enable": true,
"vim.highlightedyank.duration": 200
```
- Colored bracket pairs for code readability
- Brief highlight when yanking text (visual confirmation)

### Vim Plugin Integration

VimCode enables useful Vim plugins:

**EasyMotion:**
```json
"vim.easymotion": true
```
- `<leader><leader>w` - Jump to word
- `<leader><leader>b` - Jump backward
- `<leader><leader>s{char}` - Jump to character

**Sneak:**
```json
"vim.sneak": true
```
- `s{char}{char}` - Jump to two-character sequence forward
- `S{char}{char}` - Jump backward

**Surround:**
```json
"vim.surround": true
```
- `ysiw"` - Surround inner word with quotes
- `cs"'` - Change surrounding quotes to apostrophes
- `ds"` - Delete surrounding quotes

### Handle Keys Configuration

Critical setting for key handling:

```json
"vim.handleKeys": {
  "<C-d>": true,  // Vim handles (page down)
  "<C-u>": true,  // Vim handles (page up)
  "<C-f>": false, // VS Code handles (find)
  "<C-s>": false, // VS Code handles (save)
  "<C-b>": false  // VS Code handles (toggle sidebar)
}
```

This determines whether Vim or VS Code handles specific key combinations.

---

**Need Help?** Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for common issues and solutions.

**Ready to Master VimCode?** Read [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) for advanced workflows.
