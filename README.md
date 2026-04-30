# Hogwarts Legacy Companion Overlay

A standalone Windows overlay UI built with Direct3D 11 + Dear ImGui.
Single-file `HogwartsCompanion.exe`, no external dependencies (DLLs, assets,
or runtime redists). Background image, icon, manifest and version info are
embedded as Win32 resources.

> Status: **mockup / UI demo**. The interface lists 48+ entries grouped into
> 5 tabs (Combat / Magic / Movement / Items / World). Toggles are visual
> state only — no game-process interaction.

---

## Features

- Borderless rounded window (D3D11 swap-chain, ImGui rendering)
- Animated splash with witch-on-broom + magical particles (~3.4 s)
- 5 tabs / 48+ entries with hotkey hints
- Editor sliders (Damage×, Speed×, Game Speed, FOV, NG+, etc.)
- Custom title bar with `INSERT` show/hide and `ESC` quit
- DPI aware (PerMonitorV2), Per-monitor scaling
- Footer plate: `Trainer v2.0 • Game v1.10 Definitive • Built <date>`
- Single self-contained `.exe` (~2 MB), MSVC `/MT` static CRT
- Authenticode SHA-256 signed (self-signed `CN=Dayn Studio`) + RFC 3161 timestamp

## Build

Requirements: **MSVC 2022/2026** with the C++17 toolset, Windows 10 SDK.

```bat
:: from a Developer Command Prompt
build.bat
```

Output: `build\HogwartsCompanion.exe`.

`build.bat` automatically clones Dear ImGui into `third_party\imgui` if it
is missing.

### Compile / link flags (AV-hardening)

```
/std:c++17 /O2 /GL /MT /EHsc /Gy /GS /guard:cf /sdl
/NOLOGO /SUBSYSTEM:WINDOWS /OPT:REF /OPT:ICF /LTCG
/GUARD:CF /DYNAMICBASE /HIGHENTROPYVA /NXCOMPAT
```

### Sign (optional)

```powershell
$cert = Get-ChildItem Cert:\CurrentUser\My |
        Where-Object { $_.Subject -eq 'CN=Dayn Studio' -and $_.HasPrivateKey } |
        Select-Object -First 1
Set-AuthenticodeSignature -FilePath .\build\HogwartsCompanion.exe `
    -Certificate $cert -HashAlgorithm SHA256 `
    -TimestampServer 'http://timestamp.digicert.com'
```

The public certificate is shipped as `DaynStudio.cer` next to the binary.
Import it into `Trusted Root Certification Authorities` (current user) if
you want SmartScreen to recognise the publisher locally.

## Project layout

```
.
├── main.cpp           D3D11 + ImGui application (single TU)
├── app.rc             icon, background, manifest, VERSIONINFO
├── app.manifest       asInvoker, PerMonitorV2 DPI, supportedOS Win 8.1+
├── app.ico            multi-resolution icon
├── background.jpg     embedded as RCDATA 102
├── build.bat          MSVC build script
└── third_party/imgui  Dear ImGui (cloned by build.bat)
```

## Hotkeys

- `INSERT` — show / hide overlay
- `ESC` — quit
- Per-feature hotkeys are listed inside each tab
  (Num1-0, Ctrl+Num1-5, Alt+Num1-5, F1-F8, …)

## License

[MIT](LICENSE) © 2026 Dayn Studio.

This project is **not** affiliated with Warner Bros., Avalanche Software,
Portkey Games or the Wizarding World franchise. "Hogwarts Legacy" is a
trademark of its respective owners and is referenced solely to describe the
demonstration purpose of this UI.
