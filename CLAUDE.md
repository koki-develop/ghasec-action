# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

GitHub Actions composite action that installs and runs [ghasec](https://github.com/koki-develop/ghasec) — a security linter for GitHub Actions workflows. This repo contains no build step or application code; the entire action is defined in `action.yml`.

## Architecture

- **`action.yml`** — The composite action definition. Uses [setup-ghasec](https://github.com/koki-develop/setup-ghasec) to install the binary, then runs `ghasec` with the configured inputs.
- Action inputs: `version` (ghasec version), `token` (GitHub token), `online` (enable network-dependent rules), `args` (extra CLI args).
- Output format is hardcoded to `--format github-actions` so results appear as PR annotations.

## Related Repositories

- **ghasec** (the CLI tool): https://github.com/koki-develop/ghasec
- **setup-ghasec** (installer action): https://github.com/koki-develop/setup-ghasec

## CI

CI runs on push to `main` and on PRs. It tests the action itself (`uses: ./`) across ubuntu, macos, and windows with three jobs: offline mode, online mode, and extra-args (custom format flags).

## Release

Releases are managed by [release-please](https://github.com/googleapis/release-please-action) with `simple` release type. Commit prefixes: `feat:` → Features, `fix:` → Patches.
