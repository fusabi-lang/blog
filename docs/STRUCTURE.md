# Documentation Structure

This document describes the required structure and content for the Fusabi Blog repository documentation.

## Directory Structure

```
docs/
├── STRUCTURE.md          # This file - describes doc organization
├── RELEASE.md           # Release process documentation
├── STYLE_GUIDE.md       # Content style guide for blog posts
└── versions/
    └── vNEXT/           # Next version documentation (work in progress)
        ├── README.md    # Version-specific overview
        └── ...          # Other version-specific docs
```

## Required Sections

### 1. Root Documentation

- **STRUCTURE.md**: Describes the documentation organization and required sections
- **RELEASE.md**: Documents the release process, versioning strategy, and deployment steps
- **STYLE_GUIDE.md**: Provides guidelines for writing blog posts, including formatting, tone, and structure

### 2. Versioned Documentation

Documentation is versioned to track changes over time. Each version should have:

- A dedicated directory under `docs/versions/`
- A README.md explaining version-specific features and changes
- Any additional documentation specific to that version

The `vNEXT` directory contains work-in-progress documentation for the upcoming release.

## Documentation Standards

### Markdown Format

- All documentation must be in Markdown format (.md)
- Use proper headings hierarchy (start with h1, don't skip levels)
- Include code blocks with language syntax highlighting
- Use relative links for internal documentation references

### Content Requirements

Each major documentation file should include:

1. **Title**: Clear, descriptive title
2. **Overview**: Brief summary of the document's purpose
3. **Content**: Well-organized sections with clear headings
4. **Examples**: Practical examples where applicable
5. **References**: Links to related documentation

### Version Control

- Documentation changes should be committed alongside code changes
- Update the appropriate version directory when making breaking changes
- Keep the main docs/ directory focused on current stable version

## CI Integration

Documentation is validated in CI to ensure:

- All required files are present
- Markdown files are properly formatted
- Internal links are not broken
- Code examples are syntactically valid

See `.github/workflows/docs-check.yml` for the automated checks.

## Maintenance

- Review and update documentation quarterly
- Archive old versions when they are no longer supported
- Keep the STRUCTURE.md file up to date with any organizational changes
