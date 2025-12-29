# Create Release Action

![Release](https://github.com/subhamay-bhattacharyya-gha/create-release-action/actions/workflows/release.yaml/badge.svg)&nbsp;![Commit Activity](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Last Commit](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Release Date](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Repo Size](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![File Count](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Issues](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Top Language](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Custom Endpoint](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/bd48a52f9262cccab0a0b390bcc12680/raw/create-release-action.json?)

## Overview

A composite GitHub Action that automates semantic versioning and release management for your projects. This action leverages semantic-release to analyze commits, generate changelogs, and publish releases automatically.

## Features

- **Semantic Versioning**: Automatically determines the next version based on conventional commits
- **Release Notes Generation**: Creates detailed changelog entries from commit history
- **Automated Publishing**: Publishes releases to npm, GitHub, and other configured platforms
- **Commit Verification**: Validates commits before release
- **Release Conditions Verification**: Ensures all conditions are met before proceeding with release

## Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `github-token` | GitHub token for API access and authentication | Yes | — |
| `npm-token` | NPM token for publishing to npm registry (if needed) | No | — |
| `working-directory` | Working directory for the release process | No | `.` |

## Outputs

| Name | Description |
|------|-------------|
| `new-release-published` | Boolean indicating if a new release was published |
| `release-version` | The version of the release |
| `release-notes` | Generated release notes/changelog |

## Usage

### Basic Example

```yaml
name: Semantic Release

on:
  push:
    branches: [main]

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - uses: subhamay-bhattacharyya-gha/create-release-action@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

### With NPM Publishing

```yaml
- uses: subhamay-bhattacharyya-gha/create-release-action@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    npm-token: ${{ secrets.NPM_TOKEN }}
```

## Requirements

- Node.js and npm pre-configured in your environment
- Conventional commit messages for automatic versioning
- A properly formatted `package.json` in your repository

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
