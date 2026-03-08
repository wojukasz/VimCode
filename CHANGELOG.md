# Changelog

All notable changes are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [2.9.0] - 2026-03-08

Documentation refactoring to NvimCode style throughout.

### Changed
- **All 8 documentation files** refactored: terse imperative tone, table-heavy reference sections, `**Symptoms:** / **Solution(s):**` format in TROUBLESHOOTING.md, `**Status:**` label on every entry in KNOWN_ISSUES.md, `## Step N — Name` structure in SETUP.md
- **KEYBINDINGS.md** — removed "By Workflow" and "Tips for Learning" sections; content moved to TIPS_AND_TRICKS.md; renamed "By Prefix" → "Leader Bindings"; removed ToC
- **TIPS_AND_TRICKS.md** — received workflow sequences from KEYBINDINGS.md; removed Keyboard-First Development, Performance Optimization, Common Pitfalls sections (duplicates); removed coaching language
- **TROUBLESHOOTING.md** — removed FAQ section (10 entries); removed VS Code Freezing subsection; enforced 3-part format on every issue entry
- **SETUP.md** — removed Configuration Architecture deep-dive, Quick Installation, Next Steps, vscode-neovim section; fixed validation checklist; added Prerequisites table
- **KNOWN_ISSUES.md** — stripped emoji headings; added Status label to every issue; converted "Considering Higher Parity?" to blockquote
- **REFERENCES.md** — removed Video Tutorials, Quick Links, Contributing, License, LazyVim Concepts, VimCode Documentation, Vim-Inspired Tools sections
- **README.md** — removed Why VimCode, Philosophy, Validation Checklist, Configuration Structure, Keybinding Organization sections; converted docs list to table
- **CHANGELOG.md** — added `---` separators between version blocks; rewrote [2.0.0] as single summary sentence; added version comparison links

### Removed
- `bindings-cheatsheet.md` — generated audit artifact; content absorbed into main docs
- `validation-report.md` — generated audit artifact; issues tracked in KNOWN_ISSUES.md

### Fixed
- KNOWN_ISSUES.md: added `]b` buffer navigation bug (moved from SETUP.md checklist) with **Status:** Open
- SETUP.md: validation checklist pre-checked items, typos ("beetwen", "dosent"), editorial note ("might remove ctrl + w in the future") all removed

---

## [2.8.0] - 2026-03-08

Full which-key audit; which-key promoted to complete in-editor cheatsheet.

### Added
- **`bindings-cheatsheet.md`** — comprehensive reference for every binding in the config, organised by submenu. Includes a "Direct shortcut" column for non-leader bindings so the file is useful as a standalone reference as well as a source of truth for the which-key menu structure.
- **`validation-report.md`** — documents issues found during the audit, changes applied, and confirms coverage of all `<leader>*` bindings.
- **`<space>G` — Go To / LSP Navigation submenu** — surfaces all six `g*` navigation bindings (`gd`, `gD`, `gr`, `gI`, `gy`, `gK`) plus hover docs (`K`) in the which-key popup. Entry names include the direct shortcut (e.g. `"Hover Docs  [K]"`), so the submenu doubles as a live, actionable cheatsheet. `<space>Gd` and `gd` execute the same command.
- **`<space>cc` — Toggle Comment** added to the `c` (Code) submenu, mirroring the visual-mode `gc` binding. Works on the current line in normal mode.
- **`<space>K` — Show Hover** added as a top-level which-key entry, mirroring the standalone `K` binding.
- **`<space>w` expanded into a full navigation hub** — the Window submenu now covers all navigation you might forget:
  - `h/j/k/l` — focus left/down/up/right pane (mirrors `Ctrl+H/J/K/L`; shortcut shown in label)
  - `s` / `v` — split below / split right (aliases for top-level `<space>-` and `<space>|`)
  - `=` / `-` / `+` / `_` — resize split width/height (mirrors `Ctrl+Arrow`)
  - `1` / `2` / `3` — jump to specific editor group (mirrors `Ctrl+1/2/3`)
- **`<space>bn` and `<space>bp`** — Next Buffer / Prev Buffer added to the `b` (Buffer) submenu with `Shift+L` / `Shift+H` labels, making these discoverable without remembering the direct key.

### Fixed
- **Duplicate `<leader>ur`** — the `:nohl` binding appeared twice in `normalModeKeyBindingsNonRecursive` (once in General Utility, once in UI Toggles). The stray copy in General Utility was removed; the canonical entry in UI Toggles is kept.

### Changed
- **`<space>b` — Pin / Unpin keys reassigned** — `p` freed up for the new Prev Buffer entry; Pin moved from `p` → `P`, Unpin moved from `P` → `U`.
- **`<space>w` renamed** from `"+Window"` to `"+Window / Nav"` to reflect its new role as a navigation discovery hub.

---

## [2.7.0] - 2026-03-07

Keymapping conflict audit fixes.

### Fixed
- **EasyMotion `<leader>j*` prefix** — `<space><space>` now opens which-key instead of EasyMotion's double-leader trigger; wrapper bindings under `<leader>j` (jw, jb, jj, jk, js) restore full EasyMotion access via direct key and the which-key `+Jump` submenu
- **Removed `Ctrl+D/U` suggestion navigation** — `vim.handleKeys` intercepts those keys for half-page scroll before any `when` clause fires; removed the conflicting keybindings and documented `Ctrl+N/P` as the reliable fallback
- **`<S-h>/<S-l>` duplicate removed** — dead definitions in `settings.json` removed; `keybindings.json` wins by VS Code priority rules
- **`<space>d` delete now register-aware** — changed from `editor.action.deleteLines` (discards line) to `vim.remap dd` so deleted lines go into the unnamed register and are pasteable with `p`
- **Added `<leader>ur`** (Clear Search Highlight) to which-key UI Toggles submenu

### Changed
- `KEYBINDINGS.md`: three-layer architecture diagram added, EasyMotion bindings corrected to `<leader>j*`, Sneak `,` vs which-key `,` conflict explained

---

## [2.6.0] - 2026-03-07

LazyVim parity documentation and bracket navigation in which-key.

### Added
- **`KNOWN_ISSUES.md`** — full rewrite documenting LazyVim parity ceiling (~95%):
  - Parity table: what matches exactly vs works differently vs is architecturally impossible
  - Hard limits of VSCodeVim (JS simulation, not real Vim): visual block mode, complex macros, register parity, Ctrl+D/U in autocomplete, EasyMotion differences
  - Cross-reference to vscode-neovim for users needing higher parity
- **`SETUP.md`** — new "Alternative: vscode-neovim" section:
  - Side-by-side comparison table (VSCodeVim vs vscode-neovim + LazyVim extra)
  - Setup steps for the vscode-neovim path
  - Note that `keybindings.json` is reusable; `settings.json` is VSCodeVim-specific
- **`config/settings.json`** — `[` and `]` groups added to `whichkey.bindings`:
  - Bracket navigation (`[b ]b`, `[d ]d`, `[e ]e`, `[h ]h`, `[q ]q`) was only in `keybindings.json` and invisible in the which-key popup; now discoverable via `<space>[` and `<space>]`

---

## [2.5.0] - 2026-03-07

Bundled which-key integration with a full pre-configured popup menu.

### Added
- **which-key popup menu** (`VSpaceCode.whichkey`) promoted from optional mention to first-class feature:
  - `whichkey.bindings` tree added to `config/settings.json` covering all 9 leader groups (`f`, `s`, `c`, `b`, `g`, `w`, `x`, `u`, `q`) plus top-level direct bindings (`,`, `/`, `` ` ``, `-`, `|`, `d`, `e`, `E`)
  - `<space>` → `whichkey.show` wired at the top of `vim.normalModeKeyBindingsNonRecursive` and `vim.visualModeKeyBindings` so the menu appears immediately on space-press
  - Existing `<leader>*` vim bindings preserved as fallback — config works correctly without the extension installed
- **`.vscode/extensions.json`** — workspace extension recommendations file so VS Code prompts "Install recommended extensions?" on first open

### Changed
- `SETUP.md`: which-key moved from "Optional Extensions" to its own **"Recommended Extensions"** section with full setup instructions, popup menu preview, and explanation of the fallback behaviour
- `SETUP.md`: Quick Installation commands updated to include `VSpaceCode.whichkey`
- `README.md`: which-key listed in Features; added to Quick Start install commands; validation checklist updated

---

## [2.4.0] - 2026-03-06

Generalised documentation to be VS Code fork-agnostic.

### Changed
- README title no longer names specific editors — now "VS Code and Compatible Forks"
- README intro, tagline, features, and Supported Editors section rewritten to describe fork compatibility generically
- Supported Editors section replaced with a fork-compatibility explanation (no named list with "primary target" labels)
- SETUP.md "Cursor and Antigravity Notes" section renamed to "Editor-Specific Notes" with general fork framing
- SETUP.md prerequisites and step headings updated to be editor-neutral
- SETUP.md path table prefaced with a verification note
- Quick Install section notes that `code` CLI should be replaced with your editor's command
- KEYBINDINGS.md and TIPS_AND_TRICKS.md subtitles updated to "VS Code and compatible forks"
- TROUBLESHOOTING.md FAQ generalised to cover any VS Code-compatible fork

---

## [2.3.0] - 2026-03-06

Replaced Windsurf with Antigravity throughout; corrected editor-specific technical details.

### Changed
- Updated all references from "Windsurf (Antigravity)" to "Antigravity" (Google's agentic IDE, distinct from Windsurf)
- Corrected macOS bundle identifier: `com.windsurf.app` → `com.google.antigravity`
- Updated config paths to use `Antigravity/User/` instead of `Windsurf/User/`
- Removed `windsurf` from package.json keywords
- Version bump: package.json and README badge to 2.3.0
- Note: Windsurf (by Codeium/Cognition AI) and Antigravity (by Google) are distinct products that share technological roots; VimCode now targets Antigravity specifically as the third supported editor

---

## [2.2.0] - 2026-03-06

Documentation refinement, link cleanup, and editor-specific notes.

### Added
- `KNOWN_ISSUES.md` - Tracks known issues and limitations with workarounds and links to issue reporting
- Cursor and Antigravity section in `SETUP.md` covering AI keybinding conflicts, recommended settings, macOS key repeat for all editors, and config sharing via symlinks

### Fixed
- Removed 3 broken/unavailable links from `REFERENCES.md`: viemu.com (x2) and vscodecandothat.com
- Fixed stale version in `package.json` (was 2.0.0, should have been 2.1.0)

### Changed
- Merged Cursor/Windsurf scratch notes (`OTER.md`) into `SETUP.md`
- Updated README.md docs table to include `KNOWN_ISSUES.md`

---

## [2.1.0] - 2026-03-06

Documentation cleanup and consolidation.

### Removed
- `EDITOR_COMPARISON.md` - Removed as duplicate content; editor compatibility info is covered in `SETUP.md` and `README.md`

### Changed
- Updated `README.md` to remove `EDITOR_COMPARISON.md` links from Documentation section and Supported Editors section
- Updated `REFERENCES.md` to remove `EDITOR_COMPARISON.md` from VimCode Documentation list
- Updated `TROUBLESHOOTING.md` FAQ to point to `SETUP.md` instead of removed file

---

## [2.0.0] - 2026-01-17

Major release adding comprehensive documentation (`SETUP.md`, `TIPS_AND_TRICKS.md`, `TROUBLESHOOTING.md`, `REFERENCES.md`), GitHub community health files, package metadata, and a full keybinding realignment to LazyVim conventions with `<space>` as leader and `<leader>f*` / `s*` / `c*` / `b*` / `g*` / `w*` / `x*` / `u*` prefix organisation.

---

## [1.0.0] - 2025-01-22

Initial release with comprehensive Vim keybindings for VS Code.

### Added
- **Custom Status Line Integration:**
  - Mode-specific colors
  - Visual feedback for Vim modes
- **Enhanced Editor Settings:**
  - Bracket pair colorization
  - Improved minimap configuration
  - Better bracket guides
- **Visual Mode Features:**
  - Line sorting: `<leader>ss`
  - Case transformation: `<leader>u`, `<leader>l`
  - Select all occurrences: `<leader>a`
- **Vim Experience Improvements:**
  - Yank highlighting
  - Better fold handling
  - Custom search highlighting
  - EasyMotion and Sneak plugins enabled
- **Navigation Shortcuts:**
  - Split navigation: `ctrl+h/j/k/l`
  - Tab navigation: `alt+[`, `alt+]`
  - Definition jumping: `ctrl+]`, `ctrl+t`
- **Split Management:**
  - Resize shortcuts: `alt+h`, `alt+l`
  - Maximize toggle: `ctrl+w m`
- **Terminal Integration:**
  - Toggle terminal: `ctrl+;`
  - Maximize terminal: `ctrl+shift+;`
- **File Explorer Integration:**
  - Toggle sidebar: `<leader>e`
  - Reveal in explorer: `<leader>f`
- **Basic Operations:**
  - Exit insert mode: `jj`
  - Toggle comment: `<leader>c`
  - Clear search: `ctrl+n`


---

[2.9.0]: https://github.com/wojukasz/VimCode/compare/v2.8.0...v2.9.0
[2.8.0]: https://github.com/wojukasz/VimCode/compare/v2.7.0...v2.8.0
[2.7.0]: https://github.com/wojukasz/VimCode/compare/v2.6.0...v2.7.0
[2.6.0]: https://github.com/wojukasz/VimCode/compare/v2.5.0...v2.6.0
[2.5.0]: https://github.com/wojukasz/VimCode/compare/v2.4.0...v2.5.0
[2.4.0]: https://github.com/wojukasz/VimCode/compare/v2.3.0...v2.4.0
[2.3.0]: https://github.com/wojukasz/VimCode/compare/v2.2.0...v2.3.0
[2.2.0]: https://github.com/wojukasz/VimCode/compare/v2.1.0...v2.2.0
[2.1.0]: https://github.com/wojukasz/VimCode/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/wojukasz/VimCode/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/wojukasz/VimCode/releases/tag/v1.0.0
