# Troubleshooting

> For architectural limitations (visual block mode, macros, registers), see [KNOWN_ISSUES.md](KNOWN_ISSUES.md).

---

## Installation Issues

### Configuration Not Loading

**Symptoms:**
- Keybindings don't work after copying files
- VS Code looks the same as before

**Solutions:**

1. Verify file location:
   ```bash
   # macOS
   ls -la ~/Library/Application\ Support/Code/User/settings.json
   ls -la ~/Library/Application\ Support/Code/User/keybindings.json

   # Linux
   ls -la ~/.config/Code/User/settings.json
   ls -la ~/.config/Code/User/keybindings.json

   # Windows (PowerShell)
   dir $env:APPDATA\Code\User\settings.json
   dir $env:APPDATA\Code\User\keybindings.json
   ```

2. Check file permissions:
   ```bash
   chmod 644 ~/Library/Application\ Support/Code/User/settings.json
   chmod 644 ~/Library/Application\ Support/Code/User/keybindings.json
   ```

3. Restart VS Code completely — close all windows, quit (not just close), reopen, and test with `<leader>ff`.

4. Verify JSON syntax — open `settings.json` in VS Code and check for red squiggly lines.

### Vim Extension Not Installing

**Symptoms:**
- `code --install-extension vscodevim.vim` fails
- Extension not appearing in Extensions panel

**Solutions:**

1. Install manually: `Ctrl+Shift+X` → search "Vim" → install "Vim" by vscodevim.

2. Test marketplace connectivity:
   ```bash
   curl -I https://marketplace.visualstudio.com
   ```

3. Clear extension cache:
   ```bash
   # macOS/Linux
   rm -rf ~/.vscode/extensions
   ```
   Then reinstall extensions.

---

## Leader Key Problems

### Space Moves Cursor Instead of Triggering Leader

**Symptoms:**
- Pressing space in Normal mode moves cursor right
- Leader keybindings don't work

**Diagnosis:**
Open `settings.json` and verify `"vim.leader": "<space>"` is present.

**Solutions:**

1. Ensure leader is configured:
   ```json
   {
     "vim.leader": "<space>"
   }
   ```

2. Verify you're in Normal mode — status bar should be blue (not green for Insert). Press `Esc` first, then space.

3. Check for conflicting settings: search `settings.json` for duplicate `"leader"` mentions.

4. Restart VS Code.

### Leader Keybindings in Wrong File

**Symptoms:**
- Leader bindings not working
- Other keybindings work fine

**Cause:**
Leader bindings placed in `keybindings.json` instead of `settings.json`.

**Solution:**
Leader bindings must be in `settings.json` under `vim.normalModeKeyBindingsNonRecursive`. Move them if they're in `keybindings.json`.

```json
// settings.json — correct location
{
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["<leader>", "f", "f"],
      "commands": ["workbench.action.quickOpen"]
    }
  ]
}
```

---

## Performance Issues

### Typing Lag in Insert Mode

**Symptoms:**
- Characters appear slowly when typing
- Delay between keypress and character appearing
- Cursor movement feels sluggish

**Solutions:**

1. Add dedicated thread setting:
   ```json
   {
     "extensions.experimental.affinity": {
       "vscodevim.vim": 1
     }
   }
   ```

2. On macOS, enable key repeat:
   ```bash
   defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
   ```
   Then restart your Mac (not just VS Code).

3. Disable unused extensions — open Extensions panel (`Ctrl+Shift+X`) and disable extensions you don't use.

4. Reduce editor animations:
   ```json
   {
     "editor.smoothScrolling": false,
     "workbench.editor.enablePreview": false,
     "editor.cursorSmoothCaretAnimation": "off"
   }
   ```

---

## Keybinding Conflicts

### Ctrl+h Deletes Instead of Navigating

**Symptoms:**
- `Ctrl+h` deletes character (like backspace)
- Doesn't navigate to left split

**Cause:**
macOS Terminal maps `Ctrl+h` to delete. The keybinding in `keybindings.json` may also need a `!terminalFocus` guard.

**Solution:**
Add to `keybindings.json`:
```json
{
  "key": "ctrl+h",
  "command": "workbench.action.navigateLeft",
  "when": "vim.active && vim.mode != 'Insert'"
},
{
  "key": "ctrl+h",
  "command": "-workbench.action.terminal.sendSequence"
}
```

### Bracket Navigation Not Working

**Symptoms:**
- `[d`, `]d`, `[h`, `]h` don't work
- `oem_4` and `oem_6` not recognized

**Cause:**
Non-US keyboard layout.

**Solution:**
In `keybindings.json`, replace:
```json
// OLD (US layout)
"key": "oem_4"  // [
"key": "oem_6"  // ]

// NEW (international)
"key": "[BracketLeft]"
"key": "[BracketRight]"
```

### Suggestion Widget Conflicts

**Symptoms:**
- `Ctrl+j/k` doesn't navigate suggestions
- Autocomplete breaks

**Solution:**
Ensure these are in `keybindings.json`:
```json
{
  "key": "ctrl+j",
  "command": "selectNextSuggestion",
  "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
},
{
  "key": "ctrl+k",
  "command": "selectPrevSuggestion",
  "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
}
```

### Terminal Keybindings Conflict

**Symptoms:**
- `Ctrl+h/j/k/l` doesn't work when terminal is focused

**Solution:**
Add terminal-specific when clauses:
```json
{
  "key": "ctrl+h",
  "command": "workbench.action.navigateLeft",
  "when": "vim.active && !terminalFocus"
}
```

---

## Platform-Specific Issues

### macOS: Key Repeat Not Working

**Symptoms:**
- Holding `j` or `k` shows accent menu
- Can't hold keys to repeat

**Solution:**
```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false
defaults write com.google.antigravity ApplePressAndHoldEnabled -bool false
```

> Restart your Mac after running these commands. Verify with: `defaults read com.microsoft.VSCode ApplePressAndHoldEnabled` — should output `0`.

### Windows: PowerShell Commands Don't Work

**Symptoms:**
- `Copy-Item` command not found

**Solutions:**

1. Use PowerShell, not Command Prompt.

2. Alternative using cmd.exe:
   ```cmd
   copy config\settings.json %APPDATA%\Code\User\
   copy config\keybindings.json %APPDATA%\Code\User\
   ```

### Linux: Clipboard Not Working

**Symptoms:**
- `y` (yank) doesn't copy to clipboard

**Solution:**

1. Install clipboard utility:
   ```bash
   sudo apt install xclip      # Debian/Ubuntu
   sudo dnf install xclip      # Fedora
   sudo pacman -S xclip        # Arch
   ```

2. Enable system clipboard:
   ```json
   { "vim.useSystemClipboard": true }
   ```

---

## Extension Issues

### GitLens Keybindings Not Working

**Symptoms:**
- `<leader>gb` (blame) doesn't work
- `<leader>gl` (log) doesn't work

**Diagnosis:**
```bash
code --list-extensions | grep gitlens
# Should show: eamodio.gitlens
```

**Solutions:**

1. Install GitLens:
   ```bash
   code --install-extension eamodio.gitlens
   ```

2. Verify you're in a git repository (`git status`).

3. Check GitLens is enabled in the Extensions panel.

4. Reload window: `Ctrl+Shift+P` → "Developer: Reload Window".

### Settings Cycler Not Working

**Symptoms:**
- `<leader>ul` (line numbers toggle) doesn't work

**Solutions:**

1. Install Settings Cycler:
   ```bash
   code --install-extension hoovercj.vscode-settings-cycler
   ```

2. Uncomment `settings.cycle` section in `settings.json`:
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

### Which Key Not Appearing

**Symptoms:**
- No keybinding menu appears after pressing leader

**Note:**
VimCode works without Which Key — it's optional. All `<leader>*` bindings function without it.

**To install:**
```bash
code --install-extension VSpaceCode.whichkey
```

---

## Git Integration Problems

### Git Commands Don't Work

**Symptoms:**
- `<leader>gg` does nothing
- Source Control is empty

**Diagnosis:**
```bash
git status    # Check if folder is a git repo
git --version # Check git is installed
```

**Solutions:**

1. Initialize git repository: `git init`

2. Open the folder containing `.git` — File → Open Folder → navigate to git repository root.

3. Install git if missing:
   ```bash
   brew install git     # macOS
   sudo apt install git # Linux
   ```

4. If GitLens blame shows "Not a Git Repository": ensure you've opened the repository root, not a parent directory. Verify: `ls -la .git`

### Hunk Navigation Shows No Changes

**Symptoms:**
- `[h` and `]h` do nothing

**Causes:** No uncommitted changes, file not in git repo, or file is new (not tracked).

**Solutions:**
1. Make changes to a tracked file.
2. Leave some changes unstaged.
3. Try `[h` and `]h` again.

---

## Editor Behavior Issues

### Line Numbers Not Relative

**Symptoms:**
- Line numbers show absolute, not relative

**Solution:**
```json
{
  "editor.lineNumbers": "relative",
  "vim.smartRelativeLine": true
}
```

Line numbers are relative in Normal/Visual modes and absolute in Insert mode.

### Status Bar Color Not Changing

**Symptoms:**
- Status bar stays same color in all modes

**Solution:**
```json
{
  "vim.statusBarColorControl": true,
  "vim.statusBarColors.normal": "#519aba",
  "vim.statusBarColors.insert": "#98c379",
  "vim.statusBarColors.visual": "#c678dd",
  "vim.statusBarColors.replace": "#e06c75"
}
```

### Visual Block Mode Not Working

**Symptoms:**
- `Ctrl+v` doesn't enter visual block mode

**Cause:**
`Ctrl+v` is paste in VS Code by default. Visual block paste is also unreliable in VSCodeVim. See [KNOWN_ISSUES.md](KNOWN_ISSUES.md).

**Solution:**
Use VS Code's column edit instead:
- `Alt+Click` for multiple cursors
- `Alt+Shift+Drag` for column selection

### Search Highlighting Persists

**Symptoms:**
- Search highlights stay after search

**Solution:**
```
<leader>ur      # Clear search highlight
:noh            # Vim native alternative
```

---

> Still having issues? Open a [GitHub Issue](https://github.com/wojukasz/VimCode/issues) with your VS Code version, OS, steps to reproduce, expected vs actual behavior, and relevant `settings.json` sections.
>
> See also: [SETUP.md](SETUP.md) — installation guide | [KEYBINDINGS.md](KEYBINDINGS.md) — keybinding reference | [KNOWN_ISSUES.md](KNOWN_ISSUES.md) — architectural limitations
