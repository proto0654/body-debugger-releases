# Body Debugger — release feed

This repository holds release artifacts for the Body Debugger desktop app. Application source is kept in a separate private repository.

## What a release contains

| File | Purpose |
|------|---------|
| `Body-Debugger-Setup-<version>.exe` | Per-user NSIS installer for Windows (no administrator rights) |
| `...exe.blockmap` | Differential download data for `electron-updater` |
| `latest.yml` | The update feed: version, installer SHA-512, size |

An installed application reads `latest.yml`, compares the version with its own, downloads a newer installer in the background and asks the user to restart. It never restarts on its own.

## Rules

- Do not edit `latest.yml` or rename artifacts by hand — `electron-builder` generates them.
- Prerelease versions (`0.2.0-beta.2`) are published for closed testing.
- Rollback: publish the previous installer under its own release tag and reinstall it; user data lives in the OS profile and is not touched by install or uninstall.

## Status

Release automation is not wired up yet. Until then the repository holds an empty README only.