# MeedyaDL-Tools — Project Context

## Purpose

This repository is a **mirror host** for external/third-party tool binaries that [MeedyaDL](https://github.com/MWBMPartners/MeedyaDL) depends on at runtime. It serves two functions:

1. **Fallback distribution**: When upstream tool sources are unavailable (404, timeout, naming changes), MeedyaDL falls back to this repo's `latest` release.
2. **Installer bundling**: Release builds bundle these tools directly into MeedyaDL installers for a zero-download first-run experience.

## Architecture

- **No source code is compiled here** (except Python tools via PyInstaller in CI)
- The repo contains only automation (GitHub Actions workflows), documentation, and configuration
- All tool binaries live in the `latest` GitHub Release as assets, not in the git tree
- The `populate.yml` workflow handles downloading, repackaging, and uploading

## Asset Naming Convention

```
{tool_id}-{os}-{arch}.{ext}
```

- `os`: `linux`, `windows`, `macos`
- `arch`: `x86_64`, `x86`, `aarch64`, `armhf`
- `ext`: `.tar.gz` (Linux/macOS), `.zip` (Windows)

## Mirrored Tools

| Tool | Type | Source |
|------|------|--------|
| FFmpeg | Pre-built binary | BtbN/FFmpeg-Builds, evermeet.cx |
| yt-dlp | Pre-built binary | yt-dlp/yt-dlp releases |
| mp4decrypt | Pre-built binary | Bento4 SDK |
| MP4Box | Pre-built binary | GPAC installers |
| N_m3u8DL-RE | Pre-built binary | nilaoda/N_m3u8DL-RE releases |
| aria2c | Pre-built binary | aria2/aria2 releases |
| fpcalc | Pre-built binary | acoustid/chromaprint releases |
| AMdecrypt | Pre-built binary (Go) | glomatico/amdecrypt releases |
| Wrapper | Pre-built binary (C/C++) | WorldObservationLog/wrapper releases |
| get_iplayer | Perl script + Win installer | get-iplayer/get_iplayer releases |
| Votify | PyInstaller build | glomatico/votify (PyPI) |
| gytmdl | PyInstaller build | glomatico/gytmdl (PyPI) |
| gamdl | PyInstaller build | glomatico/gamdl (PyPI) |

## Key Files

- `.github/workflows/populate.yml` — Main CI workflow (the core of this repo)
- `README.md` — Public-facing documentation
- `LICENSE.md` — Combined licensing for all tools
- `DEV_Status.md` — Tool availability and build status tracker
- `CHANGELOG.md` — Version history

## Conventions

- Always use `continue-on-error: true` for platforms with unreliable upstream support
- Always use `set -euo pipefail` at the start of shell steps
- Clean up `work/` directories after each tool extraction
- Use `curl -fL --retry 3` for all downloads
- Log progress with `→` (start), `✓` (success), `⚠` (warning/skip)

## Maintenance

When updating this repo:
- Keep CHANGELOG.md, README.md, and DEV_Status.md in sync
- Ensure .gitignore covers any new artifact patterns
- Update the tool-by-platform matrix in DEV_Status.md when adding tools/platforms
