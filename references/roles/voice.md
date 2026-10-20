# Role: voice (stage 3)

Skip this stage when the profile has no generated voice (for example a
music video with only the song).

If the connection has no voice generation tool (Higgsfield in ChatGPT,
as of October 2026), offer the user: record the voiceover themselves
(a phone voice memo is fine) and send it, tell the story with on-screen
text instead, or switch to an app that has voice. Then cut shots to
their recording's real timing.

## Voice design (first project, or a new recurring voice)
1. List the generation server's voice tools and preset voices. Some
   servers cannot design a voice from a text description; then you
   audition stock presets.
2. Pick 3 to 5 candidates that fit the cast file's voice description,
   tuning speed and pitch if the tool allows.
3. Every candidate reads the same short audition script (a title line,
   one real line from this project, one punchline).
4. Save as `03-voice/auditions/<candidate>.mp3`, and write a notes file:
   voice ID, settings, measured pace, an honest one-line read. Send the
   files to the user. The user picks by ear; you cannot hear.
5. Never clone a real person unless the user says it is them or a
   consenting person, and they supply the recording.

## Lines
1. Get a free quote first. If the price scales with text length,
   generate one line per shot. If it is per call, batch and split at
   clean silences.
2. Use the TTS spelling from the shot list; send clean text with no
   notes or quote marks (see `model-notes.md` quirks).
3. Save as `03-voice/S01_<voice>.mp3` (shot ID first).
4. Check every file: the last word decays naturally (not cut), no
   dropped or added words, pace, and whether questions rise and
   statements fall. Flag any line that overruns its shot by more than
   1 s; do not speed it up. You can't hear: measure with code where you
   can (transcript, waveform end, pitch), and send the lines to the user
   with what to listen for.
5. Write `03-voice/voices.md`: shot, voice, line, file, duration,
   speech time, settings.
6. Fixes: regenerate only the bad sentence and splice it into existing
   silence rather than redoing the whole line.

No music, SFX, or room noise in voice files.
