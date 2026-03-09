# Keybindings

**Leader key:** `<space>` | **Which-key trigger:** `<Tab>`

## How the Three Layers Work

VimCode stacks three layers of keybindings on top of each other. Understanding this helps debug any binding that doesn't behave as expected.

```
Layer 3 — which-key (VSpaceCode.whichkey)
  Trigger:  ~ in Normal/Visual mode → whichkey.show
  Owns:     the popup menu tree (whichkey.bindings in settings.json)
  Fallback: if which-key is not installed, ~ is a no-op and
            the Layer 2 vim bindings handle everything directly

  NOTE: <space> would be the LazyVim-matching trigger but conflicts
        with vim.leader = "<space>" — the leader intercepts <space>
        before which-key can fire. ~ is used as the reliable workaround.

Layer 2 — Custom LazyVim mappings
  Leader:   settings.json → vim.normalModeKeyBindingsNonRecursive
            (first match wins; ~ → whichkey.show is entry #1)
  Modifiers: keybindings.json — Ctrl/Alt/Shift bindings
             (last definition wins for equal when-clause specificity;
              user keybindings.json always beats VSCodeVim's handlers)
  Escape:   vim.handleKeys — explicitly releases certain Ctrl keys
            back to VS Code (e.g. <C-f>, <C-w>, <C-s>)

Layer 1 — VSCodeVim defaults (vscodevim.vim)
  Core Vim: h j k l, w b e, gg G, / ? * #, etc.
  Ctrl keys intercepted by default (vim.useCtrlKeys=true):
    C-d C-u (half-page scroll — kept in vim.handleKeys)
    C-o C-i (jump list — kept)
    C-r     (redo — kept)
    C-n C-p (autocomplete in Insert — kept)
    C-f C-b C-h C-j C-k C-l C-w C-s C-a C-c C-v C-z
            (all released to VS Code via vim.handleKeys: false)
  Plugins:  EasyMotion (<leader><leader>*) — re-exposed as <leader>j*
            Sneak (s/S forward/backward, ; next, , prev)
            Surround (ys / ds / cs)
```

**Key resolution rule:** if a binding isn't firing, check whether a higher-priority layer is consuming it first. User `keybindings.json` always beats VSCodeVim's type handler for the same key+when combination.

---

## Quick Reference Card

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

---

## Leader Bindings

### File Operations — `<leader>f*`

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

### Search Operations — `<leader>s*`

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

### Code Actions — `<leader>c*`

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

### Buffer Management — `<leader>b*`

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

### Git Operations — `<leader>g*`

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

> **Note:** Git operations marked "GitLens" require the GitLens extension.

### Window Management — `<leader>w*`

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

### Diagnostics — `<leader>x*` and `[]`

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

### UI Toggles — `<leader>u*`

| Keybinding | Action | Extension |
|------------|--------|-----------|
| `<leader>uw` | Toggle word wrap | Native |
| `<leader>uz` | Toggle zen mode | Native |
| `<leader>ur` | Clear search highlight | Native |
| `<leader>ul` | Toggle line numbers | Settings Cycler |
| `<leader>uL` | Toggle relative numbers | Settings Cycler |

> **Note:** Line number toggles require the Settings Cycler extension.

---

## By Context

### LSP Navigation — `g*`

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

### Insert Mode

| Keybinding | Action | Notes |
|------------|--------|-------|
| `jk` | Exit to Normal mode | Alternative to Esc |
| `jj` | Exit to Normal mode | Alternative to Esc |
| `Ctrl+n` | Next suggestion | Autocomplete (vim default) |
| `Ctrl+p` | Previous suggestion | Autocomplete (vim default) |
| `Ctrl+j` | Next suggestion | Autocomplete (when widget visible) |
| `Ctrl+k` | Previous suggestion | Autocomplete (when widget visible) |
| `Ctrl+s` | Save file | Standard VS Code |

> **Note:** `Ctrl+d/u` for paging through suggestions is not available — `vim.handleKeys` keeps those keys for half-page scrolling and they cannot be conditionally released. Use `Ctrl+n/p` as a reliable fallback.

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

### Terminal Operations

| Keybinding | Action | Notes |
|------------|--------|-------|
| `Ctrl+/` | Toggle terminal | Show/hide |
| `<leader>ft` | Toggle terminal | Alternative |
| `Ctrl+;` | Focus terminal | Switch focus |
| `Ctrl+Shift+;` | Maximize terminal | Toggle max |

---

## Vim Plugins

### EasyMotion

Fast cursor movement to visible text. Use `<leader>j*` — the `<leader>j` group in which-key:

| Keybinding | Action |
|------------|--------|
| `<leader>jw` | Jump to word (forward) |
| `<leader>jb` | Jump to word (backward) |
| `<leader>js{char}` | Jump to character |
| `<leader>jj` | Jump to line (down) |
| `<leader>jk` | Jump to line (up) |

The native `<leader><leader>*` form still works when which-key is **not** installed. When which-key is active, use `<leader>j*` instead — `~` now triggers the which-key menu, so `<space>` remains clean as the leader key.

### Sneak

Two-character search for quick navigation.

| Keybinding | Action |
|------------|--------|
| `s{char}{char}` | Sneak forward |
| `S{char}{char}` | Sneak backward |
| `;` | Next occurrence |
| `,` | Previous occurrence |

> **Note:** The which-key menu also has `,` bound to "Switch Buffer" (`<space>,`). These do not conflict — Sneak's `,` fires when you press `,` directly in Normal mode; which-key's `,` only fires when the which-key menu is already open (i.e. after pressing `<space>`). They are entirely separate key sequences.

### Surround

Manipulate surrounding characters (quotes, brackets, tags).

| Keybinding | Action | Example |
|------------|--------|---------|
| `ysiw"` | Surround word with " | `word` → `"word"` |
| `yss"` | Surround line with " | `text` → `"text"` |
| `cs"'` | Change " to ' | `"word"` → `'word'` |
| `ds"` | Delete surrounding " | `"word"` → `word` |
| `ySiw{` | Surround with { } (spaced) | `word` → `{ word }` |

### Highlighted Yank

Visual feedback when yanking (copying) text. When you yank text (`y` in Visual mode or `yy` for line), it briefly highlights yellow.

```json
"vim.highlightedyank.enable": true,
"vim.highlightedyank.duration": 200
```

---

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

### Buffer Management

| Action | VimCode | Standard VS Code |
|--------|---------|------------------|
| Next tab | `Shift+L` | `Ctrl+Tab` |
| Previous tab | `Shift+H` | `Ctrl+Shift+Tab` |
| Close tab | `<leader>bd` | `Ctrl+W` |

---

See [TIPS_AND_TRICKS.md](TIPS_AND_TRICKS.md) for workflow examples and learning sequences.
