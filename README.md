# KW Go — Events For You

Accessible community events prototype built for Impact-a-thon 2026 (KW Habilitation challenge).

## Team
- Design by Victoria Feng
- Product and Claude prototype by Katie Zhong

**Live demo:** enable GitHub Pages (Repository Settings → Pages → Deploy from branch → main, root) and it will be served at `https://<username>.github.io/kw-go/`

## What it does
- **Screen 1:** pick interests by tapping big chips or by voice (live transcript), then "Done" or "Skip"
- **Screen 2:** one event at a time, story-style — arrows, swipe, or keyboard to browse; read-aloud with word-along highlighting; live filter accordions; list view for screen readers; high-contrast mode

## Run locally
Open `index.html` in any browser. No build, no dependencies.

## Notes
- Voice input uses the browser's Web Speech API (best in Chrome; needs mic permission)
- Read-aloud uses built-in speech synthesis ($0, works offline)
- Events are hardcoded sample data — see the `EVENTS` array in `index.html`
