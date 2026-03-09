# Codex Adapter

Codex is the default platform for this repository.

## Canonical Skill

Use the root skill folder directly:

- [`unity-mcp-ui-layout/`](../../unity-mcp-ui-layout)

## Install

### Windows

```powershell
Copy-Item -Recurse -Force .\unity-mcp-ui-layout $HOME\.codex\skills\
```

### macOS / Linux

```bash
cp -R ./unity-mcp-ui-layout ~/.codex/skills/
```

## Invoke

```text
Use $unity-mcp-ui-layout to build or fix a Unity UI layout from a mockup, screenshot, or target resolution.
```

## Example User Prompts

```text
Use $unity-mcp-ui-layout to build a 1920x1080 UGUI HUD from the attached layout image.
Translate the image into anchors, parent containers, and CanvasScaler rules.
Verify the result with screenshots instead of raw pixel placement.
```

```text
Use $unity-mcp-ui-layout to repair the current inventory layout.
Keep it in UGUI, preserve the existing visual style, and fix slot spacing, anchors, and scaling drift.
Check the result at 1920x1080 and one narrower aspect ratio.
```

```text
Use $unity-mcp-ui-layout to create a mobile settings popup in UGUI.
Keep Dimmer and PopupRoot as siblings under ModalLayer, and apply safe area to PopupRoot.
Verify portrait and landscape before finalizing.
```

```text
Use $unity-mcp-ui-layout to inspect the current UI first and tell me why the top-right HUD is drifting.
Do not redesign unrelated areas.
Find whether the issue comes from CanvasScaler, anchors, or parent layout structure, then apply the smallest fix.
```
