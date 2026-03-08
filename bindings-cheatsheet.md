# VSCode Vim / Which Key — Bindings Cheatsheet

> **Leader key:** `<space>`
> Requires [vscodevim.vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim) and [VSpaceCode.whichkey](https://marketplace.visualstudio.com/items?itemName=VSpaceCode.whichkey).
> Git commands additionally require [eamodio.gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens).

---

## Top-level `<space>`

| Key | Action | Command |
|-----|--------|---------|
| `<space>` | Show Which-Key menu | `whichkey.show` |
| `<space><space>` | *(intentionally unbound — closes menu; use `<space>ff` for Find Files)* | — |
| `<space>,` | Switch Buffer | `workbench.action.showAllEditors` |
| `<space>/` | Search in Files | `workbench.action.findInFiles` |
| `` <space>` `` | Last Buffer (alternate file) | `workbench.action.quickOpenPreviousRecentlyUsedEditorInGroup` |
| `<space>-` | Split Below | `workbench.action.splitEditorDown` |
| `<space>\|` | Split Right | `workbench.action.splitEditorRight` |
| `<space>d` | Delete Line (`dd`) | vim `dd` |
| `<space>e` | Toggle Sidebar | `workbench.action.toggleSidebarVisibility` |
| `<space>E` | Focus Explorer | `workbench.files.action.focusFilesExplorer` |
| `<space>K` | Show Hover Docs | `editor.action.showHover` |

---

## File `<space>f`

| Key | Action | Command |
|-----|--------|---------|
| `<space>ff` | Find Files | `workbench.action.quickOpen` |
| `<space>fr` | Recent Files | `workbench.action.openRecent` |
| `<space>fn` | New File | `workbench.action.files.newUntitledFile` |
| `<space>fb` | Buffers (open editors) | `workbench.action.showAllEditors` |
| `<space>fe` | Show Active File in Explorer | `workbench.files.action.showActiveFileInExplorer` |
| `<space>ft` | Toggle Terminal | `workbench.action.terminal.toggleTerminal` |

---

## Search `<space>s`

| Key | Action | Command |
|-----|--------|---------|
| `<space>sg` | Grep in Files | `workbench.action.findInFiles` |
| `<space>sw` | Search Word Under Cursor | `workbench.action.findInFiles` |
| `<space>sr` | Replace in Files | `workbench.action.replaceInFiles` |
| `<space>ss` | Symbol in File | `workbench.action.gotoSymbol` |
| `<space>sS` | Symbol in Workspace | `workbench.action.showAllSymbols` |
| `<space>sk` | Keymaps (keyboard shortcuts) | `workbench.action.openGlobalKeybindings` |
| `<space>sc` | Command Palette | `workbench.action.showCommands` |
| `<space>sh` | Help / All Commands | `workbench.action.showAllCommands` |

---

## Code (LSP) `<space>c`

| Key | Action | Command |
|-----|--------|---------|
| `<space>ca` | Code Action (Quick Fix) | `editor.action.quickFix` |
| `<space>cA` | Source Action | `editor.action.sourceAction` |
| `<space>cf` | Format Document | `editor.action.formatDocument` |
| `<space>cF` | Format Selection | `editor.action.formatSelection` |
| `<space>cr` | Rename Symbol | `editor.action.rename` |
| `<space>cd` | Line Diagnostics (hover) | `editor.action.showHover` |
| `<space>cl` | Problems Panel | `workbench.action.problems.focus` |
| `<space>co` | Organise Imports | `editor.action.organizeImports` |

---

## Buffer `<space>b`

| Key | Action | Command |
|-----|--------|---------|
| `<space>bb` | Switch Buffer | `workbench.action.showAllEditors` |
| `<space>bd` | Close Buffer | `workbench.action.closeActiveEditor` |
| `<space>bD` | Close Other Buffers | `workbench.action.closeOtherEditors` |
| `<space>bo` | Close Others (alias for `bD`) | `workbench.action.closeOtherEditors` |
| `<space>bp` | Pin Buffer | `workbench.action.pinEditor` |
| `<space>bP` | Unpin Buffer | `workbench.action.unpinEditor` |
| `<S-h>` | Prev Buffer *(keybindings.json)* | `workbench.action.previousEditor` |
| `<S-l>` | Next Buffer *(keybindings.json)* | `workbench.action.nextEditor` |

---

## Git `<space>g`

> Most commands require [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens).

| Key | Action | Command |
|-----|--------|---------|
| `<space>gg` | Git Status (Source Control) | `workbench.view.scm` |
| `<space>gs` | Git Status (alias for `gg`) | `workbench.view.scm` |
| `<space>gb` | Blame Toggle | `gitlens.toggleFileBlame` |
| `<space>gB` | Browse on Remote | `gitlens.openFileOnRemote` |
| `<space>gd` | Git Diff | `git.openChange` |
| `<space>gl` | File History | `gitlens.showQuickFileHistory` |
| `<space>gL` | Branch History | `gitlens.showQuickRepoHistory` |
| `<space>gc` | Commit Details | `gitlens.showQuickCommitDetails` |

---

## Jump / EasyMotion `<space>j`

> Requires `vim.easymotion: true` (already enabled). These wrap EasyMotion's native `<leader><leader>*` trigger.

| Key | Action | Command |
|-----|--------|---------|
| `<space>jw` | Jump to Word → | EasyMotion `<leader><leader>w` |
| `<space>jb` | Jump to Word ← | EasyMotion `<leader><leader>b` |
| `<space>jj` | Jump to Line ↓ | EasyMotion `<leader><leader>j` |
| `<space>jk` | Jump to Line ↑ | EasyMotion `<leader><leader>k` |
| `<space>js` | Jump to Char | EasyMotion `<leader><leader>s` |

---

## Window `<space>w`

| Key | Action | Command |
|-----|--------|---------|
| `<space>wd` | Close Window/Split | `workbench.action.closeActiveEditor` |
| `<space>ww` | Switch to Next Window | `workbench.action.focusNextGroup` |
| `<space>wm` | Maximise/Toggle Width | `workbench.action.toggleEditorWidths` |
| `<space>-` | Split Below *(also top-level)* | `workbench.action.splitEditorDown` |
| `<space>\|` | Split Right *(also top-level)* | `workbench.action.splitEditorRight` |

---

## Diagnostics `<space>x`

| Key | Action | Command |
|-----|--------|---------|
| `<space>xx` | Diagnostics List (Problems Panel) | `workbench.action.problems.focus` |
| `<space>xX` | Workspace Diagnostics | `workbench.actions.view.problems` |
| `<space>xl` | Location List | `workbench.action.problems.focus` |

---

## UI Toggles `<space>u`

| Key | Action | Command |
|-----|--------|---------|
| `<space>uw` | Toggle Word Wrap | `editor.action.toggleWordWrap` |
| `<space>uz` | Toggle Zen Mode | `workbench.action.toggleZenMode` |
| `<space>ur` | Clear Search Highlight | `:nohl` |
| `<space>ul` | Toggle Line Numbers *(requires Settings Cycler; currently commented out)* | `settings.cycle.lineNumbers` |
| `<space>uL` | Toggle Relative Numbers *(requires Settings Cycler; currently commented out)* | `settings.cycle.relativeLineNumbers` |

---

## Previous `[` / Next `]`

> These are defined in **keybindings.json** and mirrored here for discoverability.

| Key | Action | Command |
|-----|--------|---------|
| `[b` / `]b` | Prev / Next Buffer | `workbench.action.previousEditor` / `nextEditor` |
| `[d` / `]d` | Prev / Next Diagnostic | `editor.action.marker.prevInFiles` / `nextInFiles` |
| `[e` / `]e` | Prev / Next Error | `editor.action.marker.prev` / `next` |
| `[h` / `]h` | Prev / Next Git Hunk | `workbench.action.editor.previousChange` / `nextChange` |
| `[q` / `]q` | Prev / Next Search Result | `search.action.focusPreviousSearchResult` / `focusNextSearchResult` |

---

## Quit `<space>q`

| Key | Action | Command |
|-----|--------|---------|
| `<space>qq` | Quit VSCode | `workbench.action.closeWindow` |
| `<space>qa` | Quit All | `workbench.action.quit` |

---

## LSP Navigation — `g` prefix (Normal Mode, no leader)

> These are standard Vim-style go-to bindings triggered by pressing `g` directly — **not** via `<space>`. They cannot appear in the Which-Key `<space>` menu.

| Key | Action | Command |
|-----|--------|---------|
| `gd` | Go to Definition | `editor.action.revealDefinition` |
| `gD` | Go to Declaration | `editor.action.revealDeclaration` |
| `gr` | Go to References | `editor.action.goToReferences` |
| `gI` | Go to Implementation | `editor.action.goToImplementation` |
| `gy` | Go to Type Definition | `editor.action.goToTypeDefinition` |
| `gK` | Signature Help (parameter hints) | `editor.action.triggerParameterHints` |

---

## Standalone Normal Mode Bindings (no leader)

| Key | Action | Command |
|-----|--------|---------|
| `K` | Show Hover Documentation | `editor.action.showHover` |
| `<Esc>` | Clear Search Highlight | `:nohl` |
| `<C-n>` | Clear Search Highlight | `:nohl` |
| `<C-d>` | Page Down (half) | vim built-in |
| `<C-u>` | Page Up (half) | vim built-in |

---

## Visual Mode Bindings

| Key | Action | Command |
|-----|--------|---------|
| `<space>` | Show Which-Key menu | `whichkey.show` |
| `<space>/` | Search selected text in files | `workbench.action.findInFiles` |
| `<space>ca` | Code Action on selection | `editor.action.quickFix` |
| `<space>cf` | Format Selection | `editor.action.formatSelection` |
| `gc` | Toggle Comment | `editor.action.commentLine` |

---

## Insert Mode Bindings

| Key | Action |
|-----|--------|
| `jk` | Escape to Normal mode |
| `jj` | Escape to Normal mode (alternative) |

---

## Vim Plugin Emulations (enabled)

| Plugin | Description | Trigger |
|--------|-------------|---------|
| **EasyMotion** | Jump to any word/line/char on screen | `<space>j*` (see Jump section) |
| **vim-sneak** | Two-character search forward/back | `s{char}{char}` / `S{char}{char}` |
| **vim-surround** | Add/delete/change surrounding chars | `ys` / `ds` / `cs` |

---

*Generated from `config/settings.json` — last updated 2026-03-08.*
