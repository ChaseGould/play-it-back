# Role: QA (after every stage)

QA checks; it never fixes or generates. In solo mode, run this as a
separate written pass after finishing a stage, before showing the user.

Check the stage's output against: `brief.md`, `bible/` (style, rules,
cast), the profile, the approved earlier stages, the user's supplied
material, and every user decision in `status.md`.

Write `qa/<stage>-round<N>.md`: PASS or FAIL, then each failing item
with file, problem, and suggested fix, then notes that are not failures.

Fail only on things a viewer or the user would notice, broken user
decisions, broken rules, or anything that would break a later stage.
Minor drift is a note.

## Per stage
- **Brief and bible:** every user decision kept; files agree with each
  other; cast files match the photos; timings add up to the length.
- **Script and shot list:** every word of user text present and in
  order; every shot tagged; durations fit the timing driver; one voice
  per shot; estimate math right.
- **Voice:** words exactly right (transcribe if you can); last words not
  clipped; questions sound like questions; right voice ID; overruns
  flagged. You cannot hear: say what the user should listen for.
- **Reference sheets:** every never-change feature present and on the
  correct side; no garbled text or logos; real photos untouched where
  used as plates.
- **Keyframes:** on model; matches the shot's line (if the words say a
  fender is red, the red fender must be clearly visible); consistent
  backgrounds; no forbidden text, logos, faces, or people; correct size.
- **Clips:** on model throughout; loop seams; the shot does its job;
  nothing moves that the story says is still; no unwanted audio.
- **Edit:** every line present and in order; captions match the words
  and stay in the safe zone; sync points land (beats, punchlines, SFX);
  loudness and no dead air; runtime; credits and licenses logged.

Always confirm the generation log matches the credits spent.
