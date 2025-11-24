# Fusabi Blog Publishing

Automated blog post publishing system for the fusabi-lang organization.

## Overview

This repository provides tooling to publish blog posts to the fusabi-lang/docs blog, which is hosted on GitHub Pages.

**Blog URL**: https://fusabi-lang.github.io/docs/blog/ (once set up)

## Quick Start

### Prerequisites

1. **Nushell** - Required for running the publish script
   ```bash
   # Install via your package manager or:
   cargo install nu
   ```

2. **GitHub CLI** - Required for cloning the docs repo
   ```bash
   # Install and authenticate
   just install-gh
   gh auth login
   ```

3. **Just** - Command runner (optional but recommended)
   ```bash
   cargo install just
   ```

### Initial Setup

```bash
# Create output directory structure
just setup

# Or manually:
mkdir -p output/{daily,weekly,monthly}
```

## Usage

### Creating Blog Posts

Create blog posts in the `output/` directory:

```bash
# Create a new daily post
just new-daily

# Create a new weekly post
just new-weekly

# Create a new monthly post
just new-monthly
```

This creates markdown files in:
- `output/daily/YYYY-MM-DD.md`
- `output/weekly/YYYY-Www.md`
- `output/monthly/YYYY-MM.md`

Edit these files with your content (frontmatter will be added automatically during publishing).

### Publishing

```bash
# Publish daily update
just publish-daily

# Publish weekly report
just publish-weekly

# Publish monthly review
just publish-monthly

# Publish all unpublished posts
just publish-all

# Dry run (see what would be published)
just publish-dry-run daily
just publish-dry-run weekly
just publish-dry-run monthly
```

### Check Status

```bash
# See how many unpublished posts you have
just status
```

## Blog Structure in fusabi-lang/docs

The publish script creates this structure:

```
fusabi-lang/docs/
└── content/
    └── blog/
        ├── index.md                  # Blog landing page
        └── 2025/
            ├── 11/
            │   ├── week-2025-47.md   # Weekly reports
            │   ├── 2025-11-23.md     # Daily updates
            │   └── november-2025.md  # Monthly reviews
            └── 12/
                └── ...
```

## Frontmatter Format

The publish script automatically adds Quartz-compatible frontmatter:

```yaml
---
title: "This Week in Fusabi - 2025-W47"
description: "Weekly development report for Fusabi"
date: 2025-11-23
tags: [fusabi, weekly-report, development]
author: Fusabi Team
---
```

## How It Works

1. **Write Content**: Create markdown files in `output/` directories
2. **Publish**: Run `just publish-*` commands
3. **Automation**: Script clones fusabi-lang/docs, adds frontmatter, commits, and pushes
4. **GitHub Pages**: Automatically builds and deploys
5. **Live**: Blog post appears at fusabi-lang.github.io/docs/blog/

## Commands Reference

| Command | Description |
|---------|-------------|
| `just publish-daily` | Publish today's daily update |
| `just publish-weekly` | Publish this week's report |
| `just publish-monthly` | Publish this month's review |
| `just publish-all` | Publish all unpublished posts |
| `just publish-dry-run MODE` | Preview what would be published |
| `just new-daily` | Create a new daily post template |
| `just new-weekly` | Create a new weekly post template |
| `just new-monthly` | Create a new monthly post template |
| `just status` | Show unpublished post counts |
| `just clean` | Remove temporary docs directory |
| `just setup` | Create output directory structure |

## Directory Structure

```
fusabi-lang/blog/
├── scripts/
│   └── publish.nu           # Publishing script
├── output/
│   ├── daily/               # Daily blog posts
│   ├── weekly/              # Weekly reports
│   └── monthly/             # Monthly reviews
├── justfile                 # Command definitions
├── README.md               # This file
└── .gitignore              # Ignore temp directories
```

## Integration with Quartz

Once published to fusabi-lang/docs, your blog posts integrate with Quartz's features:
- Full-text search
- Graph view relationships
- Bidirectional links
- RSS feed generation
- Tag-based navigation

## Cost

**$0** - GitHub Pages is completely free!

## Troubleshooting

### "gh: command not found"

Install GitHub CLI:
```bash
just install-gh
```

### "Permission denied"

Ensure you're authenticated with GitHub:
```bash
gh auth login
```

### "No post found"

Create a post first:
```bash
just new-daily
# Edit output/daily/YYYY-MM-DD.md
just publish-daily
```

## Example Workflow

```bash
# 1. Create a weekly post
just new-weekly

# 2. Edit the file
$EDITOR output/weekly/$(date +%Y-W%V).md

# 3. Preview what will be published
just publish-dry-run weekly

# 4. Publish to blog
just publish-weekly

# 5. Wait 2-3 minutes for GitHub Pages to deploy

# 6. Visit https://fusabi-lang.github.io/docs/blog/
```

## License

Same as the Fusabi project.
