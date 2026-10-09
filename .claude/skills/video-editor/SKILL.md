---
name: video-editor
description: >
  Personal style layer for short-form vertical reels (TikTok / Instagram Reels / YouTube Shorts) built
  with HyperFrames. Use together with /hyperframes whenever the user asks to edit raw footage into a
  reel, trim pauses or filler words, add captions, or add motion-graphic diagrams to a talking video.
  It does not replace the HyperFrames workflows: it supplies the defaults (9:16 canvas, typography,
  caption look, motion vocabulary, editing pace) that those workflows should apply.
---

# Video editor — reel style layer on top of HyperFrames

This skill holds **my house style**. The mechanics (composition structure, timing attributes,
rendering, captions pipeline, media) belong to the official HyperFrames skills. Never invent a
parallel file layout or render command; follow the HyperFrames contract.

## 1. Always start with HyperFrames

1. Load `/hyperframes` first. It reads project state, runs the intent interview, writes `BRIEF.md`,
   and routes to the owning workflow.
2. Typical routes for my requests:

   | My request | Workflow |
   | --- | --- |
   | Raw talking video → captioned reel, footage unchanged | `/embedded-captions` |
   | Talking video + title cards, diagrams, data callouts | `/talking-head-recut` |
   | Trim pauses / filler words, jump cuts, reorder, punch-in zooms | `/general-video` + `/hyperframes-core` + `/hyperframes-keyframes` |
   | Short logo sting, title hit, unnarrated motion < 10s | `/motion-graphics` |
   | Topic or notes → video with no footage | `/faceless-explainer` |

3. Use `/media-use` for transcription (word-level timestamps), TTS, music, SFX, and images.
4. Use `/hyperframes-cli` for `init`, `lint`, `check`, `preview`, and `render`.
   Render through the CLI only, never by hand-calling FFmpeg.

## 2. Defaults to apply (record them into BRIEF.md / the design spec)

When the intent interview asks, recommend these values and say they come from this skill.
The user can still override them.

- **Canvas:** 1080×1920 (9:16), 30 fps, MP4 delivery named `final.mp4`.
- **Pace:** fast. Cut silences longer than ~0.4s, filler words ("umm", "eh", "يعني") and false starts.
  Jump cuts are fine; add a subtle punch-in (≈1.08–1.15 scale) every 2–4 cuts to hide them.
- **Typography:** high-legibility sans-serif. Inter or Montserrat for Latin, Heebo for Hebrew,
  Cairo or IBM Plex Sans Arabic for Arabic. Titles at 800–900 weight.
  Arabic and Hebrew text is `direction: rtl`.
- **Captions:** 2–4 words per line, word-by-word highlight on the spoken word,
  high contrast (white text, dark stroke or shadow, optional pill background). Keep them inside the
  9:16 safe zone: above the bottom ~20% (platform UI) and clear of the right-side action buttons.
- **Explainer graphics:** when I explain a technical concept, add a pop-in card or a simple
  diagram (boxes and arrows showing the data flow) synced to the sentence that names it.
  Check `/hyperframes-registry` for an existing block before hand-building one.
- **Motion vocabulary** (GSAP eases, seek-safe per `/hyperframes-keyframes`):
  - Pop-ins: `back.out(1.7)`, 0.35–0.5s.
  - Springy settle: `elastic.out(1, 0.6)`, used sparingly for emphasis.
  - Exits and moves: `power3.out` / `power2.inOut`, 0.25–0.4s.
  - No slow fades on a fast reel; prefer cuts, scale pops, and short slides.

## 3. Iterating

Edits are code edits on the existing project: change the timing, ease, or text in place
(`/hyperframes` "Specific edit" row). Do not rebuild from scratch. After each change run
`npx hyperframes check`, then preview, then render.
