---
name: resolve-fundamentals
description: "Use this skill whenever the user asks about DaVinci Resolve basics, getting started, what the different pages do, Free vs Studio differences, project setup, project settings, database management, media management basics, performance optimization (proxies, render cache, optimized media), keyboard shortcuts, workspace customization, or general Resolve terminology and concepts."
---

# DaVinci Resolve Fundamentals

When answering questions about DaVinci Resolve fundamentals, always cite the relevant chapter and page number (e.g., "See Ch 6, p. 137 in the DaVinci Resolve manual") so users can look up more detail in the official documentation.

## Page-Based Architecture

DaVinci Resolve organizes its workflow into seven pages, accessed via buttons at the bottom of the interface or keyboard shortcuts:

| Page | Shortcut | Purpose |
|------|----------|---------|
| **Media** | Shift-2 | Import, browse, and organize source media. Media Storage browser, Media Pool, Metadata editor. |
| **Cut** | Shift-3 | Fast, streamlined editing for quick turnarounds. Dual timeline, source tape mode, smart indicator. |
| **Edit** | Shift-4 | Full-featured NLE with source-record editing, multicam, effects, compositing, and detailed timeline control. |
| **Fusion** | Shift-5 | Node-based visual effects and compositing. Green screen, motion graphics, 3D, particle systems. |
| **Color** | Shift-6 | Professional color grading with node-based corrections, scopes, qualifiers, windows, and LUT management. |
| **Fairlight** | Shift-7 | Professional audio post-production. Multi-track mixing, EQ, dynamics, Fairlight FX, ADR, loudness metering. |
| **Deliver** | Shift-8 | Render and export. Presets for YouTube/Vimeo/TikTok, custom codecs, DCP/IMF, round-trip exports. |

**Typical workflow**: Media (import) → Cut or Edit (assemble) → Fusion (VFX, optional) → Color (grade) → Fairlight (audio mix) → Deliver (export).

Pages are fully integrated — changes on one page are immediately reflected on others.

## Free vs Studio Differences

DaVinci Resolve (free) is remarkably full-featured. Key Studio-only features:

| Feature | Free | Studio |
|---------|------|--------|
| **Resolution** | Up to 4K UHD (3840×2160) | Unlimited (8K+) |
| **GPU acceleration** | Single GPU | Multi-GPU |
| **Neural Engine AI tools** | Limited | Full (Magic Mask, Speed Warp, AI-based scene detection, DaVinci Neural Engine deinterlacing) |
| **HDR grading tools** | Basic HDR | Dolby Vision, HDR10+, HDR Vivid metadata authoring |
| **Noise reduction** | Spatial NR only | Temporal + Spatial NR, enhanced algorithms |
| **Collaboration** | Not available | Multi-user collaboration on same timeline |
| **Video Clean Feed** | Not available | Full-screen viewer output on second monitor |
| **External scripting** | Local only | Network remote scripting |
| **Some Resolve FX** | Core set | Full set (Film Grain, Lens Flare, Object Removal, etc.) |
| **Stereoscopic 3D** | Not available | Full stereoscopic workflow |

Most editing, color grading, Fusion compositing, Fairlight audio, and delivery features work in both versions.

## Project Management (Ch 3, p. 75)

### Project Libraries
- **Local** (default): Disk-based database stored on workstation. Best for individual users.
- **Network**: Database on shared network volume. For multi-workstation facilities.
- **Cloud**: Blackmagic Cloud storage. For remote collaboration.
- **Database types**: Disk database (default, file-system based) or PostgreSQL (for access control).

### Creating & Managing Projects
- **Project Manager**: First screen on launch (Shift-1). Create, rename, delete, import/export projects.
- **Import/Export**: Projects saved as `.drp` files. Right-click → Export Project (or Export with Stills and LUTs).
- **Dynamic Project Switching**: Right-click → Dynamic Project Switching to keep multiple projects in RAM.
- **Archiving**: Right-click → Archive creates `.dra` bundle with all media.

### Backups
- **Live Save**: On by default. Incremental auto-save as you work.
- **Project Backups**: Automatic periodic backups using grandfather-father-son scheme. Configure interval in User Preferences → Project Save and Load (default: every 10 min).
- **Timeline Backups**: Separate backups of individual timelines.
- **Recovery**: Right-click project → Project Backups → select backup → Load.

## Project Settings (Ch 6, p. 137)

Open via the gear icon (bottom-right) or Shift-9.

### Key Settings
- **Timeline Resolution**: Presets for HD (1920×1080), 2K, UHD (3840×2160), 4K DCI, 8K, or custom.
- **Timeline Frame Rate**: Set before importing media. Common: 23.976, 24, 25, 29.97, 30, 50, 59.94, 60 fps.
- **Color Science**: DaVinci YRGB (default), DaVinci YRGB Color Managed (RCM), ACEScc, ACEScct.
- **Pixel Aspect Ratio**: Square pixels (default), 16:9 anamorphic, cinemascope.

### Presets
- Save/load project settings presets via the option menu (three dots) in Project Settings.
- "Set Current Settings as Default Preset" makes your settings the default for new projects.

## Performance Optimization (Ch 8, p. 191)

### Timeline Proxy Mode
- **Playback → Timeline Proxy Resolution** → Half or Quarter.
- Reduces working resolution on-the-fly without creating files. Does NOT affect final render.

### Proxy Media
- Compressed/lower-res duplicates linked to source clips.
- Generate: Right-click clips in Media Pool → Generate Proxy Media.
- Toggle: **Playback → Use Proxy Media**.
- Blackmagic Proxy Generator can auto-generate proxies by watching folders.

### Optimized Media
- Pre-rendered efficient duplicates for smoother editing.
- Generate: Right-click clips → Generate Optimized Media.
- Toggle: **Playback → Use Optimized Media if Available**.
- Settings in Project Settings → Master Settings → Optimized Media and Render Cache.

### Render Cache
- **Smart Cache** (recommended): Automatically caches processor-intensive clips (H.264, H.265, RAW, Fusion effects, speed effects, transitions).
- **User Cache**: Manual control — only caches what you flag.
- Toggle: **Playback → Render Cache** → Smart / User / Off (or Option-R to cycle).
- Timeline indicators: Red bar = needs caching, Blue bar = cached.
- Clear: **Playback → Delete Render Cache** → All / Unused / Selected Clips.

### GPU Performance
- GPU status indicator in Viewer title bar: Green = good, Red = struggling.
- **Performance Mode** (User Preferences): Automatic (default) optimizes without quality loss.

## Terminology Glossary

| Term | Definition |
|------|-----------|
| **Timeline** | An edited sequence of clips. Stored in the Media Pool. Each page displays it differently. |
| **Clip** | An individual piece of video, audio, or still image in the project. |
| **Bin** | A folder in the Media Pool for organizing clips. Default bin is "Master." |
| **Smart Bin** | Auto-populating bin that collects clips matching metadata criteria (resolution, codec, etc.). |
| **Power Bin** | A bin shared across all projects in a project library. Useful for reusable assets. |
| **Compound Clip** | Multiple clips grouped into a single clip in the timeline. Can be opened and edited internally. |
| **Fusion Clip** | A clip with Fusion effects applied. Shows a Fusion badge on the timeline. |
| **Adjustment Clip** | A clip that applies effects to everything below it in the timeline (like an adjustment layer). |
| **Node** | An individual processing unit in Fusion or Color page. Nodes chain together to build effects/grades. |
| **Node Tree** | The chain of connected nodes forming a composition (Fusion) or grade (Color). |
| **Gallery Still** | A reference frame captured during grading for comparison or grade transfer. |
| **PowerGrade** | A saved grade that persists across projects. Stored in the Gallery. |
| **LUT** | Lookup Table — a color transform applied for monitoring, grading, or output. |
| **Marker** | A bookmark on a clip or timeline. Can be colored, named, and given duration. |
| **Flag** | A colored marker on a clip for organizational purposes (G key to toggle). |
| **Conform** | Matching timeline clips to source media via timecode, reel names, or filenames. |
| **Render Cache** | Pre-rendered frames with effects baked in for real-time playback. |
| **Inspector** | Panel showing editable parameters for the selected clip, node, or effect. |

## UI Basics

- **Panel focus**: The active panel receiving keyboard shortcuts. Optional red line indicator (enable in preferences).
- **Viewer modes**: Cinema Viewer (Cmd-F), Full Screen (Shift-F), Enhanced Viewer (Option-F).
- **Dual monitors**: Workspace → Dual Screen → On.
- **Layout presets**: Save custom panel arrangements via Workspace → Layout Presets.
- **Keyboard customization**: DaVinci Resolve → Keyboard Customization. Shortcuts can be per-application or per-panel.
