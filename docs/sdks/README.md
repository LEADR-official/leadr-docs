# SDK Documentation Structure

This directory contains documentation for all LEADR SDKs, organized by language and version.

## Directory Structure

```
docs/sdks/
├── python/
│   ├── sdk.meta.json         # SDK metadata and version info
│   ├── 0.1.0/                # Versioned SDK docs
│   │   ├── index.md
│   │   └── ...
│   └── latest -> 0.1.0       # Symlink to latest version
├── javascript/
│   ├── sdk.meta.json
│   ├── 0.2.0/
│   └── latest -> 0.2.0
└── sdk-versions.json         # Cross-reference of SDK/API compatibility
```

## SDK Metadata (`sdk.meta.json`)

Each SDK includes a metadata file with version and compatibility information:

```json
{
  "name": "leadr-python",
  "version": "0.1.0",
  "api_version": "1.0.0",
  "min_api_version": "1.0.0",
  "max_api_version": "1.2.0"
}
```

## SDK Version Compatibility (`sdk-versions.json`)

The `sdk-versions.json` file tracks which SDK versions are compatible with each API version:

```json
{
  "v1.0": {
    "python": ["0.1.0", "0.1.1"],
    "javascript": ["0.2.0"]
  },
  "v1.1": {
    "python": ["0.1.2", "0.2.0"],
    "javascript": ["0.2.1", "0.3.0"]
  }
}
```

This file is automatically updated when SDK PRs are merged.

## Adding SDK Documentation

SDK documentation is contributed via automated PRs from each SDK repository:

1. SDK release triggers workflow in SDK repo
2. Workflow generates docs and creates PR in this repo
3. PR includes:
   - Versioned docs in `docs/sdks/{language}/{version}/`
   - Updated `sdk.meta.json`
   - Updated symlink for `latest`
4. Review and merge PR
5. Documentation deployment happens automatically

## Version Strategy

- **API versions**: Major.minor format (e.g., v1.0, v1.1)
- **SDK versions**: Full semantic versioning (e.g., 0.1.0, 0.2.1)
- Each API documentation version shows all compatible SDK versions
- SDKs can update independently from API releases
