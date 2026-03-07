# Known Issues and VSCodeVim Ceiling

This file documents known issues, hard limitations, and areas where VimCode intentionally diverges from LazyVim due to architectural constraints. For new bugs, please [open a GitHub Issue](https://github.com/wojukasz/VimCode/issues).

---

## LazyVim Parity: What Works, What Doesn't

VimCode achieves **~95% parity with LazyVim's daily keybinding surface**. The 5% gap is structural — VSCodeVim is a JavaScript *simulation* of Vim, not actual Vim. Some things cannot be fixed with configuration alone.

### ✅ Fully Matched (Exact Parity)

These work identically to LazyVim:

- All window navigation: `Ctrl+h/j/k/l`, resize with `Ctrl+↑↓←→`
- All buffer navigation: `Shift+H/L`, `[b`/`]b`
- All LSP goto: `gd`, `gD`, `gr`, `gI`, `gy`, `K`, `gK`
- All diagnostics: `[d`/`]d`, `[e`/`]e`
- All code actions: `<leader>ca`, `<leader>cf`, `<leader>cr`, `<leader>co`
- Insert escape: `jk`
- Git hunks: `[h`/`]h`
- Line move: `Alt+j/k`
- Search/grep: `<leader>/`, `<leader>ff`, `<leader>,`, `<leader>sg`, `<leader>sr`
- which-key popup menu on `<space>` with the same group structure (`f`, `s`, `c`, `b`, `g`, `w`, `x`, `u`, `q`)

### ⚠️ Works Differently (Same Goal, Different Feel)

| Feature | LazyVim | VimCode | Why |
|---------|---------|---------|-----|
| **File picker** | Telescope (fuzzy, file preview) | VS Code Quick Open (`Ctrl+P`) | No Telescope equivalent; Quick Open is functionally equivalent |
| **Live grep** | Telescope grep with inline preview | VS Code Find in Files | Different UI, same functionality |
| **File explorer** | neo-tree.nvim (floating window) | VS Code Explorer sidebar | No floating file tree in VS Code |
| **Motion search (`s`)** | flash.nvim — one char + jump labels | vim-sneak — two chars required | flash.nvim has no VS Code port; sneak is the closest available |
| **Symbol picker** | Telescope with fuzzy + preview | VS Code goto symbol | Minor UX difference |
| **which-key discovery** | Auto-reads `desc` from all keymaps | Manually configured in `whichkey.bindings` JSON | Structural: no introspection API available in VS Code |

---

## VSCodeVim Hard Limits

These are **architectural limitations of VSCodeVim** — not bugs in VimCode, and not fixable with any amount of configuration.

### ❌ Visual Block Mode (`Ctrl+v`)

**Status:** Fundamentally broken in VSCodeVim.

Pasting in visual block mode inserts incorrect newlines. Column-wise editing (inserting the same text at the start of multiple lines) is unreliable. This is a known long-standing issue in the VSCodeVim issue tracker.

**Workaround:** Use VS Code's native multi-cursor (`Alt+Click` or `Ctrl+Alt+↑↓`) for column editing. For block selection, use `Shift+Alt+drag`.

---

### ❌ Complex Macros Involving Registers

**Status:** Partially broken.

Basic macro recording (`qq … q`, then `@q`) works. However:
- Applying macros to a visual selection (`'<,'>norm! @q`) fails
- Macro definitions cannot be edited as text (paste macro as text, edit it, reload)
- The unnamed register and macro registers are stored separately in VSCodeVim's architecture

**Workaround:** Use VS Code's multi-cursor or find-and-replace for operations that would normally use register-heavy macros in Neovim.

---

### ❌ Full Register Parity

**Status:** Partial.

Named registers (`"ay`, `"ap`) work. System clipboard register (`"+y`, `"+p`) works via `vim.useSystemClipboard`. However, the black-hole register (`"_`), expression register (`"=`), and some special registers behave differently or are not implemented.

---

### ⚠️ `Ctrl+D` / `Ctrl+U` in Autocomplete

**Status:** By design, not available.

LazyVim users expect `Ctrl+D`/`Ctrl+U` to page through autocomplete suggestions. In VimCode, `vim.handleKeys` assigns `<C-d>` and `<C-u>` to vim's half-page scroll — this cannot be made context-aware (i.e. "release to VS Code when suggest widget is visible").

**Workaround:** Use `Ctrl+J`/`Ctrl+K` (bound in `keybindings.json`) or `Ctrl+N`/`Ctrl+P` (vim insert defaults) to navigate suggestions.

---

### ⚠️ EasyMotion vs flash.nvim

**Status:** Works, but different trigger sequence.

LazyVim uses flash.nvim (`s` = jump to char with labels). VimCode uses vim-sneak (`s` = 2-char sneak). EasyMotion is available via `<leader>j*` wrappers:

| LazyVim | VimCode | Notes |
|---------|---------|-------|
| `s{char}` → labels | `s{char}{char}` | Different: sneak needs 2 chars |
| `<leader><leader>w` | `<leader>jw` | Functionally equivalent |
| `<leader><leader>j` | `<leader>jj` | Functionally equivalent |

The `<leader>j` prefix was introduced because `<space><space>` (EasyMotion's original trigger) conflicts with the which-key menu.

---

## Editor / Terminal Conflicts

- **Capital-letter filenames in terminal:** Filenames containing capital letters may conflict with terminal keybindings (e.g., `Shift+N` navigates instead of typing `N`). Workaround: use lowercase filenames or remap the conflicting terminal binding.

---

## Considering Higher Parity?

If the gaps above matter for your workflow, consider **vscode-neovim** — an alternative VS Code extension that embeds a real Neovim process rather than simulating one. It achieves ~95% true Neovim parity, supports which-key.nvim with auto-discovery, and has an official LazyVim extra (`lazyvim.org/extras/vscode`).

Trade-offs: requires Neovim installed locally, more complex setup, and is labelled experimental (though widely used in production). See [SETUP.md](SETUP.md#alternative-vscode-neovim) for a comparison.

---

## Reporting New Issues

If you encounter a problem not listed here:
1. Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for common solutions
2. Search [existing issues](https://github.com/wojukasz/VimCode/issues)
3. Open a new issue using the bug report template
