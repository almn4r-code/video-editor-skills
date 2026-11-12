<div align="center">

# 🎬 Video Editor Skills for Claude Code

**A first-pass editor for your YouTube vlogs and classes, inside DaVinci Resolve Studio.**

You film and make the taste calls. Claude imports, cuts retakes and dead air, keeps your B-roll,<br>
scores the video, writes clean captions, adds brand motion graphics and gets the export right.

`12 skills` · `0 lines of code` · `learned on real edits`

</div>

---

## Why this exists

A transcript cut is fast and precise, and that is exactly the problem: done naively, every cut becomes a jump cut, silent B-roll disappears, the music is too timid, the captions read like a court record and the export is 25 GB.

These skills are the **method, the numbers, the rules and the traps** that came out of fixing all of that on real videos. There is no code in this package. Claude reads the skills and builds the small scripts with you, for your camera, your project and your brand.

## How an edit flows

```
 raw video/ ──► ingest ──► rough cut ──► pacing ──► Resolve build ──► you watch
                  │            │            │              │               │
             transcribe    what stays   how much air   new timeline   plain-words
             + silences    (by word)    (by script)    only adds      feedback
                                                                           │
          ┌──────────────── optional finishing passes ◄────────────────────┘
          ▼
   music & sound · captions · motion overlays · voice fix · YouTube export
```

Every lesson you give in plain words ("too choppy", "music louder on B-roll") becomes a dated line in your `CLAUDE.md`, so the next video starts smarter.

## The skills

### 🧭 Start
| Skill | Teaches Claude |
|---|---|
| [`video-editor-setup`](skills/video-editor-setup/SKILL.md) | the workspace, safe key handling, your Resolve template, which scripts to build |
| [`edit-video`](skills/edit-video/SKILL.md) | the one-command flow: ingest → cut → build in Resolve → report |

### ✂️ Cut
| Skill | Teaches Claude |
|---|---|
| [`rough-cut`](skills/rough-cut/SKILL.md) | what to keep: retakes, false starts, notes to the editor, punchlines |
| [`vlog-pacing`](skills/vlog-pacing/SKILL.md) | silence detection, pads, pause rules, room at scene edges, jump-cut zoom |
| [`broll`](skills/broll/SKILL.md) | finding and watching B-roll, cutting it by action and story |
| [`resolve-scripting`](skills/resolve-scripting/SKILL.md) | what works in the Resolve API, what silently fails, what crashes it |

### 🎧 Sound
| Skill | Teaches Claude |
|---|---|
| [`voice-and-audio`](skills/voice-and-audio/SKILL.md) | loudness normalize, diagnosing a muffled voice, an EQ recipe |
| [`music-and-sound`](skills/music-and-sound/SKILL.md) | Epidemic Sound cues per section, a ducking envelope, tasteful SFX |

### ✨ Finish
| Skill | Teaches Claude |
|---|---|
| [`captions`](skills/captions/SKILL.md) | clean, correct, one-line captions, every cue read before import |
| [`motion-overlays`](skills/motion-overlays/SKILL.md) | a Remotion brand kit timed to your words, face- and caption-safe |
| [`figma-roundtrip`](skills/figma-roundtrip/SKILL.md) | design the kit in Figma, keep code and boards in sync |
| [`youtube-export`](skills/youtube-export/SKILL.md) | Deliver settings for great quality without 25 GB files |

Also included: [`templates/config.example.json`](templates/config.example.json) with starting values and ready presets for **vlogs** and **classes**, and [`LEARNINGS.md`](LEARNINGS.md), the story of what went wrong and how it was fixed.

## Install

**As a plugin** (keeps the skills together), from inside Claude Code:

```text
/plugin install <path-or-git-url-to-this-folder>
```

**Or copy the skills** into a project (`.claude/skills/`) or your user folder:

```bash
cp -R skills/* ~/.claude/skills/
```

## Your first edit, in five steps

1. **Open Claude Code** in an empty folder that will be your editing workspace.
2. **Say "set up my video editor".** Claude follows `video-editor-setup`, asks about your camera, Resolve project and brand, and builds the scripts with you.
3. **Add your key yourself.** Create `system/keys.env` with one line, `SPEECH_TO_TEXT_API_KEY=your-key`. Claude never reads or prints it, and it must never be committed.
4. **Drop a video** in `raw video/`, open your Resolve project and say **"edit the new video"**.
5. **Watch, then talk.** "Too choppy", "put back the joke at 03:10", "add captions", "graphics". Claude rebuilds as `v2`, `v3`… and never overwrites your work.

## What you need

| | Required | Optional |
|---|---|---|
| **Editor** | DaVinci Resolve **Studio** (external scripting) | |
| **Tools** | ffmpeg / ffprobe, Python 3.9+ | Node 18+ and Remotion (motion graphics) |
| **Services** | a speech-to-text API with word timestamps | Epidemic Sound MCP (music + SFX), Figma MCP (brand boards) |

## Safety, built in

- 🎞️ **Raw footage is never modified**, moved or copied.
- ➕ **In Resolve, Claude only adds**: new timelines, new clips on free tracks. Your template, timelines and projects stay untouched.
- 🔑 **Keys are never printed** or read into the conversation.
- 🙋 **Nothing is published without you**, and every taste call is yours.

## Credits and license

Created by [appariciojunior](https://github.com/appariciojunior/video-editor-skills).

[CC BY-NC 4.0](LICENSE): free to use, share and adapt **with credit**. **Not for sale**: you may not sell these skills or a modified version, or use them in anything sold (paid courses, templates, products or services). For commercial use, ask the author.
