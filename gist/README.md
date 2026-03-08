# VimCode — LazyVim keybindings for VS Code

> **Quick-start gist.** Full docs, 50+ keybindings, and multi-editor support →
> [github.com/wojukasz/VimCode](https://github.com/wojukasz/VimCode)

Bring the muscle memory of [LazyVim](https://www.lazyvim.org) to VS Code (and Cursor, Windsurf, Antigravity). Copy two config files, install four extensions, and you get modal editing with a **which-key popup** that guides you through every leader shortcut.

---

## Extensions

| Extension | Purpose | Required? |
|---|---|---|
| [vscodevim.vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim) | Vim emulation | **Yes** |
| [VSpaceCode.whichkey](https://marketplace.visualstudio.com/items?itemName=VSpaceCode.whichkey) | `<space>` popup menu | **Yes** |
| [eamodio.gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) | Git blame, log, diff | Recommended |
| [hoovercj.vscode-settings-cycler](https://marketplace.visualstudio.com/items?itemName=hoovercj.vscode-settings-cycler) | Toggle relative line numbers | Optional |

### Quick install (terminal)

**VS Code**
```bash
code --install-extension vscodevim.vim && \
code --install-extension VSpaceCode.whichkey && \
code --install-extension eamodio.gitlens && \
code --install-extension hoovercj.vscode-settings-cycler
```

**Cursor**
```bash
cursor --install-extension vscodevim.vim && \
cursor --install-extension VSpaceCode.whichkey && \
cursor --install-extension eamodio.gitlens && \
cursor --install-extension hoovercj.vscode-settings-cycler
```

---

## Copy the config files

Copy both files from this gist into your editor's user settings directory, replacing any existing files (back them up first).

| Platform | Path |
|---|---|
| macOS | `~/Library/Application Support/<Editor>/User/` |
| Linux | `~/.config/<Editor>/User/` |
| Windows | `%APPDATA%\<Editor>\User\` |

Replace `<Editor>` with `Code`, `Cursor`, `Windsurf`, etc.

- **`settings.json`** — all `<leader>` bindings and which-key menu tree
- **`keybindings.json`** — modifier key bindings (Ctrl/Alt/Shift + h/j/k/l, etc.)

Restart your editor after copying.

---

## which-key popup

Press **`<space>`** in Normal mode → a popup appears showing every available leader shortcut.

```
<space>           Quick Open (find files)
,                 Switch buffer
/                 Search in files (grep)

f  →  +File       ff=Find  fr=Recent  fn=New  fb=Buffers  ft=Terminal
s  →  +Search     sg=Grep  sw=Word  sr=Replace  ss=Symbols  sc=Commands
c  →  +Code       ca=Action  cf=Format  cr=Rename  cd=Diagnostics
b  →  +Buffer     bb=Switch  bd=Delete  bn=Next  bp=Prev
g  →  +Git        gg=Status  gb=Blame  gd=Diff  gl=Log  gc=Commit
G  →  +Go To      d=Definition  r=References  I=Implementation  y=Type
w  →  +Window     h/j/k/l=Focus  -=Split↓  |=Split→  d=Close
x  →  +Diagnostics  xx=Panel  [d=Prev  ]d=Next
u  →  +UI         uw=Wrap  uz=Zen  ur=ClearHL  ul=LineNums
```

You never need to memorise keybindings — just press `<space>` and follow the menu.

---

## Essential keybindings

### Navigation
| Key | Action |
|---|---|
| `<space><space>` | Find files |
| `<space>/` | Grep across project |
| `<space>,` | Switch buffer |
| `Shift+h` / `Shift+l` | Previous / next buffer |
| `Ctrl+h/j/k/l` | Move between splits |

### Code
| Key | Action |
|---|---|
| `<space>ca` | Code action |
| `<space>cr` | Rename symbol |
| `<space>cf` | Format document |
| `gd` | Go to definition |
| `gr` | Go to references |
| `K` | Show hover |

### Git
| Key | Action |
|---|---|
| `<space>gg` | Git status |
| `<space>gb` | Git blame |
| `<space>gd` | Git diff |
| `[h` / `]h` | Previous / next hunk |

### Vim essentials
| Key | Action |
|---|---|
| `jk` or `jj` | Escape to Normal mode |
| `<leader>j` | EasyMotion jump |
| `s` / `S` | Sneak forward / backward |
| `ys` / `ds` / `cs` | Surround add / delete / change |
| `Ctrl+s` | Save file |

---

## macOS: enable key repeat

Without this, holding `j` won't repeat in Normal mode.

```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
# Restart VS Code after running this
```

Replace `com.microsoft.VSCode` with the bundle ID for your editor (e.g. `com.todesktop.230313mzl4w4u92` for Cursor).

---

## Full documentation

| Doc | Link |
|---|---|
| Setup guide | [SETUP.md](https://github.com/wojukasz/VimCode/blob/main/SETUP.md) |
| All 50+ keybindings | [KEYBINDINGS.md](https://github.com/wojukasz/VimCode/blob/main/KEYBINDINGS.md) |
| Tips & tricks | [TIPS_AND_TRICKS.md](https://github.com/wojukasz/VimCode/blob/main/TIPS_AND_TRICKS.md) |
| Troubleshooting | [TROUBLESHOOTING.md](https://github.com/wojukasz/VimCode/blob/main/TROUBLESHOOTING.md) |
| Changelog | [CHANGELOG.md](https://github.com/wojukasz/VimCode/blob/main/CHANGELOG.md) |

---

*This gist tracks the stable core config. For the latest features, follow [VimCode](https://github.com/wojukasz/VimCode).*
