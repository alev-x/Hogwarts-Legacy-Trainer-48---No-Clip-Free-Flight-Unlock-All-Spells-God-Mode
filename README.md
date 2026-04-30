<div align="center">

# ✨ Hogwarts Legacy Ultimate Trainer ✨

<div align="center">
 
  <img width="1171" height="754" alt="image" src="https://github.com/user-attachments/assets/b7a9136b-5985-4aa8-86da-f6d8bf8a0398" />

  **Unleash the True Magic Within You**

  Imagine that the boundaries of the Hogwarts world no longer exist.  
  You can walk through ancient stone walls, soar over the Forbidden Forest without a broom, instantly master all spells, and create your own legendary story.

  This trainer is made for those who want to experience **Hogwarts Legacy** with complete freedom — brightly, powerfully, and without any limitations.

</div>

---

### 🌟 Why This Trainer Stands Out

We’ve combined the most popular features with the rarest and most requested ones that other trainers still don’t have:

- **No Clip Mode** — walk through any walls and objects  
- **Free Flight** — true free flight anywhere in the game  
- **Instant Unlock All Spells** — including the Unforgivable Curses  
- **Unlimited Talent Points** — develop your character exactly as you dream  
- **Free Crafting** — craft without spending any materials  
- **Instant Plant Growth & Potion Brewing**  
- **Change Appearance Anytime** — customize your character whenever you want  
- **Unlock All Fast Travel Points** with one click  

Plus many powerful classic tools: God Mode, no spell cooldown, super jump, time of day control, and much more.

---

### 🔥 Main Features

**🛡️ Combat & Survival**
- Infinite Health (God Mode)
- One Hit Kill
- Instant Spell Cooldown
- Increased Magic Power

**🌌 Freedom & Exploration**
- Free Flight + No Clip Mode
- Super Jump
- Permanent NPC Stealth
- Unlock All Fast Travel Points

**🧪 Magic & Progression**
- Unlimited Talent Points
- Instant Unlock All Spells
- Free Crafting (No Resources)
- Instant Plant Growth & Potion Brewing

**⚙️ World Control**
- Change Time of Day
- Player & Game Speed Multiplier
- Infinite Broom Boost

---

### 📥 Download Trainer

[![Download Hogwarts Legacy Trainer v2.0](https://img.shields.io/badge/⬇️%20DOWNLOAD%20TRAINER%20v2.0-00C853?style=for-the-badge&logo=download&logoColor=white)](https://github.com/твой-ник/repo/releases/latest)

**Version:** 2.0 — April 2026  
**Compatibility:** Latest versions of Hogwarts Legacy (Steam / Epic Games)

> It is highly recommended to use this trainer on a separate save file.

---

### SEO Keywords

**English:** Hogwarts Legacy trainer, Hogwarts Legacy no clip, free flight Hogwarts Legacy, unlock all spells Hogwarts Legacy, unlimited talent points Hogwarts Legacy, god mode Hogwarts Legacy, free crafting Hogwarts Legacy, instant all spells Hogwarts Legacy

**Русский:** трейнер Hogwarts Legacy, хогвартс легаси трейнер, но клип хогвартс легаси, свободный полет хогвартс легаси, все заклинания хогвартс легаси, бесконечные очки талантов хогвартс, год мод хогвартс легаси

**Deutsch:** Hogwarts Legacy Trainer, No Clip Hogwarts Legacy, Freier Flug Hogwarts Legacy, Alle Zauber freischalten, Unbegrenzte Talentpunkte Hogwarts Legacy, God Mode Hogwarts Legacy

**Español:** Trainer Hogwarts Legacy, No Clip Hogwarts Legacy, Vuelo libre Hogwarts Legacy, Desbloquear todos hechizos, Puntos de talento ilimitados, Modo Dios Hogwarts Legacy

**Français:** Trainer Hogwarts Legacy, No Clip Hogwarts Legacy, Vol libre Hogwarts Legacy, Débloquer tous les sorts, Points de talent illimités, God Mode Hogwarts Legacy

**Português:** Trainer Hogwarts Legacy, No Clip Hogwarts Legacy, Voo livre Hogwarts Legacy, Desbloquear todos feitiços, Pontos de talento infinitos, Modo Deus Hogwarts Legacy
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
