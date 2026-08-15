# TitanMesh

## License Purchase, Management & Free 48-Hour Trial

> [!IMPORTANT] 
> **Purchase or manage your TitanMesh license:**
> [software.usahinstitute.org](https://software.usahinstitute.org/)
>
> **Get a 48-hour TitanMesh trial license:**
> [software.usahinstitute.org](https://software.usahinstitute.org/)

## What is TitanMesh?

This repository hosts public release artifacts for TitanMesh, a commercial 3D
viewer for exploring extremely large meshes and point clouds on desktop and in
virtual reality.

**Desktop compatibility:** Windows, macOS, and Linux

**Virtual reality:** Meta Quest 3/3S support is available as an optional
licensed experience. See the release notes for the headset models supported by
each release.

The application source code is private. This repository exists only for
installer downloads, release notes, and files needed to deliver updates.

## Why TitanMesh

Most 3D viewers were not designed for the scale that modern photogrammetry,
LiDAR, and large-scale scanning workflows now produce. Files comfortably reach
tens of millions to billions of triangles or points, often weighing more than
the host machine's RAM, let alone its GPU memory. Loading such a dataset into a
general-purpose viewer typically ends in a long wait, an out-of-memory error, or
a crawl.

TitanMesh is built around a single idea: no matter the size of the model, it
should just work. The result is a viewer that opens multi-gigabyte files
quickly, navigates them at interactive frame rates, and behaves more like a
video game engine than a 3D editor.

The goal is to make exploration of massive 3D scans feel as natural as flying
through a level in a game.

## What is TitanMesh

TitanMesh helps inspect, navigate, and measure very large 3D models on a desktop
computer. It is a viewer, not a 3D editor or modeler.

Key capabilities:

- Game-style navigation with free flight, sprint, mouse look, orbit, fast
  approach to distant models, and instant camera reset
- Triangle meshes and point clouds, including billion-scale assets
- Native support for OBJ, binary STL, binary PLY, and GLB / glTF 2.0
- Textures, vertex colors, surface shading, point splats, and point-confidence
  filtering when the source data provides them
- Adjustable movement speed, detail quality, visual smoothing, model
  orientation, triangle-face display, point size, and color correction
- Distance measurement with calibration and metric / imperial units
- Persistent landmarks with titles and descriptions
- Minimap display and transparent map export
- Clean snapshots, reusable camera locations, and in-app MP4 recording
- Per-model settings that return automatically when a model is reopened
- Native VR viewing with tracked-controller navigation and synchronized desktop
  monitoring
- Signed automatic updates

TitanMesh is not a modeling tool. There are no editing, sculpting, retopology,
or simulation features.

## Feature Overview

### Massive datasets

TitanMesh is designed for models that are too large to fit into ordinary system
or graphics memory. It prepares supported files for responsive exploration,
keeps the visible scene interactive, and adjusts displayed detail automatically
as you move. The same large-model experience applies to triangle meshes and
point clouds.

### Visual quality and model appearance

TitanMesh preserves the appearance information available in supported source
files, including textures, vertex colors, and surface direction. Point clouds
are presented as points or smooth surface-like splats according to the available
data, with adjustable size. Compatible PLY point clouds also offer a
minimum-confidence control for hiding low-confidence samples.

The Settings panel includes four detail-quality presets, five visual-smoothing
levels, safe two-sided triangle display or optional back-face removal, and model
rotation in 90-degree steps. Color Correction provides Temperature, Tint,
Vibrance, and Saturation controls with live preview. These adjustments affect
the model without altering the source file.

### Navigation and display

The default free-flight camera feels familiar to anyone who has navigated a 3D
game. TitanMesh supports mouse look, sprinting, vertical travel, 360-degree
orbit, a trackpad-friendly orbit gesture, and a one-key return to the initial
view. When a model begins far from the camera, TitanMesh temporarily increases
travel speed to reduce the wait. A visual tutorial introduces the controls.

Both borderless fullscreen and resizable windowed presentation are available.
TitanMesh remembers the display choice and window size.

### Inspection, measurement, and annotation

The minimap shows the model footprint and the camera's position and direction.
It can be hidden when not needed, follows saved model orientation, and can be
exported as a transparent PNG.

The measurement tool uses a known reference distance to calibrate a model. After
calibration, users can place multiple measurement tapes, reposition their
endpoints, remove individual tapes, clear all tapes, recalibrate, and switch
between metric and imperial readouts. Calibration returns when the same model is
reopened.

Right-clicking a model surface creates a persistent landmark with a title and
description. Landmark cards can be expanded, collapsed, automatically expanded
when nearby, or deleted.

### Capture and view sharing

TitanMesh can record the application window directly to MP4. It also creates
clean, watermarked JPEG snapshots of the 3D view without menus or overlays. A
saved snapshot can later restore its camera view.

For smaller handoffs, Save Location creates a lightweight location file that can
return TitanMesh to the same view of the same model. Location files and
compatible snapshots warn before applying a view to a different model.

### Per-model continuity

TitanMesh remembers model-specific choices such as movement speed, quality,
visual smoothing, orientation, point-cloud display, minimap visibility, landmark
behavior, measurement units, calibration, color correction, and landmarks.
Restored choices are applied when the model is reopened. If saved project
information cannot be used, the model remains viewable with safe defaults.

### Native virtual reality

The optional TitanMesh VR experience brings the active desktop model into an
immersive stereo view on a supported Meta Quest headset. Guided connection
screens, QR-assisted setup, a controller tutorial, progress feedback, and clear
reconnection states help users get from the desktop to the model.

Tracked controllers provide movement, strafing, turning, elevation, a temporary
speed boost, and a confirmed reset to the starting location. A headset menu
provides synchronized control over movement speed, detail quality, visual
smoothing, and point size where applicable, with tactile and audio feedback for
interactions.

During an active VR session, the desktop mirrors the headset view for monitoring
and makes it clear that the headset controls the camera. Normal desktop and VR
preferences for speed, quality, and visual smoothing are stored independently,
so tuning one experience does not overwrite the other. TitanMesh is designed to
remain responsive through temporary local-network interruptions, and previously
received model content can be reused after reconnecting.

VR scene sharing requires the optional VR entitlement, the TitanMesh headset
app, and a desktop and headset on the same local network. A built-in VR network
speed test helps evaluate the connection before sharing a model and is available
without opening a scene. The desktop also provides headset-app download guidance
and directs users without the VR entitlement to the available trial or purchase
path.

## Supported Formats

| Format         | Triangle meshes | Point clouds | Appearance support                   |
| -------------- | :-------------: | :----------: | ------------------------------------ |
| OBJ            |       yes       |     yes      | Materials and textures when provided |
| Binary STL     |       yes       |      -       | Surface shading                      |
| Binary PLY     |       yes       |     yes      | Colors and surface information       |
| GLB / glTF 2.0 |       yes       |     yes      | Materials and textures when provided |

Text-based STL and PLY files are not supported. Re-export them in binary form
before opening them in TitanMesh.

## Downloads

Download the latest installer from the
[Releases](https://github.com/OpenSpeleo/TitanMesh-Releases/releases) page.

Other files on the Releases page support the in-app updater. Most users do not
need to download them manually.

## Installation

### macOS

1. Download the `.dmg` for your Mac (universal: Apple Silicon and Intel).
2. Open the disk image.
3. Drag TitanMesh into Applications.
4. Launch TitanMesh.

If macOS blocks the first launch, open System Settings > Privacy & Security and
allow TitanMesh to run.

The first time you start a screen recording, macOS will request screen-capture
permission. Grant it under System Settings > Privacy & Security > Screen
Recording.

### Windows

1. Download the Windows installer.
2. Run the `.msi` (recommended) or the NSIS `setup.exe`.
3. Follow the installer prompts.
4. Launch TitanMesh from the Start menu.

The MSI is recommended for most users. The NSIS installer is also available for
administrators and per-user installations.

### Linux

Choose the package format that best matches your distribution:

- Use `.AppImage` for a portable build that works across most distributions.
- Use `.tar.gz` for a manual extraction if you prefer not to use AppImage.

`.deb` and `.rpm` packages are not currently provided.

## Controls

TitanMesh launches in borderless fullscreen with FPS-style mouse capture.

| Input                                                  | Action                                                   |
| ------------------------------------------------------ | -------------------------------------------------------- |
| W A S D                                                | Move forward / left / back / right                       |
| Hold Shift                                             | Sprint                                                   |
| + / -                                                  | Move up / down                                           |
| Mouse movement                                         | Look around                                              |
| Hold middle mouse + drag                               | Rotate 360 degrees around the object in view             |
| Hold Alt (Windows/Linux) or Option (macOS) + drag      | Trackpad-friendly orbit                                  |
| Space                                                  | Return to the model's initial camera view                |
| Escape / Enter                                         | Toggle between game mode and UI mode                     |
| M                                                      | Show / hide the minimap                                  |
| Right-click a model surface (outside measurement mode) | Create a landmark                                        |
| Cmd / Ctrl + O                                         | Open model file                                          |
| Cmd / Ctrl + W                                         | Close current model                                      |
| Cmd / Ctrl + Q                                         | Quit                                                     |
| Cmd / Ctrl + L                                         | Revoke the current license                               |
| `[` / `]`                                              | Decrease / increase point splat size (point clouds only) |
| Drag-and-drop                                          | Load a model file                                        |

The scroll wheel is intentionally unassigned. Movement speed is adjusted in
Settings.

## Measurement Tool

TitanMesh includes a calibrated multi-tape distance measurement tool for
real-world readouts on model surfaces.

1. Open **Science > Measure** from the top-bar menu.
2. Calibrate once by clicking two points along a known reference distance and
   entering its real-world value (cm or inches).
3. After calibration, every two clicks place a new measurement tape with a live
   distance label.
4. Existing endpoints can be repositioned by press-and-hold drag.
5. Switch between metric (cm / m) and imperial (in / ft) at any time from the
   Settings panel.

Calibration tapes can be re-placed at any time without losing existing
measurements.

## Screen Recording

Recording captures the TitanMesh window exactly as shown on screen, including
the overlay UI, recording indicator, and elapsed time.

- Start and stop recording from the **Recording** menu in the top bar.
- No separate recording application is required.
- When you stop recording, TitanMesh asks where to save the MP4 and completes
  the file without interrupting model viewing.

Audio capture is not currently supported.

## Licensing

TitanMesh is commercial proprietary software. A valid license is required to use
the application.

An internet connection is required for activation and periodic license
validation. Limited offline use is available after a successful validation.
Expired, revoked, or released licenses return the application to the license
screen. VR scene sharing requires the optional VR entitlement on the active
desktop license.

Installer availability in this public repository does not grant a license to
use, copy, modify, reverse engineer, redistribute, or sublicense TitanMesh. Use
of TitanMesh is governed by the commercial license agreement or EULA provided by
OpenSpeleo.

## Auto-Updates

TitanMesh can check for signed releases from inside the application. Available
updates are presented with clear install, retry, and manual-download options.
Update authenticity is checked before installation, and a failed check stops the
update. Platform-managed installations that cannot be updated in place are
directed to the latest manual download.

## Hardware Requirements

Minimum:

- 64-bit Windows 10/11, macOS 12+ (Apple Silicon or Intel), or a recent Linux
  distribution
- A modern supported GPU
- Multi-core CPU
- Enough disk space for the source dataset and TitanMesh's working data

Recommended:

- A modern discrete GPU
- An SSD or NVMe drive for the dataset directory

TitanMesh degrades gracefully on weaker GPUs by reducing displayed detail rather
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
- files required by the in-app updater

## Legal

TitanMesh is proprietary commercial software.

Installer availability in this repository does not grant a license to use, copy,
modify, redistribute, reverse engineer, or sublicense TitanMesh except as
expressly allowed by a written commercial license agreement.

Third-party components bundled with TitanMesh remain subject to their respective
licenses.
