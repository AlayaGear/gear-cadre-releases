# Gear Cadre — releases

Published installers for the [Gear Cadre](https://github.com/AlayaCapybara/gear-cadre) desktop app,
and the `latest.json` manifest its auto-updater reads.

**This repository holds no source.** It exists because the source repository is private, and the
Tauri updater fetches its manifest over an unauthenticated request — a private release URL would
404 for every client. Everything here is produced by `release.yml` in the source repository.

## What is here

Each release is published under the rolling **`latest`** tag, replaced on every release:

| file | what it is |
|---|---|
| `latest.json` | the update manifest — version, and a signed URL per platform |
| `*-setup.exe` | Windows installer (NSIS) |
| `*.app.tar.gz` | macOS app bundle, one per architecture |
| `*.sig` | the minisign signature for each artifact |

## Signing

Update artifacts are signed with minisign and verified by the client before installation; the public
key is compiled into the app. That is integrity for the update channel, and it is **separate from OS
code signing**, which these builds do not yet have — Windows SmartScreen and macOS Gatekeeper will
warn on a first manual download. See the source repository's `docs/install.md`.
