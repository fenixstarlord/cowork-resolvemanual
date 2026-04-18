---
name: resolve-help
description: "Get help with any DaVinci Resolve topic. Usage: /resolve-help <topic>"
args: topic
---

# DaVinci Resolve Help

The user is asking for help with DaVinci Resolve. Their topic is: **$ARGUMENTS**

## Instructions

Follow these steps to provide the best possible answer:

### 1. Identify the Module(s)
Determine which DaVinci Resolve page(s) or module(s) the topic relates to:
- **Media Page** - importing, organizing, metadata
- **Cut Page** - fast editing, quick turnarounds
- **Edit Page** - detailed editing, multicam, effects, transitions, titles, speed effects, subtitles
- **Fusion Page** - visual effects, compositing, green screen, motion graphics, 3D
- **Color Page** - color grading, correction, scopes, LUTs, qualifiers, windows, tracking
- **Fairlight Page** - audio editing, mixing, effects, loudness
- **Deliver Page** - exporting, rendering, codecs, presets
- **Cross-cutting** - project settings, performance, media management

### 2. Pull from Relevant Skills
Use project skills to build your answer:
- `resolve-manual-index` - find the specific chapter and page number
- `resolve-fundamentals` - basics, terminology, Free vs Studio differences
- `edit-and-cut` - editing workflows
- `color` - grading and color correction
- `fusion` - VFX and compositing
- `fairlight` - audio workflows
- `deliver` - export and rendering

### 3. Use the Strict Response Template
Your answer must include all sections below:

1. **What this does** - one short explanation
2. **Steps** - numbered, concrete UI actions
3. **Manual references** - chapter and page citations
4. **Shortcuts** - include where relevant (macOS first; mention Ctrl/Alt equivalents)
5. **Tips or gotchas** - common pitfalls and fixes
6. **Free vs Studio** - clearly mark Studio-only steps/features
7. **Confidence** - High / Medium / Low

### 4. Confidence and Uncertainty Rules
If confidence is not high:
- Say what is uncertain
- Provide the most likely path anyway
- Tell the user where to verify:
  - DaVinci Resolve manual (Help -> DaVinci Resolve Reference Manual)
  - https://www.blackmagicdesign.com/products/davinciresolve/training
  - Official DaVinci Resolve YouTube channel

### 5. Citation Rules
- Always include at least one chapter/page citation
- Prefer the most specific chapter for the workflow
- If multiple pages are involved, cite each major step's source chapter/page
