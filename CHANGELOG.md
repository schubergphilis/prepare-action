# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-05-04

### Added

- `task` (go-task) installed unconditionally for all project types and jobs, with checksum verification.
- `direnv` installed unconditionally for all project types and jobs, with per-architecture checksum verification.
- `version_task` input to pin the version of `task` to be installed (default: `3.50.0`).
- Checksum verification for `hadolint` downloads using the upstream `.sha256` file.
- Pinned `docker/setup-qemu-action` and `docker/setup-buildx-action` to immutable commit SHAs.
- `.pre-commit-config.yaml` with hooks for whitespace/EOF fixing, large-file checks, merge-conflict detection, secret scanning (gitleaks), and Conventional Commits enforcement.
- `CLAUDE.md` with repository guidance for Claude Code.

### Changed

- `job` input is now **required** (was optional with a default of `unknown`).
- Updated `version_checkov` default from `3.2.125` to `3.2.521`.
- Updated `version_hadolint` default from `2.12.0` to `2.14.0`.
- Upgraded `docker/setup-qemu-action` from `v3` to `v4.0.0` (pinned SHA).
- Upgraded `docker/setup-buildx-action` from `v1` to `v4.0.0` (pinned SHA).

### Removed

- `python` project type support (steps for `poetry`, `setup-python`, and dependency installation).
- `version_poetry` and `version_python` inputs.
- `version_direnv` input; the direnv version is now an internal implementation detail.
- `pipx` installation step.
