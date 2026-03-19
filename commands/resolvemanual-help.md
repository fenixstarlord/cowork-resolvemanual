---
name: resolvemanual:help
description: "Get help with any DaVinci Resolve topic. Usage: /resolvemanual:help <topic>"
args: topic
---

# DaVinci Resolve Help

The user is asking for help with DaVinci Resolve. Their topic is: **$ARGUMENTS**

## Instructions

Follow these steps to provide the best possible answer:

### 1. Identify the Module(s)
Determine which DaVinci Resolve page(s) or module(s) the topic relates to:
- **Media Page** — importing, organizing, metadata
- **Cut Page** — fast editing, quick turnarounds
- **Edit Page** — detailed editing, multicam, effects, transitions, titles, speed effects, subtitles
- **Fusion Page** — visual effects, compositing, green screen, motion graphics, 3D
- **Color Page** — color grading, correction, scopes, LUTs, qualifiers, windows, tracking
- **Fairlight Page** — audio editing, mixing, effects, loudness
- **Deliver Page** — exporting, rendering, codecs, presets
- **Cross-cutting** — project settings, performance, media management

### 2. Pull from Relevant Skills
Use the knowledge from the plugin's skills to build your answer:
- `resolve-manual-index` — find the specific chapter and page number
- `resolve-fundamentals` — for basics, terminology, Free vs Studio differences
- `edit-and-cut` — for editing workflows
- `color` — for grading and color correction
- `fusion` — for VFX and compositing
- `fairlight` — for audio
- `deliver` — for export and rendering

### 3. Structure Your Answer
Provide a clear, step-by-step answer that includes:

1. **Brief explanation** of what the feature/workflow is
2. **Step-by-step instructions** with specific UI references (menu paths, button names, panel names)
3. **Chapter and page citation** — e.g., "For more detail, see Ch 51, p. 1070 in the DaVinci Resolve manual"
4. **Keyboard shortcuts** where applicable (note macOS shortcuts; Windows uses Ctrl instead of Cmd, Alt instead of Option)
5. **Tips or gotchas** if there are common mistakes or important caveats
6. **Studio vs Free** — note if any part of the workflow requires DaVinci Resolve Studio

### 4. When You're Not Confident
If you're not fully confident in the details of your answer:
- Say so clearly
- Suggest the user search for the topic in:
  - The official DaVinci Resolve manual (Help → DaVinci Resolve Reference Manual)
  - Blackmagic Design's training page: https://www.blackmagicdesign.com/products/davinciresolve/training
  - The official DaVinci Resolve YouTube channel

### Example Response Format

**Topic: How to remove green screen**

Green screen removal (chroma keying) is done on the **Fusion page** using the **Delta Keyer** node.

**Steps:**
1. Select the clip with green screen footage in the Edit timeline
2. Switch to the Fusion page (Shift-5)
3. In the Node Editor, select the connection between MediaIn and MediaOut
4. Add a **Delta Keyer** node (Shift-Space → type "Delta Keyer" → Enter)
5. In the Inspector, click the **eyedropper** tool and click on the green screen area in the viewer
6. Refine the key using Pre-Matte, Clean Plate, and Matte controls
7. To add a background: add a MediaIn node (for background footage) or Background node, then connect it to a Merge node's background input

*For more detail, see Ch 63, p. 1210 (Fusion Compositing Introduction) and the Delta Keyer section in the Fusion node reference.*

> **Tip:** For best results, ensure your green screen footage is well-lit and evenly colored. The Delta Keyer handles spill suppression automatically but you may need to fine-tune it.
