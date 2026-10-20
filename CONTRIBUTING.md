# Contributing to FocusRGB

Thanks for your interest! FocusRGB is developed in small, reviewed slices. These rules apply to
every repository in the organization unless a repository has its own `CONTRIBUTING.md`.

## Before you start

- **Bugs and ideas:** open an issue in the [main repository](https://github.com/FocusRGB/FocusRGB/issues)
  first, so the work can be placed on the [roadmap](https://github.com/orgs/FocusRGB/projects/1).
- **Security problems:** see [SECURITY.md](SECURITY.md). Never report them in a public issue.
- **Writing a plugin:** use the SDK for your language from
  [FocusRGB-Plugin-SDK](https://github.com/FocusRGB/FocusRGB-Plugin-SDK). The protocol is defined in
  the main repository under `sdk/spec/`.

## Branches and pull requests

- `develop` is the default branch, and `main` only changes through releases.
- Branch from `develop` with one of these prefixes: `feature/`, `slice/`, `fix/`, `chore/` or
  `docs/`. The `branch-policy` check rejects other names. The only exception is Dependabot's
  `dependabot/` branches.
- Open the pull request into `develop`, link its issue, and describe how you verified the change.
- Make small, focused commits rather than one large commit.
- All review conversations must be resolved before merging.

## Code

- Follow the repository's `.editorconfig` and existing conventions.
- Add or update tests for behaviour you change. The Release build must have no warnings.
- Don't commit build output, local caches (`build/`, `graphify-out/`), secrets or machine-specific
  paths.

## AI assistance

If an AI assistant helped with a commit or pull request, say so with an `Assisted-by: <tool>`
trailer, for example `Assisted-by: OpenAI Codex` or `Assisted-by: Claude`.

## License

By contributing you agree that your contributions are licensed under the MIT license.

Assisted-by: Claude
