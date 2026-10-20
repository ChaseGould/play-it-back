# Role: editor (stage 6)

Never regenerates shots. If a shot is unusable, report it.

Needs code execution with ffmpeg (and Python helps). Without it, use the
no-code handoff at the end.

## Build
1. Timeline in shot order at the target size (1080x1920 for 9:16,
   1920x1080 for 16:9). Shot lengths come from the real audio: voice
   durations, or the song's bar grid. Keep a little air after
   punchlines.
2. Stills: the keyframe with a slow camera move (about 10% or less).
3. Loops: crossfade 3 to 6 frames at each wrap. If a low-res loop looks
   soft, composite only its moving region over the full-res keyframe.
4. Animated clips: grade them back to their keyframe (clips drift
   darker); dissolve 3 to 4 frames from a real photo into a morph; hold
   the end frame with a slow push rather than paying for a longer clip.
5. Real-photo shots, title card, captions (burn in and also write
   `captions.srt`; captions use the real spelling of every word), and
   any end card, per `bible/style.md` and the safe zone.
6. Audio: voice first and always clear. Normalize each line, then the
   mix to about -14 LUFS integrated, true peak about -1.5 dBTP. A quiet
   room-tone bed under everything avoids dead air. Music under voice by
   about 18 to 22 dB. SFX on their exact frames, never louder than the
   voice peak.
7. Write `06-edit/edit-notes.md`: timeline with start times, sources
   and licenses for all music and SFX, loudness readings, and how to
   rebuild. Keep the build script in `06-edit/build/`.

Render a review cut first, send it to the user, then the final after
their notes. Keep each version (v1, v2...) instead of overwriting.

## Music and SFX sources
- The user's own song (music video): the master clock; never alter it.
- Free libraries the user downloads themselves: YouTube Audio Library,
  Pixabay Music and sound effects, Freesound (CC0 filter). Note the
  license in edit-notes.
- Audio the video model generated on clips you already paid for (strip
  it from the clip, cut the useful bits): engine sounds, impacts,
  ambience. Free.
- Simple sounds synthesized locally in code: room tone, clicks, a
  basic impact.
- A music or SFX generation service the user has connected and whose
  terms allow the use. Its credits are separate from the Higgsfield
  cap: quote first, get the user's OK, and log them in `status.md`.
- No music is a valid choice; deadpan narration often plays better dry.

## No-code handoff
If you cannot run ffmpeg, give the user `06-edit/edit-list.md`: each
shot in order with file name, start time, duration, camera move, caption
text and timing, audio file and offset, and transitions, plus the
loudness target. They can assemble it in CapCut, iMovie, Premiere, or
DaVinci Resolve.
