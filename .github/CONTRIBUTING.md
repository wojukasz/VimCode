# Contributing to VimCode

Thank you for your interest in contributing to VimCode! This document provides guidelines for contributing.

## How to Contribute

### Reporting Issues

- Use the appropriate issue template (Bug Report, Feature Request, or Keybinding Conflict)
- Search existing issues before creating a new one
- Provide as much detail as possible
- Include your environment details (OS, editor version, VSCodeVim version)

### Suggesting Enhancements

- Check if the feature exists in LazyVim - we aim for parity
- Explain the use case and benefit
- Suggest a keybinding that follows LazyVim conventions
- Consider if it fits the VimCode philosophy

### Pull Requests

1. **Fork the repository** and create your branch from `main`
2. **Make your changes**:
   - Follow the existing code style
   - Maintain LazyVim conventions where applicable
   - Update documentation if needed
3. **Test thoroughly**:
   - Test in VS Code (and Cursor/Windsurf if possible)
   - Verify keybindings work in Normal, Insert, and Visual modes
   - Check for conflicts with existing bindings
4. **Update documentation**:
   - Update KEYBINDINGS.md if adding/changing keybindings
   - Update SETUP.md if changing installation steps
   - Update CHANGELOG.md following existing format
5. **Submit your PR** using the pull request template

## Keybinding Guidelines

When proposing new keybindings:

1. **Follow LazyVim conventions**:
   - `<leader>f*` for file operations
   - `<leader>s*` for search operations
   - `<leader>c*` for code actions
   - `<leader>g*` for git operations
   - `<leader>b*` for buffer operations
   - `<leader>w*` for window operations
   - `<leader>x*` for diagnostics
   - `<leader>u*` for UI toggles

2. **Avoid conflicts**:
   - Check existing keybindings in KEYBINDINGS.md
   - Don't override essential Vim motions
   - Consider different keyboard layouts

3. **Be intuitive**:
   - Use mnemonic prefixes (f=find, s=search, c=code, etc.)
   - Follow VS Code conventions where it makes sense
   - Keep muscle memory consistent with LazyVim

## Development Setup

1. Fork and clone the repository
2. Install VS Code and required extensions:
   ```bash
   code --install-extension vscodevim.vim
   code --install-extension eamodio.gitlens
   code --install-extension hoovercj.vscode-settings-cycler
   ```
3. Copy config files to your VS Code settings directory
4. Make your changes and test

## Documentation

- Keep documentation clear and concise
- Use proper markdown formatting
- Include code examples where helpful
- Update table of contents if adding new sections

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on what's best for the project
- Help others learn and grow

## Questions?

- Open a GitHub Discussion for questions
- Check existing documentation first
- Be specific about your environment and issue

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for contributing to VimCode!** 🚀
