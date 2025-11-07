# leadr-docs
LEADR's centralised doc repo.

Each upstream API/SDK repo contributes a bundle via automated PR from CI, eg:

```bash
docs/sdks/<language>/<version or latest>/
  index.md
  ... other .md files ...
  assets/ (images, diagrams, etc.)
  sdk.meta.json   # small metadata (version, commit, generator)
```


