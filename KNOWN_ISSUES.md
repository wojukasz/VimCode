# Known Issues

Format: `## Title` → description → `**Workaround:**` → `**Status:**`

> For issues not listed here, see [TROUBLESHOOTING.md](TROUBLESHOOTING.md) or open a [GitHub Issue](https://github.com/wojukasz/VimCode/issues).

---

## LazyVim Parity: What Works, What Doesn't

### Exact Parity

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

### Works Differently

| Feature | LazyVim | VimCode | Why |
|---------|---------|---------|-----|
| **File picker** | Telescope (fuzzy, file preview) | VS Code Quick Open (`Ctrl+P`) | No Telescope equivalent; Quick Open is functionally equivalent |
| **Live grep** | Telescope grep with inline preview | VS Code Find in Files | Different UI, same functionality |
| **File explorer** | neo-tree.nvim (floating window) | VS Code Explorer sidebar | No floating file tree in VS Code |
| **Motion search (`s`)** | flash.nvim — one char + jump labels | vim-sneak — two chars required | flash.nvim has no VS Code port; sneak is the closest available |
| **Symbol picker** | Telescope with fuzzy + preview | VS Code goto symbol | Minor UX difference |
| **which-key discovery** | Auto-reads `desc` from all keymaps | Manually configured in `whichkey.bindings` JSON | Structural: no introspection API available in VS Code |

### Unavailable

These LazyVim features have no equivalent in VSCodeVim. See VSCodeVim Hard Limits below.

---

## VSCodeVim Hard Limits

These are **architectural limitations of VSCodeVim** — not bugs in VimCode, and not fixable with any amount of configuration.

### Visual Block Mode (`Ctrl+v`)

Pasting in visual block mode inserts incorrect newlines. Column-wise editing (inserting the same text at the start of multiple lines) is unreliable. This is a known long-standing issue in the VSCodeVim issue tracker.

**Workaround:** Use VS Code's native multi-cursor (`Alt+Click` or `Ctrl+Alt+↑↓`) for column editing. For block selection, use `Shift+Alt+drag`.

**Status:** Won't fix — VSCodeVim architectural limitation

---

### Complex Macros Involving Registers

Basic macro recording (`qq … q`, then `@q`) works. However:
- Applying macros to a visual selection (`'<,'>norm! @q`) fails
- Macro definitions cannot be edited as text (paste macro as text, edit it, reload)
- The unnamed register and macro registers are stored separately in VSCodeVim's architecture

**Workaround:** Use VS Code's multi-cursor or find-and-replace for operations that would normally use register-heavy macros in Neovim.

**Status:** Won't fix — VSCodeVim architectural limitation

---

### Full Register Parity

Named registers (`"ay`, `"ap`) work. System clipboard register (`"+y`, `"+p`) works via `vim.useSystemClipboard`. However, the black-hole register (`"_`), expression register (`"=`), and some special registers behave differently or are not implemented.

**Status:** Won't fix — partial by design

---

### `Ctrl+D` / `Ctrl+U` in Autocomplete

LazyVim users expect `Ctrl+D`/`Ctrl+U` to page through autocomplete suggestions. In VimCode, `vim.handleKeys` assigns `<C-d>` and `<C-u>` to vim's half-page scroll — this cannot be made context-aware (i.e. "release to VS Code when suggest widget is visible").

**Workaround:** Use `Ctrl+J`/`Ctrl+K` (bound in `keybindings.json`) or `Ctrl+N`/`Ctrl+P` (vim insert defaults) to navigate suggestions.

**Status:** By design

---

### EasyMotion vs flash.nvim

LazyVim uses flash.nvim (`s` = jump to char with labels). VimCode uses vim-sneak (`s` = 2-char sneak). EasyMotion is available via `<leader>j*` wrappers:

| LazyVim | VimCode | Notes |
|---------|---------|-------|
| `s{char}` → labels | `s{char}{char}` | Different: sneak needs 2 chars |
| `<leader><leader>w` | `<leader>jw` | Functionally equivalent |
| `<leader><leader>j` | `<leader>jj` | Functionally equivalent |

The `<leader>j` prefix was introduced because `<space><space>` (EasyMotion's original trigger) conflicts with the which-key menu.

**Status:** Fixed in v2.7.0

---

## Editor / Terminal Conflicts

Capital-letter filenames in terminal: filenames containing capital letters may conflict with terminal keybindings (e.g., `Shift+N` navigates instead of typing `N`).

**Workaround:** Use lowercase filenames or remap the conflicting terminal binding.

**Status:** Open

---

## `]b` Buffer Navigation

`]b` (next buffer, alternative binding) does not work reliably. `Shift+L` remains the recommended binding for next-buffer navigation.

**Workaround:** Use `Shift+L` / `Shift+H` instead of `]b` / `[b`.

**Status:** Open

---

> **Note:** If the gaps above matter for your workflow, consider **vscode-neovim** — it embeds a real Neovim process rather than simulating one and achieves near-identical LazyVim behaviour, including visual block mode, complex macros, and auto-discovery of which-key bindings. Trade-offs: requires Neovim 0.9+ installed locally and a more complex initial setup.

---

<!-- Future issue template:
## Issue Title

Description of the issue and when it occurs.

**Workaround:** Steps to work around the issue.

**Status:** Open | Fixed in vX.Y | Won't fix — reason | By design
-->
