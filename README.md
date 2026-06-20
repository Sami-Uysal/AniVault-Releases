# AniVault Releases

Distribution repository for **AniVault** — a Windows desktop anime app.

This repo holds **no source code**. It exists only to host the compiled builds and serve the **auto-update feed** that the app reads.

## What's in each release

Every published release attaches:

| File | Purpose |
|------|---------|
| `AniVault-Setup-<version>.exe` | NSIS installer (auto-updating build) |
| `AniVault-<version>.exe` | Portable build (no install) |
| `latest.yml` | Update manifest read by electron-updater |
| `*.blockmap` | Enables small delta downloads between versions |

## How auto-update works

1. An installed AniVault checks this repo's **latest release** on startup (via `electron-updater`).
2. If `latest.yml` lists a newer version, the new installer is downloaded in the background.
3. The update is applied on the next restart.

Portable builds do not auto-update — download the newer `.exe` manually.

## For users

Just grab the latest from the [Releases](../../releases/latest) page. No need to clone or build anything here.

## For the maintainer

Builds are published here automatically by `electron-builder` from the main project repo (`electron-builder --win nsis portable --publish`). Do not commit files manually — let the release pipeline upload the assets.
