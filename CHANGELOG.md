# Changelog

All notable changes to this template are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.1.1] - 2026-07-03

### Fixed
- `.github/workflows/security.yml`: grant `pull-requests: read` on the calling job so `gitleaks-action` works on PR events.
- `.github/repo-metadata.yml`: corrected `visibility:` from `private` to `public` for the template repo itself.

### Changed
- `README.md`: replaced placeholder text with a real description of what the template ships and how to use it (including `gh repo create --template` quickstart and a workflow table).
- `.github/repo-metadata.yml`: replaced boilerplate `purpose:` with an accurate description of the template repo.

---

## [0.1.0] - 2026-07-03

### Added
- `.github/workflows/security.yml` — caller workflow wiring into `garymike/security-workflows` reusable workflows (gitleaks on push/PR, full audit on schedule).
- `SECURITY.md` — private vulnerability reporting template.
- `.gitignore` — covers `.env`, keys, certs, build artifacts, editor files.
- `.editorconfig` — utf-8, LF, 2-space indent, trim trailing whitespace, final newline; Makefile uses tabs.
- `.github/dependabot.yml` — npm enabled by default; pip and github-actions commented out.
- `.github/PULL_REQUEST_TEMPLATE.md` — checklist for secrets, tests, and security impact.
- `.github/repo-metadata.yml` — visibility intent declaration checked by the weekly audit.
- `README.md` placeholder for new repos.
