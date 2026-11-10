<div align="center">

# MeetVision AI

**The free, on-device AI interview and meeting copilot that stays invisible on screen share.**

Real-time transcription, on-device screen reading, and instant AI talking points in a floating
overlay — visible to you, never to the people on the other side of the call.

[![Latest release](https://img.shields.io/github/v/release/devxadarsh/MeetVision.AI?label=latest%20release)](https://github.com/devxadarsh/MeetVision.AI/releases/latest)
[![Platforms](https://img.shields.io/badge/platforms-macOS%20%7C%20Windows-0ea5e9)](#download)
[![Price](https://img.shields.io/badge/price-free%20forever-16a34a)](https://meetvision-ai.com)
[![License](https://img.shields.io/badge/license-proprietary-6b7280)](#license)

[Website](https://meetvision-ai.com) · [Download](#download) · [Install](#install) · [FAQ](#faq) · [Support](#support)

[![Download for macOS](https://img.shields.io/badge/Download-macOS%20DMG-black?logo=apple&logoColor=white)](https://github.com/devxadarsh/MeetVision.AI/releases/latest)
[![Download for Windows](https://img.shields.io/badge/Download-Windows%20x64-0078D4?logo=windows&logoColor=white)](https://github.com/devxadarsh/MeetVision.AI/releases/latest)

</div>

---

## What is MeetVision AI?

MeetVision AI listens to your interview or meeting, transcribes the conversation on your own
machine, reads the screen you are sharing, and generates concise talking points and answers in a
floating HUD. The overlay is excluded from screen capture at the OS level, so it never appears in
Zoom, Google Meet, Microsoft Teams, or any other screen share.

It is built for interviews, sales calls, stand-ups, lectures, and any conversation where you want
fast, private, real-time support without a second pair of eyes.

### Highlights

- **Invisible on screen share** — native capture exclusion keeps the overlay and answers off every
  shared screen and recording.
- **On-device speech recognition by default** — NVIDIA Parakeet and Apple Speech run locally, with
  Metal/Neural Engine acceleration. No meeting audio leaves your machine unless you explicitly opt
  in to a cloud engine.
- **On-device screen reading** — OCR reads the shared screen on demand and turns it into queryable
  text, so the assistant can answer questions about what is actually on screen.
- **Context-aware answers** — matches your role, domain glossary, and project context; generate
  talking points for any transcript or OCR row on demand.
- **Live transcript with dictation** — speech streams into the active row with natural pause
  handling and smart voice-activity detection.
- **Two overlay styles** — a clean classic HUD or a modern glassmorphic HUD.
- **Detachable overlay** — split the control bar into its own always-on-top window, or dock it as a
  vertical icon strip on multi-monitor and ultrawide setups.
- **Post-meeting summaries** — structured overviews, key questions, and action items, exportable as
  Markdown.
- **Privacy first** — ephemeral RAM-only audio processing; no recordings or transcripts written to
  disk unless you enable it. Credentials are encrypted with the OS keychain.

---

## Download

Grab the latest build from the [Releases page](https://github.com/devxadarsh/MeetVision.AI/releases/latest).

| Platform | Architecture | Recommended asset |
| :--- | :--- | :--- |
| macOS | Apple Silicon (M1–M4) | `MeetVision AI-<version>-arm64.dmg` |
| macOS | Intel (x64) | `MeetVision AI-<version>-x64.dmg` |
| Windows | 64-bit (x64) | `MeetVision AI Setup <version>.exe` |

> The `.zip` builds for macOS are provided for users who prefer a portable archive. Most people
> should download the `.dmg`.

**System requirements**

- macOS 13 or later (macOS 14 or later is recommended for the accelerated on-device Parakeet Core ML
  engine), Apple Silicon or Intel.
- Windows 10 version 2004 or later, or Windows 11, 64-bit.
- A microphone or system-audio loopback for transcription.
- A free MeetVision account for AI answers. Audio and OCR run locally.

---

## Install

### macOS

1. Open the downloaded `.dmg`.
2. Drag **MeetVision AI** into the **Applications** folder.
3. Launch it from Applications.
4. Grant the permissions the app asks for — **Microphone**, **Screen Recording**, and
   **Accessibility** — then restart the app if prompted.
5. Optional: install [BlackHole 2ch](https://github.com/ExistentialAudio/BlackHole) if you want a
   dedicated virtual audio device. ScreenCaptureKit loopback and the built-in microphone also work.

If macOS blocks the first launch, open **System Settings → Privacy & Security**, find the MeetVision
AI notice, and choose **Open Anyway**. You can also right-click the app and choose **Open**.

### Windows

1. Run `MeetVision AI Setup <version>.exe`.
2. The installer is a one-click, per-user install — no administrator prompt and no install-location
   picker.
3. Launch **MeetVision AI** from the Start menu.
4. Allow microphone and screen-capture access when Windows asks.

If Windows SmartScreen shows a warning, choose **More info → Run anyway**. No extra audio driver is
needed on Windows; system audio is captured through OS loopback, and VB-Cable or Stereo Mix is
detected automatically if present.

### First run

1. Open **Settings → Account** and sign in with the free MeetVision account you registered at
   [meetvision-ai.com](https://meetvision-ai.com). AI requests are authenticated through your
   account.
2. Choose your speech engine. On-device Parakeet or Apple Speech is the default; Deepgram Nova-3 is
   an optional cloud engine that must be enabled explicitly.
3. Pick your overlay style, audio input, and voice-filter sensitivity.
4. Join a call and press `Cmd/Ctrl + Shift + H` to show the overlay.

---

## Keyboard shortcuts

Shortcuts are registered globally, so they work while Zoom, Meet, or Teams has focus.

| Action | macOS | Windows |
| :--- | :--- | :--- |
| Show / hide the overlay | `Cmd + Shift + H` | `Ctrl + Shift + H` |
| Toggle click-through mode | `Cmd + Shift + M` | `Ctrl + Shift + M` |
| Regenerate answer talking points | `Cmd + Shift + R` | `Ctrl + Shift + R` |
| Run a ScreenVision scan | `Cmd + Shift + S` | `Ctrl + Shift + S` |
| Give an answer for the latest row | `Alt` `Alt` (double-tap) | `Alt` `Alt` (double-tap) |
| Nudge the overlay by 30 px | `Cmd + Arrow` | `Ctrl + Arrow` |
| Nudge the overlay by 60 px | `Cmd + Shift + Arrow` | `Ctrl + Shift + Arrow` |
| Quit | `Cmd + Shift + Q` | `Ctrl + Shift + Q` |

---

## Privacy and security

- **Local by default.** Speech recognition and OCR run on your machine. Meeting audio is processed
  in memory and discarded.
- **Explicit cloud opt-in.** Cloud streaming STT (Deepgram Nova-3) is off by default and disclosed
  in Settings. Only spoken audio is streamed; silence is gated out locally.
- **Encrypted credentials.** Session tokens and any saved provider keys are protected with Electron
  `safeStorage` and the native OS keychain.
- **Locked-down desktop shell.** All windows run with `nodeIntegration: false`,
  `contextIsolation: true`, and `sandbox: true`, behind a strict Content Security Policy.
- **Visible capture indicator.** The listening/recording indicator cannot be hidden.

---

## FAQ

**Does the overlay really stay invisible when I share my screen?**
Yes. The app uses native OS capture exclusion on both overlay windows, so the HUD and its contents
are not captured by screen sharing or recording tools.

**Is my audio uploaded anywhere?**
Not with the default on-device engines. Audio stays local. If you explicitly choose a cloud speech
engine, audio is streamed to that provider and the choice is shown in Settings. AI answer generation
sends text (never audio) to the configured LLM provider.

**Do I need a paid subscription?**
No. MeetVision AI is free to use with a free MeetVision account — no credit card, no time limit.
Free-tier AI requests are routed to free OpenRouter models through the MeetVision proxy.

**Which platforms are supported?**
macOS on Apple Silicon and Intel, and 64-bit Windows 10/11. 32-bit Windows and Windows ARM64 are not
supported because no matching on-device speech runtime exists.

**Where is the source code?**
This repository distributes the compiled desktop builds. The application source is maintained in a
private repository.

**How do I update?**
Download the newest release from the [Releases page](https://github.com/devxadarsh/MeetVision.AI/releases/latest)
and install it over the current version. Your settings and encrypted credentials are preserved.

---

## About this repository

This is the public release channel for the MeetVision AI desktop application. It contains no
application source code. Each GitHub Release publishes the installers for that version:

- macOS DMG and ZIP for Apple Silicon and Intel
- Windows NSIS installer for x64

Please use the [issue tracker](https://github.com/devxadarsh/MeetVision.AI/issues) for bug reports
and feature requests, and include your OS version, app version, and a short description of what
happened.

## Support

- Website: [meetvision-ai.com](https://meetvision-ai.com)
- Email: [contact@meetvision-ai.com](mailto:contact@meetvision-ai.com)
- Releases: [github.com/devxadarsh/MeetVision.AI/releases](https://github.com/devxadarsh/MeetVision.AI/releases)
- Issues: [github.com/devxadarsh/MeetVision.AI/issues](https://github.com/devxadarsh/MeetVision.AI/issues)

## License

MeetVision AI is proprietary software. Copyright © MeetVision AI. All rights reserved.

The installers in this repository are published for end users of MeetVision AI. Redistribution,
reverse engineering, or repackaging of the application is not permitted without written permission.
The application source code is not part of this repository.
