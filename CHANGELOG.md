# Changelog

All notable changes to MeedyaDL-Tools will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- **9 new tools**: yt-dlp, aria2c, fpcalc, get_iplayer, Votify, gytmdl, gamdl, AMdecrypt, Wrapper
- **Expanded platform support**: Linux aarch64, Windows ARM64, macOS ARM (Apple Silicon), Linux armhf (Raspberry Pi)
- **PyInstaller builds**: Standalone executables for Python tools (Votify, gytmdl, gamdl) across all platforms
- **Multi-job CI workflow**: Parallel builds for binary downloads and Python tool compilation
- **CI triggers**: Push to main, PR with `update-tools` label, monthly schedule, manual dispatch
- **GitHub Issue templates**: Bug report, feature request, tool update request
- **Pull request template**: Standardized PR checklist
- **Dependabot**: Automated GitHub Actions version updates
- **Documentation**: LICENSE.md, CHANGELOG.md, DEV_Status.md, .claude/CLAUDE.md
- **.gitignore**: Exclude build artifacts, OS files, local settings
- **.gitattributes**: Collapse .claude/ in GitHub UI, normalize line endings

### Changed
- **populate.yml**: Complete rewrite from single-job to multi-job architecture
- **README.md**: Expanded with full tool listing, platform matrix, and usage instructions
- **Asset naming**: Standardized to `{tool}-{os}-{arch}.{ext}` convention

## [0.1.0] - 2026-02-22

### Added
- Initial repository setup
- Populate Tools workflow for FFmpeg, mp4decrypt, N_m3u8DL-RE, MP4Box
- Support for Linux x86_64, Windows x86_64, macOS (via Rosetta 2)
- Monthly automated updates
- Basic README documentation
