# Releasing

This repo tracks releases three ways that stay in sync: a semantic version
**tag**, an in-tree **`CHANGELOG.md`**, and a **GitHub Release**.

## Versioning

Use [Semantic Versioning](https://semver.org/spec/v2.0.0.html) — `MAJOR.MINOR.PATCH`:

- **MAJOR** — breaking changes.
- **MINOR** — new, backwards-compatible functionality.
- **PATCH** — backwards-compatible fixes.

## Keeping the changelog current

Update `CHANGELOG.md` in the **same PR** as the change, under the `## [Unreleased]`
heading. This is what keeps the changelog from rotting — never batch it up at
release time.

## Cutting a release

1. Move everything under `## [Unreleased]` into a new dated version heading, e.g.
   `## [1.2.0] - 2026-07-02`, and leave a fresh empty `Unreleased` section.
2. Commit on `main` (via PR).
3. Tag the release commit (annotated) and push the tag:

   ```bash
   git tag -a v1.2.0 -m "v1.2.0"
   git push origin v1.2.0
   ```

4. Cut a GitHub Release for the tag, reusing that version's changelog entry as
   the notes:

   ```bash
   gh release create v1.2.0 --title v1.2.0 --notes "<paste the changelog entry>"
   ```

The tag, the changelog heading, and the GitHub Release should all show the same
version.
