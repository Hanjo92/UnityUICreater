# HUD Example

## Scenario

The user provides a HUD mockup image and wants a `1920x1080` UGUI implementation that stays stable across aspect ratios.

## Recommended Prompt

```text
Use $unity-mcp-ui-layout to build a 1920x1080 UGUI HUD from the attached mockup.
Treat the image as a composition reference, not a raw pixel map.
Create the root canvas structure first, then SafeAreaRoot and HUDRoot, then add corner and center containers before leaf widgets.
Verify each structural step with screenshots and re-check one alternate aspect ratio before finalizing.
```

## Expected Working Style

1. Inspect current scene and UI roots
2. Build shell and major regions
3. Add one HUD cluster at a time
4. Verify after each slice

## Useful References

- `unity-mcp-ui-layout/references/mcp-call-recipes.md`
- `unity-mcp-ui-layout/references/ugui-hud.md`
- `unity-mcp-ui-layout/references/common-failures.md`
