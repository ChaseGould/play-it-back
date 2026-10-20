# Role: image (stage 4a reference sheets, 4b keyframes)

## Before generating
- List the server's image models, get free quotes, and pick the cheapest
  that holds the look in `bible/style.md`. Test one image first if the
  model is new.
- Upload the user's photos as references when a subject is real. If you
  can't read files attached to the chat (ChatGPT), open Higgsfield's
  upload window and have the user add them there.

## Pass 1: reference sheets (4a)
- One sheet per recurring subject: turnaround (front, side, back,
  three-quarter) plus detail panels for the features that must never
  change. Use the reference-sheet prompt suffix, not the keyframe one.
- From photos: match what the photos show, feature by feature. Models
  swap sides and simplify details; say which side each feature is on.
- If one row of a sheet is wrong, regenerate only that part and
  combine locally.
- Prep real photos used as shots: extend to the target aspect with an
  edge-only outpaint, then paste the original pixels back so the real
  subject is untouched. Blur readable plates and house numbers.
- Stop for QA and user approval before pass 2. Every later image uses
  the approved sheets as references.

## Pass 2: keyframes (4b)
- One keyframe per shot at full output resolution (for 9:16, at least
  1080x1920), with the sheets and the keyframe prompt suffix.
- Reuse: when two shots differ by one detail (lights on vs off),
  generate an edit of the first, then composite only the changed region
  onto the original so everything else is pixel-identical.
- A morph from a real photo into the generated look needs the end frame
  framed to match the photo's crop exactly.
- Loop shots need a frame that works as both start and end.
- Keep backgrounds consistent with the story's location across shots.
- No readable text, logos, or faces where the rules forbid them; ask
  for blank signs and badges.

Save as `04-images/S01.png` etc., write `04-images/keyframes.md` (shot,
file, model, settings, references, notes), and log every generation.
