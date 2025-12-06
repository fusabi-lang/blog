# Content Style Guide

This guide provides standards and best practices for writing blog posts in the Fusabi Blog.

## Overview

The Fusabi Blog publishes daily updates, weekly reports, and monthly reviews about the Fusabi programming language development. All content should be clear, informative, and accessible to a technical audience.

## Content Types

### Daily Updates

**Purpose**: Share quick progress updates, bug fixes, or small feature announcements.

**Format**:
```markdown
---
title: "Fusabi Daily Update - YYYY-MM-DD"
---

# Daily Update

## What's New

Brief summary of changes or additions.

## Details

- Bullet points of specific changes
- Keep it concise and scannable

## Next Steps

What's coming next (optional).
```

**Guidelines**:
- Keep it brief (200-400 words)
- Focus on concrete changes
- Include code examples if relevant
- Link to related PRs or issues

### Weekly Reports

**Purpose**: Summarize the week's development activities and highlight key achievements.

**Format**:
```markdown
---
title: "This Week in Fusabi - YYYY-Www"
---

# Weekly Report

## Summary

High-level overview of the week's accomplishments.

## Highlights

- Major features or improvements
- Important bug fixes
- Community contributions

## Details

### Feature 1
Description of feature work.

### Feature 2
Description of feature work.

## Looking Ahead

Preview of next week's priorities.

## Community

Shout-outs, acknowledgments, or community updates.
```

**Guidelines**:
- Aim for 500-800 words
- Organize by themes or components
- Include metrics if relevant (PRs merged, issues closed, etc.)
- Highlight community contributions
- Add screenshots or diagrams when helpful

### Monthly Reviews

**Purpose**: Provide a comprehensive overview of the month's development and strategic direction.

**Format**:
```markdown
---
title: "Fusabi Monthly Review - Month YYYY"
---

# Monthly Review

## Executive Summary

High-level overview of the month's achievements and challenges.

## Major Milestones

- Significant features completed
- Important releases
- Strategic decisions

## Development Metrics

- PRs merged: X
- Issues closed: Y
- Contributors: Z

## Technical Deep Dives

### Topic 1
In-depth discussion of significant work.

### Topic 2
In-depth discussion of significant work.

## Community Growth

Community engagement, new contributors, events.

## Roadmap Updates

Changes or progress on the roadmap.

## Next Month

Priorities and goals for the upcoming month.
```

**Guidelines**:
- Aim for 1000-1500 words
- Include charts or graphs for metrics
- Provide context and analysis, not just lists
- Reference previous months for continuity
- Celebrate wins and acknowledge challenges honestly

## Writing Style

### Tone

- **Professional but approachable**: Write like you're explaining to a colleague
- **Enthusiastic but measured**: Show excitement without hype
- **Transparent**: Be honest about challenges and setbacks
- **Inclusive**: Use "we" to include the community

### Voice

- **Active voice**: "We implemented X" not "X was implemented"
- **Present tense for current state**: "Fusabi supports X"
- **Past tense for completed work**: "We added X"

### Language

- **Clear and concise**: Avoid jargon when possible
- **Define technical terms**: Explain concepts on first use
- **Use examples**: Show, don't just tell
- **Avoid filler**: Every sentence should add value

## Formatting Standards

### Headings

- Use ATX-style headings (`#` not underlines)
- One h1 per document (the title)
- Use hierarchical structure (h2, h3, etc.)
- Keep headings descriptive and scannable

### Code Blocks

Always specify the language for syntax highlighting:

```fusabi
// Good - language specified
fn main() {
    println("Hello, Fusabi!")
}
```

### Links

- Use descriptive link text: `[pull request #42](...)` not `[here](...)`
- Link to relevant GitHub issues, PRs, and documentation
- Use relative links for internal documentation

### Lists

- Use bullets for unordered lists
- Use numbers for sequential steps
- Keep list items parallel in structure
- Don't mix list styles

### Emphasis

- **Bold** for strong emphasis or key terms
- *Italic* for subtle emphasis or introducing terms
- `Code` for inline code, commands, or file names
- Don't overuse - let content speak for itself

## Technical Content

### Code Examples

- Keep examples minimal and focused
- Include context (what problem does this solve?)
- Use realistic variable names
- Add comments for complex logic
- Test all code examples before publishing

### Error Messages

Format error messages as code blocks:
```
error: type mismatch
  --> src/main.fu:42:5
```

### Commands

Show commands with prompts:
```bash
$ fusabi build
$ fusabi run
```

### File Paths

Use inline code for file paths: `src/main.fu`

## SEO and Discoverability

### Title Optimization

- Include key terms: "Fusabi", topic name
- Keep under 60 characters when possible
- Be specific and descriptive

### Descriptions

- Write clear meta descriptions (155 characters)
- Include in frontmatter when relevant
- Summarize the post's value

### Tags

Use consistent, relevant tags:
- Primary: `fusabi`, content type (`daily-update`, `weekly-report`, `monthly-review`)
- Topic: `type-system`, `compiler`, `stdlib`, etc.
- Status: `development`, `release`, `announcement`

Example:
```yaml
tags: [fusabi, weekly-report, type-system, development]
```

## Images and Media

### Screenshots

- Use PNG format for UI screenshots
- Include alt text: `![Compiler output showing type error](path.png)`
- Keep file sizes reasonable (compress if needed)
- Store in `assets/` directory

### Diagrams

- Use Mermaid for diagrams when possible
- Keep diagrams simple and focused
- Include text descriptions for accessibility

### Videos

- Link to external hosting (YouTube, etc.)
- Provide transcripts or summaries
- Keep videos short and focused

## Frontmatter Standards

Required fields:
```yaml
---
title: "Clear, Descriptive Title"
date: YYYY-MM-DD
tags: [tag1, tag2, tag3]
---
```

Optional fields:
```yaml
description: "Brief summary for previews"
author: "Author Name"
image: "/path/to/preview-image.png"
```

## Review Checklist

Before publishing, verify:

- [ ] Spelling and grammar checked
- [ ] Code examples tested
- [ ] Links work and go to correct destinations
- [ ] Frontmatter is complete and correct
- [ ] Headings follow hierarchical structure
- [ ] Content matches the intended type (daily/weekly/monthly)
- [ ] Tone is appropriate and inclusive
- [ ] Technical accuracy verified
- [ ] No sensitive information exposed

## Examples

### Good Daily Update

```markdown
---
title: "Fusabi Daily Update - 2025-12-05"
date: 2025-12-05
tags: [fusabi, daily-update, compiler]
---

# Daily Update

## Type System Improvements

Today we improved error messages for type mismatches. The compiler now provides more context:

```fusabi
// Before: "type error"
// Now:
error: expected type `Int`, found `String`
  --> src/main.fu:10:5
   |
10 |     let x: Int = "hello"
   |                  ^^^^^^^ expected Int
```

This makes debugging much faster. See [PR #123](link) for details.

## Next

Tomorrow: implementing proper type inference for closures.
```

### Good Weekly Report

```markdown
---
title: "This Week in Fusabi - 2025-W49"
date: 2025-12-05
tags: [fusabi, weekly-report, development]
---

# Weekly Report

## Summary

This week focused on compiler performance and developer experience. We achieved a 30% improvement in compile times and shipped several quality-of-life features.

## Highlights

- Parallelized type checking (30% faster builds)
- New `fusabi doctor` command for environment diagnostics
- Improved error messages with suggestions
- 12 PRs merged, 8 issues closed

## Details

### Performance Improvements

We implemented parallel type checking across modules...

[Continue with details]

## Looking Ahead

Next week: Starting work on the async/await implementation.

## Community

Thanks to @contributor for the excellent documentation fixes!
```

## Resources

- [Markdown Guide](https://www.markdownguide.org/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Fusabi Documentation](https://fusabi-lang.github.io/docs/)

## Updates

This guide is versioned with the repository. Suggest changes via pull request.
