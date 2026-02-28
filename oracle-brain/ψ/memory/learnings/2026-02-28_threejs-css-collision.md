# Learning: Three.js Renderer vs CSS !important

**Date**: 2026-02-28
**Topic**: WebGL Rendering / CSS Conflicts

## Problem
A 3D scene that worked perfectly became a black screen after adding a full-screen CSS overlay and setting the canvas to `width: 100% !important; height: 100% !important;`.

## Cause
Three.js manages canvas dimensions by setting inline `style` attributes on the element via `renderer.setSize()`. When CSS `!important` is used in a stylesheet, it overrides these inline styles. The canvas physically resizes (via CSS), but the WebGL viewport and coordinate system do not update correctly because the internal renderer logic is being bypassed.

## Solution
1. Remove `!important` from canvas CSS.
2. Ensure the canvas container has a defined size (e.g., `flex: 1` or `height: 100%`).
3. Use `requestAnimationFrame` to ensure `renderer.setSize()` is called with the *actual* clientWidth/clientHeight after the browser finish layout.

## Code Pattern (Safe)
```javascript
function resize() {
    const s = container.getBoundingClientRect();
    camera.aspect = s.width / s.height;
    camera.updateProjectionMatrix();
    renderer.setSize(s.width, s.height);
}
```

## Oracle Pattern Sync
Pattern: `threejs-css-collision`
Concept: `web-graphics`, `css-gotchas`, `3d-rendering`
Source: `rrr: PD04-v2`
