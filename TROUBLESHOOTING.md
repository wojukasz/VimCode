# VimCode Troubleshooting Guide

Solutions to common issues when using VimCode - LazyVim-style keybindings for VS Code.

## Table of Contents

- [Installation Issues](#installation-issues)
- [Leader Key Problems](#leader-key-problems)
- [Performance Issues](#performance-issues)
- [Keybinding Conflicts](#keybinding-conflicts)
- [Platform-Specific Issues](#platform-specific-issues)
- [Extension Issues](#extension-issues)
- [Git Integration Problems](#git-integration-problems)
- [Editor Behavior Issues](#editor-behavior-issues)
- [FAQ](#faq)

## Installation Issues

### Configuration Not Loading

**Symptoms:**
- Keybindings don't work after copying files
- VS Code looks the same as before

**Solutions:**

1. **Verify file location:**
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

2. **Check file permissions:**
   ```bash
   # macOS/Linux - ensure files are readable
   chmod 644 ~/Library/Application\ Support/Code/User/settings.json
   chmod 644 ~/Library/Application\ Support/Code/User/keybindings.json
   ```

3. **Restart VS Code completely:**
   - Close all VS Code windows
   - Quit VS Code (not just close window)
   - Reopen VS Code
   - Test with `<leader>ff`

4. **Verify JSON syntax:**
   - Open settings.json in VS Code
   - Check for red squiggly lines (syntax errors)
   - Fix any JSON formatting issues

### Vim Extension Not Installing

**Symptoms:**
- `code --install-extension vscodevim.vim` fails
- Extension not appearing in Extensions panel

**Solutions:**

1. **Install manually:**
   - Open VS Code
   - Press `Ctrl+Shift+X` (Extensions)
   - Search for "Vim"
   - Click "Install" on "Vim" by vscodevim

2. **Check internet connection:**
   ```bash
   # Test marketplace connectivity
   curl -I https://marketplace.visualstudio.com
   ```

3. **Clear extension cache:**
   ```bash
   # macOS/Linux
   rm -rf ~/.vscode/extensions

   # Windows (PowerShell)
   Remove-Item -Recurse -Force $env:USERPROFILE\.vscode\extensions
   ```
   Then reinstall extensions.

4. **Use different network:**
   - Corporate firewalls may block marketplace
   - Try home network or mobile hotspot

## Leader Key Problems

### Space Moves Cursor Instead of Triggering Leader

**Symptoms:**
- Pressing space in Normal mode moves cursor right
- Leader keybindings don't work

**Diagnosis:**
```
1. Open settings.json
2. Search for "vim.leader"
3. Verify it says: "vim.leader": "<space>"
```

**Solutions:**

1. **Ensure leader is configured:**
   ```json
   {
     "vim.leader": "<space>"
   }
   ```

2. **Verify you're in Normal mode:**
   - Status bar should be blue (not green for Insert)
   - Try pressing `Esc` first, then space

3. **Check for conflicting settings:**
   - Search settings.json for other `"leader"` mentions
   - Remove any duplicate configurations

4. **Restart VS Code**

### Leader Keybindings in Wrong File

**Symptoms:**
- Leader bindings not working
- Other keybindings work fine

**Problem:**
Leader bindings are in `keybindings.json` instead of `settings.json`.

**Solution:**
Leader bindings MUST be in `settings.json` under `vim.normalModeKeyBindingsNonRecursive`. Move them from `keybindings.json` if they're there.

**Correct structure:**
```json
// settings.json
{
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["<leader>", "f", "f"],
      "commands": ["workbench.action.quickOpen"]
    }
  ]
}
```

## Performance Issues

### Typing Lag in Insert Mode

**Symptoms:**
- Characters appear slowly when typing
- Delay between keypress and character appearing
- Cursor movement feels sluggish

**Solutions:**

1. **Add dedicated thread setting (CRITICAL):**
   ```json
   {
     "extensions.experimental.affinity": {
       "vscodevim.vim": 1
     }
   }
   ```
   This runs Vim extension in a separate thread.

2. **On macOS, enable key repeat:**
   ```bash
   defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
   ```
   Then **restart your Mac** (not just VS Code).

3. **Disable unused extensions:**
   - Open Extensions panel (`Ctrl+Shift+X`)
   - Disable extensions you don't use
   - Restart VS Code

4. **Check resource usage:**
   - Open Activity Monitor (macOS) or Task Manager (Windows)
   - Look for high CPU/memory usage
   - Close resource-heavy applications

5. **Reduce editor animations:**
   ```json
   {
     "editor.smoothScrolling": false,
     "workbench.editor.enablePreview": false,
     "editor.cursorSmoothCaretAnimation": "off"
   }
   ```

6. **Disable minimap:**
   ```json
   {
     "editor.minimap.enabled": false
   }
   ```

### VS Code Freezing

**Symptoms:**
- VS Code stops responding
- Spinning wheel or "Not Responding"

**Solutions:**

1. **Disable Vim extension temporarily:**
   - Extensions panel → Vim → Disable
   - If problem persists, it's not VimCode
   - If problem stops, see typing lag solutions above

2. **Check for infinite loops:**
   - Review custom keybindings
   - Look for recursive mappings

3. **Clear workspace storage:**
   ```bash
   # macOS/Linux
   rm -rf ~/Library/Application\ Support/Code/workspaceStorage

   # Windows
   Remove-Item -Recurse $env:APPDATA\Code\workspaceStorage
   ```

4. **Start with clean profile:**
   - Create new VS Code profile
   - Test if issue persists

## Keybinding Conflicts

### Ctrl+h Deletes Instead of Navigating

**Symptoms:**
- `Ctrl+h` deletes character (like backspace)
- Doesn't navigate to left split

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
"key": "[BracketLeft]"   // [
"key": "[BracketRight]"  // ]
```

**Find all instances:**
```bash
grep -n "oem_4\|oem_6" keybindings.json
```

### Suggestion Widget Conflicts

**Symptoms:**
- `Ctrl+j/k` doesn't navigate suggestions
- Autocomplete breaks

**Solution:**
Ensure these keybindings are in `keybindings.json`:
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
- Terminal intercepts keybindings

**Solution:**
Add terminal-specific when clauses:
```json
{
  "key": "ctrl+h",
  "command": "workbench.action.navigateLeft",
  "when": "vim.active && !terminalFocus"
}
```

## Platform-Specific Issues

### macOS: Key Repeat Not Working

**Symptoms:**
- Holding `j` or `k` shows accent menu
- Can't hold keys to repeat

**Solution:**
```bash
# For VS Code
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false

# For Cursor
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false

# For Antigravity
defaults write com.windsurf.app ApplePressAndHoldEnabled -bool false
```

**IMPORTANT:** Restart your Mac (log out/in isn't enough).

**Verify it worked:**
```bash
defaults read com.microsoft.VSCode ApplePressAndHoldEnabled
# Should output: 0
```

### macOS: Ctrl+h Deletes

**Cause:**
macOS Terminal maps `Ctrl+h` to delete.

**Solution:**
See [Ctrl+h Deletes Instead of Navigating](#ctrlh-deletes-instead-of-navigating).

### Windows: PowerShell Commands Don't Work

**Symptoms:**
- `Copy-Item` command not found
- Copy commands fail

**Solutions:**

1. **Use PowerShell, not Command Prompt:**
   - Open PowerShell (not cmd.exe)
   - Run the copy commands

2. **Alternative using cmd.exe:**
   ```cmd
   copy config\settings.json %APPDATA%\Code\User\
   copy config\keybindings.json %APPDATA%\Code\User\
   ```

### Linux: Clipboard Not Working

**Symptoms:**
- `y` (yank) doesn't copy to clipboard
- Can't paste yanked text outside VS Code

**Solution:**

1. **Install clipboard utility:**
   ```bash
   # Debian/Ubuntu
   sudo apt install xclip

   # Fedora
   sudo dnf install xclip

   # Arch
   sudo pacman -S xclip
   ```

2. **Enable system clipboard:**
   ```json
   {
     "vim.useSystemClipboard": true
   }
   ```

3. **Restart VS Code**

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

1. **Install GitLens:**
   ```bash
   code --install-extension eamodio.gitlens
   ```

2. **Verify you're in a git repository:**
   ```bash
   git status
   # Should show git info, not "not a git repository"
   ```

3. **Check GitLens is enabled:**
   - Extensions panel
   - Ensure GitLens is not disabled
   - Click "Enable" if needed

4. **Reload window:**
   - `Ctrl+Shift+P`
   - "Developer: Reload Window"

### Settings Cycler Not Working

**Symptoms:**
- `<leader>ul` (line numbers toggle) doesn't work

**Solutions:**

1. **Install Settings Cycler:**
   ```bash
   code --install-extension hoovercj.vscode-settings-cycler
   ```

2. **Uncomment settings.cycle section:**

   In `settings.json`, find and uncomment:
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

3. **Verify keybinding:**

   In `settings.json`, ensure binding exists:
   ```json
   {
     "before": ["<leader>", "u", "l"],
     "commands": ["settings.cycle.lineNumbers"]
   }
   ```

### Which Key Not Appearing

**Symptoms:**
- No keybinding menu appears after pressing leader
- Expected popup doesn't show

**Note:**
VimCode doesn't require Which Key extension. It's optional.

**If you want Which Key:**

1. **Install extension:**
   ```bash
   code --install-extension VSpaceCode.whichkey
   ```

2. **Configure in settings.json:**
   ```json
   "whichkey.delay": 500,
   "whichkey.sortOrder": "alphabetically"
   ```

## Git Integration Problems

### Git Commands Don't Work

**Symptoms:**
- `<leader>gg` does nothing
- Source Control is empty

**Diagnosis:**
```bash
# Check if folder is a git repo
git status

# Check git is installed
git --version
```

**Solutions:**

1. **Initialize git repository:**
   ```bash
   git init
   ```

2. **Open folder containing .git:**
   - File → Open Folder
   - Navigate to git repository root
   - Open the folder

3. **Install git if missing:**
   ```bash
   # macOS
   brew install git

   # Linux
   sudo apt install git

   # Windows
   # Download from git-scm.com
   ```

### Git Blame Shows "Not a Git Repository"

**Symptoms:**
- GitLens blame shows error
- File not in git repo

**Solution:**
Ensure you've opened the repository root folder, not a parent directory.

**Check:**
```bash
# Should be in folder with .git directory
ls -la .git
```

### Hunk Navigation Shows No Changes

**Symptoms:**
- `[h` and `]h` do nothing
- No hunks found

**Causes:**
1. No uncommitted changes
2. File not in git repo
3. File is new (not tracked)

**Solutions:**
1. Make changes to tracked file
2. Stage some changes, leave some unstaged
3. Try `[h` and `]h` again

## Editor Behavior Issues

### Line Numbers Not Relative

**Symptoms:**
- Line numbers show absolute, not relative
- Expected relative numbers

**Solution:**
```json
{
  "editor.lineNumbers": "relative",
  "vim.smartRelativeLine": true
}
```

**Note:** Line numbers should be:
- Relative in Normal/Visual modes
- Absolute in Insert mode

### Status Bar Color Not Changing

**Symptoms:**
- Status bar stays same color in all modes
- No visual mode indicator

**Solution:**
Add to `settings.json`:
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
- Column editing doesn't work

**Cause:**
`Ctrl+v` is paste in VS Code by default.

**Solution:**
VimCode lets VS Code handle `Ctrl+v` for paste. Use VS Code's column edit:
- `Alt+Click` for multiple cursors
- `Alt+Shift+Drag` for column selection

**Or configure Vim to handle it:**
```json
{
  "vim.handleKeys": {
    "<C-v>": true
  }
}
```

**Trade-off:** You lose `Ctrl+v` for paste.

### Search Highlighting Persists

**Symptoms:**
- Search highlights stay after search
- Can't clear highlights

**Solution:**
```
<leader>ur      # Clear search highlight
```

Or use Vim's native:
```
:noh            # No highlight
```

## FAQ

### Can I use VimCode with other editors (Cursor, Antigravity)?

**Yes!** VimCode works with VS Code-based editors:
- **Cursor:** Use `~/.config/Cursor/User/` (Linux) or equivalent
- **Antigravity:** Use `~/.config/Windsurf/User/` (Linux) or equivalent

See [EDITOR_COMPARISON.md](EDITOR_COMPARISON.md) for details.

### How do I temporarily disable Vim mode?

**Quick disable:**
1. Extensions panel (`Ctrl+Shift+X`)
2. Find "Vim"
3. Click "Disable"
4. Reload window

**Toggle with keybinding:**
Add to `keybindings.json`:
```json
{
  "key": "ctrl+alt+v",
  "command": "toggleVim"
}
```

### Can I use my own keybindings?

**Absolutely!** VimCode is a starting point. Customize in:
- `settings.json` - Leader bindings
- `keybindings.json` - Modifier keys

See [TIPS_AND_TRICKS.md#customization-tips](TIPS_AND_TRICKS.md#customization-tips).

### Why are there two configuration files?

**Technical reason:**
- `settings.json` - Vim extension settings (leader bindings)
- `keybindings.json` - VS Code keybindings (modifier keys)

Vim needs to process leader bindings before VS Code sees them.

See [SETUP.md#configuration-architecture](SETUP.md#configuration-architecture).

### How do I revert to my old configuration?

**If you made backups:**
```bash
# macOS
cp ~/Library/Application\ Support/Code/User/settings.json.backup ~/Library/Application\ Support/Code/User/settings.json
cp ~/Library/Application\ Support/Code/User/keybindings.json.backup ~/Library/Application\ Support/Code/User/keybindings.json

# Linux
cp ~/.config/Code/User/settings.json.backup ~/.config/Code/User/settings.json
cp ~/.config/Code/User/keybindings.json.backup ~/.config/Code/User/keybindings.json
```

**If you didn't make backups:**
1. Delete current files
2. VS Code will recreate defaults
3. Manually re-add your settings

### Where can I get more help?

- **GitHub Issues:** [github.com/wojukasz/VimCode/issues](https://github.com/wojukasz/VimCode/issues)
- **VS Code Vim Docs:** [github.com/VSCodeVim/Vim](https://github.com/VSCodeVim/Vim)
- **LazyVim Keymaps:** [lazyvim.org/keymaps](https://www.lazyvim.org/keymaps)

### Is VimCode production-ready?

**Note from author:**
> Some keybindings are experimental. Test thoroughly before relying on them for critical work. Feedback welcome!

**Recommendation:**
- Use in personal projects first
- Validate all keybindings you use
- Customize to your workflow
- Report issues on GitHub

---

**Still having issues?** Open an issue on GitHub with:
1. Your VS Code version
2. Your OS and version
3. Steps to reproduce
4. Expected vs actual behavior
5. Relevant sections of your settings.json

**Quick Links:**
- [SETUP.md](SETUP.md) - Installation guide
- [KEYBINDINGS.md](KEYBINDINGS.md) - Keybinding reference
- [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) - Advanced usage
