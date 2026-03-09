# Setup

> **Platforms:** macOS, Linux, Windows. Platform-specific differences are noted inline.

## Prerequisites

| Requirement | Install | Verify |
|-------------|---------|--------|
| VS Code or compatible fork | [code.visualstudio.com](https://code.visualstudio.com) | `code --version` |
| VSCodeVim extension | `code --install-extension vscodevim.vim` | Extensions panel |
| Basic Vim knowledge | `vimtutor` in terminal | — |
| Git (for Git features) | [git-scm.com](https://git-scm.com) | `git --version` |

---

## Step 1 — Install Extensions

**Required:**
```bash
code --install-extension vscodevim.vim
```

**Highly recommended:**
```bash
code --install-extension eamodio.gitlens
code --install-extension hoovercj.vscode-settings-cycler
```

**Recommended:**
```bash
code --install-extension VSpaceCode.whichkey
```

**Optional:**
```bash
code --install-extension usernamehw.errorlens
code --install-extension ryuta46.multi-command
```

> Replace `code` with your editor's CLI command if needed (e.g. `cursor`, `antigravity`). If your editor has no CLI, install via `Ctrl+Shift+X`.

---

## Step 2 — Locate User Directory

Paths follow the standard VS Code fork convention — verify the exact path for your editor.

| Platform | VS Code | Cursor | Antigravity |
|----------|---------|--------|-------------|
| **macOS** | `~/Library/Application Support/Code/User/` | `~/Library/Application Support/Cursor/User/` | `~/Library/Application Support/Antigravity/User/` |
| **Linux** | `~/.config/Code/User/` | `~/.config/Cursor/User/` | `~/.config/Antigravity/User/` |
| **Windows** | `%APPDATA%\Code\User\` | `%APPDATA%\Cursor\User\` | `%APPDATA%\Antigravity\User\` |

---

## Step 3 — Backup Existing Configuration

```bash
# macOS
cp ~/Library/Application\ Support/Code/User/settings.json \
   ~/Library/Application\ Support/Code/User/settings.json.backup
cp ~/Library/Application\ Support/Code/User/keybindings.json \
   ~/Library/Application\ Support/Code/User/keybindings.json.backup

# Linux
cp ~/.config/Code/User/settings.json ~/.config/Code/User/settings.json.backup
cp ~/.config/Code/User/keybindings.json ~/.config/Code/User/keybindings.json.backup
```

```powershell
# Windows (PowerShell)
Copy-Item $env:APPDATA\Code\User\settings.json $env:APPDATA\Code\User\settings.json.backup
Copy-Item $env:APPDATA\Code\User\keybindings.json $env:APPDATA\Code\User\keybindings.json.backup
```

---

## Step 4 — Apply Configuration

```bash
# macOS
cp config/settings.json ~/Library/Application\ Support/Code/User/
cp config/keybindings.json ~/Library/Application\ Support/Code/User/

# Linux
cp config/settings.json ~/.config/Code/User/
cp config/keybindings.json ~/.config/Code/User/
```

```powershell
# Windows (PowerShell)
Copy-Item config\settings.json $env:APPDATA\Code\User\
Copy-Item config\keybindings.json $env:APPDATA\Code\User\
```

---

## Step 5 — Platform-Specific Setup

**macOS — enable key repeat:**
```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```
You may need to restart your Mac for this to take effect. Without it, holding `j` or `k` in Normal mode may show accent menus instead of repeating.

**Non-US keyboards:**
In `keybindings.json`, replace `oem_4` with `[BracketLeft]` and `oem_6` with `[BracketRight]` for layout-independent bracket navigation.

---

## Step 6 — Restart Your Editor

Close and reopen your editor for all changes to take effect. To apply without restarting: `Ctrl+Shift+P` → "Reload Window".

---

## Validation

Verify your setup with this checklist:

- [ ] `Tab` in Normal mode — which-key menu appears (if VSpaceCode.whichkey is installed)
- [ ] `Space` in Normal mode — cursor should NOT move (leader is active)
- [ ] `i` — status bar turns green (Insert mode)
- [ ] `Esc` or `jk` — status bar turns blue (Normal mode)
- [ ] `v` — status bar turns purple (Visual mode)
- [ ] `<leader>ff` — opens file picker (Quick Open)
- [ ] `<leader>fr` — shows recent files
- [ ] `<leader>fn` — creates new file
- [ ] `<leader>fb` — lists open buffers
- [ ] `<leader>e` — toggles sidebar
- [ ] `<leader>/` — opens workspace search
- [ ] `<leader>sg` — opens search/grep
- [ ] `<leader>ss` — shows document symbols
- [ ] `<leader>ca` — shows code actions (on a code symbol)
- [ ] `<leader>cf` — formats document
- [ ] `<leader>cr` — renames symbol (on a code symbol)
- [ ] `gd` — jumps to definition (on a code symbol)
- [ ] `gr` — shows references (on a code symbol)
- [ ] `K` — shows hover documentation (on a code symbol)
- [ ] `Ctrl+o` — navigates back after `gd`
- [ ] `Shift+H` — switches to previous buffer/tab
- [ ] `Shift+L` — switches to next buffer/tab
- [ ] `<leader>bd` — closes current buffer
- [ ] `Ctrl+h` — focuses left split
- [ ] `Ctrl+j` — focuses split below
- [ ] `Ctrl+k` — focuses split above
- [ ] `Ctrl+l` — focuses right split
- [ ] `<leader>-` — splits window horizontally
- [ ] `<leader>|` — splits window vertically
- [ ] `[d` — jumps to previous diagnostic
- [ ] `]d` — jumps to next diagnostic
- [ ] `<leader>xx` — opens problems panel
- [ ] `<leader>gg` — opens Git status (Source Control)
- [ ] `<leader>gb` — toggles Git blame (requires GitLens)
- [ ] `<leader>gd` — shows Git diff (requires GitLens)
- [ ] `[h` / `]h` — navigate Git hunks (if changes exist)
- [ ] `jk` or `jj` — exits Insert mode
- [ ] `Alt+j` / `Alt+k` — moves lines up/down
- [ ] `Ctrl+/` — toggles terminal
- [ ] No typing lag in Insert mode

---

## Optional Features

### Settings Cycler (Line Number Toggle)

Enables `<leader>ul` to cycle through line number modes (on → relative → off).

1. Install the extension (see Step 1).
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
3. Restart VS Code.

### Which Key (Keybinding Discovery)

Which Key shows a popup menu of available bindings — exactly like `which-key.nvim` in Neovim / LazyVim. The full binding tree is **already included** in `config/settings.json` under `whichkey.bindings`.

**Setup (one step):**
```bash
code --install-extension VSpaceCode.whichkey
```

After restarting, pressing `<Tab>` in Normal mode opens the menu:

> **Note:** `<Tab>` is used as the trigger instead of `<space>` (the LazyVim default). Both `<space>` and `vim.leader` are `<space>`, which creates a conflict — the leader intercepts the keypress before which-key can fire. `<Tab>` sidesteps this. All `<leader>*` bindings still use `<space>` and are unaffected.
```
<space>     Find Files          (Quick Open)
,           Switch Buffer
/           Search in Files
f  →        +File
g  →        +Git
c  →        +Code
s  →        +Search
b  →        +Buffer
w  →        +Window
x  →        +Diagnostics
u  →        +UI Toggles
q  →        +Quit
```

All existing `<leader>*` vim bindings remain intact as a fallback — they work normally if which-key is not installed.

To customise the menu, edit the `whichkey.bindings` array in your `settings.json`. See the [vscode-which-key docs](https://vspacecode.github.io/docs/whichkey/) for the full binding format.

---

## Platform-Specific Notes

### macOS

- Key repeat is essential — see Step 5.
- `Ctrl+h` may conflict with terminal delete. Use `<leader>ft` to toggle terminal if conflicts arise.

### Windows

- Use PowerShell for copy commands (`Copy-Item`); Command Prompt uses `copy` syntax instead.
- Path separators: use backslashes in Windows paths (`config\settings.json`), or PowerShell also accepts forward slashes.

### Linux

- X11 and Wayland both work with VimCode — no specific configuration needed.
- Clipboard integration requires `xclip` or `xsel` on X11: `sudo apt install xclip` (Debian/Ubuntu).

---

## Editor-Specific Notes

This section covers known considerations for specific VS Code forks. The config format is identical across VS Code forks — differences are config paths, CLI commands, and editor-specific AI keybindings. Tested on Antigravity; VS Code, Cursor, and Windsurf are untested but expected to work.

> Config paths follow the standard VS Code fork convention (e.g. `~/.config/<EditorName>/User/` on Linux). If the path doesn't exist, check your editor's documentation.

### Cursor — AI Keybinding Conflicts

Cursor's chat interface uses keybindings that conflict with Vim navigation:
- **`Ctrl+K`** — Cursor AI command palette (conflicts with Vim split navigation)
- **`Ctrl+L`** — Cursor AI features (conflicts with split navigation)

**Solution:** Move Cursor's AI keybinding:
```json
{
  "cursor.aiChat.openAIChatKeyBinding": "cmd+shift+k"
}
```

Cursor's AI autocomplete may also interfere with suggestion navigation (`Ctrl+j/k`). Adjust `when` clauses in `keybindings.json` if needed.

**Recommended Cursor settings:**
```json
{
  "vim.leader": "<space>",
  "extensions.experimental.affinity": {
    "vscodevim.vim": 1
  }
}
```

### macOS Key Repeat (All Editors)

```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false
defaults write com.google.antigravity ApplePressAndHoldEnabled -bool false
```

Restart your Mac after running these commands.

---

See [KNOWN_ISSUES.md](KNOWN_ISSUES.md) for a comparison with vscode-neovim and for architectural limitations of VSCodeVim.

See [KEYBINDINGS.md](KEYBINDINGS.md) for the complete keybinding reference. See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) if you encounter issues.
