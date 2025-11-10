# Documentation Versioning

This document explains how documentation versioning works in the LEADR documentation portal.

## Overview

Documentation versions are tied to API releases using a PR-based workflow. All changes are visible and traceable through pull requests.

## Versioning Strategy

- **API versions**: Use **major.minor** format (e.g., `v1.0`, `v1.1`, `v2.0`)
- **SDK versions**: Use **full semantic versioning** (e.g., `0.1.0`, `0.2.1`)
- **Documentation versions**: Follow API major.minor versions (e.g., `v1.0`, `v1.1`)

### Version Conversion

When an API releases `v1.2.3`, the documentation is deployed as `v1.2`:
- `v1.2.3` → `v1.2` (documentation version)
- `v1.2.4` → `v1.2` (updates existing `v1.2` docs)
- `v1.3.0` → `v1.3` (new documentation version)

This means patch releases update the same documentation version, while minor/major releases create new versions.

## Workflow

### 1. API Release Triggers PR

When a new API version is released in `leadr-oss`:

1. Release workflow generates API documentation
2. Creates a `.api-version` file containing the release tag (e.g., `v1.2.3`)
3. Creates a PR in `leadr-docs` with:
   - Updated API docs in `docs/api/`
   - The `.api-version` file
   - Commit message: `docs(api): update API docs for v1.2.3`

### 2. Review and Merge PR

1. Review the PR to ensure docs look correct
2. Merge to `main` branch

### 3. Automatic Deployment

When the PR is merged:

1. GitHub Actions workflow detects the `.api-version` file
2. Extracts the version and converts to major.minor (e.g., `v1.2.3` → `v1.2`)
3. Deploys documentation using mike: `mike deploy v1.2`
4. Updates the `latest` alias to point to this version
5. Sets `latest` as the default version

### 4. Documentation Published

The versioned documentation is now live at:
- https://docs.leadr.gg/v1.2/ (specific version)
- https://docs.leadr.gg/latest/ (latest alias)
- https://docs.leadr.gg/ (defaults to latest)

## SDK Versioning

SDKs follow a similar PR-based workflow but maintain full semantic versioning:

### Directory Structure

```
docs/sdks/
├── python/
│   ├── sdk.meta.json
│   ├── 0.1.0/
│   ├── 0.1.1/
│   └── latest -> 0.1.1
└── sdk-versions.json
```

### SDK Release Process

1. SDK release triggers workflow in SDK repository
2. Workflow generates docs and creates PR in `leadr-docs`
3. PR includes:
   - Versioned docs in `docs/sdks/{language}/{version}/`
   - Updated `sdk.meta.json` with version info
   - Updated `latest` symlink
4. Review and merge PR
5. Next API docs deployment includes the updated SDK docs

### SDK Compatibility Matrix

The `docs/sdks/sdk-versions.json` file tracks SDK version compatibility:

```json
{
  "v1.0": {
    "python": ["0.1.0", "0.1.1"],
    "javascript": ["0.2.0"]
  },
  "v1.1": {
    "python": ["0.1.2", "0.2.0"],
    "javascript": ["0.2.1"]
  }
}
```

This allows each API documentation version to display all compatible SDK versions.

## Manual Version Deployment

To manually deploy a specific version:

1. Create a `.api-version` file:
   ```bash
   echo "v1.2.3" > docs/api/.api-version
   ```

2. Commit and push to `main`:
   ```bash
   git add docs/api/.api-version
   git commit -m "docs(api): deploy documentation for v1.2.3"
   git push origin main
   ```

3. The workflow will automatically deploy as `v1.2`

## Updating Existing Versions

To update an existing version (e.g., fix typos in v1.2 docs):

1. Update the `.api-version` file to match the version (e.g., `v1.2.0`)
2. Make your documentation changes
3. Commit and push to `main`
4. The workflow will redeploy the `v1.2` version with your updates

## Version Management

### Listing Versions

View all deployed versions:
```bash
uv run mike list
```

### Deleting Versions

Remove an old version:
```bash
uv run mike delete v1.0 --push
```

### Setting Default Version

Change the default version:
```bash
uv run mike set-default v1.2 --push
```

## Troubleshooting

### Deployment Skipped

If you see "No .api-version file found - skipping deployment" in the workflow logs:
- The `.api-version` file is missing or in the wrong location
- It should be at `docs/api/.api-version`
- Ensure the file is committed and pushed

### Wrong Version Deployed

Check the version extraction logic:
```bash
# Test locally
cat docs/api/.api-version | tr -d '[:space:]' | sed -E 's/^v?([0-9]+\.[0-9]+).*/v\1/'
```

This should output the major.minor version (e.g., `v1.2`).

## References

- [Mike Documentation](https://github.com/jimporter/mike)
- [MkDocs Documentation](https://www.mkdocs.org/)
- API Repository: `leadr-oss`
- SDK Repositories: TBD
