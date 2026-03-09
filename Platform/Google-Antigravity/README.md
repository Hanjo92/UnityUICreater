# Google Antigravity Adapter

This adapter repackages the Unity MCP UI layout workflow as a more execution-oriented prompt package for Google Antigravity-style custom instructions or workspace guidance.

## Files

- `SYSTEM_PROMPT.md`: base instruction set for the assistant

## Usage

1. Open `SYSTEM_PROMPT.md`
2. Paste or adapt it into your Antigravity custom instruction area
3. Use it together with Unity MCP access or an equivalent Unity bridge
4. Pair it with task prompts that include a layout image, target resolution, and the intended UI stack when known

## Goal

Make Antigravity follow the same rules as the Codex skill, but in a firmer system-prompt style that emphasizes execution discipline:

- inspect first
- build in slices
- convert images into relative layout
- use anchors and scaling instead of raw pixels
- verify with screenshots

## Example User Prompts

```text
Build this Unity HUD from the attached mockup at 1920x1080.
Treat the image as a composition reference, not a raw pixel map.
Create parent regions first, choose anchors and CanvasScaler rules, then verify with screenshots.
```

```text
Repair the current UGUI inventory so that slot spacing, detail panel sizing, and scaling remain stable across resolutions.
Preserve the current style.
Inspect first, make bounded changes, and verify at the target resolution and one alternate aspect ratio.
```

```text
Create a modal reward popup for mobile.
Use a ModalLayer with sibling Dimmer and PopupRoot, and keep safe-area handling on PopupRoot.
Do not build the whole screen at once. Implement the popup structure first, then verify portrait and landscape.
```

```text
Compare the current UI against the attached reference image.
Find the structural differences causing the layout drift.
Fix anchors, parent containers, and scaling rules before changing styling or local offsets.
```
