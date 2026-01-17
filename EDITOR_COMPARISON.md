# Editor Comparison: VS Code, Cursor, and Antigravity

VimCode is designed primarily for VS Code but works with VS Code-based editors. This guide explains compatibility, differences, and potential issues with each editor.

## Quick Summary

| Editor | Compatibility | Configuration Path | Notes |
|--------|--------------|-------------------|-------|
| **VS Code** | ✅ Full support | `~/.config/Code/User/` | Primary target, fully tested |
| **Cursor** | ⚠️ Compatible | `~/.config/Cursor/User/` | AI features may conflict |
| **Antigravity** | ✅ Compatible | `~/.config/Windsurf/User/` | VS Code fork, minimal issues |

## VS Code (Primary Target)

**Status:** ✅ Fully Supported

VimCode is designed and tested for VS Code. All features work as documented.

### Configuration Location

| Platform | Path |
|----------|------|
| **macOS** | `~/Library/Application Support/Code/User/` |
| **Linux** | `~/.config/Code/User/` |
| **Windows** | `%APPDATA%\Code\User\` |

### Key Features

- **50+ LazyVim keybindings** with space as leader
- **Full LSP integration** for code navigation
- **GitLens integration** for Git operations
- **Performance optimized** with dedicated thread
- **Comprehensive documentation** and troubleshooting

### Installation

```bash
# Install core extension
code --install-extension vscodevim.vim

# Copy configuration
cp config/settings.json ~/.config/Code/User/
cp config/keybindings.json ~/.config/Code/User/
```

See [SETUP.md](SETUP.md) for complete installation instructions.

## Cursor (AI-Powered Editor)

**Status:** ⚠️ Compatible with Caveats

Cursor is a VS Code fork with AI features. VimCode works, but AI keybindings may conflict.

### Configuration Location

| Platform | Path |
|----------|------|
| **macOS** | `~/Library/Application Support/Cursor/User/` |
| **Linux** | `~/.config/Cursor/User/` |
| **Windows** | `%APPDATA%\Cursor\User\` |

### Potential Conflicts

#### AI Chat Interface

Cursor's chat interface may use keybindings that conflict with Vim:
- **`Ctrl+K`** - Cursor AI command palette (conflicts with Vim navigation)
- **`Ctrl+L`** - Cursor AI features (conflicts with split navigation)

**Solution:**
Either disable Cursor AI keybindings or remap VimCode bindings.

#### AI Autocomplete

Cursor's AI autocomplete may interfere with:
- Suggestion navigation (`Ctrl+j/k`)
- Normal mode completion

**Solution:**
Test autocomplete behavior and adjust `when` clauses if needed.

### Installation for Cursor

```bash
# Install VSCodeVim in Cursor
cursor --install-extension vscodevim.vim

# Copy configuration
cp config/settings.json ~/Library/Application\ Support/Cursor/User/     # macOS
cp config/keybindings.json ~/Library/Application\ Support/Cursor/User/  # macOS

# Linux
cp config/settings.json ~/.config/Cursor/User/
cp config/keybindings.json ~/.config/Cursor/User/
```

### Recommended Cursor Settings

Add to `settings.json` to minimize conflicts:

```json
{
  // Disable conflicting Cursor keybindings
  "cursor.aiChat.enabled": true,
  "cursor.aiChat.openAIChatKeyBinding": "cmd+shift+k",  // Move away from Ctrl+K

  // VimCode settings (keep these)
  "vim.leader": "<space>",
  "extensions.experimental.affinity": {
    "vscodevim.vim": 1
  }
}
```

### Testing Checklist

After installing in Cursor, verify:

- [ ] `<leader>ff` - File finder works
- [ ] `Ctrl+h/j/k/l` - Split navigation works
- [ ] `gd` - Go to definition works
- [ ] Cursor AI chat is accessible
- [ ] No typing lag in Insert mode

## Antigravity (Windsurf)

**Status:** ✅ Compatible

Antigravity (Windsurf) is a VS Code fork. VimCode works with minimal issues.

### Configuration Location

| Platform | Path |
|----------|------|
| **macOS** | `~/Library/Application Support/Windsurf/User/` |
| **Linux** | `~/.config/Windsurf/User/` |
| **Windows** | `%APPDATA%\Windsurf\User\` |

### Known Issues

**None reported.** Antigravity closely follows VS Code, so VimCode should work without modification.

### Installation for Antigravity

```bash
# Install VSCodeVim in Antigravity
# (Use Antigravity's extension marketplace)

# Copy configuration
cp config/settings.json ~/Library/Application\ Support/Windsurf/User/     # macOS
cp config/keybindings.json ~/Library/Application\ Support/Windsurf/User/  # macOS

# Linux
cp config/settings.json ~/.config/Windsurf/User/
cp config/keybindings.json ~/.config/Windsurf/User/
```

### macOS Key Repeat

Enable key repeat for Antigravity:

```bash
defaults write com.windsurf.app ApplePressAndHoldEnabled -bool false
```

Restart your Mac for this to take effect.

## Common Compatibility Considerations

### Extension Availability

Not all VS Code extensions are available in Cursor/Antigravity:

| Extension | VS Code | Cursor | Antigravity |
|-----------|---------|--------|-------------|
| VSCodeVim | ✅ | ✅ | ✅ |
| GitLens | ✅ | ✅ | ⚠️ Check |
| Settings Cycler | ✅ | ✅ | ⚠️ Check |
| Which Key | ✅ | ✅ | ⚠️ Check |

**Recommendation:** Test each extension individually in your editor.

### Performance

All editors should support the dedicated thread setting:

```json
{
  "extensions.experimental.affinity": {
    "vscodevim.vim": 1
  }
}
```

This is **critical** for preventing typing lag.

### Platform-Specific Settings

**macOS key repeat** works the same way for all editors:

```bash
# VS Code
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false

# Cursor
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false

# Antigravity
defaults write com.windsurf.app ApplePressAndHoldEnabled -bool false
```

## Switching Between Editors

If you use multiple editors, you can:

### Option 1: Separate Configurations

Maintain separate configs per editor (more control):
- VS Code: `~/.config/Code/User/`
- Cursor: `~/.config/Cursor/User/`
- Antigravity: `~/.config/Windsurf/User/`

### Option 2: Symlinks

Share configuration between editors (less maintenance):

```bash
# Example: Share VS Code config with Cursor
ln -s ~/.config/Code/User/settings.json ~/.config/Cursor/User/settings.json
ln -s ~/.config/Code/User/keybindings.json ~/.config/Cursor/User/keybindings.json
```

**Warning:** Symlinks mean changes affect all editors.

## Troubleshooting Multi-Editor Issues

### Issue: Keybindings Don't Work in Cursor

**Solution:**
1. Verify Cursor uses the correct config path
2. Check for Cursor-specific keybinding conflicts
3. Open Cursor's Keyboard Shortcuts UI and search for conflicts

### Issue: GitLens Not Working in Antigravity

**Solution:**
1. Check if GitLens is available in Antigravity's marketplace
2. Install manually if needed
3. Verify you're in a git repository

### Issue: Different Behavior Between Editors

**Diagnosis:**
Compare extension versions:
```bash
# VS Code
code --list-extensions --show-versions

# Cursor
cursor --list-extensions --show-versions
```

**Solution:**
Ensure extension versions match across editors.

## Recommendations

### For VS Code Users

✅ **Use VimCode as-is.** Everything works out of the box.

### For Cursor Users

⚠️ **Test thoroughly.**
1. Install VimCode configuration
2. Test AI features separately
3. Remap conflicts if needed
4. Consider using `Cmd+Shift+K` for Cursor AI instead of `Ctrl+K`

### For Antigravity Users

✅ **Should work smoothly.**
1. Install VSCodeVim extension
2. Copy VimCode configuration
3. Test keybindings
4. Report any issues

## Getting Help

**Editor-specific issues:**
- VS Code: [VimCode Issues](https://github.com/wojukasz/VimCode/issues)
- Cursor: [Cursor Support](https://cursor.sh/support)
- Antigravity: [Windsurf Support](https://codeium.com/windsurf)

**VSCodeVim issues:**
- [VSCodeVim GitHub](https://github.com/VSCodeVim/Vim/issues)

---

**See also:**
- [SETUP.md](SETUP.md) - Installation guide
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Common issues
- [KEYBINDINGS.md](KEYBINDINGS.md) - Keybinding reference
