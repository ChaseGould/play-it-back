# Profile: music video

Evidence: proven on two finished clips (October 2026): "Burning in the
Cold" (30 s, 16:9, one masked character, Seedance, 633 credits) and
"Play It Back" (28 s, 9:16, a virtual artist, Seedance plus free
FFmpeg-animated stills, 534 credits). Both skipped lip sync on purpose.

Use for: any video cut to a song the user supplies.

## Timing
The song is the master clock and an immutable file: never re-encode,
trim, or change it.
1. Measure BPM and the bar grid, anchored on a clear downbeat (the drop,
   the first kick). Note the song's sections (intro, verse, chorus,
   drop) with timestamps.
2. Get lyric timing (embedded subtitles, a lyrics file, or a transcript).
3. Cut every shot on bar lines; give key actions an in-point offset so
   they land exactly on the beat.

## Stages
- Voice: usually `n/a`.
- Add a "rights" check at kickoff (who made the song, on which
  service and plan; see `rights.md`). A free-plan AI song blocked one
  finished clip from shipping.
- Decide lip sync per shot at stage 2. Default: avoid it with masks,
  wide shots, backs, silhouettes, instrument close-ups, and cutaways.
  If singing on camera is essential, mark those shots in the shot list
  and, at stage 5, test one of them with an audio-driven model
  (`model-notes.md`) before rendering the rest. Count the test in the
  stage 5 estimate. Lip sync needs code to pad the audio
  (`no-code.md`).

## Defaults
- Motion: more animated shots than narrated formats, but stills with a
  push-in on the beat are fine for verses and lyric lines.
- Drafts at low resolution, then finalize only the takes the user picks.
- Lyric captions optional; if used, time them from the lyric file.

## Rules
- Attach the artist or character face reference to every shot, wide
  ones included, or faces drift.
- Never push in to a face from a wide frame; models invent a new face.
- Use deliberate cuts on bar lines; never fake one continuous move
  across two generations.
- Gate start frames hard; video models copy their defects.
- Ask for blank signs; models add fake neon text and symbols.
- What the user flags most in review: hands, generic backgrounds, frozen
  motion in stills, wrong reflections. Fix small things by editing the
  image, not regenerating.

## Lessons from use
- 2026-10: All-video clips on Seedance cost 530 to 630 credits for
  about 30 s. Mixing in stills with editor motion cuts that sharply.
