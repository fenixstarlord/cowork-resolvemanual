---
name: edit-and-cut
description: "Use this skill whenever the user asks about editing, cutting, trimming, the Edit page, the Cut page, timelines, multicam editing, compound clips, nested timelines, transitions, titles, Text+, generators, speed effects, speed ramps, retime curves, freeze frames, slow motion, subtitles, closed captioning, compositing in timeline, blend modes, opacity, keyframing in the timeline, text-based editing, three-point editing, four-point editing, insert edit, overwrite edit, ripple edit, roll edit, slip edit, slide edit, markers, match frame, audio editing in Edit page, or anything related to editing video in DaVinci Resolve."
---

# Edit Page & Cut Page — Video Editing

When answering editing questions, cite relevant chapters: Cut Page (Ch 26-32, p. 497-653), Edit Page (Ch 33-54, p. 654-1128). Always include chapter and page references.

## Cut Page vs Edit Page

DaVinci Resolve has two editing pages. Understanding when to use each:

| Feature | Cut Page (Ch 26, p. 497) | Edit Page (Ch 33, p. 654) |
|---------|----------|-----------|
| **Designed for** | Fast, streamlined editing | Full-featured, detailed editing |
| **Timeline** | Dual timeline (upper=full, lower=zoomed) | Single timeline with flexible track layout |
| **Viewer** | Single viewer with 4 modes | Dual viewer (Source + Timeline) |
| **Edit placement** | Smart Indicator auto-positions edits | Manual placement with traditional edit modes |
| **Best for** | Quick turnarounds, simple projects, rough cuts | Complex projects, multicam, detailed effects, compositing |
| **Trimming** | Simplified trim tools | Full trim suite (ripple, roll, slip, slide, dynamic) |
| **Effects** | Basic effects via toolbar | Full Effects Library, Inspector, keyframing |

**Key difference**: The Cut page uses a **Smart Indicator** (thin line on the upper timeline) that automatically positions your next edit at the most logical point. The Edit page gives you full manual control over edit placement.

Both pages edit the same timeline — changes on one are reflected on the other.

## Cut Page Workflow (Ch 26-32, p. 497-653)

### Viewer Modes (Ch 26, p. 497)
- **Source Clip**: View individual clips from Media Pool
- **Source Tape**: All Media Pool clips laid end-to-end like a tape — scroll through everything
- **Timeline**: View the edited timeline
- **Multi Source**: Multiple source clips in grid for quick comparison

### Editing Methods (Ch 28, p. 542)
- **Smart Insert**: Inserts at the nearest edit point (Smart Indicator position)
- **Append**: Adds to the end of the timeline
- **Close Up**: Creates an automatic close-up by scaling and repositioning
- **Place on Top**: Places clip on the next higher video track at playhead
- **Source Overwrite**: Syncs and overwrites using timecode matching
- **Ripple Overwrite**: Replaces clip and adjusts timeline length to match

### Quick Export (Ch 32, p. 650)
- Toolbar button or File → Quick Export
- Preset icons for YouTube, Vimeo, H.264, ProRes, etc.
- Fast way to render without going to Deliver page

### Cut Page Inspector (Ch 30, p. 597)
- Access via toolbar → Inspector button
- Transform, Cropping, Dynamic Zoom, Compositing, Speed, Stabilization, Audio

## Edit Page Core Concepts

### Timeline (Ch 34, p. 697)
- **Create timeline**: File → New Timeline (or Ctrl/Cmd-N)
- **Timeline settings**: Right-click timeline in Media Pool → Timelines → Timeline Settings
- **Multiple timelines**: Create as many as needed; each stored in Media Pool
- **Track types**: Video tracks (stack from bottom up), Audio tracks (below the divider)
- **Add tracks**: Right-click track header → Add Track (video or audio)

### Viewers (Ch 33, p. 654)
- **Source Viewer** (left): Preview clips from Media Pool before editing
- **Timeline Viewer** (right): Preview the edited timeline
- **Cinema Viewer**: Cmd-F for full-screen viewer
- Set In/Out points: I (In), O (Out), Option-X (clear both)

### Edit Modes (Ch 36, p. 743)

| Mode | What It Does | Shortcut |
|------|-------------|----------|
| **Insert** | Pushes existing clips forward to make room | F9 |
| **Overwrite** | Replaces content at playhead position | F10 |
| **Replace** | Replaces clip at playhead, matching duration | F11 |
| **Fit to Fill** | Speeds up/slows down source to fit marked duration | Shift-F11 |
| **Place on Top** | Places on next available higher track | F12 |
| **Append to End** | Adds after last clip in timeline | Shift-F12 |

### Three-Point Editing (Ch 39, p. 818)
1. Set In/Out on source clip (I/O keys) — defines what portion to use
2. Set In or Out on timeline — defines where to place it
3. Choose edit type (Insert/Overwrite/etc.)
Three points determine the edit; the fourth is calculated automatically.

### Four-Point Editing (Ch 39, p. 818)
- Set both In and Out on source AND timeline
- Used with Fit to Fill to speed-change source to match timeline duration

## Trimming (Ch 44, p. 915)

### Trim Types
| Trim | What It Does | How |
|------|-------------|-----|
| **Ripple** | Extend/shorten clip, shifting everything after it | Drag edit point with Trim mode (T), or select edge and drag |
| **Roll** | Move edit point between two clips (one gets longer, other shorter) | Drag the edit point between clips |
| **Slip** | Move content within clip without changing position or duration | Middle area of clip in Trim mode |
| **Slide** | Move clip's position, adjusting adjacent clips | Drag clip with Slide tool (hold Shift in Trim mode) |
| **Dynamic Trim** | Trim while playing — use JKL to trim in real-time | Enter Trim mode → JKL keys |

### Using Trim Mode
1. Press **T** to enter Trim mode (or select Trim tool from toolbar)
2. Click near an edit point — Resolve auto-selects ripple or roll based on cursor position
3. Drag to trim, or use **,** and **.** keys for frame-by-frame trimming
4. Press **A** to return to Selection mode

## Multicam Editing (Ch 42, p. 889)

### Setup
1. Select all camera angles in Media Pool
2. Right-click → Create Multicam Clip Using Selected Clips
3. Choose sync method: Timecode, In Point, Audio Waveform, or Marker
4. Set angle order

### Editing
1. Place multicam clip on timeline
2. Right-click timeline viewer → Multicam (or click Multicam button in viewer)
3. Play the timeline — click the angle you want to cut to in the multi-viewer
4. Resolve creates cuts and angle switches automatically
5. Refine by trimming individual cuts afterward

## Compound Clips & Nested Timelines (Ch 43, p. 904)

### Compound Clips
- Select multiple clips → Right-click → Create Compound Clip
- Compound clip acts as a single clip but can be double-clicked to open and edit its contents
- Useful for grouping related clips, applying effects to groups, or simplifying complex timelines

### Nested Timelines
- Drag any timeline from Media Pool into another timeline
- Acts like a compound clip — double-click to open the nested timeline
- Changes in the nested timeline automatically update in the parent

## Transitions (Ch 48, p. 1017)

### Adding Transitions
- **Drag**: Open Effects Library → Toolbox → Video Transitions → drag to edit point
- **Quick add**: Select edit point → press Ctrl/Cmd-T for default transition (cross dissolve)
- **Default transition**: Set by right-clicking any transition → Set as Standard Transition

### Common Transitions
- **Cross Dissolve**: Gradual blend between clips (most common)
- **Dip to Color**: Fade through black (or other color) between clips
- **Wipe**: Various wipe patterns
- **Iris**: Opening/closing shape reveals
- **Resolve FX transitions**: Advanced transitions (blur dissolve, motion blur cut, etc.)

### Customizing
- Drag transition edges to change duration
- Double-click to open Inspector with parameters (alignment, curve, start/end ratio)
- Transition alignment: Center, Start, End on cut

## Titles & Generators (Ch 49, p. 1037)

### Title Types
- **Titles** (Toolbox → Titles): Simple text overlays
  - **Text+**: Full-featured title with 2D/3D layout, multiple shading layers, animation (built on Fusion)
  - **Scroll**: Scrolling credits
  - **Lower Third**: Pre-built lower third templates
- **Fusion Titles**: Pre-built animated title templates (drag to timeline, edit text in Inspector)
- **Generators**: Color backgrounds, gradients, noise patterns, counting bars

### Adding Titles
1. Open Effects Library → Toolbox → Titles
2. Drag a title to a video track above your footage
3. Select the title clip → open Inspector
4. Edit text, font, size, color, position in the Inspector
5. For Text+: Use the Fusion page for advanced animation

## Speed Effects (Ch 51, p. 1070)

### Constant Speed Change
- Right-click clip → Change Clip Speed
- Enter percentage (50% = half speed, 200% = double speed)
- Options: Ripple Timeline (adjust duration), Freeze Frame, Reverse Speed

### Speed Ramps (Retime Curves)
1. Right-click clip → Retime Controls (or Ctrl/Cmd-R)
2. Speed percentage appears on the clip
3. Add speed points: Click the dropdown arrow → Add Speed Point
4. Drag speed points to create ramps between different speeds
5. Click the percentage to change speed for each segment
6. For smooth ramps: Right-click speed point → choose curve type (ease in/out)

### Freeze Frame
- Right-click clip → Change Clip Speed → check Freeze Frame
- Or: Position playhead → right-click → Add Freeze Frame (inserts freeze at playhead)

### Retime Process (Motion Interpolation)
- **Nearest**: Fastest, can look choppy
- **Frame Blend**: Blends adjacent frames (softer motion)
- **Optical Flow**: Best quality slow motion (creates new intermediate frames)
- **Speed Warp**: AI-powered (Studio only) — highest quality for extreme speed changes

## Subtitles & Closed Captioning (Ch 52, p. 1083)

### Adding Subtitles
1. **Timeline → Create Subtitle Track** (or right-click track area → Add Subtitle Track)
2. Position playhead → right-click subtitle track → Add Subtitle
3. Type subtitle text in the Inspector
4. Adjust In/Out points to set timing
5. Repeat for each subtitle

### Importing Subtitles
- **File → Import → Subtitle**: Import SRT, VTT, or other subtitle formats
- Subtitles appear on the subtitle track and can be edited

### Subtitle Inspector
- Text content, font, size, color, background, position
- Multiple subtitle tracks for different languages

### Exporting Subtitles
- **Burned-in**: Render with subtitles baked into the video
- **Separate file**: Export as SRT or SCC file alongside video (configure in Deliver page)

## Compositing in Timeline (Ch 50, p. 1053)

### Opacity & Blend Modes
- Select clip on upper track → Inspector → Compositing section
- **Opacity**: 0-100% transparency
- **Composite Mode**: Normal, Add, Subtract, Multiply, Screen, Overlay, and many more
- These work on clips stacked on higher video tracks

### Transform
- Inspector → Transform section
- **Position** (X/Y), **Zoom** (scale), **Rotation**, **Anchor Point**
- **Dynamic Zoom**: Auto Ken Burns effect — set start and end crop/position
- **Cropping**: Left, Right, Top, Bottom crop values

### Picture-in-Picture
1. Place the PiP clip on a track above the main clip
2. Select PiP clip → Inspector → Transform
3. Reduce **Zoom** (e.g., 0.3 for 30% size)
4. Adjust **Position X/Y** to place in corner
5. Optionally add **Drop Shadow** from Resolve FX

## Keyframing (Ch 53, p. 1103)

### Setting Keyframes
1. Select clip → open Inspector
2. Click the **diamond keyframe icon** next to any parameter
3. Move playhead to a different frame → change the parameter value
4. A new keyframe is automatically created
5. Resolve interpolates between keyframes

### Keyframe Editor
- Click the **keyframe icon** at bottom-right of clip in timeline to expand the keyframe editor
- View and edit keyframe curves directly
- Right-click keyframes to change interpolation: Linear, Ease In/Out, etc.

## Text-Based Editing (Ch 40, p. 847)

- Resolve can transcribe audio and display it as text in the Timeline
- **Timeline → Transcribe Audio**: Generates a transcript
- Edit by selecting/deleting text — corresponding timeline clips are affected
- Useful for interview-style content, podcasts, rough cuts

## Audio in Edit Page (Ch 45, p. 949)

- **Volume**: Drag the volume line on audio clips
- **Fade handles**: Drag from clip edges for fade in/out
- **Audio Inspector**: EQ, pitch, volume envelope
- **Audio tracks**: Add via right-click on track header
- **Link/Unlink audio**: Ctrl/Cmd-Shift-L to unlink audio from video
- For detailed audio work, switch to Fairlight page

## Tips & Gotchas

- **Snapping**: Press N to toggle snapping (clips snap to edit points, markers, playhead)
- **Linked selection**: Video and audio are linked by default. Unlink to move independently (Ctrl/Cmd-Shift-L)
- **Auto-select tracks**: Enable/disable auto-select on track headers to control which tracks are affected by edits
- **Blade tool**: Press B for the blade/razor tool to split clips at the cursor. Ctrl/Cmd-B splits at playhead.
- **Match Frame**: Press F to find the source clip for the current timeline clip (reverse match frame)
- **Markers**: Press M to add a marker. Double-click to edit name/color. Shift-Up/Down to navigate markers.
- **Undo**: Ctrl/Cmd-Z. Resolve has extensive undo history.
- **Render Cache**: If the timeline stutters, enable Smart Render Cache (Playback → Render Cache → Smart)
- **Position lock**: Right-click clip → Lock to prevent accidental moves
- **Copy/Paste attributes**: Right-click → Copy, then right-click target → Paste Attributes (choose which attributes to paste)
