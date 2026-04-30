# Changelog

All notable changes to this project are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] — 2026-04-30

### Added
- Rounded splash window (520×320, corner radius 28 px)
- Rounded main window (1180×760, corner radius 22 px) via `SetWindowRgn`
- Footer plate with `Trainer v2.0 • Game v1.10 Definitive • Built <date>`
- 5 tabs / 48+ entries (Combat, Magic, Movement, Items, World)
- Editor sliders (Damage×, Speed×, Game Speed, FOV, NG+, Auto-Loot Radius)
- Authenticode SHA-256 signature with RFC 3161 timestamp
- Embedded `app.manifest` (asInvoker, PerMonitorV2 DPI, supportedOS Win 8.1+)
- Neutral `VERSIONINFO` block (Dayn Studio / Hogwarts Legacy Companion)

### Changed
- Window centered on the primary monitor work area
- Splash auto-resizes to full UI on completion (~3.4 s)
- Cards rendered with translucent backgrounds (alpha 130)

### Removed
- Test "H" glyph from header
- Spiral / vortex letter animation on splash

### Security / hardening
- `/GS /guard:cf /sdl` compile flags
- `/GUARD:CF /DYNAMICBASE /HIGHENTROPYVA /NXCOMPAT` linker flags
- `INSERT` / `ESC` handled via `WM_KEYDOWN` (no `GetAsyncKeyState`)
