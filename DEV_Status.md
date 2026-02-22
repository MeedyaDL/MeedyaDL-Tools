# Development Status

Current build status and tool availability for MeedyaDL-Tools.

## Build Status

| Job | Status |
|-----|--------|
| Download Binaries | ![workflow](https://github.com/MeedyaDL/MeedyaDL-Tools/actions/workflows/populate.yml/badge.svg) |

## Tool-by-Platform Availability

| Tool | linux-x86_64 | linux-aarch64 | linux-x86 | linux-armhf | win-x86_64 | win-aarch64 | macos-aarch64 |
|------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| FFmpeg | OK | OK | — | — | OK | — | OK |
| yt-dlp | OK | OK | — | — | OK | OK | OK |
| mp4decrypt | OK | — | — | — | OK | — | OK |
| MP4Box | OK | — | — | — | OK | — | OK |
| N_m3u8DL-RE | OK | OK | — | — | OK | OK | OK |
| aria2c | OK* | — | — | — | OK | — | OK** |
| fpcalc | OK | OK | — | — | OK | — | OK |
| get_iplayer | OK*** | OK*** | — | OK*** | OK**** | — | OK*** |
| Votify | OK | OK | — | — | OK | — | OK |
| gytmdl | OK | OK | — | — | OK | — | OK |
| gamdl | OK | OK | — | — | OK | — | OK |
| AMdecrypt | OK | OK | OK | — | OK | OK | OK |
| Wrapper | OK | — | — | — | — | — | — |

**Legend:**
- **OK** = Pre-built binary downloaded from upstream
- **OK*** = Compiled from source in CI
- **OK**** = Installed via Homebrew in CI
- **OK***** = Perl script (requires Perl runtime on target)
- **OK****** = Windows installer (.exe)
- **—** = Not available (no upstream binary, cannot cross-compile)

## Known Limitations

### Platform Gaps

| Platform | Issue | Impact |
|----------|-------|--------|
| **Linux x86 (32-bit)** | Most upstream projects have dropped 32-bit support | Only AMdecrypt provides 32-bit Linux builds |
| **Windows ARM64** | Very few tools provide native ARM64 builds | Only yt-dlp, N_m3u8DL-RE, and AMdecrypt available |
| **Linux armhf** | Raspberry Pi 3 (32-bit ARM) has minimal support | Only get_iplayer (Perl script) available |
| **Wrapper** | Only supports Linux x86_64 | C/C++ project with no cross-platform releases |

### Build Notes

| Tool | Notes |
|------|-------|
| **aria2c (Linux)** | Compiled from source; linked against system OpenSSL |
| **aria2c (macOS)** | Installed via Homebrew; dynamically linked |
| **Python tools** | Built with PyInstaller `--onefile`; may have hidden import issues |
| **get_iplayer** | Perl script on Unix (requires `perl`); Windows installer bundles Perl |
| **FFmpeg (macOS)** | evermeet.cx provides x86_64 binary; runs via Rosetta 2 on Apple Silicon |
| **MP4Box** | Extracted from platform-specific installers (.deb, .exe, .pkg) |

## Version Tracking

Tool versions are automatically fetched from upstream on each CI run. Check the [latest release](https://github.com/MeedyaDL/MeedyaDL-Tools/releases/tag/latest) for current versions.

## Upstream Repositories

| Tool | Repository | Release Strategy |
|------|-----------|-----------------|
| FFmpeg | [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) | Rolling `latest` tag |
| yt-dlp | [yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) | Semver releases |
| mp4decrypt | [Bento4 SDK](https://www.bok.net/Bento4/) | Fixed version (pinned) |
| MP4Box | [GPAC](https://gpac.io/) | Nightly builds |
| N_m3u8DL-RE | [nilaoda/N_m3u8DL-RE](https://github.com/nilaoda/N_m3u8DL-RE) | Semver releases |
| aria2c | [aria2/aria2](https://github.com/aria2/aria2) | Semver releases |
| fpcalc | [acoustid/chromaprint](https://github.com/acoustid/chromaprint) | Semver releases |
| get_iplayer | [get-iplayer/get_iplayer](https://github.com/get-iplayer/get_iplayer) | Semver releases |
| Votify | [glomatico/votify](https://github.com/glomatico/votify) | PyPI releases |
| gytmdl | [glomatico/gytmdl](https://github.com/glomatico/gytmdl) | PyPI releases |
| gamdl | [glomatico/gamdl](https://github.com/glomatico/gamdl) | PyPI releases |
| AMdecrypt | [glomatico/amdecrypt](https://github.com/glomatico/amdecrypt) | GoReleaser |
| Wrapper | [WorldObservationLog/wrapper](https://github.com/WorldObservationLog/wrapper) | Commit-hash tags |
