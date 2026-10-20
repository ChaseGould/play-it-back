# Motion policy: still, loop, animated

Every shot in the shot list gets exactly one tag. This is the single
biggest cost decision in the project.

| Tag | What it is | How it's made | Cost |
|---|---|---|---|
| `still` | One keyframe with an editor camera move (slow push-in, pull-out, pan, tilt, parallax), about 10% or less | Image only; the move is done in the edit | Image only |
| `loop` | 3 to 5 s clip whose last frame matches its first, so the editor can loop it under a long hold (headlights glowing, exhaust, grass, hair in wind) | Image-to-video with the same start and end frame; crossfade 3 to 6 frames at the wrap | Short cheap clip |
| `animated` | Real motion: a transformation, an action beat, a performance | Image-to-video, sometimes with an end frame | Full clip price |

Defaults (the profile can change them):
- Narrated or talky formats: about 60% still, 25% loop, 15% animated
  by screen time. Real video only for the hero moments.
- Music videos: more animated shots, because motion on the beat is the
  point, but stills with a push-in still work for verses and lyric
  lines.
- Ads: animate the product moment and the hook; stills for supporting
  claims and the end card.

Rules that came from real projects:
- Don't animate what the story says isn't moving. A can "rolling
  around every turn" in a parked truck looked silly as a loop; the user
  had it replaced with a still.
- Loops on cheap low-res models can look soft next to full-res stills.
  The editor can composite only the moving part of the loop over the
  full-res keyframe.
- Prefer deliberate cuts between generations; never fake one continuous
  move across two separate clips.
- Hold an animated clip's end frame in the edit (freeze plus a slow
  push) instead of paying for a longer clip.
