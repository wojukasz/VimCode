# Changelog

All notable changes to this configuration will be documented in this file.

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

> Windsurf (by Codeium/Cognition AI) and Antigravity (by Google) are distinct products that share technological roots. VimCode now targets Antigravity specifically as the third supported editor.

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

## [2.0.0] - 2026-01-17

Major update with comprehensive documentation, community health files, and refined keybindings.

### Added
- **GitHub Community Health Files:**
  - `.github/CONTRIBUTING.md` - Contribution guidelines following LazyVim conventions
  - `.github/ISSUE_TEMPLATE/` - Bug report, feature request, and keybinding conflict templates
  - `.github/PULL_REQUEST_TEMPLATE.md` - Structured PR template
- **Package Metadata:**
  - `package.json` - npm/GitHub package metadata with keywords for discoverability
  - Install scripts for VS Code and Cursor
- **Comprehensive Documentation:**
  - `SETUP.md` - Detailed installation and configuration guide
  - `TIPS_AND_TRICKS.md` - Advanced usage patterns and workflows
  - `TROUBLESHOOTING.md` - Common issues and solutions
  - `REFERENCES.md` - Additional resources and learning materials
- **Enhanced Keybindings Documentation:**
  - Significantly expanded `KEYBINDINGS.md` with comprehensive key mapping documentation
  - Quick reference cheatsheet
  - Organized by LazyVim conventions

### Changed
- **Keybindings aligned with LazyVim conventions:**
  - Primary leader key: `<space>` (space)
  - Organized by prefix: `<leader>f*` (files), `<leader>s*` (search), `<leader>c*` (code), etc.
  - File Explorer Toggle: `<space>e`
  - Workspace Search: `<space>/`
  - Better consistency with LazyVim muscle memory
- **Configuration Structure:**
  - Unified configuration in `config/` directory
  - Single `settings.json` and `keybindings.json` for all compatible editors
  - Multi-editor support for VS Code, Cursor, and Antigravity
- **Documentation Improvements:**
  - Updated `README.md` with improved structure and clarity
  - Better organization of all documentation files
  - Enhanced contribution guidelines

### Fixed
- Corrected changelog entries and version history
- Improved keybinding consistency
- Fixed documentation references

### Removed
- Promotional marketing content
- Redundant documentation files
- Multi-editor scaffolding (consolidated to single config)

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
