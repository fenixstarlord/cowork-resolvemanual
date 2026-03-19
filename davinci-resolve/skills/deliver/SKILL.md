---
name: deliver
description: "Use this skill whenever the user asks about exporting, rendering, delivery, export settings, codecs, H.264, H.265, ProRes, DNxHD, render queue, YouTube export, Vimeo export, TikTok export, Quick Export, render presets, file formats, DCP, IMF, audio export, XML export, AAF export, EDL export, round-trip workflow, individual clips vs single clip render, frame rate conversion, resolution output, or anything related to the Deliver page in DaVinci Resolve."
---

# Deliver Page — Rendering & Export

When answering Deliver questions, cite relevant chapters: Ch 185-190, p. 4019-4101 in the DaVinci Resolve manual.

## Page Overview (Ch 186, p. 4024)

The Deliver page is where you render your final output. Access it via the Deliver button or Shift-8.

### Interface Layout
- **Render Settings** (left): Video, Audio, and File panels for configuring output
- **Viewer** (top center): Preview of rendered output
- **Timeline** (bottom): Set In/Out points to render a portion, or render entire timeline
- **Render Queue** (right): Manage queued render jobs

## Quick Export (Any Page)

The fastest way to export — available from **File → Quick Export** on any page.

1. Optionally set In/Out points on timeline (I/O keys)
2. **File → Quick Export**
3. Choose a preset icon (YouTube, Vimeo, TikTok, H.264, H.265, ProRes, etc.)
4. Browse to save location → Save
5. Can also upload directly to YouTube, Vimeo, TikTok, Dropbox, Frame.io

## Render Presets (Ch 186, p. 4024)

### Social Media Presets
| Preset | Format | Codec | Audio |
|--------|--------|-------|-------|
| **YouTube** (720p/1080p/1440p/2160p) | MP4 | H.264 | AAC |
| **Vimeo** (720p/1080p/2160p) | MP4 | H.264 | AAC |
| **TikTok** (HD/FHD) | MP4 | H.264 | AAC |
| **Dropbox / Dropbox Replay** | MP4 | H.264 | AAC |

### Master Presets
| Preset | Format | Codec | Audio |
|--------|--------|-------|-------|
| **ProRes Master** | QuickTime | ProRes 422 HQ | Linear PCM |
| **H.264 Master** | QuickTime | H.264 | AAC |
| **H.265 Master** | QuickTime | H.265 | AAC |

### Exchange Presets (Round-Trip)
| Preset | Format | Codec | Purpose |
|--------|--------|-------|---------|
| **Final Cut Pro X XML** | Individual Clips | ProRes 422 HQ | Round-trip to FCP X |
| **Final Cut Pro 7 XML** | Individual Clips | ProRes 422 HQ | Round-trip to FCP 7 |
| **Premiere XML** | Individual Clips | ProRes 422 HQ | Round-trip to Premiere |
| **Avid AAF** | Individual Clips | DNxHR 444 12-bit | Round-trip to Avid |
| **Pro Tools** | AAF + audio files | Linear PCM | Round-trip to Pro Tools |

### Specialized
| Preset | Purpose |
|--------|---------|
| **Audio Only** | Export audio without video |
| **IMF** | Interoperable Master Format |
| **DCP** | Digital Cinema Package |
| **Frame.io** | Direct upload to Frame.io |

## Common Export Workflows

### Export for YouTube (Recommended Settings)
1. Go to Deliver page (Shift-8)
2. Select the **YouTube** preset (choose resolution: 1080p or 2160p)
3. Settings are pre-configured: MP4, H.264, AAC audio
4. Set filename and destination in the File panel
5. Click **Add to Render Queue** → **Start Render**

**For higher quality**: Use Custom preset with:
- Format: MP4 or QuickTime
- Codec: H.265 (better quality at same file size, but slower encode)
- Resolution: Match your timeline (1920×1080 or 3840×2160)
- Frame rate: Match your timeline
- Quality: Automatic or set bitrate manually (YouTube recommends 8 Mbps for 1080p, 35-45 Mbps for 4K)

### Export a High-Quality Master
1. Select **ProRes Master** preset (or Custom)
2. Format: QuickTime
3. Codec: ProRes 422 HQ (good balance) or ProRes 4444 (if alpha/HDR needed)
4. Audio: Linear PCM
5. This creates a large, high-quality file suitable for archiving or further post-production

### Export Audio Only
1. Select **Audio Only** preset (or Custom with Export Video unchecked)
2. Format: WAVE (for uncompressed) or MP3/FLAC/AAC
3. Sample Rate: 48 kHz (standard for video) or 44.1 kHz (for music)
4. Bit Depth: 24-bit (professional) or 16-bit (consumer)

## Video Render Settings (Ch 187, p. 4033)

### Key Settings
- **Format**: QuickTime, MP4, MXF, DPX, EXR, TIFF, AVI, etc.
- **Codec**: H.264, H.265, ProRes (422/422HQ/4444/4444XQ), DNxHD/DNxHR, JPEG2000
- **Resolution**: Defaults to timeline resolution. Can override with custom values.
- **Frame Rate**: Defaults to timeline frame rate. Can convert (e.g., 29.97 to 23.976 with pulldown).

### H.264/H.265 Encoding Options
- **Quality**: Automatic (recommended) or manual bitrate
- **Encoding Profile**: Auto, Main, Main10, High
- **Multi-pass Encode**: Slower but better quality distribution
- **Key Frames**: Automatic (recommended) or manual interval

### Advanced Options
- **Export Alpha**: Enable when you need transparency (requires ProRes 4444, DNxHR 444, or EXR)
- **Render at Source Resolution**: For Individual Clips mode — each clip renders at its native resolution
- **Force Debayer Res to Highest Quality**: Ensures RAW footage is rendered at full quality
- **Use Constant Bit Rate**: Forces CBR encoding (some delivery specs require this)

## Audio Render Settings

- **Format**: WAVE, MP3, FLAC, AAC, or embedded in video container
- **Codec**: Linear PCM (uncompressed, default), AAC, MP3, IEEE Float
- **Sample Rate**: 48 kHz (standard), 44.1, 96, 192 kHz
- **Bit Depth**: 16, 24, or 32-bit
- **Render one track per channel**: Splits multichannel audio into separate mono files (for Pro Tools/mixing)
- **Output Track**: Select Main bus or specific Submix for export
- **Normalization**: Normalize to EBU R128, ATSC A/85, or other loudness standards

## Single Clip vs Individual Clips (Ch 187, p. 4033)

| | Single Clip | Individual Clips |
|---|---|---|
| **Output** | One file for entire timeline | Separate file per clip |
| **Timecode** | Uses project/timeline timecode | Uses source clip timecode |
| **Frame Rate** | Mixed rates convert to timeline rate | Each clip keeps original rate |
| **Effects** | All effects baked in | Optional "Render Timeline Effects" checkbox |
| **Use Case** | Final delivery, master file | Round-trip to other NLEs, dailies, VFX pulls |

## Render Queue (Ch 187, p. 4033)

- **Add jobs**: Configure settings → click **Add to Render Queue**
- **Multiple jobs**: Change settings and add again — queue multiple renders with different settings
- **Edit job**: Click the pencil icon to modify a queued job
- **Reorder**: Drag jobs up/down in the queue
- **Start Render**: Click the **Start Render** button
- **Show All Projects**: Toggle to see/render jobs from other projects in the same library
- **Re-render**: Previously rendered jobs remain in queue for re-rendering

## File Naming

- **Filename Uses**: Custom name, Timeline Name (Single Clip), or Source Filename (Individual Clips)
- **Custom Name**: Type a name + optional metadata variables (%scene_%shot_%take)
- **Unique Filenames**: Auto-appends track/clip numbers to prevent overwrites

## DCP & IMF Delivery (Ch 188, p. 4067)

### DCP (Digital Cinema Package)
- Use the DCP preset or Custom with DCP format
- JPEG2000 encoding
- SMPTE or Interop packaging
- Can use native Resolve encoder or easyDCP (if licensed)

### IMF (Interoperable Master Format)
- SMPTE ST.2067 standard
- Supports multiple video/audio/subtitle tracks
- Preset types: Generic, Netflix-qualified
- Includes composition metadata

## Round-Trip Exports (Ch 190, p. 4090)

When sending projects back to other NLEs:
- **Color corrections**: Rendered for FCP X, not included for other NLEs
- **Transitions**: Included in XML/AAF/EDL
- **Speed effects**: Included (can bake in with Optical Flow)
- **Compositing**: Sent back in XML/AAF
- **Audio effects**: NOT exported — Fairlight FX stay in Resolve
- **Handles**: Add frame handles for editor flexibility when rendering Individual Clips

### Export Formats
- **XML** (FCP X / FCP 7 / Premiere): File → Export Timeline → choose format
- **AAF** (Avid / Pro Tools): File → Export Timeline → AAF
- **EDL**: File → Export Timeline → EDL

## Tips & Gotchas

- **Set In/Out points** on the timeline to render only a portion (useful for test renders)
- **Test render**: Render a short section first to verify quality and settings before committing to full render
- **Disk space**: Check available disk space before rendering large projects. H.264/H.265 produce much smaller files than ProRes.
- **Render speed**: H.265 encodes significantly slower than H.264 but produces better quality at the same bitrate
- **Custom presets**: Save your preferred settings as a custom preset. Check "Add to Quick Export" to make it available in File → Quick Export.
- **Background rendering**: Resolve renders in the foreground by default. You can continue working in a different project while rendering.
- **Burn-in timecode**: Enable Data Burn-In in the render settings if you need timecode overlay on the output
- **Subtitles**: Export subtitles as burned-in or as separate SRT/SCC files (configure in render settings)
