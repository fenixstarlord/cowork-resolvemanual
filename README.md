# DaVinci Resolve Assistant Plugin

A Cowork plugin that helps you figure out how to do anything in DaVinci Resolve, powered by structured knowledge from the official DaVinci Resolve 20 Reference Manual.

## What It Does

This plugin gives Claude deep knowledge of DaVinci Resolve's features, workflows, and UI — organized by module (Edit, Cut, Color, Fusion, Fairlight, Deliver). When you ask a question about Resolve, Claude will:

- Give you step-by-step instructions with specific menu paths, button names, and keyboard shortcuts
- Cite the relevant chapter and page number from the official manual
- Note when a feature requires DaVinci Resolve Studio (vs. the free version)
- Suggest official resources when it's not fully confident

## Installation

1. **Add the marketplace** (if you haven't already):
   ```
   claude plugin marketplace add <owner>/<repo>
   ```

2. **Install the plugin**:
   ```
   claude plugin install resolvemanual@<marketplace-name>
   ```

## What's Included

### Skills

| Skill | Covers |
|-------|--------|
| **resolve-fundamentals** | Page-based architecture, Free vs Studio, project settings, terminology |
| **resolve-manual-index** | Master index of the full manual — the backbone for finding any topic |
| **edit-and-cut** | Edit & Cut pages — editing, trimming, multicam, transitions, titles, speed effects, subtitles |
| **color** | Color page — grading, nodes, scopes, qualifiers, windows, LUTs, Magic Mask |
| **fusion** | Fusion page — compositing, green screen, tracking, masks, particles, 3D |
| **fairlight** | Fairlight page — audio mixing, EQ, dynamics, noise reduction, loudness |
| **deliver** | Deliver page — export presets, codecs, render queue, DCP/IMF |

### Commands

- `/resolvemanual:help <topic>` — Ask about any DaVinci Resolve topic and get a structured, step-by-step answer with manual references

## Example Questions

- "How do I remove green screen in Resolve?"
- "How do I export for YouTube?"
- "How do I match color between two clips?"
- "How do I add subtitles?"
- "What's the difference between the Cut and Edit page?"
- "How do I use Fusion to add a lower third?"
- "How do I fix audio levels in Fairlight?"
- "How do I stabilize shaky footage?"
- "How do I use speed ramps?"
- "How do I create a compound clip?"

## Important Notes

- This plugin is based on the **DaVinci Resolve 20 Reference Manual** but Claude may not have every detail — always verify with official docs for edge cases or version-specific features
- For the most current information, check [Blackmagic Design's official training resources](https://www.blackmagicdesign.com/products/davinciresolve/training)
- Keyboard shortcuts listed use macOS conventions — on Windows/Linux, substitute Ctrl for Cmd and Alt for Option
