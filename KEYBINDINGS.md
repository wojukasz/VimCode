# VimCode Keybindings Quick Reference

> **Note:** This reference is for VS Code. See `config/vscode/` for configuration files.

> Leader key: `<space>`

## Navigation

| Key | Action | Mode |
|-----|--------|------|
| `H` | Previous tab | Normal |
| `L` | Next tab | Normal |
| `ctrl+h` | Focus left split | Normal |
| `ctrl+j` | Focus split below | Normal |
| `ctrl+k` | Focus split above | Normal |
| `ctrl+l` | Focus right split | Normal |
| `ctrl+1` | Focus first editor group | Any |
| `ctrl+2` | Focus second editor group | Any |
| `alt+[` | Previous editor | Any |
| `alt+]` | Next editor | Any |
| `ctrl+]` | Go to definition | Normal |
| `ctrl+o` | Navigate back | Any |

## File Operations

| Key | Action | Mode |
|-----|--------|------|
| `<leader>fs` | Save file | Normal |
| `<leader>q` | Close file | Normal |
| `<leader>f` | Reveal in explorer | Normal |
| `<leader>fy` | Copy file path | Normal |
| `<leader>fn` | New file | Normal |
| `ctrl+k p` | Copy path of active file | Any |

## Sidebar & Explorer

| Key | Action | Mode |
|-----|--------|------|
| `<leader>e` | Toggle file explorer | Normal |
| `ctrl+shift+1` | Open file in left split | Explorer |
| `ctrl+shift+2` | Open file in right split | Explorer |
| `ctrl+enter` | Rename file | Explorer |
| `enter` | Open file | Explorer |

## Window Management

| Key | Action | Mode |
|-----|--------|------|
| `<leader>w` | Split editor | Normal |
| `alt+h` | Decrease split width | Any |
| `alt+l` | Increase split width | Any |
| `ctrl+w m` | Toggle maximize editor | Any |

## Git Operations

| Key | Action | Mode |
|-----|--------|------|
| `<leader>gb` | Toggle blame | Normal |
| `<leader>gs` | Stage file | Normal |
| `<leader>gp` | Pull | Normal |
| `<leader>gP` | Push | Normal |
| `<leader>gh` | File history | Normal |
| `<leader>gd` | View changes | Normal |

## Search

| Key | Action | Mode |
|-----|--------|------|
| `<leader>sw` or `<space>/` | Search in workspace / Find in files | Normal |
| `F4` | Next search result | Any |
| `shift+F4` | Previous search result | Any |
| `ctrl+n` | Clear search highlight | Normal |

## Code Actions

| Key | Action | Mode |
|-----|--------|------|
| `<leader>c` | Toggle comment | Normal/Visual |
| `<leader>rn` | Rename symbol | Normal |
| `<space>f` | Format document | Any |
| `F8` | Next problem | Any |
| `shift+F8` | Previous problem | Any |

## Terminal

| Key | Action | Mode |
|-----|--------|------|
| `ctrl+;` | Toggle terminal focus | Any |
| `ctrl+shift+;` | Maximize terminal | Any |
| `<leader>tn` | New terminal | Normal |

## Visual Mode

| Key | Action | Mode |
|-----|--------|------|
| `<leader>ss` | Sort lines ascending | Visual |
| `<leader>u` | Transform to UPPERCASE | Visual |
| `<leader>l` | Transform to lowercase | Visual |
| `<leader>a` | Select all occurrences | Visual |

## Insert Mode

| Key | Action | Mode |
|-----|--------|------|
| `jj` | Exit insert mode | Insert |
| `ctrl+j` | Next suggestion | Autocomplete |
| `ctrl+k` | Previous suggestion | Autocomplete |

## Vim Plugins Enabled

- **EasyMotion**: `<leader><leader>w` (word), `<leader><leader>b` (back)
- **Sneak**: `s{char}{char}` to jump to occurrence
- **Highlighted Yank**: Visual feedback on yank operations
