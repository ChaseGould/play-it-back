# Profile: character cartoon

Evidence: proven. A Spanish-learning kids show pilot (October 2026): a
35 s vertical episode with a recurring cast, on-camera dialogue with lip
sync, about 190 credits including show setup.

Use for: recurring made-up characters who talk to each other, series or
episodes, and anything for kids.

## Timing
The script and the recorded voice lines drive timing.

## Stages
For a series, do a one-time show setup before the first episode, as
its own project folder (`<show>/show/`, with its own `status.md` and
budget cap): concept, cast, voice design (one voice per character, user
picks by ear), and reference sheets (empty set plates first, then
characters). Each episode is a project folder under `<show>/episodes/`
that reuses the approved voices and sheets from `<show>/show/`. For a
one-off cartoon, these are just stages 1, 3, and 4a of the project.

## Lip sync
- Test one shot on two models first. Wan 2.7 kept the supplied audio
  exactly where it was placed and tracked syllables; Seedance moved the
  line by about 1 s and drifted off model.
- Pad each line with silence to the clip length and offset, pass it as
  the audio reference, render, strip the clip audio, and lay the clean
  line back in the edit.
- Two characters in a shot: check the listener's mouth stays closed.

## Rules for a kids audience (apply in any profile)
- No flashing or strobing, no sudden loud sounds, gentle loudness.
- Correct language and pronunciation; QA transcribes every line.
- No calls to action aimed at kids; follow the platform's "made for
  kids" setting and AI-content disclosure.
- Music and SFX made in-house or clearly licensed.
- Characters' expressions read friendly; explicit prompt words help
  ("big round wide-open eyes").

## Lessons from use
- 2026-10: Keyframe edits that add a small prop (a seatbelt) were often
  ignored; local crops and composites fixed them.
- 2026-10: One 7 s clip could be split into two reaction shots to save a
  generation.
