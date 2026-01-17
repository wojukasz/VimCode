# Repository Discoverability Guide

This guide explains how to maximize the discoverability of VimCode for people searching for Vim configurations for VS Code.

## Table of Contents

- [GitHub Repository Setup](#github-repository-setup)
- [SEO Optimization](#seo-optimization)
- [Community Engagement](#community-engagement)
- [Content Marketing](#content-marketing)
- [Distribution Channels](#distribution-channels)
- [Tracking & Analytics](#tracking--analytics)

## GitHub Repository Setup

### 1. Repository Topics (Tags)

**Add these topics to your GitHub repository** (Settings → General → Topics):

```
vim vscode neovim lazyvim vscodevim vscode-vim vim-config vim-configuration
keybindings modal-editing productivity developer-tools vim-keybindings
vscode-settings dotfiles text-editor code-editor lsp gitlens cursor-editor
```

**How to add:**
1. Go to https://github.com/wojukasz/VimCode
2. Click the ⚙️ gear icon next to "About"
3. Add the topics listed above
4. Check "Releases" and "Packages" if applicable
5. Save changes

### 2. Repository Description

Update the "About" section with:

```
🚀 LazyVim-inspired Vim configuration for VS Code | 50+ keybindings | Full LSP & Git integration | Works with VS Code, Cursor & Windsurf
```

### 3. Social Preview Image

Create a social preview image (1280x640px) featuring:
- VimCode logo/name
- Key selling points: "LazyVim for VS Code"
- Screenshot of the editor in action
- GitHub stats (stars, downloads)

Upload to: Repository Settings → Social preview → Upload an image

### 4. Repository Settings Checklist

- [ ] Topics/tags added (see list above)
- [ ] Short description updated
- [ ] Website URL set (if you have one)
- [ ] Social preview image uploaded
- [ ] License file present (✓ MIT)
- [ ] Issues enabled
- [ ] Discussions enabled (recommended)
- [ ] Wiki disabled (use docs instead)
- [ ] Projects disabled (unless using)

## SEO Optimization

### Search Terms People Use

Common search queries to target:
- "vim config for vscode"
- "vscode vim keybindings"
- "neovim to vscode"
- "lazyvim vscode"
- "best vim setup vscode"
- "vscodevim configuration"
- "vim mode vscode"
- "vscode vim settings"
- "neovim keybindings vscode"
- "vim bindings visual studio code"

### README Optimization

Your README.md should naturally include:
- ✓ "Vim configuration for VS Code" in the first paragraph
- ✓ "LazyVim" mentioned prominently
- ✓ "keybindings" in headings and content
- ✓ "VSCodeVim" extension mentioned
- Add: More screenshots showing the config in action
- Add: GIF/video demo of key features

### Metadata Files

Files that boost SEO:
- ✓ `package.json` - Enables GitHub package discovery (created!)
- ✓ Comprehensive documentation (SETUP.md, KEYBINDINGS.md, etc.)
- Consider: `.github/ISSUE_TEMPLATE/` for better issue discovery
- Consider: `.github/PULL_REQUEST_TEMPLATE.md`

## Community Engagement

### 1. Reddit Communities

Post to these subreddits (read rules first):
- r/vim - "Share your Vim configuration"
- r/neovim - LazyVim users migrate to VS Code
- r/vscode - "My Vim setup for VS Code"
- r/programming - "Bringing Vim to VS Code"
- r/commandline - Terminal-like workflow enthusiasts

**Post template:**
```
Title: [Tool] VimCode - LazyVim-inspired config for VS Code with 50+ keybindings

Body:
I've spent the last [time] creating a comprehensive Vim configuration
for VS Code that mirrors LazyVim. Features include:

- 50+ organized keybindings (<leader>f*, <leader>s*, etc.)
- Full LSP integration
- Git operations via GitLens
- Window management with Ctrl+h/j/k/l
- Works with VS Code, Cursor, and Windsurf

GitHub: [link]
Free and MIT licensed!

[Screenshot or GIF]
```

### 2. Hacker News

Post to Show HN: https://news.ycombinator.com/submit
- Title: "Show HN: VimCode – LazyVim config for VS Code"
- Best time: Tuesday-Thursday, 8-10 AM EST

### 3. Dev.to / Hashnode

Write a blog post:
- "How I Brought LazyVim to VS Code"
- "50+ Vim Keybindings for VS Code Users"
- "From Neovim to VS Code Without Losing Muscle Memory"

Cross-post to:
- dev.to (tags: vim, vscode, productivity)
- hashnode.dev
- medium.com

### 4. GitHub Discussions

Enable Discussions on your repo:
- Create categories: General, Show and Tell, Q&A
- Pin a welcome post
- Encourage users to share their customizations

### 5. Discord/Slack Communities

Share in:
- VS Code Discord
- Vim/Neovim Discord servers
- r/vim Discord
- Programming Discord communities

## Distribution Channels

### 1. Awesome Lists

Submit PRs to these curated lists:

**Primary targets:**
- [awesome-vscode](https://github.com/viatsko/awesome-vscode) - Add to "Vim" category
- [awesome-vim](https://github.com/akrawchyk/awesome-vim) - Add to "Tools" or "Integration"
- [awesome-neovim](https://github.com/rockerBOO/awesome-neovim) - Add to "VS Code" section
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) - Editor configurations

**How to submit:**
1. Fork the awesome list repository
2. Add your project with description
3. Follow their contribution guidelines
4. Submit PR with clear description

**Example entry:**
```markdown
- [VimCode](https://github.com/wojukasz/VimCode) - LazyVim-inspired configuration for VS Code with 50+ keybindings and full LSP integration.
```

### 2. GitHub Stars

Encourage starring:
- Add "⭐ Star this repo if you find it useful!" to README
- Add star badge: `![GitHub stars](https://img.shields.io/github/stars/wojukasz/VimCode?style=social)`
- Mention in documentation

### 3. Alternative Platforms

- **GitLab**: Mirror your repository
- **Codeberg**: Mirror for open-source enthusiasts
- **Bitbucket**: Additional visibility

### 4. Update Your Gist

Add prominent link at the top of your gist:

```markdown
> 📢 **This configuration has evolved into a full project!**
> Check out [VimCode](https://github.com/wojukasz/VimCode) for the latest version with 50+ keybindings, comprehensive docs, and multi-editor support.

---
```

### 5. VS Code Marketplace (Future)

Consider creating an extension:
- Package configs as a VS Code extension
- Users can install via marketplace
- Automatic configuration application
- Massive discoverability boost

**Steps:**
1. Create extension scaffold with `yo code`
2. Package settings/keybindings
3. Add activation script
4. Publish to marketplace

## Content Marketing

### 1. Screenshots & Media

Create and add to README:

**Screenshot ideas:**
- [ ] Split window navigation with overlays showing keys
- [ ] Leader key menu/cheatsheet overlay
- [ ] Before/after comparison with default VS Code
- [ ] Multi-editor support (VS Code, Cursor, Windsurf side-by-side)

**GIF demos:**
- [ ] File navigation workflow (`<leader>ff`, `<leader>/`)
- [ ] Git operations (`<leader>gg`, blame, diff)
- [ ] LSP features (go to definition, rename, code actions)
- [ ] Window management (splits, navigation)

**Tools:**
- Kap (macOS) - https://getkap.co/
- ScreenToGif (Windows) - https://www.screentogif.com/
- Peek (Linux) - https://github.com/phw/peek

### 2. Video Tutorial

Create a YouTube video:
- "Setup VimCode in 5 Minutes"
- "LazyVim Workflow in VS Code"
- "Why I Switched from Neovim to VS Code (But Kept Vim)"

Add video to README and link in repo description.

### 3. Comparison Content

Create comparison tables:
- VimCode vs vanilla VSCodeVim
- VimCode vs other Vim configs for VS Code
- Feature parity with LazyVim

### 4. Use Case Stories

Document real workflows:
- "How I use VimCode for [language/framework]"
- "My daily workflow with VimCode"
- Interview users who switched

## Social Media

### Twitter/X

Tweet about:
- ✅ Launch announcement
- Feature highlights (thread)
- Milestones (stars, forks)
- User testimonials/screenshots
- Tips & tricks

**Hashtags:**
```
#vim #vscode #neovim #lazyvim #vscodevim #coding #productivity
#developer #programming #texteditor #codeeditor
```

**Handles to tag:**
- @code (VS Code official)
- @neovim
- Vim influencers

### LinkedIn

Professional angle:
- "Boosting Productivity: Vim Workflow in VS Code"
- Share your journey creating the config
- Post in relevant groups

### Mastodon

Active dev communities:
- Post in #vim, #vscode, #neovim tags
- Share in programming instances

## Tracking & Analytics

### GitHub Insights

Monitor:
- Traffic sources (Insights → Traffic)
- Popular content (which docs are viewed)
- Referring sites
- Clone/download stats

### Add Tracking Badges

Update README.md with:

```markdown
![GitHub stars](https://img.shields.io/github/stars/wojukasz/VimCode?style=social)
![GitHub forks](https://img.shields.io/github/forks/wojukasz/VimCode?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/wojukasz/VimCode?style=social)
![GitHub issues](https://img.shields.io/github/issues/wojukasz/VimCode)
![GitHub pull requests](https://img.shields.io/github/issues-pr/wojukasz/VimCode)
![GitHub last commit](https://img.shields.io/github/last-commit/wojukasz/VimCode)
![GitHub contributors](https://img.shields.io/github/contributors/wojukasz/VimCode)
```

### Analytics Tools

Optional external tracking:
- Google Analytics for docs site
- Plausible (privacy-friendly)
- Simple Analytics

## Quick Wins Checklist

Complete these tasks first for maximum impact:

- [ ] Add GitHub topics (5 minutes)
- [ ] Update repository description (2 minutes)
- [ ] Add shields.io badges to README (5 minutes)
- [ ] Update gist with link to main repo (3 minutes)
- [ ] Enable GitHub Discussions (2 minutes)
- [ ] Post on r/vim and r/vscode (15 minutes)
- [ ] Submit to awesome-vscode (20 minutes)
- [ ] Create one GIF demo (30 minutes)
- [ ] Tweet announcement (5 minutes)
- [ ] Cross-post to dev.to (30 minutes)

**Total time: ~2 hours for major discoverability boost**

## Long-term Strategy

### Monthly Tasks
- [ ] Share tips/tricks on social media
- [ ] Write blog post about features
- [ ] Respond to issues/discussions
- [ ] Update documentation based on feedback

### Quarterly Tasks
- [ ] Review and update SEO keywords
- [ ] Analyze traffic sources
- [ ] Create new demo content
- [ ] Reach out to influencers

### Yearly Tasks
- [ ] Major version release announcement
- [ ] Conference talk/lightning talk
- [ ] Comprehensive video series
- [ ] VS Code marketplace extension (if not done)

## Success Metrics

Track these over time:
- GitHub stars (target: 100 → 500 → 1000)
- Repository clones per week
- Issue/discussion engagement
- External mentions/backlinks
- Search ranking for "vim config vscode"

## Additional Resources

- [GitHub Repository Best Practices](https://github.com/github/opensource.guide)
- [Open Source Guides](https://opensource.guide/)
- [Awesome README Guide](https://github.com/matiassingers/awesome-readme)
- [Shields.io Badge Generator](https://shields.io/)

---

**Remember:** Consistency beats intensity. Regular small updates and engagement will grow your audience steadily.

**Need help?** Open a discussion in the VimCode repository!
