# Scene Bible Template

Use this template to convert a loose set of backgrounds into a stable scene system.

## 1. Scene Roles

| Asset | Role | Persistent Space | Use | Notes |
| --- | --- | --- | --- | --- |
| `example_room_morning.png` | `BASE_SPACE` | `home_room` | main room anchor | owns layout |
| `example_room_night.png` | `STATE_VARIANT` | `home_room` | night lighting | inherits layout |
| `example_desk_closeup.png` | `CLOSE_UP` | `home_room` | object interaction | crop only |
| `example_argument.png` | `MEMORY_CUT` | none | event insert | not a room base |
| `example_report.png` | `UI_OR_REPORT_SURFACE` | none | interface layer | screen-space UI |

Role definitions:

- `BASE_SPACE`: the canonical layout for a persistent space.
- `STATE_VARIANT`: the same space with different light, time, weather, emotional state, or temporary prop state.
- `CLOSE_UP`: a partial view of a known base-space object or corner.
- `MEMORY_CUT`: a subjective memory image that does not define a reusable room.
- `EVENT_INSERT`: a one-off event shot, cutaway, flashback, or evidence beat.
- `UI_OR_REPORT_SURFACE`: menus, reports, overlays, terminal views, letters, logs, and other interface surfaces.
- `EXTERNAL_SPACE`: a separate persistent location with its own base layout.

## 2. Persistent Space Contract

```yaml
scene_id: home_room
base_asset: example_room_morning.png
scene_role: BASE_SPACE
layout_lock: true
core_anchors:
  bed:
    relation: left side, fixed scale, fixed wall relation
  desk:
    relation: foreground right, fixed surface orientation
  window:
    relation: back wall center/right, primary light source
  door:
    relation: back/side wall, fixed entry direction
interaction_hotspots:
  curtain:
    attach_to: window
  phone:
    attach_to: desk
allowed_variants:
  - lighting
  - weather
  - time_of_day
  - emotional_overlay
  - clutter_state
  - temporary_props
forbidden_changes:
  - moving core furniture
  - changing window/door positions
  - changing desk orientation
  - changing room proportions
  - replacing persistent props without a story reason
```

## 3. Variant Contract

```yaml
asset: example_room_night.png
inherits_from: home_room
scene_role: STATE_VARIANT
variant_type: night_lighting
allowed_to_change:
  - light color
  - visible shadow density
  - screen tone
must_match_base:
  - bed position
  - desk position
  - window position
  - camera angle
  - major object scale
```

## 4. Runtime Mapping

Prefer adding role metadata beside current runtime keys:

```json
{
  "key": "room_night",
  "path": "assets/images/backgrounds/example_room_night.png",
  "scene_id": "home_room",
  "scene_role": "STATE_VARIANT",
  "inherits_from": "home_room"
}
```

Do not rename working runtime keys only to make the scene bible cleaner. Use aliases or metadata until there is a deliberate migration.

## 5. Generation Prompt Frame

```text
Scene type:
Base space:
Fixed anchors:
Allowed changes:
Forbidden changes:
Output purpose:
Validation checklist:
```

Example:

```text
Scene type: STATE_VARIANT
Base space: the same small bedroom from the approved morning base
Fixed anchors: bed left, desk foreground right, window back wall, plant by window, phone on desk
Allowed changes: night lighting, cooler color temperature, softer shadows, slightly messier desk
Forbidden changes: moving the bed, changing the window shape or position, replacing the desk, changing camera angle
Output purpose: narrative background, no UI text
Validation checklist: furniture positions match base, light source still comes from window, object scale stays consistent
```

## 6. Review Checklist

- Is there exactly one base image per persistent space?
- Are variants labeled as variants instead of new spaces?
- Are close-ups attached to base-space objects?
- Are memory/event images excluded from spatial continuity rules?
- Do runtime keys map to roles without breaking existing data?
- Are UI overlays treated independently from background layout?
- Did visual inspection confirm anchor positions, not just mood/style?

## 7. Minimal Rule

Use this formula when deciding whether an image belongs to the same space:

```text
Scene = Base Layout + State Overlay + Optional Insert + Fixed UI Layer
```

If the base layout changes, it is not a variant. It is either a new space, a memory cut, or a mistake.
