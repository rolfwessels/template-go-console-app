# 🌐 template-go-console-app

[![GitHub release](https://img.shields.io/github/v/release/rolfwessels/template-go-console-app)](https://github.com/rolfwessels/template-go-console-app/releases)
[![Go CI](https://github.com/rolfwessels/template-go-console-app/actions/workflows/github-action.yml/badge.svg)](https://github.com/rolfwessels/template-go-console-app/actions/workflows/github-action.yml)

A Go CLI starter with a version-printing command, a development container, and release builds for Linux, macOS, and Windows.

## 🛠 Prerequisites

- Git and `make` (use WSL on Windows for the Makefile commands).
- Go 1.26 for local development, or Docker with Compose for the development container.

## 🚀 Quick start

Run this command from the repository root with Go installed. To use Docker, first run `make build up` on the host and continue in the development shell it opens.

```sh
make start
```

The starter prints its development version.

```text
template-go-console-app vdev
```

The dev shell shows a 🐳 prompt and saves Zsh history in a project volume across `make down` and rebuilds.

## 📋 Make commands

| Command | Purpose |
| --- | --- |
| `make start` | Run the CLI. |
| `make test` | Run the Go tests. |
| `make scan` | Audit imported Go packages and the Go standard library. |
| `make verify` | Run tests and the dependency audit. |
| `make build up` | Build the development container and open its shell. |
| `make down` | Stop the development container from the host. |

Run `make help` for more targets.

## 💻 Development

The command and its tests live in `cmd/template-go-console-app/`. See [AGENTS.md](AGENTS.md) for branch naming, pull requests, and verification.

## 📦 Releases and deployment

- `make publish` builds five platform archives under `dist/`. On Linux amd64, run `make install` on the host afterward to link the local binary into `~/.local/bin`.
- Pull request builds attach archives as workflow artifacts. Merges to `main` publish a versioned [GitHub release](https://github.com/rolfwessels/template-go-console-app/releases). To update a downloaded binary, extract the latest archive for your platform and replace the old copy.
- Set the major and minor version with `versionPrefix` in the Makefile. The patch comes from the Git commit count. Run `make version` to see the resulting version.
- Use `make docker-build` to build the runtime image or `make docker-publish` to build and push it after configuring your registry.
