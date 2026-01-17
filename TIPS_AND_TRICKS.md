# VimCode Tips and Tricks

Power user guide for maximizing productivity with VimCode - LazyVim-style keybindings for VS Code.

## Table of Contents

- [Power User Workflows](#power-user-workflows)
- [Vim Plugin Mastery](#vim-plugin-mastery)
- [Efficient Code Navigation](#efficient-code-navigation)
- [Advanced Editing Techniques](#advanced-editing-techniques)
- [Git Workflows](#git-workflows)
- [Customization Tips](#customization-tips)
- [Performance Optimization](#performance-optimization)
- [Common Pitfalls and Solutions](#common-pitfalls-and-solutions)
- [Productivity Hacks](#productivity-hacks)
- [Keyboard-First Development](#keyboard-first-development)

## Power User Workflows

### The 30-Second File Navigation Workflow

Master file navigation without touching the mouse:

```
1. <leader>ff        # Quick Open
2. Type: "user"      # Fuzzy search
3. Ctrl+j/k          # Navigate results
4. Enter             # Open file
5. gd                # Jump to definition
6. Ctrl+o            # Back to original
7. <leader>bd        # Close file
```

**Time saved:** 5-10 seconds per file operation

### The Code Review Workflow

Reviewing code changes efficiently:

```
1. <leader>gg        # Open Source Control
2. Click file        # See diff
3. [h                # Previous hunk
4. ]h                # Next hunk
5. <leader>gb        # Toggle blame
6. <leader>gl        # View file history
7. <leader>gc        # See commit details
```

**Pro tip:** Use `[h` and `]h` to navigate hunks without leaving the editor.

### The Refactoring Workflow

Safe and efficient code refactoring:

```
1. viw               # Select word
2. <leader>a         # Select all occurrences
3. c                 # Change (multi-cursor)
4. Type new name     # Edit simultaneously
5. Esc               # Exit insert
6. <leader>cf        # Format document
7. <leader>ca        # Fix any issues
8. :w                # Save
```

**Alternative:** Use `<leader>cr` for symbol-aware rename.

### The Search and Replace Workflow

Finding and replacing across the workspace:

```
1. *                 # Search word under cursor
2. <leader>sg        # Grep in workspace
3. Review results    # Check all occurrences
4. <leader>sr        # Search & replace
5. Enter pattern     # Confirm changes
6. <leader>ur        # Clear highlights
```

**Pro tip:** Use `<leader>sw` to search the word under cursor directly.

### The Debugging Workflow

Fixing errors systematically:

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

**Pro tip:** Use `[e` and `]e` to navigate errors in current file only.

### The Multi-File Editing Workflow

Editing multiple files efficiently:

```
1. <leader>ff        # Open file 1
2. Ctrl+\            # Split vertically
3. <leader>ff        # Open file 2
4. Ctrl+h/l          # Switch between
5. Edit both         # Side-by-side
6. <leader>wm        # Maximize current
7. <leader>wm        # Restore split
8. <leader>wd        # Close split
```

**Layout tip:**
- Use `<leader>-` for horizontal splits (top/bottom)
- Use `<leader>|` for vertical splits (left/right)

## Vim Plugin Mastery

### EasyMotion: Jump Anywhere

EasyMotion is your teleportation tool:

**Word jumping:**
```
<leader><leader>w    # Jump to word forward
<leader><leader>b    # Jump to word backward
```

**Line jumping:**
```
<leader><leader>j    # Jump to line below
<leader><leader>k    # Jump to line above
```

**Character jumping:**
```
<leader><leader>s{char}    # Jump to any char on screen
```

**Real-world example:**
```
You're at line 50, need to edit line 200:
1. <leader><leader>j    # Activate line jump
2. Letters appear       # On each line
3. Type the letter      # Instant jump
```

**Pro tip:** EasyMotion is faster than `20j` or `150j` for long distances.

### Sneak: Two-Character Search

Sneak is precision navigation:

**Basic usage:**
```
s th        # Sneak forward to "th"
S th        # Sneak backward to "th"
;           # Next occurrence
,           # Previous occurrence
```

**Real-world example:**
```
Finding a function call:
1. s fn     # "fn" for "function"
2. ;        # Next "fn"
3. ;        # Keep going
```

**When to use Sneak vs EasyMotion:**
- **Sneak:** When you know the two characters
- **EasyMotion:** When you can see the target

### Surround: Master of Wrapping

Surround makes quote/bracket manipulation effortless:

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

**Real-world examples:**

Converting function call:
```
Before: myFunction(arg)
1. ci(                  # Change inside ()
2. Type new args        # Edit
Result: myFunction(newArg)
```

Adding quotes:
```
Before: const name = value
1. Move to "value"
2. ysiw"                # Surround with "
Result: const name = "value"
```

Changing quote style:
```
Before: const str = "hello"
1. Move to "
2. cs"'                 # Change " to '
Result: const str = 'hello'
```

### Visual Block Mode: Column Editing

Edit multiple lines simultaneously:

**Basic column edit:**
```
1. Ctrl+v        # Visual block mode
2. j/k           # Select lines
3. I             # Insert at start
4. Type text     # Add to all lines
5. Esc           # Apply changes
```

**Append to end:**
```
1. Ctrl+v        # Visual block mode
2. j/k           # Select lines
3. $             # Go to end
4. A             # Append
5. Type text     # Add to all lines
6. Esc           # Apply
```

**Real-world example - Adding comments:**
```
Before:
let x = 1
let y = 2
let z = 3

1. Ctrl+v       # Visual block
2. 2j           # Select 3 lines
3. I            # Insert mode
4. // (space)   # Type comment
5. Esc          # Apply

After:
// let x = 1
// let y = 2
// let z = 3
```

## Efficient Code Navigation

### The Jump List

VS Code maintains a jump list of your navigation history:

```
Ctrl+o      # Jump to older position (back)
Ctrl+i      # Jump to newer position (forward)
```

**Example workflow:**
```
1. Working in file A
2. gd to file B        # Jump to definition
3. gd to file C        # Jump again
4. Ctrl+o              # Back to file B
5. Ctrl+o              # Back to file A
6. Ctrl+i              # Forward to file B
```

**Pro tip:** This works across files. You can jump back through 20+ locations.

### LSP Navigation Patterns

Master the `g*` family of commands:

**The Definition Chain:**
```
1. K            # Read hover docs
2. gd           # Go to definition
3. gI           # Go to implementation
4. gr           # See all references
5. Ctrl+o       # Return home
```

**Type exploration:**
```
1. Position on type
2. gy           # Go to type definition
3. Read the type
4. Ctrl+o       # Back
```

**Finding usages:**
```
1. Position on function
2. gr           # Go to references
3. j/k          # Browse list
4. Enter        # Jump to usage
5. Ctrl+o       # Back to list
```

### Buffer Navigation Mastery

Efficient buffer (tab) switching:

**Methods ranked by speed:**

1. **Fastest: Alt-Tab style**
   ```
   Shift+H     # Previous buffer (instant)
   Shift+L     # Next buffer (instant)
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

**Pro workflow:**
```
Working on 3 files:
- Use Shift+L/H to cycle
- Use <leader>` to toggle between main 2
- Use <leader>bb when you need a specific one
```

### Symbol Navigation

Jump to functions, classes, variables:

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

**Pro tip:** Use `@` prefix in Quick Open:
```
<leader>ff      # Quick Open
@               # Symbol mode
Type name       # Search symbols
```

## Advanced Editing Techniques

### Text Objects

Text objects are vim's superpower:

**Inner vs Outer:**
- `i` = inner (excludes delimiters)
- `a` = outer (includes delimiters)

**Common text objects:**
```
iw    # inner word
aw    # a word (with space)
iW    # inner WORD (includes punctuation)
aW    # a WORD

i"    # inner quotes
a"    # a quotes (includes ")
i(    # inner parentheses
a(    # a parentheses (includes ())
i{    # inner braces
a{    # a braces (includes {})
i[    # inner brackets
a[    # a brackets (includes [])

it    # inner tag (HTML/XML)
at    # a tag

ip    # inner paragraph
ap    # a paragraph

is    # inner sentence
as    # a sentence
```

**Practical examples:**

Delete inside quotes:
```
"hello world"
1. Position cursor anywhere in quotes
2. di"           # Delete inside "
Result: ""
```

Change function arguments:
```
myFunc(arg1, arg2, arg3)
1. Position inside ()
2. ci(           # Change inside (
3. Type new args
Result: myFunc(newArgs)
```

Select HTML content:
```
<div>content</div>
1. Position in tag
2. vit          # Visual inner tag
Result: "content" selected
```

### Macros

Record and replay repetitive edits:

**Recording a macro:**
```
1. q{letter}    # Start recording (qa, qb, qc, etc.)
2. Perform edits
3. q            # Stop recording
```

**Playing a macro:**
```
@{letter}       # Play once
10@{letter}     # Play 10 times
@@              # Repeat last macro
```

**Real-world example - Adding semicolons:**
```
Before:
let x = 1
let y = 2
let z = 3

1. qa           # Start recording to 'a'
2. A;           # Append ;
3. Esc          # Normal mode
4. j            # Next line
5. q            # Stop recording
6. 2@a          # Repeat 2 more times

After:
let x = 1;
let y = 2;
let z = 3;
```

**Pro tip:** Save complex macros in your settings.json:
```json
"vim.normalModeKeyBindings": [
  {
    "before": ["<leader>", "m", "s"],
    "after": ["A", ";", "<Esc>", "j"]
  }
]
```

### Search and Replace

Master vim's search and replace:

**Basic substitution:**
```
:s/old/new/         # Current line, first occurrence
:s/old/new/g        # Current line, all occurrences
:%s/old/new/g       # All lines, all occurrences
:%s/old/new/gc      # All lines, with confirmation
```

**Visual selection replace:**
```
1. V            # Visual line mode
2. Select lines
3. :s/old/new/g
```

**Real-world examples:**

Rename variable in function:
```
1. Position on function
2. V             # Visual line
3. Select function
4. :s/oldName/newName/g
```

Add comments to multiple lines:
```
1. V             # Visual line
2. Select lines
3. :s/^/\/\/ /   # Add // at start
```

### Dot Command

The `.` command repeats your last change:

**Example - Deleting multiple words:**
```
1. daw          # Delete a word
2. .            # Repeat (delete next word)
3. .            # Repeat again
```

**Example - Adding text:**
```
1. A;           # Append semicolon
2. Esc          # Normal mode
3. j            # Next line
4. .            # Repeat append
```

**Pro tip:** Structure your edits to be repeatable with `.`

## Git Workflows

### GitLens Integration

VimCode integrates deeply with GitLens:

**Inline blame:**
```
<leader>gb      # Toggle blame
```
Now you see who wrote each line and when.

**File history:**
```
<leader>gl      # File history
j/k             # Browse commits
Enter           # View commit
```

**Branch history:**
```
<leader>gL      # Branch log
Browse commits
Enter           # View details
```

**Browse on remote:**
```
<leader>gB      # Open file on GitHub/GitLab
```
Instantly jump to the web version.

### Hunk Navigation

Navigate changes within a file:

```
[h              # Previous hunk
]h              # Next hunk
<leader>gd      # View diff
```

**Workflow for reviewing changes:**
```
1. <leader>gd   # Open diff
2. [h           # Jump to first hunk
3. Review change
4. ]h           # Next hunk
5. Repeat
```

### Git Status Workflow

Efficient source control management:

```
1. <leader>gg   # Git status
2. Click file   # View diff
3. Stage        # Prepare commit
4. Message      # Write commit
5. Commit       # Save changes
```

**Keyboard-only staging:**
```
1. <leader>gg   # Git status
2. Tab          # Focus file list
3. j/k          # Navigate files
4. Space        # Stage/unstage
5. Enter        # View diff
```

## Customization Tips

### Custom Keybindings

Add your own keybindings in `settings.json`:

**Example - Custom leader bindings:**
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

**Example - Remapping existing keys:**
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
"vim.statusBarColors.normal": "#519aba",      // Blue
"vim.statusBarColors.insert": "#98c379",      // Green
"vim.statusBarColors.visual": "#c678dd",      // Purple
"vim.statusBarColors.replace": "#e06c75",     // Red
"vim.statusBarColors.visualline": "#c678dd",  // Purple
"vim.statusBarColors.visualblock": "#c678dd", // Purple
```

**Pro tip:** Match your theme colors for consistency.

### Editor Appearance

**Font ligatures:**
```json
"editor.fontFamily": "'Fira Code', 'Cascadia Code', monospace",
"editor.fontLigatures": true,
"editor.fontSize": 14,
"editor.lineHeight": 22
```

**Cursor customization:**
```json
"editor.cursorBlinking": "solid",
"editor.cursorStyle": "block",
"editor.cursorSmoothCaretAnimation": "on"
```

**Minimap:**
```json
"editor.minimap.enabled": true,
"editor.minimap.renderCharacters": false,
"editor.minimap.showSlider": "mouseover"
```

### VS Code Profiles

Create a Vim-specific profile:

1. **Command Palette:** `Profiles: Create Profile`
2. **Name:** "Vim Mode"
3. **Select:** Settings, Keybindings, Extensions
4. **Done**

**Benefits:**
- Isolate Vim configuration
- Easily disable Vim mode
- Share profile with others
- Experiment without breaking main setup

## Performance Optimization

### Critical Settings

**Dedicated thread (prevents lag):**
```json
"extensions.experimental.affinity": {
  "vscodevim.vim": 1
}
```

**Disable animations:**
```json
"workbench.editor.enablePreview": false,
"editor.smoothScrolling": false
```

**Limit extensions:**
- Only enable extensions you actively use
- Use Profiles to manage extension sets
- Disable unused language servers

### Handle Keys Optimization

Fine-tune key handling in `settings.json`:

```json
"vim.handleKeys": {
  "<C-d>": true,     // Vim handles (page down)
  "<C-u>": true,     // Vim handles (page up)
  "<C-f>": false,    // VS Code handles (find)
  "<C-s>": false,    // VS Code handles (save)
  "<C-c>": false,    // VS Code handles (copy)
  "<C-v>": false,    // VS Code handles (paste)
  "<C-x>": false     // VS Code handles (cut)
}
```

**Rule of thumb:**
- Vim handles: navigation (`C-d`, `C-u`, `C-b`, `C-f`)
- VS Code handles: system commands (`C-s`, `C-c`, `C-v`)

### macOS Key Repeat

Essential for smooth Vim usage:

```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
defaults write com.cursor.Cursor ApplePressAndHoldEnabled -bool false
defaults write com.windsurf.app ApplePressAndHoldEnabled -bool false
```

**Restart required:** Log out and back in.

## Common Pitfalls and Solutions

### Leader Key Not Working

**Problem:** Pressing space moves cursor instead of triggering leader.

**Solutions:**
1. Check `"vim.leader": "<space>"` is set
2. Ensure leader bindings are in `settings.json`, NOT `keybindings.json`
3. Restart VS Code
4. Verify you're in Normal mode (not Insert)

### Typing Lag

**Problem:** Characters appear slowly when typing.

**Solutions:**
1. Add dedicated thread setting (see Performance)
2. Disable unused extensions
3. On macOS, enable key repeat
4. Close resource-heavy panels (terminal, output)

### Ctrl+h Not Working

**Problem:** `Ctrl+h` deletes instead of navigating left.

**Solution:** Add to `keybindings.json`:
```json
{
  "key": "ctrl+h",
  "command": "workbench.action.navigateLeft",
  "when": "vim.active && vim.mode != 'Insert'"
}
```

### Escape Key Too Far

**Problem:** Reaching for Esc is slow.

**Solutions:**
1. Use `jk` or `jj` (configured in VimCode)
2. Remap Caps Lock to Esc (OS level)
3. Add custom mapping:
   ```json
   "vim.insertModeKeyBindings": [
     {"before": ["k", "j"], "after": ["<Esc>"]}
   ]
   ```

### Clipboard Not Working

**Problem:** Yank doesn't copy to system clipboard.

**Solution:** Enable system clipboard:
```json
"vim.useSystemClipboard": true
```

**Alternative:** Use `"+y` (explicit register)

## Productivity Hacks

### One-Line Workflows

Master these single-command operations:

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

Fast inline edits:

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
X           # Delete character before
```

### Visual Selection Tricks

Efficient text selection:

```
viw         # Select inner word
vaw         # Select a word
vi"         # Select inside quotes
va"         # Select with quotes
vip         # Select paragraph
vap         # Select paragraph with blank line
gv          # Reselect last selection
o           # Toggle cursor position in Visual mode
```

### Quick Navigation

Move faster within file:

```
gg          # Top of file
G           # Bottom of file
50G         # Line 50
%           # Matching bracket
{           # Previous paragraph
}           # Next paragraph
(           # Previous sentence
)           # Next sentence
H           # Top of screen
M           # Middle of screen
L           # Bottom of screen
```

### Marks

Set bookmarks in your code:

**Setting marks:**
```
m{a-z}      # Set local mark (file)
m{A-Z}      # Set global mark (across files)
```

**Jumping to marks:**
```
'{mark}     # Jump to line of mark
`{mark}     # Jump to exact position of mark
''          # Jump to previous location
```

**Example workflow:**
```
1. ma          # Mark position as 'a'
2. Navigate away
3. 'a          # Return to mark
```

**Pro tip:** Use `mM` (capital) to mark important spots across files.

## Keyboard-First Development

### Eliminate Mouse Usage

**Challenge:** Work for 1 hour without touching the mouse.

**Key principles:**
1. **File navigation:** `<leader>ff`, `<leader>e`
2. **Code navigation:** `gd`, `gr`, `K`
3. **Editing:** `ci(`, `di"`, `ysiw"`
4. **Git:** `<leader>gg`, `[h`, `]h`
5. **Terminal:** `Ctrl+/`, type commands
6. **Search:** `<leader>sg`, `[q`, `]q`

### The 10-Minute Rule

If you're about to reach for the mouse, ask:
- "Is there a keybinding for this?"
- "Can I get there with `gd` or `gr`?"
- "Should I set a custom keybinding?"

**Invest time in keybindings now, save hours later.**

### Speed Drills

Practice these daily:

**Drill 1: File navigation (2 min)**
```
<leader>ff → open file → edit → <leader>bd → repeat 10x
```

**Drill 2: Symbol navigation (2 min)**
```
gd → gr → Ctrl+o → Ctrl+o → repeat 10x
```

**Drill 3: Text objects (2 min)**
```
ci( → ci" → ci{ → daw → repeat 10x
```

**Goal:** Muscle memory. Don't think, just type.

### Customization Workflow

When you find yourself doing the same sequence repeatedly:

1. **Identify:** "I keep doing X, Y, Z"
2. **Check:** "Is there a keybinding?"
3. **Create:** Add custom binding
4. **Practice:** Use it 10 times
5. **Refine:** Adjust if needed

**Example:**
```
Repetitive task: Save → Format → Close
Custom binding: <leader>wq (write and quit)
```

## Advanced Tips

### Folding

Collapse code sections:

```
zo          # Open fold
zc          # Close fold
za          # Toggle fold
zR          # Open all folds
zM          # Close all folds
```

**Workflow:**
```
1. zM       # Close all folds
2. See file structure
3. zr       # Open fold levels incrementally
```

### Multiple Cursors

Create multiple cursors:

```
<leader>a   # Select all occurrences (Visual mode)
Ctrl+d      # Add next occurrence (VS Code)
gb          # Add next occurrence (Vim)
```

**Workflow:**
```
1. viw          # Select word
2. <leader>a    # Select all
3. c            # Change all
4. Type         # Edit simultaneously
5. Esc          # Exit
```

### Quick Fix Menu

Leverage VS Code's quick fix:

```
<leader>ca      # Code action menu
j/k             # Navigate options
Enter           # Apply fix
```

**Common actions:**
- Import missing modules
- Implement interface
- Extract to function
- Add type annotations

---

**Next Steps:**
- **Practice:** Choose 3 workflows and use them daily for a week
- **Customize:** Add personal keybindings for your most common tasks
- **Share:** Teach these tricks to teammates

**See also:**
- [KEYBINDINGS.md](KEYBINDINGS.md) - Complete shortcuts reference
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Common issues
- [SETUP.md](SETUP.md) - Configuration details
