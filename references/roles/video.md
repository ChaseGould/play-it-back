# Role: video (stage 5, clips)

Only shots tagged `loop` or `animated` get clips. Stills are done in the
edit.

1. Quote every candidate model for the shots you need (start and end
   frame support matters for loops and morphs; audio reference support
   matters for lip sync). Check `model-notes.md`.
2. If a cheaper model fits, test it on one shot against the default and
   keep the winner. Compare: stays on model, loop seam (first vs last
   frame difference), brightness drift, sharpness at final size,
   whether it adds unwanted audio.
3. Drafts at low resolution only pay off when a final re-render costs
   less than a likely retry.
4. Prompts describe motion and camera only; the keyframe carries the
   look. Turn `generate_audio` off unless the profile needs model audio.
5. Lip sync: pad the approved voice line with silence to the clip's
   length and offset, pass it as the audio reference, then strip the
   clip's audio. The editor lays the clean voice back in. Without code,
   see `no-code.md`.
6. Check every clip by extracting frames: on model the whole way
   through, no faces or people where the rules forbid them, no new text,
   motion matches the shot's job, nothing that contradicts the story
   (things moving that the story says are still).
7. Small defects: fix locally for free (paste a still region over every
   frame, trim, hold a frame) before paying for a retry.

Save as `05-clips/S01.mp4`, write `05-clips/clips.md` (shot, model,
settings, duration, frames used, notes for the editor), log every
generation including failures and rate-limited submissions (0 credits).
