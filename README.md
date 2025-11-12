# LEADR Documentation

Centralized documentation repository for [LEADR](https://leadr.gg) - the cross-platform leaderboard backend for indie game developers.

**Live documentation**: https://docs.leadr.gg

## Overview

This repository aggregates documentation from multiple upstream repositories (API and SDKs) and publishes versioned documentation using MkDocs Material and Mike. Upstream repositories contribute documentation bundles via automated pull requests from CI/CD pipelines.

**Important**: All upstream documentation bundles must be provided as Markdown files (.md). The build process uses MkDocs to convert these to static HTML.

## Documentation Structure

```
docs/
├── api/                           # API documentation
│   ├── .api-version               # Version trigger file (e.g., "v1.2.3")
│   ├── openapi.json               # OpenAPI specification
│   ├── http-api/                  # HTTP API guides
│   └── reference/                 # Generated API reference
├── sdks/                          # SDK documentation
│   ├── sdk-versions.json          # SDK-API compatibility matrix
│   └── {language}/                # Per-language SDK docs
│       ├── sdk.meta.json          # SDK metadata (version, commit, generator)
│       ├── {version}/             # Versioned SDK documentation
│       │   ├── index.md
│       │   ├── *.md               # Documentation pages
│       │   └── assets/            # Images, diagrams, etc.
│       └── latest -> {version}    # Symlink to latest version
└── *.md                           # General documentation pages
```

## Configuration

The `mkdocs.yml` file is the central configuration point for the entire documentation site. It controls:
- Site metadata (name, URL, description)
- Navigation structure and page ordering
- Theme configuration (Material theme with custom overrides)
- Plugins (search, autorefs, section-index)
- Markdown extensions (admonition, code highlighting, tabbed content)
- Build output directory (`site-md`)

Any changes to site structure, navigation, or features should be made in this file.

## Versioning

### API Documentation
- **Format**: Major.minor (e.g., `v1.0`, `v1.1`)
- **Conversion**: Release `v1.2.3` → docs version `v1.2`
- **Patch updates**: Update existing version (e.g., `v1.2.4` updates `v1.2` docs)
- **Minor/major**: Create new version (e.g., `v1.3.0` creates `v1.3` docs)

### SDK Documentation
- **Format**: Full semantic versioning (e.g., `0.1.0`, `0.2.1`)
- **Location**: `docs/sdks/{language}/{version}/`
- **Compatibility**: Tracked in `docs/sdks/sdk-versions.json`

## How It Works

### Automated Documentation Updates

1. **Upstream Release**: When an API or SDK version is released, CI generates documentation and creates a PR to this repository
2. **PR Contents**:
   - Updated documentation files
   - `.api-version` file (for API releases)
   - Updated metadata files
3. **Review & Merge**: Review the PR and merge to `main`
4. **Automatic Deployment**: GitHub Actions detects the version and deploys with Mike to GitHub Pages

### Deployment Process

When a PR is merged, the `deploy.yml` workflow runs, and:
1. Extract version from `.api-version` (e.g., `v1.2.3`) if present
2. Convert to major.minor format (e.g., `v1.2`)
3. Deploy using Mike: `mike deploy v1.2 latest --update-aliases`
4. Set `latest` as default version
5. Push to `gh-pages` branch

Documentation is available at:
- `https://docs.leadr.gg/v1.2/` - Specific version
- `https://docs.leadr.gg/latest/` - Latest version
- `https://docs.leadr.gg/` - Defaults to latest

## Local Development

### Prerequisites
- Python 3.11+
- [uv](https://github.com/astral-sh/uv) package manager

### Setup & Usage

```bash
# Install dependencies (uv handles this automatically)
uv sync

# Serve docs locally with hot-reload
uv run mkdocs serve

# Build static site (output to site-md/)
uv run mkdocs build

# List deployed versions
uv run mike list

# Deploy a version manually
uv run mike deploy v1.2 latest --update-aliases

# Set default version
uv run mike set-default latest
```

## Manual Version Deployment

To manually deploy or update a version, the deployment workflow can be triggered manually and passed a version number as input.

## Documentation

- [VERSIONING.md](VERSIONING.md) - Detailed versioning and deployment guide

![Umami pixel](https://cloud.umami.is/p/qE29SYTi9 "Umami pixel")
