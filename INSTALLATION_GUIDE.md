# VSCode Vim LazyVim Configuration Guide

Complete VSCode configuration for LazyVim-style keybindings using the VSCode Vim extension.

## 📋 Overview

This configuration provides 50+ LazyVim-style keybindings in VSCode, giving you consistent muscle memory between VSCode and Neovim with LazyVim. All bindings are validated against current VSCode commands and include proper conflict resolution.

## 🎯 Features

- ✅ **Complete LazyVim alignment** - Space-leader patterns (`<leader>f*`, `<leader>s*`, `<leader>c*`, etc.)
- ✅ **Window navigation** - `Ctrl+h/j/k/l` to move between splits
- ✅ **LSP integration** - `gd`, `gr`, `gI`, `K` for code navigation
- ✅ **Diagnostic navigation** - `[d`, `]d`, `[e`, `]e` for errors
- ✅ **Git integration** - GitLens support for blame, history, diff
- ✅ **Proper conflict resolution** - Smart when clauses prevent keybinding conflicts
- ✅ **Performance optimised** - Dedicated thread prevents typing lag
- ✅ **Self-documenting** - Extensive comments explain every binding

## 📦 Required Extensions

**Core requirement:**
- [VSCode Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim) - Modal editing

**Highly recommended:**
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - Git operations (`<leader>gb`, `<leader>gl`, etc.)
- [Settings Cycler](https://marketplace.visualstudio.com/items?itemName=hoovercj.vscode-settings-cycler) - Line number toggling (`<leader>ul`)

**Optional but useful:**
- [Which Key](https://marketplace.visualstudio.com/items?itemName=VSpaceCode.whichkey) - Keybinding discovery menu
- [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - Inline diagnostics

## 🚀 Quick Installation

1. Install VSCode Vim extension
2. Copy `settings.json` and `keybindings.json` to VSCode user directory
3. Restart VSCode
4. Test with validation checklist below

For detailed instructions, see full installation guide below.

## ✅ Quick Validation

Test these essential bindings to verify setup:

- [ ] `Space` in Normal mode doesn't move cursor
- [ ] `<leader>ff` (Space, f, f) opens file picker
- [ ] `<leader>/` (Space, /) opens workspace search
- [ ] `gd` jumps to definition
- [ ] `Shift+H` / `Shift+L` switches buffers
- [ ] `Ctrl+h/j/k/l` navigates between splits

## 📚 Full Installation Guide

See detailed installation instructions, troubleshooting, and complete keybinding reference at the end of this document.

---

## 🔑 Keybinding Quick Reference

### Essential Patterns

| Pattern | Purpose | Examples |
|---------|---------|----------|
| `<leader>f*` | File operations | `<leader>ff` find, `<leader>fr` recent |
| `<leader>s*` | Search operations | `<leader>sg` grep, `<leader>ss` symbols |
| `<leader>c*` | Code actions | `<leader>ca` action, `<leader>cf` format |
| `<leader>b*` | Buffer management | `<leader>bd` close, `<leader>bb` switch |
| `<leader>g*` | Git operations | `<leader>gg` status, `<leader>gb` blame |
| `<leader>w*` | Window management | `<leader>wd` close, `<leader>-` split |
| `<leader>x*` | Diagnostics | `<leader>xx` problems |
| `<leader>u*` | UI toggles | `<leader>uw` wrap, `<leader>uz` zen |

### Most Used Bindings

| Binding | Action | Category |
|---------|--------|----------|
| `<leader>ff` | Find files | File |
| `<leader>/` | Search in files | Search |
| `<leader>e` | Toggle sidebar | File |
| `<leader>ca` | Code action | Code |
| `<leader>cf` | Format document | Code |
| `gd` | Go to definition | LSP |
| `gr` | Go to references | LSP |
| `K` | Show hover | LSP |
| `Shift+H` | Previous buffer | Buffer |
| `Shift+L` | Next buffer | Buffer |
| `[d` | Previous diagnostic | Diagnostic |
| `]d` | Next diagnostic | Diagnostic |
| `Ctrl+h/j/k/l` | Navigate splits | Window |
| `<leader>gg` | Git status | Git |
| `<leader>gb` | Git blame | Git |

---

## 📖 Full Installation Instructions

### Step 1: Install Required Extensions

```bash
# Core requirement
code --install-extension vscodevim.vim

# Recommended
code --install-extension eamodio.gitlens
code --install-extension hoovercj.vscode-settings-cycler
```

### Step 2: Locate VSCode User Directory

**Windows:** `%APPDATA%\Code\User\`
**macOS:** `~/Library/Application Support/Code/User/`
**Linux:** `~/.config/Code/User/`

### Step 3: Backup Existing Configuration

```bash
# Windows
copy %APPDATA%\Code\User\settings.json %APPDATA%\Code\User\settings.json.backup
copy %APPDATA%\Code\User\keybindings.json %APPDATA%\Code\User\keybindings.json.backup

# macOS/Linux
cp ~/Library/Application\ Support/Code/User/settings.json ~/Library/Application\ Support/Code/User/settings.json.backup
cp ~/Library/Application\ Support/Code/User/keybindings.json ~/Library/Application\ Support/Code/User/keybindings.json.backup
```

### Step 4: Apply Configuration

Copy `settings.json` and `keybindings.json` to your VSCode user directory (Step 2).

**For Settings Cycler (line number toggle):**
1. Uncomment the `settings.cycle` section at bottom of `settings.json`
2. Uncomment `<leader>ul` bindings in UI TOGGLES section

### Step 5: Platform-Specific Setup

**macOS only:**
```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```

**Non-US keyboards:**
Replace `oem_4` with `[BracketLeft]` and `oem_6` with `[BracketRight]` in `keybindings.json`

### Step 6: Restart VSCode

---

## 🔧 Troubleshooting Guide

### Leader key not working
- Verify `"vim.leader": "<space>"` in settings.json
- Ensure leader bindings are in settings.json, NOT keybindings.json
- Restart VSCode

### Typing lag
- Check `extensions.experimental.affinity` setting exists
- Disable unused extensions
- On macOS, enable key repeat (Step 5)

### Bracket navigation not working
- Non-US keyboard: Use scan codes `[BracketLeft]` / `[BracketRight]`
- Open Keyboard Shortcuts UI to debug key detection

### GitLens not working
- Install extension: `code --install-extension eamodio.gitlens`
- Ensure you're in a git repository

### Line numbers toggle not working
- Install Settings Cycler
- Uncomment `settings.cycle` section
- Uncomment `<leader>ul` binding

---

## 📋 Complete Validation Checklist

### Core Leader Functionality
- [ ] Space in Normal mode doesn't move cursor
- [ ] `<leader>ff` opens file picker
- [ ] `<leader>/` opens workspace search
- [ ] `<leader>e` toggles sidebar

### File Operations
- [ ] `<leader>ff` - Find files
- [ ] `<leader>fr` - Recent files
- [ ] `<leader>fn` - New file
- [ ] `<leader>fb` - Show buffers

### Search Operations
- [ ] `<leader>sg` - Search in files
- [ ] `<leader>ss` - Document symbols
- [ ] `<leader>sk` - Keybindings
- [ ] `<leader>sc` - Command palette

### LSP Navigation
- [ ] `gd` - Go to definition
- [ ] `gr` - Go to references
- [ ] `K` - Show hover

### Code Actions
- [ ] `<leader>ca` - Code action
- [ ] `<leader>cf` - Format document
- [ ] `<leader>cr` - Rename

### Buffer Management
- [ ] `Shift+H` - Previous buffer
- [ ] `Shift+L` - Next buffer
- [ ] `<leader>bd` - Close buffer
- [ ] `[b` / `]b` - Navigate buffers

### Window Navigation
- [ ] `Ctrl+h/j/k/l` - Navigate splits
- [ ] `<leader>-` - Split below
- [ ] `<leader>|` - Split right

### Diagnostics
- [ ] `[d` / `]d` - Navigate diagnostics
- [ ] `[e` / `]e` - Navigate errors
- [ ] `<leader>xx` - Problems panel

### Git (requires GitLens)
- [ ] `<leader>gg` - Git status
- [ ] `<leader>gb` - Git blame
- [ ] `<leader>gd` - Git diff
- [ ] `[h` / `]h` - Navigate hunks

### Other Features
- [ ] `jk` / `jj` - Escape to Normal
- [ ] `Alt+j` / `Alt+k` - Move lines
- [ ] `<` / `>` in Visual - Indent/reselect
- [ ] `Ctrl+/` - Toggle terminal
- [ ] No typing lag

---

## 📚 Complete Keybinding Reference

### File Operations - `<leader>f*`

| Binding | Action |
|---------|--------|
| `<leader><space>` | Find files (Quick Open) |
| `<leader>,` | Switch buffer |
| `<leader>/` | Search in files |
| `<leader>ff` | Find files |
| `<leader>fr` | Recent files |
| `<leader>fn` | New file |
| `<leader>fb` | List buffers |
| `<leader>fe` | Reveal in explorer |
| `<leader>ft` | Toggle terminal |
| `<leader>e` | Toggle sidebar |
| `<leader>E` | Focus explorer |

### Search Operations - `<leader>s*`

| Binding | Action |
|---------|--------|
| `<leader>sg` | Search/grep in files |
| `<leader>sw` | Search word |
| `<leader>sr` | Search & replace |
| `<leader>ss` | Goto symbol (file) |
| `<leader>sS` | Goto symbol (workspace) |
| `<leader>sk` | Keyboard shortcuts |
| `<leader>sc` | Command palette |
| `<leader>sh` | Help/all commands |

### Code Actions - `<leader>c*`

| Binding | Action |
|---------|--------|
| `<leader>ca` | Code action (quick fix) |
| `<leader>cA` | Source action |
| `<leader>cf` | Format document |
| `<leader>cF` | Format selection |
| `<leader>cr` | Rename symbol |
| `<leader>cd` | Line diagnostics (hover) |
| `<leader>cl` | Open problems panel |
| `<leader>co` | Organise imports |

### LSP Navigation - `g*`

| Binding | Action |
|---------|--------|
| `gd` | Go to definition |
| `gD` | Go to declaration |
| `gr` | Go to references |
| `gI` | Go to implementation |
| `gy` | Go to type definition |
| `gK` | Signature help |
| `K` | Show hover |

### Buffer Management - `<leader>b*`

| Binding | Action |
|---------|--------|
| `<leader>bb` | Switch buffer |
| `<leader>bd` | Delete buffer (close tab) |
| `<leader>bD` | Delete other buffers |
| `<leader>bo` | Close other editors |
| `<leader>bp` | Pin buffer |
| `<leader>bP` | Unpin buffer |
| `<leader>`` | Last buffer (alternate) |
| `Shift+H` | Previous buffer |
| `Shift+L` | Next buffer |
| `[b` | Previous buffer (alt) |
| `]b` | Next buffer (alt) |

### Git Operations - `<leader>g*`

| Binding | Action | Extension |
|---------|--------|-----------|
| `<leader>gg` | Git status | Native |
| `<leader>gs` | Git status | Native |
| `<leader>gb` | Toggle blame | GitLens |
| `<leader>gB` | Browse on remote | GitLens |
| `<leader>gd` | Git diff | Native |
| `<leader>gl` | Git log (file) | GitLens |
| `<leader>gL` | Git log (branch) | GitLens |
| `<leader>gc` | Commit details | GitLens |
| `[h` | Previous hunk | Native |
| `]h` | Next hunk | Native |

### Window Management - `<leader>w*` and Ctrl+hjkl

| Binding | Action |
|---------|--------|
| `<leader>wd` | Close window/split |
| `<leader>ww` | Switch window |
| `<leader>wm` | Maximise window |
| `<leader>-` | Split below |
| `<leader>\|` | Split right |
| `Ctrl+h` | Focus left split |
| `Ctrl+j` | Focus below split |
| `Ctrl+k` | Focus above split |
| `Ctrl+l` | Focus right split |
| `Ctrl+←→↑↓` | Resize splits |

### Diagnostics - `<leader>x*` and `[` / `]`

| Binding | Action |
|---------|--------|
| `<leader>xx` | Open problems panel |
| `<leader>xX` | Workspace diagnostics |
| `[d` | Previous diagnostic (all files) |
| `]d` | Next diagnostic (all files) |
| `[e` | Previous error (current file) |
| `]e` | Next error (current file) |
| `[q` | Previous search result |
| `]q` | Next search result |

### UI Toggles - `<leader>u*`

| Binding | Action | Notes |
|---------|--------|-------|
| `<leader>uw` | Toggle word wrap | Native |
| `<leader>uz` | Toggle zen mode | Native |
| `<leader>ur` | Clear search highlight | Native |
| `<leader>ul` | Toggle line numbers | Needs Settings Cycler |
| `<leader>uL` | Toggle relative numbers | Needs Settings Cycler |

### Other Important Bindings

| Binding | Action | Context |
|---------|--------|---------|
| `jk` / `jj` | Escape to Normal | Insert mode |
| `Alt+j` | Move line down | Editor |
| `Alt+k` | Move line up | Editor |
| `<` | Indent left & reselect | Visual mode |
| `>` | Indent right & reselect | Visual mode |
| `gc` | Toggle comment | Visual mode |
| `Ctrl+/` | Toggle terminal | All modes |
| `Ctrl+1/2/3` | Focus editor group | All modes |
| `Ctrl+s` | Save file | All modes |

---

## 📖 Additional Resources

- [LazyVim Keymaps](https://www.lazyvim.org/keymaps)
- [VSCode Vim](https://github.com/VSCodeVim/Vim)
- [VSCode Keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)
- [GitLens](https://gitlens.amod.io/)

## 📝 Notes

### Why Two Config Files?

**settings.json:** All space-leader bindings (`<leader>...`)
**keybindings.json:** Modifier key bindings (Ctrl, Alt, Shift) and special characters

### Performance Tips

1. `extensions.experimental.affinity` runs Vim in dedicated thread (CRITICAL)
2. Disable unused extensions
3. On macOS, enable key repeat
4. Use VSCode profiles for Vim-specific setup

### Keyboard Layouts

US layout uses `oem_*` codes. Non-US should use scan codes:
- `[BracketLeft]` instead of `oem_4`
- `[BracketRight]` instead of `oem_6`
- `[Slash]` instead of `oem_2`
