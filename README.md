# MeedyaDL-Tools

Pre-built external tool binaries for [MeedyaDL](https://github.com/MeedyaDL/MeedyaDL).

## Purpose

This repository serves as a **mirror** for external tool binaries that MeedyaDL depends on at runtime. When upstream sources are unavailable (404, timeout, naming changes), MeedyaDL's dependency manager falls back to downloading from this repo's `latest` release.

Release builds also bundle these tools directly into the installer for a zero-download first-run experience.

## Asset Naming Convention

```
{tool_id}-{os}-{arch}.{ext}
```

| Component | Values |
|-----------|--------|
| `tool_id` | `ffmpeg`, `mp4decrypt`, `nm3u8dlre`, `mp4box` |
| `os` | `linux`, `windows`, `macos` |
| `arch` | `x86_64`, `aarch64` |
| `ext` | `.tar.gz` (Linux/macOS), `.zip` (Windows) |

## Hosted Tools

| Tool | Upstream Source | Platforms |
|------|---------------|-----------|
| **FFmpeg** | [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) (Linux/Windows), [evermeet.cx](https://evermeet.cx/ffmpeg/) (macOS) | All |
| **mp4decrypt** | [Bento4 SDK](https://www.bok.net/Bento4/) | macOS (universal), Linux x64, Windows x64 |
| **N_m3u8DL-RE** | [nilaoda/N_m3u8DL-RE](https://github.com/nilaoda/N_m3u8DL-RE) | All |
| **MP4Box** | [GPAC](https://gpac.io/) | Linux x64, Windows x64, macOS |

## Updating

The **Populate Tools** workflow (`Actions > Populate Tools > Run workflow`) downloads the latest binaries from all upstream sources, repackages them with standardized names, and uploads them to the `latest` release. It also runs automatically on the 1st of each month.

## License

The binaries hosted here are redistributed under their respective upstream licenses. This repository only provides packaging automation.
