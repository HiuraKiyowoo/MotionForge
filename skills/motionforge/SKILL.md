---
name: motionforge
description: "Cinematic web motion graphics for promos, openers, explainers, kinetic typography, product demos, UI showcases, and visual storytelling. Use when an animation should feel like a video rather than a slide deck."
license: MIT
metadata:
  version: "2.0.0"
  homepage: https://github.com/HiuraKiyowoo/MotionForge
---

# MotionForge

Build deterministic, cinematic motion graphics in a browser with HTML, CSS, JavaScript, GSAP, and Three.js when useful. Deliver a directly watchable `index.html`; do not require `npm install` just to watch it.

## Trigger and output

Use this skill for promo videos, openers, bumpers, logo stings, intros/outros, kinetic typography, product/UI demos, explainers, and visual storytelling. Default output is a browser animation that autoplays and loops. Keep review controls hidden; expose scrub/debug UI only with `?debug=1`, and hold autoplay for export with `?clean=1`.

Use a modern browser and CDN assets for viewing. Node/Puppeteer and FFmpeg are optional for snapshots, frame export, and MP4. If those tools are unavailable, still deliver a watchable HTML file and explain the recording/export limitation.

## Non-negotiable rules

1. **Make a video, not a slide deck.** Do not build a sequence of static sections that only fade in/out. Preserve a subject or visual world, move the camera or world, and make objects carry the action. The valid cartoon-stage exception is documented in `references/kartun-panggung.md`.
2. **Use a style brief before code.** Choose the concept, structure fingerprint, palette/source, display font, surface, background motion, render family, camera language, transition family, and one special moment. Read `references/gallery.md` when the user wants examples or has no style.
3. **Derive style from the user's theme and assets.** A starter is architecture, not a visual skin. Do not reuse a previous project's palette, font, texture, layout, or signature motion by default.
4. **Keep typography alive and restrained.** For openers use one short sentence and at most one main object per scene; avoid default kicker + subtitle + body + badges. In explainers, use at most two text levels per moment and turn facts into visual actions.
5. **Make motion deterministic.** Drive all animation from the GSAP timeline clock (`tl.time()` or timeline progress). Do not use `Date.now()`, frame-accumulated velocity, or uncontrolled `Math.random()`. A frame rendered twice must be identical.
6. **Keep the world readable.** Make the camera serve the story, vary shot scale and viewpoint with motivation, and keep text legible on a 1080-wide phone stage (body ≥44px, labels ≥34px, credits ≥30px unless the brief requires otherwise).
7. **Respect asset rights.** Use user assets, generated assets, or licensed stock. Do not copy a reference gallery's text, palette, exact composition, scene order, characters, crop, or signature moment.

## Workflow

### 1. Clarify the brief

Collect or infer: product/topic, audience, purpose, language, ratio, duration, audio/voice-over, brand assets, and desired energy. If key explainer choices are missing, ask one compact question before coding. Default to 16:9; use 9:16 only when requested.

### 2. Choose direction and concept

If style is open-ended, read `references/gallery.md` and offer three candidates with one recommendation. For an opener/promo, read `references/opener-konsep.md` and select a concept born from the product—not a generic hook → cards → CTA template. For an explainer, select one of the documented modes: continuous action, cartoon collage, visual journalism, white catalog, vintage sketch, or cartoon stage.

Write a short style brief and rundown before touching a starter. The rundown must state the subject/world, shot changes, major objects, transitions, and ending.

### 3. Select the starter and assets

Use the matching starter from `assets/`:

| Request | Starter |
|---|---|
| opener, promo, bumper, intro, kinetic type | `starter-opener.html` |
| continuous action explainer | `starter-explainer.html` |
| cartoon collage | `starter-explainer-kartun.html` |
| visual journalism | `starter-explainer-jurnalisme.html` |
| white product catalog | `starter-explainer-katalog.html` |
| vintage sketch/history | `starter-explainer-sketsa.html` |
| cartoon stage with characters | `starter-explainer-panggung.html` |

Start from the style-specific starter for explainers; do not use the opener starter for an explainer or build the architecture from zero without a reason. Read the matching reference before editing. Ask before using photos of people/places/products if the source is not supplied or licensed.

### 4. Build the timeline

Keep CSS/JS inline when possible so `index.html` opens with `file://`. Use GSAP timelines and named scene labels. Animate a persistent world, subject, camera, UI state, or object transformation. Use motivated cuts, whip/push-through transitions, parallax, and reveals instead of repeating fade + scale on every scene. For footage, sync playback to the same timeline clock so scrubbing and frame export remain exact.

### 5. Verify mechanically

Before delivery, inspect code and run the applicable checks:

```bash
grep -c 'class="scene"\|<section' index.html
node scripts/snap.mjs index.html                 # optional Puppeteer contact sheet
node scripts/export-frames.mjs index.html       # optional MP4 path
```

A high section count is not automatically wrong, but three or more static sections switched by opacity/`autoAlpha` is a slide-deck failure. Check that the world persists, actions are visible, transitions vary with purpose, typography is not the only moving element, and no scene is a static card with one sentence.

Open the result in a browser at key timeline moments. Verify autoplay/loop, `?debug=1`, `?clean=1`, phone readability, no flash of hidden elements, no console errors, and deterministic repeated frames. Read `references/anti-ppt.md` before a final handoff.

### 6. Export or hand off

Deliver the playable HTML first. Export MP4 only when requested and when Node/Puppeteer/FFmpeg are available. Without FFmpeg, offer a browser/OBS recording and state that it may drop frames. If voice-over exists, read `references/explainer.md` and use `scripts/vo-pauses.html` or FFmpeg `silencedetect` to align beats.

## Branch references

Read only the references needed for the current request:

- **Style/gallery:** `references/gallery.md`, `references/opener-konsep.md`, `references/techniques.md`.
- **Explainer modes:** `references/explainer.md`, `references/kartun-panggung.md`.
- **Quality/anti-slide:** `references/anti-ppt.md`, `references/architecture.md`.
- **After Effects:** `references/ae-bridge-higgsfield.md` when the user explicitly requests the Higgsfield bridge.
- **Runtime tools:** `scripts/serve.py`, `scripts/snap.mjs`, `scripts/export-frames.mjs`, `scripts/vo-pauses.html`.
- **Edge cases:** `references/legacy-full-rules.md` only when the current dispatcher and dedicated references do not cover the case.

## Final checklist

```text
[ ] brief, ratio, duration, audio/VO, and audience are settled
[ ] concept and style brief were written before code
[ ] the selected gallery direction was used as principle, not copied as skin
[ ] the matching starter/reference was used
[ ] one persistent subject/world carries the video
[ ] no static slide sequence, fade-only scene changes, or generic card parade
[ ] motion is timeline-deterministic and frame-repeatable
[ ] text is short, readable, and not the only moving element
[ ] camera/transition choices are motivated and varied
[ ] index.html opens directly without npm install
[ ] browser review passed at key timestamps
[ ] debug/clean modes and autoplay/loop behave as intended
[ ] export limitations are disclosed if MP4 was not rendered
```
