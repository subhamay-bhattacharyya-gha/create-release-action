# Create Release GitHub Action

![Release](https://github.com/subhamay-bhattacharyya-gha/create-release-action/actions/workflows/release.yaml/badge.svg)&nbsp;![Commit Activity](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Last Commit](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Release Date](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Repo Size](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![File Count](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Issues](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Top Language](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/create-release-action)&nbsp;![Custom Endpoint](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/46c708478f131e15ec4fa24d658bc75d/raw/create-release-action.json?)

> 🔖 A composite GitHub Action that generates a timestamped release tag, creates a draft GitHub release, and optionally triggers auto-publish.

---

## 🧩 Action: `create-release-action`

This GitHub Action generates the **next release tag** in the format `Rel-<sequence>-YYYYMMDDHHMMSS`, creates a **draft release**, and optionally displays a **clickable publish link** that triggers a GitHub Action or external API.

---

## 🚀 Features

- Generates the next semantic release tag using the latest tag
- Formats tags as `Rel-<sequence>-<timestamp>`
- Creates a **draft release**
- Optionally attaches release assets from `dist/*.zip` or `dist/*.tar.gz`
- Displays a link to **manually or automatically publish** the release

---

## 🔧 Inputs

| Name           | Description                                  | Required |
|----------------|----------------------------------------------|----------|
| `github-token` | GitHub token used for API authentication     | ✅ Yes   |

---

## ✅ Outputs

| Name       | Description                        |
|------------|------------------------------------|
| `new-tag`  | The generated release tag (e.g. `Rel-003-20250714183045`) |

---

## 📦 Example Usage

```yaml
name: Create Release

on:
  workflow_dispatch:

jobs:
  generate-release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Generate release tag and create draft
        uses: subhamay-bhattacharyya-gha/create-release-action@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```
--

## License

MIT