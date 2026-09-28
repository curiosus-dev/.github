# Contributing

Thanks for helping! This guide applies to all [curiosus-dev](https://github.com/curiosus-dev) .NET libraries.

## Before you start

- **Bugs and features:** open an issue first for anything bigger than a small fix, so we can agree on the approach.
- **Security issues:** never in public issues, see the [security policy](SECURITY.md).

## Build and test

Everything runs through [Cake](https://cakebuild.net/), the same way as on CI:

```bash
dotnet tool restore                      # once after clone
dotnet cake                              # clean, build, all tests
dotnet cake --target=UnitTests           # unit tests only
dotnet cake --target=IntegrationTests    # integration tests (some need Docker)
```

The required .NET SDK versions are listed in the repository README.

## Pull requests

1. Fork the repository and create a branch from the default branch.
2. Keep the change focused: one fix or feature per pull request.
3. Add or update tests for the changed behavior.
4. Follow the code style: `.editorconfig` in the repository is the source of truth (4 spaces, 130 characters per line,
   nullable reference types, XML docs on public APIs).
5. Add an entry to the package `CHANGELOG.md` under `## [Unreleased]` in [Keep a Changelog](https://keepachangelog.com)
   format. Breaking changes are marked with **Breaking:**.
6. Don't add version sections to the CHANGELOG: the package version comes from its top `## [x.y.z]` section,
   maintainers add it when releasing.
7. Title the pull request in the [Conventional Commits](https://www.conventionalcommits.org) format
   (`fix(email.smtp): validate server certificates`), the merge commit takes it. Breaking changes get `!` after the type.

CI must be green before a pull request is merged. Workflow runs from first-time contributors need a maintainer's
approval, so the first run may take a while to start.

## Releases

Packages follow [Semantic Versioning](https://semver.org). The CHANGELOG is the only place for a version: maintainers
release a package by turning its `## [Unreleased]` section into `## [x.y.z] - yyyy-mm-dd`. Merging to the default branch
publishes every version that is not on nuget.org yet and creates a tag and a GitHub release with the section as notes.
The pull request build summary lists the packages the merge will release.

## License

By contributing you agree that your contributions are licensed under the license of the repository (MIT).
