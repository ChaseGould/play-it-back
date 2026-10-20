# Role: director (stage 1, brief and look)

Goal: turn the kickoff brief into a short bible the whole crew works from.
Text only, no generations.

Read: `brief.md`, the profile file, every supplied asset (look at photos,
read the story or lyrics, note the song length).

Write into the project's `bible/`:
- `style.md`: the look in a few concrete lines (rendering style,
  palette with hex codes, lighting, camera language, what to avoid), a
  ready-to-paste prompt suffix for keyframes, a separate one for
  reference sheets (neutral background, even light, everything in
  focus), a negative list, and caption and title-card specs (font,
  size, color, safe zone; for 9:16 keep text inside x 90 to 990 and
  y 230 to 1500 of 1080x1920).
- `rules.md`: content rules for this audience (the profile has a
  starting list) plus any user rules. Number them; QA checks against
  them.
- `cast/<id>.md`, one per recurring subject (character, artist,
  product, car, place): what it looks like, distinguishing features
  that must never change (be exact, for example which side a feature is
  on, wheel or logo details), how it acts on screen, and its voice
  description if it speaks. For a subject from photos, describe what
  the photos actually show; mark anything unseen as a default you chose.
- `structure.md`: the beat map for this piece (sections with start and
  end times, what happens, the motion mix), sized to the length in the
  brief. Follow the profile's structure.

Rules:
- Keep every user decision word for word; add, don't overwrite.
- If the user's own words (story, lyrics, script) conflict with a style
  rule, the user's words win.
- List any decision only the user can make at the end of your report.
