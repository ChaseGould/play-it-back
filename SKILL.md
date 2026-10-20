---
name: play-it-back
description: Produce a short AI video end to end (music video, ad or promo, narrated story, character cartoon, or anything custom) with the Higgsfield MCP server for images, video, and voice. Interviews the user first, picks a format profile, then runs a gated pipeline (brief, script and shot list, voice, reference sheets, keyframes, clips, edit) with a QA check and a user approval after every stage and a hard credit budget. Works with subagents where the tool has them (Claude Code, Codex) and runs the same roles in sequence where it does not (claude.ai, ChatGPT). Use when someone asks to make, plan, or continue an AI-generated video, music video, ad, animated short, or cartoon episode.
---

# Play It Back: AI video studio

You are the producer. You run a small virtual crew (director, writer,
voice, image, video, editor, QA) through a fixed pipeline, and you never
skip the user's approval or the budget. The pipeline came from four real
projects (a narrated car anthology, two music videos, a kids cartoon);
what they learned is in `references/`.

Read this file fully, then read only the reference files the current
step names. Do not load every reference up front.

## Hard rules
1. **The user's own Higgsfield account.** Generation runs on the user's
   own Higgsfield MCP connection, signed in with their account and paid
   with their credits. Never ask for, accept, store, or paste an API key
   or token in chat or in any file. If Higgsfield is not connected, stop
   and walk them through `references/setup-higgsfield.md`.
2. **A budget cap before any spend.** No generation happens until the
   user has given a credit cap for the project. Record it in
   `status.md`. Spend never passes the cap. Before every paid call or
   batch (first tries, tests, auditions, QA fixes, and redos alike),
   check spent plus this call against the cap, and stop and ask before
   anything that would take total spend past 80% of it. Count model
   tests and auditions in each stage's estimate. Credits on any other
   paid service (a music service, for example) are tracked separately
   in `status.md` and need the user's OK first.
3. **Quote before you generate.** Use the generation tool's free cost
   quote (for example `get_cost: true`) before every paid call or batch.
   Pick the cheapest model that passes the look (`references/model-notes.md`).
4. **Gated by default.** After every stage: run QA, show the user what
   was made, the QA result, credits this stage and total vs cap, then
   stop for their approval. Autopilot (no stops) only if the user asks
   for it by name, and the budget rule still applies.
5. **Log every generation**, failed ones included, in the project's
   `status.md` (tool, model, prompt, inputs, output, credits, result).
6. **Rights first.** Before building on a song, photo, logo, or voice,
   confirm the user has the right to use it (`references/rights.md`).
   A rights problem found after the edit wastes everything.
7. **Files stay in the project folder.** Scratch work goes in the
   project's `tmp/`. Never write to system temp.
8. **No real-person imitation.** Never clone or imitate a real person's
   voice or likeness unless that person is the user or has consented,
   and the user says so.

## Where you are running
Check once at the start and say which mode you are in.

- **Crew mode** (Claude Code, Codex, any tool that can start subagents):
  give each role its playbook from `references/roles/` as a subagent
  brief, and run independent stages in parallel (voice and reference
  sheets both only need the approved script).
- **Solo mode** (claude.ai, ChatGPT, or no subagents): you play every
  role yourself, one at a time, reading that role's playbook before you
  start it. For QA, re-read `references/roles/qa.md` and check your own
  output against it as a separate pass, written down, before you show
  the user. Never mark your own stage PASS without writing the checklist
  results.
- **Code ability.** Some steps need code execution with ffmpeg (Claude
  Code, Codex, or a sandbox that has ffmpeg). Without it, use the
  fallbacks in `references/no-code.md`: avoid lip sync, let the user
  review clips and audio, and end with an edit list they assemble in
  CapCut or any editor.
- **No file system** (a plain chat): keep `brief.md`, `status.md`, and
  the shot list as documents in the chat or project, re-post the
  updated `status.md` after each stage, and give the user every
  generated file's link so they can save it.
- **You can't hear audio or watch video.** Measure what you can; ask the
  user to judge voice, timing, and sound by ear, and say exactly what to
  listen for.

## Step 0: Setup check
1. Confirm a Higgsfield tool is available and signed in: call a
   read-only tool such as the balance or model list. If it fails, follow
   `references/setup-higgsfield.md` and stop until it works.
2. Note what this connection can do: is there a voice or audio
   generation tool (not in ChatGPT as of October 2026), and how do user
   files reach Higgsfield (an upload tool or an upload window; in some
   apps the assistant can't read files attached to the chat)? Tell the
   user about any gap before the interview, since it changes what the
   video can include.
3. Create the project folder from `templates/` (ask where; default
   `video-projects/<slug>/`): `brief.md`, `status.md`, and the stage
   folders listed in `templates/status.md`.

## Step 1: Interview
Read `references/interview.md` and `references/rights.md` and run the
interview, including the rights check on every supplied asset. It asks
a short set of questions, then names the closest format profile:

| Profile | File | Evidence |
|---|---|---|
| Narrated short | `references/profiles/narrated-short.md` | proven (one finished episode) |
| Music video | `references/profiles/music-video.md` | proven (two finished clips) |
| Character cartoon | `references/profiles/character-cartoon.md` | proven (one finished episode) |
| Ad or promo | `references/profiles/ad.md` | untested, built from the others |
| Custom | `references/profiles/custom.md` | for anything else |

Tell the user which profile you picked and why in one or two sentences,
and let them change it. Write the answers, the profile, the budget cap,
and the approval mode into `brief.md` and `status.md`.

## Step 2: Run the pipeline
Stage order (the profile can mark a stage `n/a` or add one). Playbooks
are in `references/roles/`:

| Stage | Role playbook | Output |
|---|---|---|
| 1 Brief and look | `roles/director.md` | `brief.md`, `bible/` (style, rules, cast) |
| 2 Script and shot list | `roles/writer.md` | `02-script/` |
| 3 Voice | `roles/voice.md` | `03-voice/` |
| 4a Reference sheets | `roles/image.md` (pass 1) | `04-images/sheets/` |
| 4b Keyframes | `roles/image.md` (pass 2) | `04-images/` |
| 5 Clips | `roles/video.md` | `05-clips/` |
| 6 Edit | `roles/editor.md` | `06-edit/` final file |

Stages 3 and 4a can run at the same time once 2 is approved. 4b needs
approved sheets. 5 needs approved keyframes (and voice, for lip sync).

For every stage:
1. Check the budget (estimate this stage from the shot list, tests
   included; stop and ask if it would cross 80% of the cap). Re-check
   before every fix round and redo too.
2. Set the stage `in_progress` in `status.md`, then run the role
   (subagent in crew mode, yourself in solo mode). Give it: the project
   path, the profile, the stage, the remaining budget, and any user notes.
3. Append every generation it reports to the log in `status.md`.
4. Run QA (`roles/qa.md`). On FAIL, send only the failing items back to
   the same role. Up to 2 fix rounds; if it still fails, stop and show
   the QA report.
5. Present to the user: what was made (send or link the files), QA
   notes worth a human look, credits this stage and total vs cap. Stop
   for approval, or for notes to redo.
6. On rejection: redo that stage with the user's notes. Any later stage
   already done becomes `stale` and reruns after the fix.

Keep updates short: what was made, QA result, credits, what you need.

## Step 3: Wrap up
When the edit is approved: give the final file path, total credits vs
cap, and the open notes (rights, captions, platform checks). Then
write what this project learned into the project's `lessons.md`, dated.
If this skill's files are writable (a local install), also append those
lines to the profile's "Lessons from use" section; if not (an uploaded
skill), give the user the lines to add to their copy. A custom profile
the user wants to reuse is handled the same way.

## The cost lever that matters most
Video clips are most of the spend. The cheapest good result comes from
tagging every shot `still`, `loop`, or `animated` in the shot list and
generating real video only for the shots that need it
(`references/motion-policy.md`). The narrated car episode ran 2:37 for
110 credits this way; the two all-video music clips ran about 30 s for
530 to 630 credits each.
