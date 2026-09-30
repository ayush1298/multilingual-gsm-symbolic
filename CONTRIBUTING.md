# Contributing

## Setup

```bash
make install
```

## Testing

```bash
make test
```

## Linting

```bash
make lint
```

## Publishing

Releases are automated with [python-semantic-release](https://python-semantic-release.readthedocs.io/) (see `.github/workflows/release.yml`).
When the tests pass on `main`, the version is bumped based on the [conventional commit](https://www.conventionalcommits.org/) messages since the last release, a `vX.Y.Z` tag is pushed, and the package is published to PyPI and GitHub Releases:

- `feat: ...` bumps the minor version (0.4.14 → 0.5.0)
- `fix: ...` or `perf: ...` bumps the patch version (0.4.14 → 0.4.15)
- other prefixes (`docs:`, `ci:`, `chore:`, ...) or non-conventional messages do not trigger a release

As PRs are squash-merged, it is the PR title that decides the release, so make sure it uses the right prefix.

The package version is not stored in `pyproject.toml`; it is read from the latest git tag at build time (via `hatch-vcs`), so a release only pushes a tag and never commits to `main`.

To publish manually instead:

```bash
# Build and publish to PyPI
uv build
uv publish
```

Credentials can be provided via `UV_PUBLISH_TOKEN` or with `--token` / `--username` + `--password` flags.
See the [uv publish docs](https://docs.astral.sh/uv/guides/publish/) for details.
