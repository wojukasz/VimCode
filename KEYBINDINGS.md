# VimCode Keybindings Reference

Complete shortcuts guide and cheat sheet for VimCode - LazyVim-style keybindings for VS Code.

**Leader key:** `<space>`

## Quick Reference Card

### Most Essential Keybindings

```
┌─────────────────────────────────────────────────────────────┐
│  FILE          │  SEARCH        │  CODE                     │
├─────────────────────────────────────────────────────────────┤
│  <leader>ff    │  <leader>/     │  <leader>ca  Code action  │
│  Find files    │  Search files  │  <leader>cf  Format       │
│                │                │  <leader>cr  Rename       │
│  <leader>fr    │  <leader>sg    │  gd          Definition   │
│  Recent files  │  Grep search   │  gr          References   │
│                │                │  K           Hover        │
│  <leader>e     │  <leader>ss    │                           │
│  Toggle sidebar│  Doc symbols   │                           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  NAVIGATION    │  BUFFERS       │  GIT                      │
├─────────────────────────────────────────────────────────────┤
│  Ctrl+h/j/k/l  │  Shift+H       │  <leader>gg  Git status   │
│  Split nav     │  Prev buffer   │  <leader>gb  Git blame    │
│                │                │  <leader>gd  Git diff     │
│  [d  ]d        │  Shift+L       │  [h  ]h      Hunk nav     │
│  Diagnostic    │  Next buffer   │                           │
│                │                │                           │
│  [e  ]e        │  <leader>bd    │                           │
│  Error nav     │  Close buffer  │                           │
└─────────────────────────────────────────────────────────────┘
```

## Table of Contents

- [By Workflow](#by-workflow)
  - [File Navigation Workflow](#file-navigation-workflow)
  - [Code Editing Workflow](#code-editing-workflow)
  - [Search and Replace Workflow](#search-and-replace-workflow)
  - [Git Workflow](#git-workflow)
  - [Debugging Workflow](#debugging-workflow)
- [By Prefix (LazyVim Convention)](#by-prefix-lazyvim-convention)
  - [File Operations - `<leader>f*`](#file-operations---leaderf)
  - [Search Operations - `<leader>s*`](#search-operations---leaders)
  - [Code Actions - `<leader>c*`](#code-actions---leaderc)
  - [Buffer Management - `<leader>b*`](#buffer-management---leaderb)
  - [Git Operations - `<leader>g*`](#git-operations---leaderg)
  - [Window Management - `<leader>w*`](#window-management---leaderw)
  - [Diagnostics - `<leader>x*` and `[]`](#diagnostics---leaderx-and-)
  - [UI Toggles - `<leader>u*`](#ui-toggles---leaderu)
- [By Context](#by-context)
  - [LSP Navigation - `g*`](#lsp-navigation---g)
  - [Insert Mode](#insert-mode)
  - [Visual Mode](#visual-mode)
  - [Explorer Navigation](#explorer-navigation)
  - [Terminal Operations](#terminal-operations)
- [Vim Plugins](#vim-plugins)
- [Comparison with Standard VS Code](#comparison-with-standard-vs-code)

## By Workflow

### File Navigation Workflow

**Opening files:**
```
<leader>ff  → Find files (Quick Open)
<leader>fr  → Recent files
<leader>e   → Toggle file explorer
<leader>fe  → Reveal current file in explorer
```

**Switching between files:**
```
Shift+H     → Previous buffer (tab)
Shift+L     → Next buffer (tab)
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

**Example workflow - Opening and navigating files:**
```
1. <leader>ff          # Open file picker
2. Type filename       # Search
3. Enter               # Open
4. Shift+L             # Switch to next tab
5. Shift+H             # Back to previous
6. <leader>bd          # Close when done
```

### Code Editing Workflow

**Navigating code:**
```
gd          → Go to definition
gD          → Go to declaration
gr          → Go to references
gI          → Go to implementation
gy          → Go to type definition
K           → Show hover documentation
gK          → Show signature help
Ctrl+o      → Navigate back
Ctrl+i      → Navigate forward
```

**Code actions:**
```
<leader>ca  → Code action (quick fix)
<leader>cA  → Source action
<leader>cf  → Format document
<leader>cF  → Format selection
<leader>cr  → Rename symbol
<leader>co  → Organize imports
```

**Diagnostics:**
```
[d          → Previous diagnostic
]d          → Next diagnostic
[e          → Previous error
]e          → Next error
<leader>xx  → Open problems panel
<leader>cd  → Show line diagnostics
```

**Example workflow - Refactoring:**
```
1. gd               # Jump to definition
2. <leader>cr       # Rename symbol
3. Type new name    # Enter new name
4. Enter            # Apply rename
5. <leader>cf       # Format document
6. Ctrl+o           # Return to original location
```

### Search and Replace Workflow

**Searching:**
```
<leader>/   → Search in workspace
<leader>sg  → Grep in files
<leader>sw  → Search word under cursor
<leader>ss  → Document symbols
<leader>sS  → Workspace symbols
```

**Search navigation:**
```
[q          → Previous search result
]q          → Next search result
<leader>ur  → Clear search highlight
```

**Replacing:**
```
<leader>sr  → Search and replace
```

**Example workflow - Find and replace:**
```
1. <leader>sw       # Search word under cursor
2. Review results   # Navigate with j/k
3. <leader>sr       # Open search & replace
4. Type replacement # Enter replacement text
5. Review changes   # Check each occurrence
6. Apply            # Confirm replacement
```

### Git Workflow

**Viewing changes:**
```
<leader>gg  → Git status (Source Control)
<leader>gs  → Git status (alt)
<leader>gd  → Git diff (current file)
<leader>gb  → Toggle Git blame
<leader>gB  → Browse file on remote (GitHub/GitLab)
```

**Git history:**
```
<leader>gl  → Git log (file history)
<leader>gL  → Git log (branch log)
<leader>gc  → Show commit details
```

**Hunk navigation:**
```
[h          → Previous Git hunk
]h          → Next Git hunk
```

**Example workflow - Review and commit:**
```
1. <leader>gg       # Open Source Control
2. Review changes   # Check modified files
3. <leader>gd       # View diff
4. <leader>gb       # Toggle blame
5. [h / ]h          # Navigate hunks
6. Stage & commit   # In Source Control panel
```

### Debugging Workflow

**Problems and diagnostics:**
```
<leader>xx  → Open problems panel
<leader>xX  → Workspace diagnostics
[d          → Previous diagnostic (all files)
]d          → Next diagnostic (all files)
[e          → Previous error (current file)
]e          → Next error (current file)
```

**Code inspection:**
```
K           → Show hover (type info, docs)
gK          → Show signature help
<leader>cd  → Line diagnostics
<leader>ca  → Quick fix
```

**Example workflow - Fixing errors:**
```
1. <leader>xx       # Open problems panel
2. Review errors    # See all issues
3. ]e               # Jump to first error
4. K                # Check error details
5. <leader>ca       # Apply quick fix
6. ]e               # Next error
7. Repeat 4-6       # Fix all errors
```

## By Prefix (LazyVim Convention)

### File Operations - `<leader>f*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader><space>` | Find files (Quick Open) | Same as `<leader>ff` |
| `<leader>,` | Switch buffer | Quick switcher |
| `<leader>/` | Search in files | Workspace search |
| `<leader>ff` | Find files | Quick Open picker |
| `<leader>fr` | Recent files | Recently opened |
| `<leader>fn` | New file | Create new file |
| `<leader>fb` | Show buffers | List open files |
| `<leader>fe` | Reveal in explorer | Show current file |
| `<leader>ft` | Toggle terminal | Show/hide terminal |
| `<leader>e` | Toggle sidebar | Primary/Activity Bar |
| `<leader>E` | Focus explorer | Jump to file tree |

### Search Operations - `<leader>s*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader>sg` | Search/grep in files | Full text search |
| `<leader>sw` | Search word under cursor | Quick search |
| `<leader>sr` | Search & replace | Find and replace |
| `<leader>ss` | Goto symbol (document) | Current file symbols |
| `<leader>sS` | Goto symbol (workspace) | All files symbols |
| `<leader>sk` | Search keybindings | Keyboard shortcuts |
| `<leader>sc` | Command palette | All commands |
| `<leader>sh` | Search help | All commands (alt) |

### Code Actions - `<leader>c*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader>ca` | Code action (quick fix) | Suggestions, refactors |
| `<leader>cA` | Source action | File-level actions |
| `<leader>cf` | Format document | Run formatter |
| `<leader>cF` | Format selection | Format selected code |
| `<leader>cr` | Rename symbol | Refactor rename |
| `<leader>cd` | Line diagnostics | Hover with errors |
| `<leader>cl` | Open problems panel | Same as `<leader>xx` |
| `<leader>co` | Organize imports | Sort and remove unused |

### Buffer Management - `<leader>b*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader>bb` | Switch buffer | Quick switcher |
| `<leader>bd` | Delete buffer (close) | Close current file |
| `<leader>bD` | Delete other buffers | Close all except current |
| `<leader>bo` | Close other editors | In current group |
| `<leader>bp` | Pin buffer | Keep tab open |
| `<leader>bP` | Unpin buffer | Allow auto-close |
| `<leader>`` | Last buffer (alternate) | Toggle between 2 files |
| `Shift+H` | Previous buffer | Tab navigation |
| `Shift+L` | Next buffer | Tab navigation |
| `[b` | Previous buffer (alt) | Alternative binding |
| `]b` | Next buffer (alt) | Alternative binding |

### Git Operations - `<leader>g*`

| Keybinding | Action | Extension |
|------------|--------|-----------|
| `<leader>gg` | Git status | Native |
| `<leader>gs` | Git status (alt) | Native |
| `<leader>gb` | Toggle Git blame | GitLens |
| `<leader>gB` | Browse on remote | GitLens |
| `<leader>gd` | Git diff | Native |
| `<leader>gl` | Git log (file) | GitLens |
| `<leader>gL` | Git log (branch) | GitLens |
| `<leader>gc` | Show commit | GitLens |
| `[h` | Previous hunk | Native |
| `]h` | Next hunk | Native |

**Note:** Git operations marked "GitLens" require the GitLens extension.

### Window Management - `<leader>w*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader>wd` | Close window/split | Close editor group |
| `<leader>ww` | Switch window | Focus next group |
| `<leader>wm` | Maximize window | Toggle maximize |
| `<leader>-` | Split below | Horizontal split |
| `<leader>\|` | Split right | Vertical split |
| `Ctrl+h` | Focus left split | Window navigation |
| `Ctrl+j` | Focus below split | Window navigation |
| `Ctrl+k` | Focus above split | Window navigation |
| `Ctrl+l` | Focus right split | Window navigation |
| `Ctrl+←→↑↓` | Resize splits | Adjust split size |
| `Ctrl+1/2/3` | Focus editor group | Direct group focus |

### Diagnostics - `<leader>x*` and `[]`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<leader>xx` | Open problems panel | Show all diagnostics |
| `<leader>xX` | Workspace diagnostics | All files |
| `[d` | Previous diagnostic | All files |
| `]d` | Next diagnostic | All files |
| `[e` | Previous error | Current file only |
| `]e` | Next error | Current file only |
| `[q` | Previous search result | Search navigation |
| `]q` | Next search result | Search navigation |

### UI Toggles - `<leader>u*`

| Keybinding | Action | Extension |
|------------|--------|-----------|
| `<leader>uw` | Toggle word wrap | Native |
| `<leader>uz` | Toggle zen mode | Native |
| `<leader>ur` | Clear search highlight | Native |
| `<leader>ul` | Toggle line numbers | Settings Cycler |
| `<leader>uL` | Toggle relative numbers | Settings Cycler |

**Note:** Line number toggles require the Settings Cycler extension.

## By Context

### LSP Navigation - `g*`

| Keybinding | Action | Notes |
|------------|--------|-------|
| `gd` | Go to definition | Jump to source |
| `gD` | Go to declaration | Jump to header/interface |
| `gr` | Go to references | Show all uses |
| `gI` | Go to implementation | Jump to impl |
| `gy` | Go to type definition | Type source |
| `gK` | Signature help | Function params |
| `K` | Show hover | Docs and type info |
| `Ctrl+o` | Navigate back | After jumping |
| `Ctrl+i` | Navigate forward | Redo navigation |

**LSP Navigation Pattern:**
```
1. Hover with K          # Inspect
2. Jump with gd          # Definition
3. Explore with gr       # References
4. Return with Ctrl+o    # Go back
```

### Insert Mode

| Keybinding | Action | Notes |
|------------|--------|-------|
| `jk` | Exit to Normal mode | Alternative to Esc |
| `jj` | Exit to Normal mode | Alternative to Esc |
| `Ctrl+j` | Next suggestion | Autocomplete |
| `Ctrl+k` | Previous suggestion | Autocomplete |
| `Ctrl+s` | Save file | Standard VS Code |

**Tips:**
- Use `jk` or `jj` instead of reaching for Esc
- `Ctrl+j/k` works in suggestion widgets for Vim-style navigation

### Visual Mode

| Keybinding | Action | Notes |
|------------|--------|-------|
| `<` | Indent left & reselect | Stay in Visual |
| `>` | Indent right & reselect | Stay in Visual |
| `gc` | Toggle comment | Comment lines |
| `<leader>a` | Select all occurrences | Multi-cursor |
| `<leader>ss` | Sort lines (ascending) | Line sorting |
| `<leader>u` | Transform to UPPERCASE | Text transform |
| `<leader>l` | Transform to lowercase | Text transform |

**Visual Mode Workflows:**
```
Indenting:      vip >>>>> (select paragraph, indent 4 times)
Commenting:     V3j gc    (select 3 lines, toggle comment)
Multi-cursor:   viw <leader>a  (select word, select all)
```

### Explorer Navigation

| Keybinding | Action | Context |
|------------|--------|---------|
| `j` | Down | File explorer |
| `k` | Up | File explorer |
| `h` | Collapse folder | File explorer |
| `l` | Expand folder | File explorer |
| `Enter` | Open file | File explorer |
| `Ctrl+Enter` | Rename | File explorer |
| `Ctrl+Shift+1` | Open in left split | File explorer |
| `Ctrl+Shift+2` | Open in right split | File explorer |

**Explorer Workflow:**
```
1. <leader>e        # Toggle explorer
2. j/k              # Navigate files
3. l                # Expand folder
4. h                # Collapse folder
5. Enter            # Open file
6. <leader>e        # Close explorer
```

### Terminal Operations

| Keybinding | Action | Notes |
|------------|--------|-------|
| `Ctrl+/` | Toggle terminal | Show/hide |
| `<leader>ft` | Toggle terminal | Alternative |
| `Ctrl+;` | Focus terminal | Switch focus |
| `Ctrl+Shift+;` | Maximize terminal | Toggle max |

**Terminal Tips:**
- `Ctrl+/` - Quick terminal toggle from anywhere
- `Ctrl+;` - Jump between editor and terminal
- In terminal: Type `exit` or Ctrl+D to close

## Vim Plugins

VimCode enables several Vim plugins for enhanced functionality:

### EasyMotion

Fast cursor movement to visible text.

| Keybinding | Action |
|------------|--------|
| `<leader><leader>w` | Jump to word (forward) |
| `<leader><leader>b` | Jump to word (backward) |
| `<leader><leader>s{char}` | Jump to character |
| `<leader><leader>j` | Jump to line (down) |
| `<leader><leader>k` | Jump to line (up) |

**Usage:**
```
1. <leader><leader>w    # Activate EasyMotion
2. Letters appear       # On each word
3. Type letter          # Jump to word
```

### Sneak

Two-character search for quick navigation.

| Keybinding | Action |
|------------|--------|
| `s{char}{char}` | Sneak forward |
| `S{char}{char}` | Sneak backward |
| `;` | Next occurrence |
| `,` | Previous occurrence |

**Usage:**
```
1. s th             # Type 's' then 'th'
2. Cursor jumps     # To first 'th'
3. ;                # Next 'th'
4. ,                # Previous 'th'
```

### Surround

Manipulate surrounding characters (quotes, brackets, tags).

| Keybinding | Action | Example |
|------------|--------|---------|
| `ysiw"` | Surround word with " | `word` → `"word"` |
| `yss"` | Surround line with " | `text` → `"text"` |
| `cs"'` | Change " to ' | `"word"` → `'word'` |
| `ds"` | Delete surrounding " | `"word"` → `word` |
| `ySiw{` | Surround with { } (spaced) | `word` → `{ word }` |

**Common patterns:**
```
ysiw"      # Surround word with quotes
ysiw(      # Surround word with parentheses
cs"'       # Change quotes to apostrophes
ds"        # Remove quotes
```

### Highlighted Yank

Visual feedback when yanking (copying) text.

**Settings:**
```json
"vim.highlightedyank.enable": true,
"vim.highlightedyank.duration": 200
```

When you yank text (`y` in Visual mode or `yy` for line), it briefly highlights yellow.

## Comparison with Standard VS Code

### Opening Files

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Quick Open | `<leader>ff` | `Ctrl+P` |
| Recent files | `<leader>fr` | `Ctrl+R` |
| File explorer | `<leader>e` | `Ctrl+Shift+E` |

### Search

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Find in files | `<leader>/` | `Ctrl+Shift+F` |
| Symbol search | `<leader>ss` | `Ctrl+Shift+O` |
| Command palette | `<leader>sc` | `Ctrl+Shift+P` |

### Code Navigation

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Go to definition | `gd` | `F12` |
| Go to references | `gr` | `Shift+F12` |
| Rename | `<leader>cr` | `F2` |
| Format | `<leader>cf` | `Shift+Alt+F` |

### Window Management

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Split vertically | `<leader>\|` | `Ctrl+\` |
| Split horizontally | `<leader>-` | (not default) |
| Focus left split | `Ctrl+h` | `Ctrl+1` |
| Focus right split | `Ctrl+l` | `Ctrl+2` |

**Key advantage:** VimCode uses Vim's `hjkl` for intuitive split navigation.

### Buffer Management

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Next tab | `Shift+L` | `Ctrl+Tab` |
| Previous tab | `Shift+H` | `Ctrl+Shift+Tab` |
| Close tab | `<leader>bd` | `Ctrl+W` |

**Key advantage:** VimCode bindings are easier to reach and more mnemonic.

## Tips for Learning

### Start with These 10 Keybindings

1. `<leader>ff` - Find files
2. `<leader>e` - Toggle sidebar
3. `gd` - Go to definition
4. `<leader>ca` - Code action
5. `Shift+H/L` - Switch buffers
6. `Ctrl+h/j/k/l` - Navigate splits
7. `[d / ]d` - Navigate diagnostics
8. `<leader>gg` - Git status
9. `K` - Show hover
10. `jk` - Exit insert mode

### Memory Aids

**Mnemonic patterns:**
- `f` = **F**ile operations
- `s` = **S**earch operations
- `c` = **C**ode actions
- `b` = **B**uffer management
- `g` = **G**it operations
- `w` = **W**indow management
- `x` = Diagnostics (like e**X**amining errors)
- `u` = **U**I toggles

**Vim conventions:**
- `[` / `]` = Navigate backwards/forwards
- `g*` = LSP **g**oto operations
- `K` = Knowledge (hover documentation)
- `Ctrl+o/i` = Jump **O**lder/**I**nner (back/forward)

### Practice Workflows

**File navigation:**
```
<leader>ff → type filename → Enter → edit → <leader>bd
```

**Code refactoring:**
```
gd → <leader>cr → new name → <leader>cf → Ctrl+o
```

**Git review:**
```
<leader>gg → review → <leader>gd → [h/]h → <leader>gb
```

### Printable Cheat Sheet

```
╔═══════════════════════════════════════════════════════════╗
║                    VIMCODE CHEAT SHEET                    ║
╠═══════════════════════════════════════════════════════════╣
║ LEADER: <space>                                           ║
╠═══════════════════════════════════════════════════════════╣
║ FILES              SEARCH             CODE                ║
║ <ld>ff  Find       <ld>/   Search     <ld>ca  Action      ║
║ <ld>fr  Recent     <ld>sg  Grep       <ld>cf  Format      ║
║ <ld>e   Sidebar    <ld>ss  Symbols    <ld>cr  Rename      ║
╠═══════════════════════════════════════════════════════════╣
║ LSP                BUFFERS            GIT                 ║
║ gd  Definition     H       Prev       <ld>gg  Status      ║
║ gr  References     L       Next       <ld>gb  Blame       ║
║ K   Hover          <ld>bd  Close      <ld>gd  Diff        ║
╠═══════════════════════════════════════════════════════════╣
║ NAVIGATION         DIAGNOSTICS        WINDOWS             ║
║ ^h/j/k/l  Splits   [d  Prev           <ld>-   Split H     ║
║ ^o/^i     Back/Fwd ]d  Next           <ld>|   Split V     ║
║ [b/]b     Buffers  [e  Prev err       <ld>wd  Close       ║
╚═══════════════════════════════════════════════════════════╝
Note: <ld> = <leader> = <space>  |  ^ = Ctrl
```

---

**Need Help?** See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for common keybinding issues.

**Learn Workflows:** Read [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) for advanced usage patterns.
