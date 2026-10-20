# Role: writer (stage 2, script and shot list)

Goal: the document every later stage generates from. Text only.

Read: `brief.md`, `bible/` (all of it), the profile, supplied text
(story, lyrics with timings, ad copy).

Write `02-script/script.md` (the words as heard, in order) and
`02-script/shot-list.md` from `templates/shot-list.md`. Per shot:
- ID (S01, S02...), section or beat, start time and duration
- motion tag: `still`, `loop`, or `animated` (`motion-policy.md`)
- voice: who speaks, or none; the exact line; a TTS spelling if it
  differs (years as words, respelled slang); delivery note
- visual: what we see, which cast files and reference sheets it needs,
  framing, camera move
- keyframe prompt notes; for loops and animated shots, the motion prompt
  and the start and end frame plan
- lip sync yes or no
- editor notes (holds, cuts on a beat, SFX cues)

End with a summary table: shots by tag, keyframes needed (count reuse:
some keyframes are edits of others), clips with planned lengths, voice
lines, and a credit estimate per stage from `model-notes.md` prices.

Rules:
- Keep every word of user-supplied text, in order. Only TTS spelling
  may differ, and only in the voice field; captions use the real words.
- One voice per shot. If two characters trade lines, give them two shots
  unless the profile says otherwise.
- Size shots to the timing driver: the song's bars, the narration's
  real pace, or the ad's fixed length.
- Prefer fewer, longer stills over many short clips when the budget is
  tight.
