# Play It Back (AI video studio skill)

A skill that walks an AI assistant through making a short AI video
(music video, ad, narrated story, cartoon, or anything custom) with the
Higgsfield MCP server. It interviews you first, picks a format, asks
for a credit budget, and stops for your approval after every stage.

## What you need
1. A Higgsfield account with credits. You connect it yourself, signed
   in with your own account; the skill never asks for a key or token.
   Steps per app: `references/setup-higgsfield.md`.
2. One of these apps:
   - **Claude Code or Codex** (best): full pipeline including the final
     edit, with subagents doing the stages. Needs ffmpeg installed for
     the edit.
   - **claude.ai or ChatGPT**: everything up to the clips, played by one
     assistant step by step. The final edit comes as a shot-by-shot edit
     list you assemble in CapCut or any editor, unless the app can run
     ffmpeg.

## Install
- **Claude Code:** copy this `play-it-back` folder into
  `~/.claude/skills/` (or a project's `.claude/skills/`).
- **Codex:** copy it into `~/.codex/skills/`.
- **claude.ai:** zip the folder and upload it under Settings,
  Capabilities, Skills.
- **ChatGPT:** if your plan supports skills, upload the zipped folder.
  If not, make a Project, paste `SKILL.md` into its instructions, and
  add the `references/` and `templates/` files to the project's files.

Menu names change; use the closest current label.

## Use
Say something like "make a music video for this song" and attach the
song, or "help me make a 30 second ad for my coffee truck". Expect to
answer about ten questions first, including your budget.

## Costs
Video is most of the spend. Mostly-stills videos run tens of credits
for a minute or more; all-video clips can run several hundred credits
for 30 seconds. You set the cap; the assistant stops at 80% of it.
