# OkuRead

<img src="assets/okuread.png" width="96" height="96" alt="OkuRead: a picture, speaker, sparkle and magenta magnifier">

OkuRead makes text in screen images available to screen readers. It creates a
whole-screen OCR snapshot and can display replacement text at its source
positions. Reading text remains available when replacement text is hidden.

[Download the Windows installer](https://github.com/Cem-Kaya/oku_read_public/releases)
or [report a problem](https://github.com/Cem-Kaya/oku_read_public/issues).

The WinGet package is submitted as **CemKaya.OkuRead**. Follow the
[community submission](https://github.com/microsoft/winget-pkgs/pull/470112)
for its review and availability in the WinGet catalog.

## Install

The MSI installs for the current user. Setup downloads verified PP-OCRv6 Medium
models without requiring a GPU. The first requested read prepares TensorRT
engines locally and offline for the computer's NVIDIA GPU. Internet access is
required during setup; models are not bundled in the MSI.

When a requested read needs to prepare engines, a compact **One-time setup for
this GPU** window shows component progress and explains that preparation may
take a couple of minutes. Cancel or Escape stops the request; completed
engine files remain reusable. Cached reads skip this window. Preparation stays
offline.

OkuRead is currently unsigned. Verify the installer against the SHA256SUMS
published with its release. Included NVIDIA and other third-party components
retain their own license terms, which are included in the installation.

## Requirements and current limits

- 64-bit Windows and a supported NVIDIA RTX GPU with a compatible CUDA 12.9 driver.
- Every enabled display must currently be driven by a supported NVIDIA GPU.
  Displays driven by an Intel or AMD integrated GPU are not yet supported.
- Device preparation covers the RTX 2060, RTX 3050 family, RTX 4090 and RTX 5070 Ti
  architectures. Actual hardware qualification has so far been on an RTX 4090;
  this does not establish successful OCR use or performance on the other GPUs.

## Use

- **Ctrl+Alt+G:** open a new snapshot, or close the current overlay.
- **Refresh:** take a whole-screen snapshot without selecting an app. With Auto
  off this runs once; with Auto on the configured timer continues.
- **Pause / Resume:** remove or restore the snapshot's visual and accessible text.
- **Read:** open the snapshot as a reading document.
- **Auto:** refresh automatically; off by default. Settings includes As fast as
  possible, 2 FPS, 5 FPS and 15 FPS targets alongside the longer intervals. Reads
  run one at a time; actual speed depends on the GPU and screen content.
- **Settings → Start with Windows:** opt in to starting in the tray. Models stay
  unloaded until the first explicit read.

The installer creates desktop and Start menu shortcuts. The app, notification
area, taskbar, executables and installer use the same OkuRead icon.

| Action | Shortcut |
| --- | --- |
| Refresh | Ctrl+Alt+Shift+R |
| Pause / Resume | Ctrl+Alt+Shift+P |
| Auto on / off | Ctrl+Alt+Shift+A |
| Click through on / off | Ctrl+Alt+Shift+C |
| Show text on / off | Ctrl+Alt+Shift+T |
| Settings | Ctrl+Alt+Shift+S |
| Show controls | Ctrl+Alt+O |

Closing the overlay keeps OkuRead in the tray. Quit exits the application.
For a reading check, keep one snapshot unchanged for at least 60 seconds.

## Privacy

Screen capture and OCR processing stay on the computer. The application runtime
makes no network requests and does not save captured images, recognized text or
product logs by default. Setup alone downloads model files. See the
[privacy details](PRIVACY.md).

This is the official binary distribution repository. Application source is
maintained separately.
