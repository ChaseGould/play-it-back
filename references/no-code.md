# No-code fallbacks (solo mode without ffmpeg)

Some steps need code execution with ffmpeg or Python. Where the app
can't run code, use these instead and tell the user what changes.

| Step | Needs code because | Fallback |
|---|---|---|
| Lip sync (padding voice to clip length) | Audio editing | Avoid lip sync: narration, wide shots, backs, masks, cutaways. If the user insists, pass the unpadded line and accept looser sync. |
| Splicing a fixed word into a voice line | Audio editing | Regenerate the whole line instead. |
| Beat grid for a music video | Audio analysis | Ask the user for the BPM (or look it up from the song's metadata or a tap-tempo site) and the timestamps of the sections; cut on whole bars from that. |
| Compositing a small fix onto a keyframe | Image editing | Regenerate with a tighter prompt, or accept the change if QA notes it only as drift. |
| Outpaint, then paste the original back | Image editing | Use the outpaint result only if the real subject looks unchanged to the user; otherwise frame the shot so no outpaint is needed. |
| Checking clips frame by frame | Video decoding | Send the clips to the user to watch; give them the QA checklist for that stage. |
| Measuring loudness, durations, pitch | Audio analysis | Use durations the generation tool reports; ask the user to listen. |
| Final edit | ffmpeg | `roles/editor.md`, "No-code handoff": an edit list the user assembles in CapCut, iMovie, Premiere, or DaVinci Resolve. |

Everything else (interview, bible, script, shot list, voice lines,
sheets, keyframes, clips, QA by checklist) works without code.
