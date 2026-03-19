---
name: fairlight
description: "Use this skill whenever the user asks about audio editing, audio mixing, sound design, audio effects, EQ, equalization, compression, dynamics, limiting, noise reduction, de-essing, de-humming, audio levels, loudness, LUFS, audio tracks, busses, bus routing, ADR, voice recording, Fairlight FX, audio meters, panning, surround sound, immersive audio, Dolby Atmos, fades, crossfades, audio automation, mix automation, or anything related to the Fairlight page in DaVinci Resolve."
---

# Fairlight Page — Audio Post-Production

When answering Fairlight questions, cite relevant chapters: Ch 170-184, p. 3663-4018 in the DaVinci Resolve manual.

## Page Overview (Ch 170, p. 3663)

Fairlight is a full professional audio post-production environment built into Resolve. It provides multi-track editing, mixing, effects processing, ADR, and loudness metering.

### Interface Layout
- **Audio Timeline**: Multi-lane format (one track can have multiple channels based on type). Supports clip layering.
- **Mixer**: Left section = track channel strips, Right section = bus channel strips. Each strip has Input, FX, EQ, Dynamics, Pan, Sends, Fader.
- **Monitoring Panel** (top): Track meters, bus meters, control room meters, loudness meters.
- **Media Pool**: Audio clip browser with preview.
- **Inspector**: Clip-level audio parameters.

## Track Types & Setup (Ch 171, p. 3719)

| Track Type | Channels | Use Case |
|-----------|----------|----------|
| **Mono** | 1 | Dialogue, single-mic recordings |
| **Stereo** | 2 (L/R) | Music, stereo ambience |
| **5.1** | 6 | Surround sound |
| **7.1** | 8 | Extended surround |
| **Adaptive** | Variable | Flexible channel count |

- **Add tracks**: Right-click track header area → Add Track (or Add Tracks for multiple)
- **Change type**: Right-click track → Change Track Type To
- **Color-code tracks**: Right-click → Change Track Color (16 options)
- **Lock tracks**: Lock icon prevents edits to locked tracks

### Bus Routing
- **Main Bus**: Default output bus for final mix
- **Submix Buses**: Create via Mixer for grouping (e.g., all dialogue, all music, all SFX)
- **Bus Sends**: Route individual tracks to submix buses (set send level per track)
- **VCA**: Virtual Control Assignment — control groups of faders from one master fader (assign tracks to VCAs 1-10)

## Audio Editing (Ch 175, p. 3772)

### Selection Modes
- **Pointer Mode** (A key): Click to select clips. With track selected, playhead auto-selects clips at intersection.
- **Range Mode** (R key): Select partial clip regions with In/Out points.
- **Focus Mode**: Multi-tool — I-beam (upper area) for time selection, Hand (lower area) for clip moves, Trim tool (near gain line) for trimming.

### Basic Operations
- **Split clip**: Position playhead → Ctrl/Cmd-B (or Razor tool)
- **Move clips**: Drag to new position or track
- **Trim**: Drag clip edges to shorten/lengthen
- **Slip**: Move content within clip boundaries without changing clip position
- **Fades**: Drag the fade handle at clip edges. Adjustable curve shape.
- **Crossfades**: Overlap two clips → automatic crossfade. Or use Batch Fade & Crossfade Editor.
- **Gain line**: Drag the horizontal line on clips to adjust clip gain (volume)

### Clip Layering
- When clips overlap, the top layer plays and mutes overlapping lower layers
- Overwrite Mode (default): Overlapping portions are removed from lower clip (non-destructive)

## Mixer Channel Strip (Ch 177, p. 3843)

Each track's mixer strip (top to bottom):

1. **Input**: Patch inputs, buses, utility signals
2. **Track FX**: Voice Isolation, Dialogue Leveler, Dialogue Separator, Music Remixer, Ducker
3. **Effects**: Insert Fairlight FX, VST, or AU plugins
4. **EQ**: 4-band parametric EQ with High/Low Pass filters
   - 4 EQ types: Earth, Air, Ice, Fire (different frequency response characters)
   - Graphical display + numeric controls
   - Double-click the EQ area to expand full-size editor
5. **Dynamics**: 3-section processor
   - **Expander/Gate**: Reduce noise during quiet sections
   - **Compressor**: Even out dynamic range (set threshold, ratio, attack, release)
   - **Limiter**: Hard ceiling to prevent clipping
   - Double-click to expand full-size editor
6. **Pan**: Stereo balance or surround panning. Option-double-click for 3D Audio Pan (Atmos, Auro 3D).
7. **Bus Sends**: Route to submixes
8. **Fader**: Main level control. Double-click resets to 0 dB. Hold Shift for 0.1 dB fine control.

### Processing Order
- Default: EQ → Dynamics → Effects
- Can be reordered via the **Order** dropdown on the channel strip

## Common Audio Tasks

### Fix Audio Levels
1. Go to Fairlight page (Shift-7)
2. Play the timeline and watch the **track meters** and **loudness meter**
3. Adjust individual track faders to balance levels
4. Use **Dynamics → Compressor** to even out inconsistent levels (start with ratio 3:1, threshold around -20 dB)
5. Add a **Limiter** on the Main bus to prevent clipping (ceiling at -1 dB)
6. Check the **Loudness meter** for broadcast/platform standards

### Remove Background Noise
1. Select the audio clip or track
2. Open Mixer → Effects slot → add **Noise Reduction** (Fairlight FX)
3. Use **Auto Speech Mode** for dialogue (automatically detects and removes noise around speech)
4. Or manually: set Learn mode, play a noise-only section, then apply reduction
5. Adjust **Threshold** and **Amount** to taste — too aggressive causes artifacts

### Fix Sibilance (De-Esser)
1. Add **De-Esser** (Fairlight FX) to the track's Effects slot
2. Set frequency range (typically 4-8 kHz for sibilance)
3. Adjust threshold until "s" sounds are controlled but speech remains natural

### Remove Hum (De-Hummer)
1. Add **De-Hummer** (Fairlight FX) to the track
2. Set to 50 Hz (EU/Asia) or 60 Hz (North America) based on your power frequency
3. Enable harmonics to remove overtones

### Set Up EQ for Dialogue
1. Double-click the EQ section on the track's mixer strip
2. **High-pass filter**: Set around 80-100 Hz to remove rumble
3. **Band 1**: Slight cut around 200-300 Hz to reduce muddiness
4. **Band 3**: Slight boost around 2-4 kHz for clarity/presence
5. **Low-pass filter**: Set around 12-16 kHz to remove hiss (optional)

## Loudness Standards & Metering (Ch 182, p. 3978)

| Standard | Target | Region/Use |
|----------|--------|-----------|
| **EBU R128** | -23 LUFS | Europe/UK broadcast |
| **ATSC A/85** | -24 LKFS | North America broadcast |
| **YouTube** | -14 LUFS | YouTube recommended |
| **Spotify** | -14 LUFS | Spotify normalization target |
| **Apple Music** | -16 LUFS | Apple normalization target |
| **Podcast** | -16 to -18 LUFS | General podcast standard |

- **Loudness meter** display options: Relative scale (0 = target) or Absolute scale (shows LUFS values)
- **Measurements**: Short-term, Short Max, Range (LU), Integrated (overall program loudness)
- **Audio normalization** can be applied on export in Deliver page

## Mix Automation (Ch 178, p. 3892)

- **Arm automation**: Click the automation arm button on a track
- **Record**: Play the timeline and move faders/knobs — changes are recorded as automation
- **Automation modes**: Touch (returns to previous value when released), Latch (holds new value), Write (overwrites everything)
- **Edit automation**: Switch to automation view and edit curves directly on the timeline

## Fairlight FX (Ch 181, p. 3935)

Built-in cross-platform audio plugins:

| Effect | Purpose |
|--------|---------|
| **Noise Reduction** | Remove background noise from dialogue |
| **De-Esser** | Control sibilance ("s" sounds) |
| **De-Hummer** | Remove electrical hum (50/60 Hz) |
| **Dialogue Leveler** | Automatically even out dialogue levels |
| **Voice Isolation** | AI-powered voice separation from background (Studio) |
| **Music Remixer** | AI-powered stem separation (Studio) |
| **Dialogue Separator** | Separate dialogue from other audio (Studio) |
| **Reverb** | Add room/space ambience |
| **Delay** | Echo/delay effects |
| **Chorus** | Thicken audio with modulated copies |
| **Flanger** | Sweeping comb filter effect |
| **Distortion** | Overdrive/distortion |
| **Limiter** | Brick-wall limiting |
| **Soft Clipper** | Gentle saturation/clipping |
| **Ducker** | Auto-duck music under dialogue |

- VST and AU (macOS) third-party plugins are also supported
- Add effects: Click the Effects slot in the Mixer → select plugin

## Recording & ADR (Ch 173-174, p. 3752-3771)

### Basic Recording
1. Arm a track for recording (click the R/arm button on track header)
2. Set input source in Mixer → Input slot
3. Position playhead → click Record (or press Shift-R on some keyboard layouts)
4. Record your audio → press Stop

### ADR (Automated Dialog Replacement) (Ch 174, p. 3762)
- Three panels: **List** (cue management), **Record** (session control), **Setup** (configuration)
- Set up cues with In/Out timecodes, character names, dialogue text
- 3-beep countdown, video streamer, on-screen cue text
- Multiple takes with star ratings
- Import/export cue lists as CSV

## Tips & Gotchas

- **Audio from Edit page**: Audio adjustments made in Edit page Inspector carry over to Fairlight (and vice versa)
- **Track vs clip volume**: Track fader controls overall track level; clip gain line controls individual clip levels. Use both for different purposes.
- **Monitoring**: Solo a track (S button) to hear it in isolation. Mute (M) to silence a track.
- **Smart Zoom**: Cmd/Ctrl-Option-E to auto-fit track height for easy editing
- **Fairlight FX are cross-platform**: They work on macOS, Windows, and Linux (unlike VST/AU which are platform-specific)
- **Audio effects are NOT exported** when doing round-trip exports (AAF/XML). They stay in Resolve.
