# Create Release Action

![Release](https://github.com/subhamay-bhattacharyya-gha/create-release-action/actions/workflows/release.yaml/badge.svg)&nbsp;![Commit Activity](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Last Commit](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Release Date](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Repo Size](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![File Count](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Issues](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Top Language](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Custom Endpoint](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/bd48a52f9262cccab0a0b390bcc12680/raw/create-release-action.json?)

## Overview

A composite GitHub Action that automates the creation of timestamped release tags and draft GitHub releases. This action generates sequential release tags in the format `Rel-<sequence>-YYYYMMDDHHMMSS` and creates draft releases with auto-generated changelogs.

## Features

- **Sequential Release Tags**: Generates the next release tag using the latest tag in format `Rel-<sequence>-YYYYMMDDHHMMSS`
- **Draft Release Creation**: Automatically creates draft GitHub releases
- **Changelog Generation**: Creates detailed changelog entries from commit history since the last tag
- **Asset Collection**: Supports attaching release assets (zip/tar.gz files from dist directory)
- **Timestamped Releases**: Each release includes a UTC timestamp for precise tracking

## Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `github-token` | GitHub token for API access and authentication | Yes | — |
| `release-tag` | Optional release tag to checkout (defaults to current branch) | No | — |

## Outputs

| Name | Description |
|------|-------------|
| `new-tag` | The new release tag (e.g., Rel-004-20250702191245) |
| `release_url` | The URL of the created draft release |

## Usage

### Basic Example

```yaml
name: Create Release

on:
  push:
    branches: [main]

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: subhamay-bhattacharyya-gha/create-release-action@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

### With Release Tag Output

```yaml
- uses: subhamay-bhattacharyya-gha/create-release-action@main
  id: create-release
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}

- name: Display release info
  run: |
    echo "Created tag: ${{ steps.create-release.outputs.new-tag }}"
    echo "Release URL: ${{ steps.create-release.outputs.release_url }}"
```

## Requirements

- GitHub token with permissions to create releases
- Repository with Git history (tags will be fetched automatically)

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
