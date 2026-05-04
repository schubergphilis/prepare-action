# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A GitHub composite action (`action.yml`) that prepares runner environments for specific project types and pipeline jobs. It is Linux-only and supports `amd64` and `arm64` architectures.

Supported combinations:

| `type`      | `job`  | Tools installed                   |
| ----------- | ------ | --------------------------------- |
| `container` | `lint` | task, direnv, hadolint            |
| `container` | `scan` | task, direnv, checkov             |
| `container` | `ci`   | task, direnv, QEMU                |
| `container` | `cd`   | task, direnv, QEMU, Docker Buildx |

`task` and `direnv` are installed unconditionally for all types/jobs. Every tool download is checksum-verified before installation.

## Local Development

Lint the action file:
```bash
yamllint action.yml
```

Run pre-commit checks:
```bash
pre-commit run --all-files
```

The CI pipeline (`.github/workflows/pipeline.yml`) runs `yamllint` and then exercises all job/type combinations against the live action using `uses: ./`.

## Conventions

- Commits must follow **Conventional Commits** format (enforced by `conventional-pre-commit` hook at commit-msg stage).
- Tool versions are exposed as optional inputs with pinned defaults; checksums must be updated whenever a default version changes.
