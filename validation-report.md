# Validation Report — VSCode Vim / Which Key Configuration

> Audited: `config/settings.json`
> Date: 2026-03-08

---

## Summary

| Check | Status |
|-------|--------|
| Duplicate `before` sequences in `normalModeKeyBindingsNonRecursive` | ⚠️ **1 found — fixed** |
| Duplicate `before` sequences in `visualModeKeyBindingsNonRecursive` | ✅ None |
| Dead whichkey entries (no matching vim binding) | ℹ️ Intentional (see §3) |
| `vim.visualModeKeyBindings` used instead of `…NonRecursive` | ✅ Correct key used |
| JSON syntax errors | ✅ None (valid JSONC) |
| `<leader>*` bindings missing from whichkey | ✅ All represented (see §4) |

---

## §1 — Duplicate `before` sequences ⚠️ FIXED

### `<leader>ur` defined twice in `normalModeKeyBindingsNonRecursive`

The sequence `["<leader>", "u", "r"]` → `:nohl` appeared in **two separate sections**:

| Location | Section |
|----------|---------|
| General Utility Mappings block | "clear search (LazyVim 'unredraw')" |
| UI Toggles block | `<leader>ur` canonical location |

Both entries were identical (same `before`, same `commands`). The VSCodeVim extension uses the **last matching entry**, so the duplicate was redundant rather than harmful — but it creates maintenance confusion (two places to update if the command changes).

**Fix applied:** Removed the duplicate from the General Utility Mappings block. The canonical entry in the UI Toggles block is retained.

---

## §2 — Bindings NOT represented in whichkey

### Non-leader bindings (expected — cannot appear in `<space>` menu)

The following bindings are triggered by keystrokes that do **not** start with `<space>`. The Which-Key menu only activates on `<space>`, so these bindings are structurally unreachable through it. This is expected and correct behaviour.

| Binding | Mode | Action |
|---------|------|--------|
| `K` | Normal | Show Hover (`editor.action.showHover`) |
| `<Esc>` | Normal | Clear search highlight (`:nohl`) |
| `<C-n>` | Normal | Clear search highlight (`:nohl`) |
| `gd` | Normal | Go to Definition |
| `gD` | Normal | Go to Declaration |
| `gr` | Normal | Go to References |
| `gI` | Normal | Go to Implementation |
| `gy` | Normal | Go to Type Definition |
| `gK` | Normal | Signature Help |
| `gc` | Visual | Toggle Comment |

**Action taken:** `K` was added to `whichkey.bindings` as a top-level entry under `<space>K` (the slot was free) so it is discoverable from the menu. The remaining `g*` and `gc` bindings cannot be surfaced in the `<space>` menu — the `g` slot is already used by the `+Git` submenu. All are documented in `bindings-cheatsheet.md`.

### `<leader><space>` — intentional omission

The vim binding `["<leader>", "<space>"]` → `workbench.action.quickOpen` exists in `normalModeKeyBindingsNonRecursive` but is **deliberately absent** from `whichkey.bindings`. The configuration file explains:

> "Leaving it unbound means double-space closes the which-key menu, preserving EasyMotion's `<leader><leader>` trigger for users who invoke it without which-key (or via `<leader>j*` wrappers). Use `<leader>ff` or `<leader>f f` for Find Files instead."

This is a design decision, not an oversight. No change required.

---

## §3 — Dead whichkey entries (entries with no matching vim binding)

### `[` / `]` Prev / Next submenus

The `whichkey.bindings` contains `[` and `]` submenus covering buffer, diagnostic, error, git hunk, and search-result navigation. These do **not** have matching entries in `vim.normalModeKeyBindingsNonRecursive` — they are instead bound in **`keybindings.json`** (noted in comments: "Bracket navigation ([d, ]d) not working: these are defined in keybindings.json").

The configuration comment explicitly acknowledges this:

> "These mirror the keybindings.json bracket bindings so they appear in the which-key menu. The VS Code commands are identical — this is purely for discoverability."

This is intentional. The whichkey entries execute the same VSCode commands directly, providing discoverability without breaking the separate keybindings.json definitions. **No change required.**

---

## §4 — Coverage of all `<leader>*` bindings in whichkey

All `<leader>`-prefixed vim bindings are confirmed present in `whichkey.bindings`:

| Vim binding | whichkey entry | Status |
|-------------|----------------|--------|
| `<leader>,` | top-level `,` Switch Buffer | ✅ |
| `<leader>/` | top-level `/` Search in Files | ✅ |
| `` <leader>` `` | top-level `` ` `` Last Buffer | ✅ |
| `<leader>-` | top-level `-` Split Below | ✅ |
| `<leader>\|` | top-level `\|` Split Right | ✅ |
| `<leader>d` | top-level `d` Delete Line | ✅ |
| `<leader>e` | top-level `e` Toggle Sidebar | ✅ |
| `<leader>E` | top-level `E` Focus Explorer | ✅ |
| `<leader>jw/jb/jj/jk/js` | `j` submenu (Jump/EasyMotion) | ✅ |
| `<leader>ff/fr/fn/fb/fe/ft` | `f` submenu (File) | ✅ |
| `<leader>sg/sw/sr/ss/sS/sk/sc/sh` | `s` submenu (Search) | ✅ |
| `<leader>ca/cA/cf/cF/cr/cd/cl/co` | `c` submenu (Code) | ✅ |
| `<leader>bb/bd/bD/bo/bp/bP` | `b` submenu (Buffer) | ✅ |
| `<leader>gg/gs/gb/gB/gd/gl/gL/gc` | `g` submenu (Git) | ✅ |
| `<leader>wd/ww/wm` | `w` submenu (Window) | ✅ |
| `<leader>xx/xX/xl` | `x` submenu (Diagnostics) | ✅ |
| `<leader>uw/uz/ur` | `u` submenu (UI Toggles) | ✅ |
| `<leader>qq/qa` | `q` submenu (Quit) | ✅ |

---

## §5 — JSON / JSONC syntax

`settings.json` uses JSONC (JSON with Comments), which is the format VSCode accepts for `settings.json`. All `//` comments are valid in this context.

No missing closing brackets, mismatched braces, trailing commas, or unclosed strings were found.

---

## §6 — `vim.visualModeKeyBindings` vs `vim.visualModeKeyBindingsNonRecursive`

The file correctly uses `vim.visualModeKeyBindingsNonRecursive` throughout. Using the non-recursive variant prevents accidental re-triggering of mapped keys (e.g., a binding whose output itself triggers another binding). **No issue.**

---

## Changes Made

| File | Change |
|------|--------|
| `config/settings.json` | Removed duplicate `<leader>ur` entry from General Utility section |
| `config/settings.json` | Added `{ "key": "K", … }` top-level whichkey entry for Show Hover |
| `bindings-cheatsheet.md` | Created — full reference for all bindings organised by submenu |
| `validation-report.md` | Created — this file |
