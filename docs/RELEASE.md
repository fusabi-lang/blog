# Release Process

This document describes the release process for the Fusabi Blog repository.

## Overview

The Fusabi Blog uses automated GitHub Actions workflows for building, testing, and deploying blog content. Releases are tagged semantically to track content batches and infrastructure changes.

## Release Types

### Content Releases

Content releases are optional and can be used to mark significant content milestones:

- **Patch (v1.0.1)**: Individual blog posts or minor corrections
- **Minor (v1.1.0)**: Weekly or monthly content batches
- **Major (v2.0.0)**: Major blog redesigns or structural changes

### Infrastructure Releases

Infrastructure releases track changes to the publishing system, workflows, or scripts:

- **Patch**: Bug fixes in scripts or workflows
- **Minor**: New features (e.g., new post types, automation improvements)
- **Major**: Breaking changes to the publishing workflow

## Semantic Versioning

We follow [Semantic Versioning 2.0.0](https://semver.org/):

- **MAJOR.MINOR.PATCH** (e.g., 1.2.3)
- Pre-release versions may use suffixes: 1.0.0-beta.1

## Release Workflow

### Automated Process

1. **Create a release branch** (if needed for major changes):
   ```bash
   git checkout -b release/v1.2.0
   ```

2. **Ensure all changes are committed**:
   ```bash
   git status
   ```

3. **Push the branch and create a PR**:
   ```bash
   git push -u origin release/v1.2.0
   gh pr create --title "Release v1.2.0" --body "Release notes here"
   ```

4. **Merge the PR** after review and CI passes

5. **Create a release using GitHub CLI**:
   ```bash
   gh release create v1.2.0 \
     --title "Release v1.2.0" \
     --notes "Release notes here" \
     --latest
   ```

### GitHub Actions Automation

The release workflow (`.github/workflows/release.yml`) automatically:

1. Builds and validates the blog content
2. Runs all tests
3. Generates a changelog from commit messages
4. Creates release artifacts if needed
5. Deploys to GitHub Pages (if applicable)

## Branch Protection

### Main Branch Rules

The `main` branch is protected with the following rules:

- **Required reviews**: At least 1 approval required
- **Status checks**: All CI checks must pass
- **Up-to-date branch**: Branch must be up to date before merging
- **No force pushes**: Force pushes are disabled
- **No deletions**: Branch cannot be deleted

### Release Branches

Release branches (e.g., `release/v1.2.0`) should:

- Be created from `main`
- Be merged back to `main` via PR
- Be deleted after successful merge

## CODEOWNERS

The CODEOWNERS file defines required reviewers for different parts of the repository:

- **/.github/**: GitHub configuration and workflows
- **/docs/**: Documentation files
- **/scripts/**: Publishing scripts

See `.github/CODEOWNERS` for the complete list.

## Changelog Generation

Changelogs are automatically generated from commit messages. Use conventional commits:

- `feat:` - New features
- `fix:` - Bug fixes
- `docs:` - Documentation changes
- `chore:` - Maintenance tasks
- `refactor:` - Code refactoring
- `test:` - Test additions or changes

Example:
```
feat: add support for yearly blog posts
fix: correct frontmatter date formatting
docs: update release process documentation
```

## Deployment

### Manual Deployment

To manually trigger a deployment:

```bash
# Using the justfile
just publish-all

# Or directly with the script
nu scripts/publish.nu all
```

### Automated Deployment

GitHub Actions automatically deploys on:

- Push to `main` branch
- New release tags
- Manual workflow dispatch

## Rollback Procedure

If a release has issues:

1. **Identify the last good release**:
   ```bash
   gh release list
   ```

2. **Revert to the previous version**:
   ```bash
   git revert <commit-hash>
   git push origin main
   ```

3. **Create a hotfix release** if needed:
   ```bash
   gh release create v1.2.1 --title "Hotfix v1.2.1" --notes "Fixes issue from v1.2.0"
   ```

## Release Checklist

Before creating a release:

- [ ] All tests pass locally and in CI
- [ ] Documentation is up to date
- [ ] CHANGELOG.md is updated (or will be auto-generated)
- [ ] Version number follows semantic versioning
- [ ] Breaking changes are documented
- [ ] Migration guide provided (if needed)
- [ ] All required reviewers have approved

## Version Management

Current version information:

- **Location**: Git tags
- **Format**: `vMAJOR.MINOR.PATCH`
- **Latest**: Use `gh release view` to check

## Support and Questions

For questions about the release process:

- Open an issue with the `question` label
- Consult the STRUCTURE.md for documentation organization
- Review past releases for examples: `gh release list`

## References

- [Semantic Versioning](https://semver.org/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub CLI Manual](https://cli.github.com/manual/)
