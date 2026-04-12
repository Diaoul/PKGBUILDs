# PKGBUILDs

AUR packages maintained by Antoine Bertin, automated with Renovate + GitHub Actions.

## Workflow

- **PKGBUILD changes** go via a PR — the `updpkgsums` CI runs `updpkgsums`, `makepkg`, and commits updated checksums and `.SRCINFO` back to the branch automatically
- **Action/workflow fixes** (`.github/actions/`, `.github/workflows/`) go directly to main, then open PRs are rebased on top
- Renovate has `automerge: true` — once CI passes, PRs merge automatically without manual review

## Testing PKGBUILD changes

Always build and verify locally before pushing:

```bash
cd <pkgname>
makepkg --nodeps   # or --syncdeps to install deps
tar -tf <pkg>.pkg.tar.zst | grep usr/share/icons  # verify installed files
sudo pacman -U <pkg>.pkg.tar.zst  # install and check
```

## Known gotchas

- **paru**: The Docker action uses `paru` built from source (not `paru-bin`) to avoid libalpm version mismatches. Do not switch back to `paru-bin`.
- **No runtime upgrades**: The entrypoint does NOT run `pacman -Syu` at runtime. The Docker image digest is kept fresh by Renovate instead.
- **gruvbox-plus-icon-theme**: Since v6.0.0 there are two theme folders (`Gruvbox-Plus-Dark` and `Gruvbox-Plus-Light`) — both must be installed.

## Renovate

- Custom regex manager detects `pkgver=X.Y.Z # renovate: datasource=... depName=...` in PKGBUILDs
- Docker image digest in `.github/actions/aur/Dockerfile` is kept up to date by Renovate
