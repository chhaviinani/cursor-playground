---
name: repo-map
description: Builds a visual repo map as a Cursor canvas in the sandbox layout. Use when the user asks to build a repo map, map this repo, visualize the folder, or show how files and rules connect.
---

# Repo map

when i ask you to build a repo map, use this type of format you just created in canvas

Read and follow `~/.cursor/skills-cursor/canvas/SKILL.md` before writing the file. Output is a canvas, not a markdown dump.

## Write here

`/Users/<user>/.cursor/projects/<workspace>/canvases/repo-map.canvas.tsx`

Reuse that path if a repo map canvas already exists. Import only from `cursor/canvas`. Default-export one component. Embed real repo data; no empty sections.

## Layout (keep this order)

1. **Title** — `H1` repo name + one-sentence what this folder is for.
2. **Stats** — `Row` of `Stat`: file count, project rules, project skills, and the default edit target (or equivalent primary file). Use `tone="warning"` on a zero that matters.
3. **How the folder is wired** — `H2` + short caption + horizontal DAG via `computeDAGLayout`. Nodes are files/folders; edges show ownership and “this points work at that.” Highlight the primary file with `accent.primary` border and `fill.primary` background. Caption: source and date.
4. **What is on disk** — `UsageBar` of file mix (with `Swatch` legend) + striped `Table` of Path / Role / Agent should. Tone the primary-file row `success`.
5. **Rules in force** — `Grid` of `Card`s (filename in `CardHeader`, always vs glob in a `Pill`). `Callout` only if something important is missing (e.g. no skills).
6. **Intended loop** — what a human should do here + `CollapsibleSection` file tree.
7. **Footer** — workspace path + what this repo is *not*.

## Graph rules

- Direction `horizontal`. Node ~188×52. Label = filename; subtitle = kind (rule, demo file, onboarding).
- Draw edges with `theme.stroke.primary`. Colors only from `useHostTheme()`.
- No gradients, emojis, or box-shadows. Mix open sections with cards — do not card every block.

## Chat

Link the canvas with its full absolute path. Keep the chat note short; the canvas is the deliverable.
