# TitanMesh

This repository hosts public release artifacts for TitanMesh, a commercial
desktop application for visualizing extremely large 3D datasets - meshes and
point clouds that may exceed available RAM and GPU memory.

**Compatibility:** Windows, macOS, and Linux

The application source code is private. This repository exists only for
installer downloads, release notes, and signed auto-update metadata.

## Why TitanMesh

Most 3D viewers were not designed for the scale that modern photogrammetry,
LiDAR, and large-scale scanning workflows now produce. Files comfortably reach
tens of millions to billions of triangles or points, often weighing more than
the host machine's RAM, let alone its GPU memory. Loading such a dataset into a
general-purpose viewer typically ends in a long wait, an out-of-memory error,
or a crawl.

TitanMesh is built around a single idea: no matter the size of the model, it 
should just work. Memory streaming optimization, paths prediction, memory 
co-location, adaptive level of details, etc. The result is a viewer that opens
multi-gigabyte files quickly, navigates them at interactive frame rates, and
behaves more like a video game engine than a 3D editor.

The goal is to make exploration of massive 3D scans feel as natural as flying
through a level in a game.

## What is TitanMesh

TitanMesh helps inspect, navigate, and measure very large 3D models on a
desktop computer. It is a viewer, not a 3D editor or modeler.

Key capabilities:

- Out-of-core streaming for datasets larger than RAM and GPU memory
- GPU-accelerated rendering on Metal (macOS), DirectX (Windows), and Vulkan (Linux)
- Game-style navigation: WASD movement, FPS-style mouse look, middle-mouse orbit, scroll zoom
- Triangle meshes and point clouds, including billion-scale assets
- Native support for OBJ, STL, PLY, and GLB / glTF 2.0
- Automatic on-disk preprocessing into a spatial cache for fast re-opening
- Adaptive level of detail with graceful degradation under GPU memory pressure
- Point splatting with auto-sized, perspective-correct billboards for dense point clouds
- Diffuse texture mapping (OBJ MTL, glTF baseColorTexture)
- Multi-tape distance measurement with calibration and metric / imperial units
- In-app screen recording to MP4 with no external tooling required
- Minimap overlay with model footprint and camera arrow
- Borderless fullscreen viewport with a clean overlay UI
- Built-in license activation with bounded offline use
- Signed automatic updates

TitanMesh is not a modeling tool. There are no editing, sculpting, retopology,
or simulation features.

## Supported Formats

| Format | Triangles | Point clouds | Textures | Streaming (>= 2 GB) |
|--------|:---------:|:------------:|:--------:|:-------------------:|
| OBJ    | yes       | yes (vertex-only) | yes (`map_Kd`) | yes |
| STL (binary + ASCII) | yes | -    | -        | yes (binary)        |
| PLY (ASCII + binary) | yes | yes  | optional UVs | yes |
| GLB / glTF 2.0       | yes | yes  | yes (`baseColorTexture`) | yes |

Non-streaming small files load entirely in memory; large files automatically
trigger the streaming preprocessor on first open.

## Downloads

Download the latest installer from the
[Releases](https://github.com/OpenSpeleo/TitanMesh-Releases/releases) page.

Additional files such as `.sig` files and `latest.json` are used by the signed
auto-updater. Most users do not need to download them manually.

## Installation

### macOS

1. Download the `.dmg` for your Mac (universal: Apple Silicon and Intel).
2. Open the disk image.
3. Drag TitanMesh into Applications.
4. Launch TitanMesh.

If macOS blocks the first launch, open System Settings > Privacy & Security
and allow TitanMesh to run.

The first time you start a screen recording, macOS will request screen-capture
permission. Grant it under System Settings > Privacy & Security > Screen
Recording.

### Windows

1. Download the Windows installer.
2. Run the `.msi` (recommended) or the NSIS `setup.exe`.
3. Follow the installer prompts.
4. Launch TitanMesh from the Start menu.

The MSI uses Windows Installer Restart Manager and is the canonical
auto-update path. The NSIS installer is provided for administrators who prefer
a silent / per-user install workflow.

### Linux

Choose the package format that best matches your distribution:

- Use `.AppImage` for a portable build that works across most distributions.
- Use `.tar.gz` for a manual extraction if you prefer not to use AppImage.

`.deb` and `.rpm` packages are not currently provided.

## Controls

TitanMesh launches in borderless fullscreen with FPS-style mouse capture.

| Input | Action |
|-------|--------|
| W A S D | Move forward / left / back / right |
| Space / Shift | Move up / down |
| Mouse movement | Look around (FPS-style, always active) |
| Hold middle mouse + drag | Rotate 360 degrees around the object in view |
| Scroll wheel | Zoom forward / backward |
| Escape | Toggle between game mode and UI mode |
| Cmd / Ctrl + O | Open model file |
| Cmd / Ctrl + W | Close current model |
| Cmd / Ctrl + Q | Quit |
| Cmd / Ctrl + L | Revoke the current license |
| `[` / `]` | Decrease / increase point splat size (point clouds only) |
| Drag-and-drop | Load a model file |

## Measurement Tool

TitanMesh includes a calibrated multi-tape distance measurement tool for
real-world readouts on model surfaces.

1. Open **Science > Measure** from the top-bar menu.
2. Calibrate once by clicking two points along a known reference distance and
   entering its real-world value (cm or inches).
3. After calibration, every two clicks place a new measurement tape with a
   live distance label.
4. Existing endpoints can be repositioned by press-and-hold drag.
5. Switch between metric (cm / m) and imperial (in / ft) at any time from the
   Settings panel.

Calibration tapes can be re-placed at any time without losing existing
measurements.

## Screen Recording

Recording captures the TitanMesh window exactly as shown on screen, including
the overlay UI and the recording indicator.

- Start and stop recording from the **Recording** menu in the top bar.
- Recording is encoded in-process to H.264 inside an MP4 container - no
  ffmpeg or other external tool is required.
- When you stop recording, TitanMesh asks where to save the file and
  finishes muxing in the background.

Audio capture is not currently supported.

## Licensing

TitanMesh is commercial proprietary software. A valid license is required to
use the application.

Repeated offline restarts do not extend the offline window. Explicit denial,
expiry, or revocation immediately wipes local entitlement state and returns
the app to the license gate. The system also detects clock rollback and
forces a fresh online validation when tampering is suspected.

Installer availability in this public repository does not grant a license to
use, copy, modify, reverse engineer, redistribute, or sublicense TitanMesh.
Use of TitanMesh is governed by the commercial license agreement or EULA
provided by OpenSpeleo.

## Auto-Updates

TitanMesh checks this repository for signed update metadata:

```text
https://github.com/OpenSpeleo/TitanMesh-Releases/releases/latest/download/latest.json
```

Updates are cryptographically signed. The installed app verifies update 
signatures against an embedded public key before installing them. A 
failed signature aborts the install and surfaces a clear error with 
`Retry` and `Download Latest` actions.

Each platform is updated using the natural mechanism for that OS:

- **macOS**: the running `.app` bundle is replaced from a signed `.app.tar.gz`
  and the new bundle is launched on next start.
- **Linux**: the AppImage is replaced atomically over the running file. System
  package installs (e.g. `/usr/bin/titanmesh`) are skipped and surface a
  manual-update message.
- **Windows**: the MSI installs via Windows Installer with Restart Manager;
  the NSIS installer is also signed and available for admins.

## Hardware Requirements

Minimum:

- 64-bit Windows 10/11, macOS 12+ (Apple Silicon or Intel), or a recent Linux
  distribution
- A GPU supporting modern graphics APIs (Metal, Direct3D 12, or Vulkan)
- Multi-core CPU
- Enough disk space for both the source dataset and its `.tmcache` sidecar

Recommended:

- A modern discrete GPU
- An SSD or NVMe drive for the dataset directory (streaming performance scales
  directly with disk throughput)

TitanMesh degrades gracefully on weaker GPUs by reducing LOD detail rather
than failing.

## Support

For license, installation, or product support, contact OpenSpeleo through the
support channel provided with your purchase or license.

When reporting a problem, include:

- TitanMesh version (visible in the top bar)
- operating system and version
- installer type used (DMG, MSI, NSIS exe, AppImage, tar.gz)
- the file format and approximate size of the dataset, if relevant
- a brief description of what you expected and what happened

Do not post license keys, private datasets, or other sensitive data in public
issues.

## Repository Purpose

This repository is intentionally limited to release distribution.

It may contain:

- release notes
- installers
- updater metadata
- updater signatures

## Legal

TitanMesh is proprietary commercial software.

Installer availability in this repository does not grant a license to use,
copy, modify, redistribute, reverse engineer, or sublicense TitanMesh except
as expressly allowed by a written commercial license agreement.

Third-party components bundled with TitanMesh remain subject to their
respective licenses.
