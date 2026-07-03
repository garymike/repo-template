# repo-template

A GitHub repository template pre-wired with security defaults. Every new repo created from this template starts with:

- **Gitleaks** secret scanning on every push and PR
- **Dependabot** configuration (uncomment the ecosystems you use)
- **Weekly security audit** via [garymike/security-workflows](https://github.com/garymike/security-workflows)
- **SECURITY.md** — private vulnerability reporting instructions
- **`.github/repo-metadata.yml`** — visibility intent declaration checked by the weekly audit
- **PR template** — checklist covering secrets, tests, and security impact
- **`.editorconfig`** — consistent formatting defaults
- **`.gitignore`** — covers `.env`, keys, certs, common build artifacts
- **`CHANGELOG.md` + `RELEASING.md`** — release tracking via semver tags, an in-tree changelog, and GitHub Releases

## Using this template

Click **Use this template** → **Create a new repository** on GitHub, or:

```bash
gh repo create <name> --template garymike/repo-template --private
```

After creating your repo, do three things:

1. **Update `.github/repo-metadata.yml`** — set `visibility:` to `public` or `private` and replace the `purpose:` placeholder with a one-line description of the repo.
2. **Update `README.md`** — replace this file with your project's README.
3. **Update `.github/dependabot.yml`** — uncomment the package ecosystems your project uses.
4. **Reset `CHANGELOG.md`** — keep the `Unreleased` heading and clear the scaffold note as you add real changes. See [RELEASING.md](RELEASING.md) for how to cut a release.

## Security pipeline

The template wires into two reusable workflows in [garymike/security-workflows](https://github.com/garymike/security-workflows):

| Workflow | Trigger | What it checks |
|---|---|---|
| `security-scan.yml` | push, PR | Gitleaks secrets, unpinned actions, SECURITY.md presence |
| `security-audit.yml` | weekly + manual | Dependabot, Actions permissions, branch protection, delete-on-merge |

The weekly [Claude security audit skill](https://github.com/garymike/skills) runs across all repos and catches anything the per-repo GHA can't see — new repos missing the template, account-level drift, OAuth/PAT hygiene.
