# VS Code Vim Configuration

Enhanced VS Code configuration with Vim keybindings for efficient coding workflows. This setup combines the power of Vim motions with VS Code's modern features.

Some of the shortcuts are experimental and I am trying things on the go so please leave a comment and feel free to adjust.

## Features

### 💻 Editor Navigation
- Vim-style split navigation (`ctrl+h/j/k/l`)
- Quick file switching with `alt+[` and `alt+]`
- Efficient split management with `alt+h/l` for resizing

### 📁 File Explorer
- Toggle sidebar: `<leader>e`
- File navigation with Vim keys
- Quick file operations (rename, create, delete)

### 🔍 Search and Replace
- Enhanced workspace search with `<leader>s w`
- Find in files: `ctrl+shift+f`
- Navigate results: `F4/Shift+F4`

### ⚡ Quick Actions
- Format document: `ctrl+space f`
- Go to definition: `ctrl+]`
- Navigate back: `ctrl+t`

### 🔧 Git Integration
- Toggle blame: `<leader>g b`
- Quick stage: `<leader>g s`
- Pull: `<leader>g p`
- Push: `<leader>g P`
- View history: `<leader>g h`

### 🖥️ Terminal Integration
- Toggle terminal: `ctrl+;`
- Maximize terminal: `ctrl+shift+;`
- Create new terminal: `<leader>t n`

## Installation

1. Copy `settings.json` to your VS Code user settings
2. Copy `keybindings.json` to your VS Code keybindings
3. Install required extensions:
   - Vim
   - GitLens (for enhanced git features)

## Required Extensions

- [Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Multi Command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)

## Key Concepts

- Leader key is set to `<space>`
- Consistent use of Vim navigation patterns
- Integration with VS Code's native features
- Enhanced terminal and git workflows

## Common Workflows

### File Navigation
1. Open sidebar: `<leader>e`
2. Navigate files: `j/k`
3. Expand/collapse: `l/h`
4. Open in split: `ctrl+shift+1/2`

### Git Operations
1. Stage changes: `<leader>g s`
2. View changes: `<leader>g d`
3. Push changes: `<leader>g P`

### Code Navigation
1. Go to definition: `ctrl+]`
2. Return from definition: `ctrl+t`
3. Find in workspace: `<leader>s w`

## Customization

Edit the following files to customize the configuration:
- `settings.json`: VS Code and Vim settings
- `keybindings.json`: Custom keyboard shortcuts

## Contributing

Feel free to submit issues and enhancement requests!
