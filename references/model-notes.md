# Model notes (as of October 2026)

Models, prices, and quirks change monthly. Treat this as a starting
point: always get a free quote, and when two candidates are close, test
one shot on each before committing the rest. Append new findings with a
date.

## Prices seen on Higgsfield (credits)
| Kind | Model | Price seen | Notes |
|---|---|---|---|
| Voice (TTS) | `seed_audio` presets | about 0.1 to 1 per line, by text length | No emotion control; see quirks |
| Image | `gpt_image_2_5` low 1k | 0.25 | Good for reference sheets |
| Image | `gpt_image_2_5` low 2k | 0.5 | Enough for 1080x1920 keyframes |
| Image | `gpt_image_2_5` high 2k | about 2.75 | Used for a music video's hero frames |
| Image | `nano_banana_pro` | 2 | Served as nano_banana_2 at times |
| Outpaint | `flux_2_pro_outpaint` | 2.2 | Extends edges only; paste the original back over its area |
| Video | `wan3_0` 480p | 1.0 per second | Best value for loops; start and end frame; returned silent |
| Video | `wan2_7` 720p | 1.5 per second | Start and end frame; audio-driven lip sync that keeps your audio placement exactly |
| Video | `seedance_2_5` | 3 per second at 480p, about 7 at 720p, about 12 at 1080p | Strong motion and identity with references; expensive; can move supplied audio and drift off model |
| Video | `grok_video_v15_lite` | 1.0 per second | Start frame only, so no loops or morphs |
| Video | `kling3_0_turbo`, `minimax_h3_max`, `veo3_1_lite` | about 1.5 per second | Not tested head to head |

Rough project totals: a 2:37 narrated episode, mostly stills, 110
credits. A 35 s kids episode with lip sync, about 190 including show
setup. A 30 s all-video music clip on Seedance with 1080p finals, 530
to 630.

## Quirks worth knowing
- **seed_audio cuts off the last word** at the end of a file. Append a
  throwaway sentence ("That is all.") and cut it off in the silence
  before it. Check the true end of every line, not just the silence
  after it.
- **seed_audio and quote marks:** quoted dialogue can make it drop the
  words outside the quotes. Use commas instead of quotes in the spoken
  text; keep quotes in captions.
- **Questions vs statements:** a line ending in "?" may rise too much
  (upspeak) or, without "?", read flat. Generate two or three takes and
  pick by ear; a rise of about 3 to 6 semitones sounds natural.
- **Respell for TTS:** years as words ("nineteen eighty-six"), slang
  ("Ole" for "Ol'"), accents ("ombray" for "ombre"). Captions keep the
  real spelling.
- **One-sided features** (a black fender on one side, one earring):
  describe them by side of the picture and say which way the vehicle or
  person faces. Models swap sides often.
- **Generated text and logos come out garbled.** Ask for blank signs and
  badges; composite real logos and text in the edit.
- **Image edits re-render everything.** For a small change, generate the
  edit, then composite only the changed region back over the original.
- **Plain outpaint can redraw the whole photo.** Use an edge-only
  outpaint and paste the original pixels back.
- **Seedance copies defects from the start frame,** and invents faces on
  push-ins to masked or small faces. Gate start frames hard; attach the
  face reference to every shot.
- **Lip sync:** pad each voice line with silence to the exact clip
  length and offset, pass it as the audio reference, render the clip,
  then lay the clean voice back in the edit at the same offset.
- **Clip brightness drifts darker** over a clip; the editor grades it
  back to the keyframe.
- **Higgsfield music and SFX models** were restricted to its game
  pipeline in October 2026. Get music elsewhere (`roles/editor.md`).
