---
name: fusion
description: "Use this skill whenever the user asks about Fusion, visual effects, compositing, green screen removal, chroma keying, Delta Keyer, motion graphics, lower thirds, titles, Text+, node-based compositing, Fusion nodes, masks, rotoscoping, tracking, planar tracking, paint, particle systems, 3D compositing, Fusion keyframing, spline editor, MediaIn, MediaOut, Merge node, or anything related to the Fusion page in DaVinci Resolve."
---

# Fusion Page — Visual Effects & Compositing

When answering Fusion questions, cite relevant chapters: Fusion Fundamentals (Ch 63-88, p. 1210-1854), Fusion Page Effects/Nodes (Ch 89-124, p. 1867-2953). Always include chapter and page references so users can look up more detail.

## Core Concepts

Fusion uses a **node-based** compositing workflow (unlike layer-based tools like After Effects). Each node is a single operation (blur, color correct, merge, key, etc.) connected together in a **node tree** flowing left to right.

- **Nodes** have inputs (triangles on left) and outputs (squares on right)
- One output can connect to multiple inputs (branching)
- Multiple outputs combine through **Merge** nodes
- The node tree flows from source (MediaIn) → processing → output (MediaOut)

### Accessing Fusion
- Click a clip in the Edit timeline, then switch to the Fusion page (Shift-5)
- The clip's Fusion composition opens automatically
- A **Fusion badge** appears on clips in the Edit timeline that have Fusion effects

## Key Nodes (Ch 63, p. 1210)

| Node | Purpose | How to Add |
|------|---------|-----------|
| **MediaIn** | Brings timeline clip into Fusion. Auto-created. | Automatic |
| **MediaOut** | Sends result back to timeline. Auto-created. | Automatic |
| **Merge** | Combines two images (foreground over background). The primary compositing node. | Shift-Space → type "Merge" |
| **Background** | Generates a solid color or gradient. Use as base layer. | Shift-Space → type "Background" |
| **Transform** | Pan, tilt, rotate, scale. Resolution-independent. | Shift-Space → type "Transform" |
| **Text+** | Rich text generator with 2D/3D layout, shading, and animation. | Shift-Space → type "Text+" |
| **Delta Keyer** | Professional chroma keyer for green/blue screen removal. | Shift-Space → type "Delta Keyer" |
| **Color Corrector** | Color adjustment node within Fusion. | Shift-Space → type "Color Corrector" |
| **Blur** | Gaussian, directional, and other blur types. | Shift-Space → type "Blur" |
| **Polygon/Ellipse/Rectangle** | Mask shapes for rotoscoping and isolation. | Shift-Space → type name |

**Adding nodes**: Press Shift-Space to open the Select Tool dialog, type the node name, press Enter. Or drag from the Effects Library panel.

## Interface Layout (Ch 64, p. 1216)

- **Toolbar** (top): Buttons to show/hide Media Pool, Effects Library, Clips, Nodes, Spline Editor, Keyframes Editor, Inspector
- **Viewers** (top area): Dual viewers for comparing nodes. Drag a node to a viewer to load it.
- **Node Editor** (center): Where you build compositions. Navigate with scroll/zoom, or use the Navigator mini-map (press V).
- **Inspector** (right): Parameters for the selected node. Tools tab and Modifiers tab.
- **Keyframes Editor**: Timeline-style keyframe management (below node editor)
- **Spline Editor**: Edit animation curves for precise timing control

## Common Workflows

### Green Screen Removal (Ch 63, p. 1210; Delta Keyer)
1. Select clip in Edit timeline → go to Fusion page
2. Add a **Delta Keyer** node between MediaIn and MediaOut
3. In the Inspector, use the **eyedropper** to sample the green/blue screen area
4. Adjust **Clean Plate**, **Matte** controls to refine the key
5. Connect a **Background** node (or another MediaIn) to the Merge node's background input
6. Fine-tune with **Pre-Matte** (shrink/grow matte), **Spill Suppression**, and **Fringe** controls

**Node chain**: MediaIn → Delta Keyer → Merge (foreground) ← Background/MediaIn2 (background) → MediaOut

### Lower Third Title (Text+ node)
1. Select clip → Fusion page
2. Add a **Background** node (set color and opacity for the bar/shape)
3. Add a **Text+** node (type your text, set font/size/color)
4. Add a **Merge** node to combine Background + Text+
5. Add another **Merge** to composite the lower third over the MediaIn footage
6. Use **Transform** nodes to position elements
7. Animate with keyframes (right-click parameter → Animate, then set keyframes on the timeline)

### Picture-in-Picture
1. Add a **Transform** node after the second MediaIn
2. Adjust **Size** (scale down) and **Center** (position) in the Inspector
3. Merge the transformed clip over the main footage using a **Merge** node

### Animated Title
1. Add **Text+** node → type text → set font and styling in Inspector (Styled Text tab)
2. Go to the **Layout** tab for positioning, rotation, shearing
3. Go to **Transform** tab for animation center point
4. Right-click **Size** or **Position** → Animate → set keyframes at different frames
5. Use the **Spline Editor** to adjust ease in/out curves

## Masks & Rotoscoping (Ch 80, p. 1672)

- **Mask types**: Polygon (B-Spline or Bezier), Ellipse, Rectangle, Paint mask
- Add masks by selecting a node, then adding a mask from the toolbar or Shift-Space
- Masks connect to the **effect mask input** (blue triangle) on nodes
- **Rotoscoping**: Draw Polygon mask around subject → animate mask points frame by frame
- **Tip**: Use fewer control points for easier animation. Use Bezier handles for smooth curves.

## Tracking (Ch 82-83, p. 1724-1766)

### Point Tracker (Ch 82, p. 1724)
1. Add a **Tracker** node
2. Place tracking points on high-contrast features
3. Click **Track Forward** (or Track Reverse)
4. Apply tracking data to: Stabilize, Match Move, Corner Pin, or Perspective positioning

### Planar Tracker (Ch 83, p. 1760)
- Tracks flat surfaces (signs, screens, walls) for replacement or stabilization
- Better than point tracking for surfaces that rotate/skew in perspective
- Set the tracking region → Track → apply as Corner Pin or Stabilize

## Keyframing & Animation (Ch 71-72, p. 1458-1507)

- **Set keyframe**: Right-click any parameter → Animate. Then change the value at different frames.
- **Keyframe shortcuts**: Set keyframe at current frame, navigate between keyframes
- **Keyframes Editor**: Shows all animated parameters as horizontal bars with diamond keyframe markers
- **Spline Editor**: Edit curves between keyframes for precise easing (linear, smooth, flat, etc.)
- **Motion paths**: Animated position creates a visible motion path in the viewer (Ch 73, p. 1508)

## Particle Systems (Ch 87, p. 1845)

- **pEmitter**: Creates particles (source)
- **pRender**: Renders particles to 2D image
- Basic chain: pEmitter → pRender → Merge → MediaOut
- Control particle count, velocity, lifespan, color, size
- Add **pDirectionalForce**, **pTurbulence**, etc. between Emitter and Render for behaviors

## 3D Compositing (Ch 85, p. 1772)

- **3D nodes**: Shape3D, Text3D, ImagePlane3D, Camera3D, PointLight3D/SpotLight/AmbientLight, Merge3D, Renderer3D
- 3D workflow: Create 3D objects → light them → add Camera3D → Merge3D → Renderer3D (converts to 2D) → Merge over footage
- **Renderer3D** is required to flatten 3D scene back to 2D for final output

## Tips & Gotchas

- **Performance**: Complex Fusion compositions can be slow. Use Proxy mode (viewer dropdown) and enable Render Cache for Fusion output.
- **Resolution**: Fusion works at the timeline resolution by default. Use the **DoD** (Domain of Definition) to limit processing area for speed.
- **Viewer loading**: Drag nodes directly onto viewer panes. Left viewer = comparison, Right viewer = working view.
- **Undo**: Ctrl/Cmd-Z works per-node and globally.
- **Copy/Paste nodes**: Select nodes → Ctrl/Cmd-C → Ctrl/Cmd-V. Can paste between clips.
- **Groups and Macros** (Ch 68, p. 1366): Group nodes for organization. Create Macros to save reusable node setups.
- **Fusion Templates**: Save compositions as templates in the Effects Library for drag-and-drop reuse in Edit page.

## Studio-Only Fusion Features

- **GPU-accelerated** rendering across multiple GPUs (free version: single GPU)
- Some advanced nodes and Resolve FX may require Studio
- **Optical Flow** nodes for retiming (Speed Warp quality level)
