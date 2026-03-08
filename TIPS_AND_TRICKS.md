# Tips and Tricks

> **Getting started:** Learn these 10 bindings first: `<leader>ff` (find files), `<leader>e` (sidebar), `gd` (definition), `<leader>ca` (code action), `Shift+H/L` (switch buffers), `Ctrl+h/j/k/l` (navigate splits), `[d`/`]d` (diagnostics), `<leader>gg` (git status), `K` (hover), `jk` (exit insert).

## Table of Contents

- [Power User Workflows](#power-user-workflows)
- [Vim Plugin Mastery](#vim-plugin-mastery)
- [Efficient Code Navigation](#efficient-code-navigation)
- [Advanced Editing Techniques](#advanced-editing-techniques)
- [Git Workflows](#git-workflows)
- [Customization Tips](#customization-tips)
- [Productivity Hacks](#productivity-hacks)
- [Advanced Tips](#advanced-tips)

## Power User Workflows

### File Navigation

```
1. <leader>ff        # Quick Open
2. Type filename     # Fuzzy search
3. Ctrl+j/k          # Navigate results
4. Enter             # Open file
5. gd                # Jump to definition
6. Ctrl+o            # Back to original
7. <leader>bd        # Close file
```

**Switching between files:**
```
Shift+H     → Previous buffer
Shift+L     → Next buffer
[b          → Previous buffer (alt)
]b          → Next buffer (alt)
<leader>bb  → Quick buffer switcher
<leader>`   → Alternate file (last buffer)
```

**Managing files:**
```
<leader>fn  → New file
<leader>bd  → Close current file
<leader>bD  → Close other files
<leader>bp  → Pin file (prevent auto-close)
<leader>bP  → Unpin file
```

### Code Review

```
1. <leader>gg        # Open Source Control
2. Review changes    # Check modified files
3. [h                # Previous hunk
4. ]h                # Next hunk
5. <leader>gb        # Toggle blame
6. <leader>gl        # View file history
7. <leader>gc        # See commit details
```

> Use `[h` and `]h` to navigate hunks without leaving the editor.

### Refactoring

```
1. gd               # Jump to definition
2. <leader>cr       # Rename symbol
3. Type new name    # Enter new name
4. Enter            # Apply rename
5. <leader>cf       # Format document
6. Ctrl+o           # Return to original location
```

**Multi-cursor alternative:**
```
1. viw               # Select word
2. <leader>a         # Select all occurrences
3. c                 # Change (multi-cursor)
4. Type new name     # Edit simultaneously
5. Esc               # Exit insert
```

### Search and Replace

```
1. *                 # Search word under cursor
2. <leader>sg        # Grep in workspace
3. Review results    # Check all occurrences
4. <leader>sr        # Search & replace
5. Enter pattern     # Confirm changes
6. <leader>ur        # Clear highlights
```

> Use `<leader>sw` to search the word under cursor directly.

### Git Operations

```
1. <leader>gg       # Open Source Control
2. Review changes   # Check modified files
3. <leader>gd       # View diff
4. <leader>gb       # Toggle blame
5. [h / ]h          # Navigate hunks
6. Stage & commit   # In Source Control panel
```

### Debugging

```
1. <leader>xx        # Open problems panel
2. Review errors     # Understand issues
3. ]e                # Jump to first error
4. K                 # Read error message
5. <leader>ca        # Quick fix
6. ]e                # Next error
7. Repeat 4-6        # Fix all
8. <leader>cf        # Format
9. <leader>xx        # Verify clean
```

> Use `[e` and `]e` to navigate errors in the current file only.

### Multi-File Editing

```
1. <leader>ff        # Open file 1
2. Ctrl+\            # Split vertically
3. <leader>ff        # Open file 2
4. Ctrl+h/l          # Switch between splits
5. Edit both         # Side-by-side
6. <leader>wm        # Maximize current
7. <leader>wm        # Restore split
8. <leader>wd        # Close split
```

Use `<leader>-` for horizontal splits (top/bottom), `<leader>|` for vertical splits (left/right).

---

## Vim Plugin Mastery

### EasyMotion: Jump Anywhere

**Word jumping:**
```
<leader>jw    # Jump to word forward
<leader>jb    # Jump to word backward
```

**Line jumping:**
```
<leader>jj    # Jump to line below
<leader>jk    # Jump to line above
```

**Character jumping:**
```
<leader>js{char}    # Jump to any char on screen
```

### Sneak: Two-Character Search

```
s th        # Sneak forward to "th"
S th        # Sneak backward to "th"
;           # Next occurrence
,           # Previous occurrence
```

**When to use Sneak vs EasyMotion:**
- Sneak: when you know the two characters at the target
- EasyMotion: when you can see the target visually

### Surround: Wrapping Text

**Adding surrounds:**
```
ysiw"       # Surround word with "quotes"
ysiw(       # Surround word with (parentheses)
ysiw{       # Surround word with {braces}
ysiw[       # Surround word with [brackets]
ySiw{       # Surround with { spaced }
yss"        # Surround entire line
```

**Changing surrounds:**
```
cs"'        # Change " to '
cs({        # Change ( to {
cs])        # Change [ to ]
```

**Deleting surrounds:**
```
ds"         # Delete surrounding "
ds(         # Delete surrounding ()
dst         # Delete surrounding HTML tag
```

### Visual Block Mode: Column Editing

> **Note:** Visual block paste is unreliable in VSCodeVim. For column editing, use VS Code's native multi-cursor: `Alt+Click` or `Ctrl+Alt+↑↓`. See [KNOWN_ISSUES.md](KNOWN_ISSUES.md) for details.

Basic column edit (when it works):
```
1. Ctrl+v        # Visual block mode
2. j/k           # Select lines
3. I             # Insert at start
4. Type text     # Add to all lines
5. Esc           # Apply changes
```

---

## Efficient Code Navigation

### The Jump List

```
Ctrl+o      # Jump to older position (back)
Ctrl+i      # Jump to newer position (forward)
```

Works across files — you can jump back through 20+ locations.

### LSP Navigation Patterns

**The definition chain:**
```
1. K            # Read hover docs
2. gd           # Go to definition
3. gI           # Go to implementation
4. gr           # See all references
5. Ctrl+o       # Return home
```

**Finding usages:**
```
1. Position on function
2. gr           # Go to references
3. j/k          # Browse list
4. Enter        # Jump to usage
5. Ctrl+o       # Back to list
```

### Buffer Navigation

Methods ranked by speed:

1. **Fastest:**
   ```
   Shift+H     # Previous buffer
   Shift+L     # Next buffer
   ```

2. **Quick switch:**
   ```
   <leader>`   # Alternate buffer (toggle between 2)
   ```

3. **Buffer list:**
   ```
   <leader>bb  # Buffer switcher
   Type name   # Fuzzy search
   Enter       # Open
   ```

### Symbol Navigation

**In current file:**
```
<leader>ss      # Document symbols
Type name       # Fuzzy search
Enter           # Jump
```

**In workspace:**
```
<leader>sS      # Workspace symbols
Type name       # Find across all files
Enter           # Jump to file
```

---

## Advanced Editing Techniques

### Text Objects

- `i` = inner (excludes delimiters)
- `a` = outer (includes delimiters)

```
iw    # inner word        aw    # a word (with space)
i"    # inner quotes      a"    # a quotes (includes ")
i(    # inner parens      a(    # a parens (includes ())
i{    # inner braces      a{    # a braces (includes {})
i[    # inner brackets    a[    # a brackets (includes [])
it    # inner tag         at    # a tag
ip    # inner paragraph   ap    # a paragraph
```

**Practical examples:**
```
di"         # Delete inside quotes
ci(         # Change inside parentheses
ysiw"       # Surround word with quotes
vit         # Select inside HTML tag
```

### Macros

**Recording:**
```
1. q{letter}    # Start recording (qa, qb, qc, etc.)
2. Perform edits
3. q            # Stop recording
```

**Playing:**
```
@{letter}       # Play once
10@{letter}     # Play 10 times
@@              # Repeat last macro
```

### Dot Command

The `.` command repeats your last change:

```
daw     # Delete a word
.       # Repeat (delete next word)
j.      # Next line, repeat again
```

Structure edits to be repeatable with `.` — e.g., `A;` appends a semicolon; `j.` repeats it on the next line.

### Search and Replace

See [REFERENCES.md](REFERENCES.md) for vimtutor, which covers `:s` in depth.

```
:s/old/new/         # Current line, first occurrence
:s/old/new/g        # Current line, all occurrences
:%s/old/new/g       # All lines, all occurrences
:%s/old/new/gc      # All lines, with confirmation
```

---

## Git Workflows

### GitLens Integration

| Binding | Action |
|---------|--------|
| `<leader>gb` | Toggle inline blame |
| `<leader>gl` | File history |
| `<leader>gL` | Branch log |
| `<leader>gB` | Open file on GitHub/GitLab |

### Hunk Navigation

```
[h              # Previous hunk
]h              # Next hunk
<leader>gd      # View diff
```

### Git Status Workflow

```
1. <leader>gg   # Git status
2. Tab          # Focus file list
3. j/k          # Navigate files
4. Space        # Stage/unstage
5. Enter        # View diff
```

---

## Customization Tips

### Custom Keybindings

Add your own leader bindings in `settings.json`:

```json
"vim.normalModeKeyBindingsNonRecursive": [
  {
    "before": ["<leader>", "t", "p"],
    "commands": ["workbench.action.tasks.runTask"]
  },
  {
    "before": ["<leader>", "d", "b"],
    "commands": ["editor.debug.action.toggleBreakpoint"]
  }
]
```

**Remapping existing keys:**
```json
"vim.normalModeKeyBindings": [
  {
    "before": ["Y"],
    "after": ["y", "$"]
  }
]
```

### Status Bar Customization

Customize mode colors in `settings.json`:

```json
"vim.statusBarColors.normal": "#519aba",
"vim.statusBarColors.insert": "#98c379",
"vim.statusBarColors.visual": "#c678dd",
"vim.statusBarColors.replace": "#e06c75",
"vim.statusBarColors.visualline": "#c678dd",
"vim.statusBarColors.visualblock": "#c678dd"
```

### Sharing Config Between Editors

Use symlinks to share a single VimCode configuration across editors:

```bash
ln -s ~/.config/Code/User/settings.json ~/.config/Cursor/User/settings.json
ln -s ~/.config/Code/User/keybindings.json ~/.config/Cursor/User/keybindings.json
```

> Changes to symlinked files affect all editors simultaneously.

> Performance settings: see [SETUP.md](SETUP.md) and [TROUBLESHOOTING.md](TROUBLESHOOTING.md#performance-issues).

> For common problems, see [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

---

## Productivity Hacks

### One-Line Workflows

```
*           # Search word under cursor
#           # Search word backward
.           # Repeat last change
;           # Repeat last f/t motion
,           # Reverse last f/t motion
%           # Jump to matching bracket
``          # Jump to last position
''          # Jump to last line
```

### Quick Edits

```
cw          # Change word
ciw         # Change inner word
caw         # Change a word (with space)
C           # Change to end of line
cc          # Change entire line
S           # Substitute line (same as cc)
s           # Substitute character
r           # Replace single character
x           # Delete character
```

### Visual Selection

```
viw         # Select inner word
vaw         # Select a word
vi"         # Select inside quotes
va"         # Select with quotes
vip         # Select paragraph
gv          # Reselect last selection
o           # Toggle cursor position in Visual mode
```

### Quick Navigation

```
gg          # Top of file
G           # Bottom of file
50G         # Line 50
%           # Matching bracket
{           # Previous paragraph
}           # Next paragraph
H           # Top of screen
M           # Middle of screen
L           # Bottom of screen
```

### Marks

```
m{a-z}      # Set local mark (file)
m{A-Z}      # Set global mark (across files)
'{mark}     # Jump to line of mark
`{mark}     # Jump to exact position of mark
''          # Jump to previous location
```

Use capital marks (`mM`) to bookmark important spots across files.

---

## Advanced Tips

### Folding

```
zo          # Open fold
zc          # Close fold
za          # Toggle fold
zR          # Open all folds
zM          # Close all folds
```

### Multiple Cursors

```
<leader>a   # Select all occurrences (Visual mode)
gb          # Add next occurrence (Vim)
```

```
1. viw          # Select word
2. <leader>a    # Select all
3. c            # Change all
4. Type         # Edit simultaneously
5. Esc          # Exit
```

### Quick Fix Menu

```
<leader>ca      # Code action menu
j/k             # Navigate options
Enter           # Apply fix
```

Common actions: import missing modules, implement interface, extract to function, add type annotations.

---

**See also:**
- [KEYBINDINGS.md](KEYBINDINGS.md) — Complete shortcuts reference
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) — Common issues
- [SETUP.md](SETUP.md) — Configuration details
