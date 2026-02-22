# MeedyaDL-Tools

Pre-built external tool binaries for [MeedyaDL](https://github.com/MWBMPartners/MeedyaDL).

## Purpose

This repository serves as a **mirror** for external tool binaries that MeedyaDL depends on at runtime:

- **Fallback distribution** — When upstream sources are unavailable (404, timeout, naming changes), MeedyaDL falls back to downloading from this repo's `latest` release.
- **Installer bundling** — Release builds bundle these tools directly into MeedyaDL installers for a zero-download first-run experience.

## Hosted Tools

| Tool | Description | Upstream Source | License |
| ---- | ----------- | -------------- | ------- |
| **FFmpeg** | Media encoder/decoder | [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) | GPL v2+ |
| **yt-dlp** | Video/audio downloader | [yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) | Unlicense |
| **mp4decrypt** | MP4 DRM decryption | [Bento4 SDK](https://www.bok.net/Bento4/) | GPL v2 |
| **MP4Box** | MP4 multiplexer | [GPAC](https://gpac.io/) | LGPL v2.1 |
| **N_m3u8DL-RE** | HLS/DASH downloader | [nilaoda/N_m3u8DL-RE](https://github.com/nilaoda/N_m3u8DL-RE) | MIT |
| **aria2c** | Multi-protocol downloader | [aria2/aria2](https://github.com/aria2/aria2) | GPL v2 |
| **fpcalc** | Audio fingerprinting (AcoustID) | [acoustid/chromaprint](https://github.com/acoustid/chromaprint) | LGPL v2.1 |
| **get_iplayer** | BBC iPlayer downloader | [get-iplayer/get_iplayer](https://github.com/get-iplayer/get_iplayer) | GPL v3 |
| **Votify** | Spotify downloader | [glomatico/votify](https://github.com/glomatico/votify) | — |
| **gytmdl** | YouTube Music downloader | [glomatico/gytmdl](https://github.com/glomatico/gytmdl) | — |
| **gamdl** | Apple Music downloader | [glomatico/gamdl](https://github.com/glomatico/gamdl) | — |
| **AMdecrypt** | Apple Music decryption bridge | [glomatico/amdecrypt](https://github.com/glomatico/amdecrypt) | — |
| **Wrapper** | FairPlay DRM decryption server | [WorldObservationLog/wrapper](https://github.com/WorldObservationLog/wrapper) | — |

## Platform Support

| Tool | Linux x86_64 | Linux aarch64 | Linux armhf | Windows x64 | Windows ARM64 | macOS ARM |
| ---- | :---: | :---: | :---: | :---: | :---: | :---: |
| FFmpeg | Y | Y | — | Y | — | Y |
| yt-dlp | Y | Y | — | Y | Y | Y |
| mp4decrypt | Y | — | — | Y | — | Y |
| MP4Box | Y | — | — | Y | — | Y |
| N_m3u8DL-RE | Y | Y | — | Y | Y | Y |
| aria2c | Y | — | — | Y | — | Y |
| fpcalc | Y | Y | — | Y | — | Y |
| get_iplayer | Y* | Y* | Y* | Y** | — | Y* |
| Votify | Y | Y | — | Y | — | Y |
| gytmdl | Y | Y | — | Y | — | Y |
| gamdl | Y | Y | — | Y | — | Y |
| AMdecrypt | Y | Y | — | Y | Y | Y |
| Wrapper | Y | — | — | — | — | — |

**Y** = pre-built binary &nbsp; **Y*** = Perl script (requires Perl runtime) &nbsp; **Y**** = Windows installer &nbsp; **—** = not available

## Asset Naming Convention

```text
{tool_id}-{os}-{arch}.{ext}
```

| Component | Values |
| --------- | ------ |
| `tool_id` | `ffmpeg`, `yt-dlp`, `mp4decrypt`, `mp4box`, `nm3u8dlre`, `aria2c`, `fpcalc`, `get_iplayer`, `votify`, `gytmdl`, `gamdl`, `amdecrypt`, `wrapper` |
| `os` | `linux`, `windows`, `macos` |
| `arch` | `x86_64`, `x86`, `aarch64`, `armhf` |
| `ext` | `.tar.gz` (Linux/macOS), `.zip` (Windows), `.exe` (installers) |

## Automation

The **Populate Tools** workflow automatically:

1. Downloads latest binaries from all upstream sources
2. Builds Python tools (Votify, gytmdl, gamdl) via PyInstaller for each platform
3. Repackages everything with standardized names
4. Uploads to the `latest` GitHub Release

### Triggers

| Trigger | When |
| ------- | ---- |
| **Push to main** | Every commit to the main branch |
| **PR with label** | Pull requests labeled `update-tools` |
| **Monthly schedule** | 1st of each month at 06:00 UTC |
| **Manual** | Actions > Populate Tools > Run workflow |

## Usage

Download assets from the [latest release](../../releases/tag/latest):

```bash
# Example: download yt-dlp for Linux x86_64
curl -fL -o yt-dlp.tar.gz \
  "https://github.com/MeedyaDL/MeedyaDL-Tools/releases/download/latest/yt-dlp-linux-x86_64.tar.gz"
tar -xzf yt-dlp.tar.gz
./yt-dlp --version
```

## Contributing

1. Fork and create a branch
2. Make your changes
3. Add the `update-tools` label to your PR to trigger a test build
4. Submit for review

See [DEV_Status.md](DEV_Status.md) for current build status and known issues.

## License

The automation code in this repository is MIT licensed. Bundled tool binaries are redistributed under their respective upstream licenses. See [LICENSE.md](LICENSE.md) for full details.
