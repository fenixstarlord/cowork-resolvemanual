# DaVinci Resolve Assistant (OpenCode Skills + Commands)

An OpenCode environment that helps you figure out how to do anything in DaVinci Resolve, powered by structured knowledge from the official DaVinci Resolve 20 Reference Manual.

## What It Does

This project gives OpenCode deep knowledge of DaVinci Resolve's features, workflows, and UI, organized by module (Edit, Cut, Color, Fusion, Fairlight, Deliver). When you ask a question about Resolve, the assistant will:

- Give you step-by-step instructions with specific menu paths, button names, and keyboard shortcuts
- Cite the relevant chapter and page number from the official manual
- Note when a feature requires DaVinci Resolve Studio (vs. the free version)
- Suggest official resources when it's not fully confident

## OpenCode Usage

Use this repository as a normal OpenCode project.

1. Open the project in OpenCode
2. Ask a Resolve question directly, or run the command below
3. The assistant uses the skills in `skills/` to produce structured answers with chapter/page citations

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
| **reel-name-patterns** | Reel name extraction pattern syntax, operators, and examples for the "Assist using reel names" Pattern field |

### Commands

- `/resolve-help <topic>` — Primary command for structured Resolve help
- `/resolvemanual:help <topic>` — Legacy alias kept for compatibility

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

- This project is based on the **DaVinci Resolve 20 Reference Manual** but the assistant may not have every detail; verify with official docs for edge cases or version-specific features
- For the most current information, check [Blackmagic Design's official training resources](https://www.blackmagicdesign.com/products/davinciresolve/training)
- Keyboard shortcuts listed use macOS conventions — on Windows/Linux, substitute Ctrl for Cmd and Alt for Option

## Repository Layout

- `skills/` - Resolve knowledge packs by module
- `commands/resolve-help.md` - Primary command prompt
- `commands/resolvemanual-help.md` - Legacy compatibility alias
- `docs/DaVinci_Resolve_20_Reference_Manual.md` - Source manual reference
