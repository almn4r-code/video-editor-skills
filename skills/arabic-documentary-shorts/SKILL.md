---
name: arabic-documentary-shorts
description: Vertical (9:16) Arabic documentary and motion-graphics explainer videos in the calm, editorial Saudi style (the genre made popular by studios like Thmanyah) - a hook in 3 seconds, a narrated story with archive photos, documents, maps and big numbers, RTL kinetic typography, quiet music, built as a timeline in DaVinci Resolve. Works from a script only (AI or recorded narration) or from the creator's recording. Use for "وثائقي قصير", "فديو شرح", "موشن جرافيك", "زي ثمانية", "Thmanyah-style", "Arabic explainer", "documentary short".
---

# Arabic documentary shorts (9:16)

A 45–90 s vertical film that tells **one story with one insight**. The look is editorial: paper, ink, one accent colour, archive material, words that appear as they are said. Calm, never loud.

**The genre, not the brand.** We borrow pacing, structure and restraint. Never use another studio's name, logo, intro sting, sound logo, fonts or footage. The creator's own brand lives in `brand.json`.

Prerequisites: `video-editor-setup` is done; the `motion-overlays` Remotion kit exists (this skill adds RTL components to it).

## Two modes, one pipeline

| The creator gives | Start at |
|---|---|
| an idea or a script (text only) | **1. Research & script** |
| a narration recording or a talking video | transcribe (verbatim, word timestamps), then `rough-cut` for retakes, then **3. Beats** |

Ask once per video which kind it is: **documentary** (archive + narration, V1 is photos/footage) or **motion explainer** (no footage, V1 is the paper background and every visual is a graphic). Many are a mix.

## 1. Research & script
- **Facts:** every number, date, name and quote checked in at least two sources; keep `sources.md` (claim → link). Never invent a quote or round a number differently from the source. If sources disagree, say so to the creator.
- **Structure** (60 s ≈ 130–150 Arabic words):
  1. **Hook 0–3 s**: a surprising fact, a question or a contradiction. No greeting, no "في هذا الفيديو".
  2. **Context 3–12 s**: who, where, when, in one or two sentences.
  3. **Story 12–45 s**: chronological, one turning point ("لكن…", "وفي عام…").
  4. **Numbers**: one or two big numbers at most, each with a comparison people feel.
  5. **Insight 45–55 s**: what it means; the line people repeat.
  6. **Close**: a soft question or a short final line. No "لا تنسى الاشتراك" unless asked.
- **Language:** clear simplified فصحى or the creator's dialect, chosen once and recorded in CLAUDE.md. Short sentences (≤ 14 words). One idea per sentence.
- Show the script with the timing of each part and **wait for OK**.

## 2. Narration
- **Recorded by the creator:** quiet room, 10 cm from the mic, one take per paragraph; then `voice-and-audio`.
- **AI voice (TTS):** the key lives in `system/keys.env` (never read or printed). Before sending text:
  - numbers and dates written **as words** the way they should be read ("ألفين وعشرين", not "2020");
  - **تشكيل** on ambiguous words and names (عِلم / عَلَم), foreign names spelled the way they are said;
  - one paragraph per request, so a bad read is re-done alone.
  Listen to every paragraph; list the words read wrong and fix only those.
- Get **word timestamps** for the final narration (transcribe it), they drive every beat.
- Pace: calm, ~2.3 words/s. Breaths ≤ 0.35 s; leave 0.6–0.9 s of air before the turning point and before the insight.

## 3. Beats
A visual change every **2–4 s**; never a still frame longer than 5 s. Propose the beat sheet (time · component · copy · asset) and **wait for OK**. Write `beats.json` as in `motion-overlays` (`at_word`, `end_word`, `data`).

| Moment | Visual |
|---|---|
| hook | full-frame KineticHeadline or one archive photo with a slow push |
| place / time | MapPin, MapRoute, YearStamp ("١٩٧٣") |
| a person | ArchivePhoto + NameTag (name, role, year) |
| a document, a headline | DocumentHighlight: photo of the page, a marker sweeps the line being read |
| a number | BigNumber counting up + one comparison line |
| change over time | Timeline (years right → left), BeforeAfter |
| two sides | Compare (right = first, RTL) |
| a strong line | QuoteCard with SourceTag |
| the insight | KineticHeadline, accent on one word |

**Assets:** archive photos, footage, maps and documents must be ones the creator may use (own, licensed, public domain or with permission). Keep `assets.md` (file → source → licence) and show a small SourceTag ("المصدر: …") on screen when the licence or the claim needs it. Never pass off a generated image as a real archive photo; label reconstructions ("صورة توضيحية").

## 4. The look (tokens in `brand.json`)
- **Frame:** 1080×1920, the creator's fps (ask; default 30). **Safe area** for app UI: top 220 px, bottom 420 px, left 60 px, right 160 px. Nothing important outside it.
- **Palette:** paper (off-white, e.g. `#F3EEE4`), ink (near-black, `#141414`), a mid grey for secondary text, and **one** accent the creator picks. Dark variant = ink background, paper text. No gradients, no glow.
- **Type:** an Arabic sans that the creator has licensed or an open one (IBM Plex Sans Arabic, Readex Pro, Noto Kufi Arabic, Alexandria). Bold for headlines, regular for body. Headlines 96–140 px, body 54–64 px, labels 34–40 px. Line height 1.35–1.5 (Arabic needs more than Latin). Right-aligned, `dir="rtl"`.
- **Numerals:** pick Arabic-Indic (١٢٣) or Western (123) once, per creator; never mix in one video. Dates: say which calendar (هـ / م).
- **Texture:** light paper grain on backgrounds, film grain 3–5 % on photos; archive photos may go black-and-white with the accent as the only colour.
- **Motion:** one ease-in-out move per element (glide/fade 12–18 frames), hold, glide out. Words of a headline appear **word by word with the narration**, right to left. Photos: slow push 100 → 106–110 % over the shot, never a fast zoom. Cuts on the word, not on the beat of the music. No bounce, no shake, no glitch.

## 5. Captions (Arabic)
Follow `captions` with these Arabic rules:
- 1–2 lines, **max 32 characters per line**, centred, in the lower third but above the 420 px bottom safe band; the key word of the line in the accent colour.
- Arabic punctuation (، ؛ ؟), no tatweel, no diacritics unless the word is ambiguous.
- When a full-frame headline shows the same words, hide the caption for that cue.
- **Render Arabic captions and every Arabic text in Remotion** (transparent ProRes 4444), not as Resolve subtitles or Text+, unless you have checked in this creator's Resolve version that letters join and run right to left. Check one frame over the picture either way.

## 6. Music & sound
- Music: minimal, ambient, piano/strings/soft pulse; one cue, maybe a lift at the turning point. Sits low **all the time**: about −28 to −24 LUFS under narration (deeper than the vlog duck in `music-and-sound`), up to −18 LUFS in gaps with no voice. Ends with the video, not cut mid-phrase.
- SFX, quiet and few: paper slide on DocumentHighlight, soft tick on BigNumber, a low hit on the hook. No cartoon whooshes.
- Mix: narration −14 LUFS integrated, true peak ≤ −1 dBTP (social platforms).

## 7. Build in Resolve
Follow `resolve-scripting`. New timeline "<video> - Doc v1" (v2, v3… never overwrite), **1080×1920**:
- **V1** photos/footage (motion explainer: the background render), **V2** motion graphics, **V3** captions render;
- **A1** narration, **A2** music, **A3** SFX;
- photos placed with the push already in the Remotion render, or as Resolve dynamic zoom — one method per video;
- markers: blue = source to credit, pink = needs the creator (missing asset, a fact to confirm).

## 8. Check before handing over (non-negotiable)
Export a still every 2 s with the safe area and caption band drawn on it and **look**: text inside the safe area, nothing on a face, Arabic letters joined and RTL, numerals consistent, no line longer than allowed, accent on the right word. Watch the first 3 s alone: would you stop scrolling?

## Report
Length, hook line, beat list (time · component · copy), sources and licences used, every TTS word you re-did, anything guessed (a date, a spelling) and every pink marker. Then stop; the creator watches it.

## Export
H.264 or H.265, 1080×1920, the timeline fps, ~16–20 Mbps, AAC 320 kbps 48 kHz. Name `<video>_9x16_v<n>.mp4`.
