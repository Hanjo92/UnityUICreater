# Popup Safe Area Example

## Scenario

The user wants a mobile popup that respects safe area and does not drift in portrait or landscape.

## Recommended Prompt

```text
Use $unity-mcp-ui-layout to build this as a mobile UGUI popup.
Keep Dimmer and PopupRoot as siblings under ModalLayer, and apply safe area to PopupRoot.
Build title, content, and footer sections inside PopupRoot using local layout rules instead of hard-coded offsets.
Verify portrait and landscape before finalizing.
```

## Expected Working Style

1. Create or inspect ModalLayer
2. Keep Dimmer and PopupRoot as siblings
3. Apply safe area to PopupRoot
4. Verify title, close button, content, and footer placement in portrait and landscape

## Useful References

- `unity-mcp-ui-layout/references/mcp-call-recipes.md`
- `unity-mcp-ui-layout/references/ugui-popup.md`
- `unity-mcp-ui-layout/references/ugui-mobile-safe-area.md`
- `unity-mcp-ui-layout/references/common-failures.md`
