---
name: scene-anchor-system
description: Use when a game, visual novel, interactive story, or visual project needs consistent background spaces, scene bibles, asset role classification, image-generation constraints, or manifest-to-background mapping without layout drift.
---

# Scene Anchor System

## Core Principle

Same space means same structure. Treat scene art as anchored spaces plus state changes, not as separate illustrations that only share a mood or style.

## Workflow

1. Locate current background assets, runtime manifest keys, design docs, screenshots, and any image-generation prompts.
2. Classify every visual asset into one role: `BASE_SPACE`, `STATE_VARIANT`, `CLOSE_UP`, `MEMORY_CUT`, `EVENT_INSERT`, `UI_OR_REPORT_SURFACE`, or `EXTERNAL_SPACE`.
3. Pick exactly one base image for each persistent space. Do not allow two competing bases for the same room, corridor, shop, street, or hub.
4. Lock object anchors for persistent spaces: core furniture, windows, doors, desks, beds, major props, horizon/camera relation, and interaction hotspots.
5. Define allowed changes for variants: lighting, weather, time of day, emotional overlay, temporary props, clutter state, and mild camera noise.
6. Map runtime keys or manifest entries to scene roles before changing code, data, or prompts.
7. Patch or create a scene bible and Codex/agent constraints before generating new art or wiring replacements.

## Rules

- Variants may change atmosphere, not topology.
- Close-ups may crop or magnify a base-space object, but must not contradict the base layout when returning to the main scene.
- Memory cuts and event inserts are allowed to be compositionally different, but they must be labeled as inserts rather than persistent spaces.
- UI overlays are screen layers unless the project explicitly treats them as diegetic objects in the scene.
- Narrative variables, skip states, compression states, or report states should alter overlays, text, lighting, and availability; they should not silently move furniture or redefine the room.
- Preserve existing runtime keys unless the project already has a migration plan. Add role metadata beside current keys instead of renaming casually.

## Output Contract

When using this skill, report:

- Current evidence inspected: files, manifests, screenshots, or docs.
- Asset classification table.
- One base scene per persistent space.
- Locked anchors and interaction hotspots.
- Allowed and forbidden changes for variants.
- Manifest or schema recommendations.
- Unresolved art decisions that need human confirmation.
- Validation checklist and what could not be visually verified.

## Validation

Use structured manifest/data parsing when available. Inspect screenshots or actual image files before claiming visual consistency. If only filenames and docs are available, label the result as a semantic audit rather than a visual QA pass.

## Reference

For a reusable scene bible template, read `references/scene-bible-template.md`.
