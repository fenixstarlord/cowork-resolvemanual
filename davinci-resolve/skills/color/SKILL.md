---
name: color
description: "Use this skill whenever the user asks about color grading, color correction, color wheels, lift gamma gain, log wheels, HDR grading, LUTs, lookup tables, color nodes, serial nodes, parallel nodes, layer nodes, color curves, hue vs hue, hue vs saturation, qualifiers, HSL qualifier, power windows, masks in color page, scopes, waveforms, vectorscope, parade, histogram, color matching, shot matching, gallery stills, PowerGrades, Magic Mask, Color Warper, ColorSlice, primaries, secondaries, image stabilization in color page, Resolve FX, noise reduction, film grain, or anything related to the Color page in DaVinci Resolve."
---

# Color Page — Color Grading & Correction

When answering Color page questions, cite relevant chapters: Color (Ch 125-149, p. 2953-3414), Color Page Effects (Ch 151-169, p. 3416-3662). Always include chapter and page references.

## Page Overview (Ch 126, p. 2965)

The Color page is a professional grading environment organized around a node-based correction pipeline with dedicated scopes, qualifiers, and tracking tools.

### Interface Layout
- **Viewer** (top center): Preview with split-screen wipe controls for before/after comparison
- **Gallery** (top left): Store and recall stills, grades, and PowerGrades
- **Node Editor** (top right): Build grade node trees
- **Timeline** (middle): Thumbnail timeline and mini timeline for clip navigation
- **Left Palettes**: Camera Raw, Color Match, Color Wheels (Primaries), HDR, RGB Mixer, Motion Effects
- **Center Palettes**: Curves, Color Warper, Qualifiers, Windows, Tracker, Magic Mask, Blur, Key, Sizing
- **Scopes** (bottom or floating): Waveform, Parade, Vectorscope, Histogram
- **Keyframe Editor** (bottom): Animate grade changes over time

## Node-Based Grading (Ch 143-145, p. 3308-3339)

Every grade is built as a chain of **nodes**, each performing one correction. This allows precise, non-destructive, stackable adjustments.

### Node Types
| Node Type | Purpose | Shortcut |
|-----------|---------|----------|
| **Serial** | Processes sequentially — output of one feeds into next. Most common. | Option-S |
| **Parallel** | Multiple corrections processed independently, then combined. Good for simultaneous isolated adjustments. | Option-P |
| **Layer** | Compositing-style nodes with foreground/background. Useful for keyed corrections. | Option-L |
| **Splitter/Combiner** | Split image into individual channels (Y, R, G, B) for per-channel grading. | Option-Y |
| **Group** | Pre-Group and Post-Group nodes that affect all clips in a group. | Right-click → Add Group |
| **Outside Node** | Automatically applies correction to everything NOT selected by the previous node's qualifier/window. | Option-O |

### Node Operations
- **Add Serial Node**: Option-S (most common operation)
- **Add before/after**: Right-click → Add Node → choices
- **Label nodes**: Right-click → Label → type description (e.g., "Skin Tone", "Sky", "Overall Look")
- **Enable/Disable node**: Ctrl/Cmd-D (toggles selected node on/off)
- **Reset node**: Right-click → Reset Node Grade (or Ctrl/Cmd-Home for all corrections)

## Primary Grading Controls (Ch 131-133, p. 3058-3127)

### Color Wheels (Primaries)
Four display modes (switch via dropdown at top of palette):

1. **Primaries Wheels** (default): Lift (shadows), Gamma (midtones), Gain (highlights), Offset (all)
   - Drag the color balance indicator to shift color
   - Use the ring below each wheel to adjust luminance (master wheel)

2. **Primaries Bars**: Horizontal sliders for Y (luminance), R, G, B channels of each range
   - More precise numeric control than wheels

3. **Log Wheels**: Shadows, Midtones, Highlights, Offset
   - Better for cinematic/filmic grading — more natural response
   - Especially useful with log-encoded footage

4. **HDR Wheels** (Ch 132, p. 3077): Zone-based grading with customizable exposure zones
   - Dark, Shadow, Light, Specular zones (expandable to 6 zones)
   - Each zone has color wheel + exposure control
   - **Studio only** for full HDR metadata authoring (Dolby Vision, HDR10+)

### Key Controls on All Modes
- **Contrast**: Expand or compress tonal range
- **Pivot**: Set the center point around which Contrast operates
- **Saturation**: Overall color saturation (also per-range controls)
- **Hue**: Shift all hues (rarely used for correction — more for creative effects)
- **Color Boost**: Increases saturation of desaturated areas without oversaturating already-saturated areas
- **Shadow/Highlight Tint**: Quick warm/cool adjustment to shadows or highlights

## Curves (Ch 134, p. 3107)

Multiple curve types for precise color manipulation:

| Curve Type | Purpose |
|-----------|---------|
| **Custom** | Traditional RGB curves (like Photoshop). Master + R/G/B channels. Most versatile. |
| **Hue vs Hue** | Shift specific hues to different hues (e.g., make greens more teal) |
| **Hue vs Sat** | Adjust saturation of specific hues (e.g., desaturate only yellows) |
| **Hue vs Lum** | Adjust luminance of specific hues |
| **Lum vs Sat** | Adjust saturation based on luminance (e.g., desaturate shadows) |
| **Sat vs Sat** | Adjust saturation based on existing saturation levels |

- Add control points by clicking on the curve
- **Eyedropper**: Sample a color from the image to auto-place a control point at that hue/lum/sat
- Soft/hard roll-off on each control point

## ColorSlice (Ch 135, p. 3128) and Color Warper (Ch 136, p. 3135)

### Color Warper
- A 2D color manipulation tool — shows all colors as a circular mesh
- Drag mesh points to shift specific colors
- More intuitive than curves for targeted color changes
- Can select and manipulate specific hue/saturation ranges visually

### ColorSlice
- Similar concept to Color Warper but uses a "slice" approach
- Divide the color space into adjustable segments
- Each segment can be independently shifted

## Qualifiers (Ch 137, p. 3157)

Qualifiers let you isolate specific colors in the image for targeted correction (secondary grading).

### HSL Qualifier (most common)
1. Select the **eyedropper** tool in the Qualifier palette
2. Click on the image area you want to isolate (e.g., skin tone, sky)
3. Refine with **Hue**, **Saturation**, and **Luminance** range sliders
4. Toggle **Highlight** (Shift-H) to see the selected area as a matte
5. Make corrections — they only affect the qualified area

### 3D Qualifier
- Alternative qualifier that uses a 3D color space model
- Can sometimes produce better results for tricky selections
- Add samples with + eyedropper, remove with - eyedropper

### Qualifier Workflow
- Use qualifiers on a dedicated node (typically node 2 or later in the serial chain)
- First node = primary correction, subsequent nodes = secondary (qualified) corrections
- **Outside Node** (Option-O): Automatically affects everything NOT selected

## Power Windows (Ch 138, p. 3185)

Shape-based isolation tools that restrict corrections to specific image regions:

| Window Type | Shape | Use Case |
|------------|-------|----------|
| **Circle** | Oval/ellipse | Faces, spotlights, vignettes |
| **Linear** | Two parallel lines with gradient | Horizons, sky/ground splits |
| **Polygon** | Custom polygon | Irregular shapes |
| **PowerCurve** | Bezier curve shape | Precise custom shapes |
| **Gradient** | Radial/linear gradient | Smooth falloff effects |

- **Softness**: Control edge feathering for each window
- **Combining windows**: Use multiple windows on one node; switch between Add/Subtract modes
- **Tracking windows**: Track windows to follow movement (see Tracker below)

## Magic Mask (Ch 139, p. 3201)

AI-powered masking tool that automatically isolates people or objects. **Studio feature** (Neural Engine).

### Person Mode
- Select a person in the frame → Magic Mask isolates them
- Can isolate specific body parts: face, hair, arms, torso, legs
- Tracks automatically through the clip

### Object Mode
- Draw a stroke on the object → Magic Mask isolates it
- Track forward/backward through the clip

## Tracking (Ch 140, p. 3229)

Track power windows to follow moving subjects:

1. Position your window/qualifier on the subject
2. Open the **Tracker** palette
3. Choose tracking type: Point, Area, 3D
4. Choose what to track: Pan, Tilt, Zoom, Rotate, Perspective 3D
5. Click **Track Forward** (or Reverse)
6. The window follows the subject throughout the clip

## Scopes (Ch 127, p. 2983)

Video scopes are essential for accurate, objective grading:

| Scope | Shows | Primary Use |
|-------|-------|-------------|
| **Waveform** | Luminance levels (0-100 IRE or 0-1023) | Exposure, black/white point |
| **Parade** | R, G, B channels separately | Color balance, matching channels |
| **Vectorscope** | Hue and saturation on a circular plot | Skin tone line, saturation levels |
| **Histogram** | Pixel distribution across tonal range | Overall exposure distribution |

- **Scopes placement**: Workspace → Video Scopes (or dock in page layout)
- **Broadcast safe**: Use waveform to ensure levels stay within 0-100 IRE for broadcast
- **Skin tone line**: On vectorscope, skin tones should fall on the line between yellow and red (roughly 11 o'clock)

## Gallery & Grade Management (Ch 141-142, p. 3256-3307)

### Gallery Stills
- **Grab still**: Right-click viewer → Grab Still (or Ctrl/Cmd-Option-G)
- **Compare**: Double-click a still to toggle split-screen comparison with current grade
- **Apply grade from still**: Middle-click (or right-click → Apply Grade) to copy the grade to current clip
- **Albums**: Organize stills into albums for different scenes/looks

### PowerGrades
- Grades saved in the PowerGrade album persist across projects
- Useful for building a library of reusable looks

### Grade Versions
- Multiple grade versions per clip (right-click → Versions)
- Compare different grading approaches without losing work

### Shot Matching Workflow
1. Grade your hero/reference shot first
2. Grab a still of it (right-click → Grab Still)
3. Navigate to the next clip
4. Use **Color Match** (automatic) or manually match using the still as split-screen reference
5. Fine-tune with curves and color wheels
6. Alternatively: Right-click still → Apply Grade to apply the exact same node tree

## LUTs (Lookup Tables) (Ch 125, p. 2953; Ch 9, p. 219)

- **Technical LUTs**: Transform color spaces (e.g., Log to Rec.709)
- **Creative LUTs**: Apply looks/styles (e.g., film emulations)
- **Apply LUT to node**: Right-click node → LUT → select from list
- **Apply as input LUT**: Right-click clip in Media Pool → LUT → select
- **LUT browser**: Color → LUT → browse and preview LUTs
- **Monitor LUT**: Applied for viewing only, doesn't affect render (Workspace → Monitor LUT)

## Image Stabilization (Ch 152, p. 3429)

The Color page Tracker palette includes a **Stabilizer** mode:

1. Open **Tracker** palette → switch to **Stabilizer** mode
2. Choose tracking points or use automatic analysis
3. Choose stabilization type: Translation, Translation + Rotation, or Perspective
4. Choose smoothing: Smooth (reduces shake) or Stabilize (locks shot)
5. Set **Smooth** strength (higher = more stable, more crop)
6. Click **Stabilize** to analyze

**Note**: Stabilization is also available in the Edit page Inspector (simpler controls) and the Cut page.

## Resolve FX in Color Page (Ch 151-169, p. 3416-3662)

Key Resolve FX categories available as Color page plugins:

| Category | Key Effects |
|----------|-----------|
| **Blur** | Gaussian, Lens Blur, Directional Blur, Radial Blur, Zoom Blur |
| **Color** | Color Space Transform, DCTL, Color Compressor |
| **Film Emulation** | Film Grain (Studio), Halation, Film Damage |
| **Generate** | Lens Flare, Light Rays |
| **Key** | 3D Keyer, HSL Keyer, Luma Keyer |
| **Light** | Glow, Lens Flare, Light Rays, Aperture Diffraction |
| **Refine** | Dead Pixel Fixer, Dust Buster, Deflicker, Automatic Dirt Removal |
| **Revival** | Film Damage, Chromatic Aberration Correction |
| **Sharpen** | Sharpen, Unsharp Mask |
| **Stylize** | Blanking Fill, Drop Shadow, Tilt-Shift, Vignette |
| **Temporal** | Noise Reduction (Temporal + Spatial), Motion Blur |
| **Transform** | Lens Correction, DVE (Digital Video Effect) |
| **Warp** | Mesh Warp, Face Refinement (Studio) |

- Add Resolve FX via: Right-click node → Add OFX → select plugin
- Or use the OpenFX panel in the Color page

## Common Grading Workflows

### Basic Color Correction (Ch 125, p. 2953)
1. **Node 1 — Primary correction**: Set white balance, exposure (lift/gamma/gain), contrast, saturation
2. Use **scopes** (waveform for exposure, parade for color balance)
3. Set black point (Lift) and white point (Gain) using waveform as guide
4. Adjust Gamma for midtone brightness
5. Balance color channels using Parade scope

### Secondary Corrections
1. Add a new Serial Node (Option-S)
2. Use **Qualifier** to isolate a color range (e.g., skin tones, sky)
3. Or use **Power Window** to isolate an area
4. Make targeted adjustments on this node
5. Add more nodes for additional isolated corrections

### Color Matching Between Shots
1. Grade your reference shot → Grab Still
2. Move to next clip → display still as split-screen
3. Use **Color Match** (auto) or manually match exposure/color using wheels + scopes
4. Or apply the grade from the still directly

## Tips & Gotchas

- **Always start with primary correction** before doing secondaries (qualifier/window work)
- **Label your nodes** — complex grades can have 10+ nodes, labels keep things organized
- **Ctrl/Cmd-D** to bypass a node (temporarily disable to see before/after)
- **Shift-D** to bypass all grades (compare with/without all corrections)
- **Image processing order** (Ch 144, p. 3329): Input sizing → Color input LUT → Node tree → Color output LUT → Output sizing
- **Qualifier + Window**: Use both on the same node for extremely precise isolation
- **HDR grading**: Requires HDR-capable monitoring for accurate results
- **Noise reduction** (Temporal + Spatial): Set in Motion Effects palette. Temporal NR requires Studio for best quality.
- **Copy grades**: Use **ColorTrace** (Ch 149, p. 3395) to copy grades from one timeline/project to another based on timecode matching
