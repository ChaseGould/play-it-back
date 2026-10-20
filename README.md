# Play It Back

An AI video studio in a skill. Tell your AI assistant what you want (a
music video for your song, a 30 second ad, a narrated story about your
car, a cartoon) and it runs the whole production with you: interview,
script and shot list, voice, reference images, keyframes, video clips,
and the final edit.

It's built for Claude and ChatGPT, and makes images, video, and voice
through the Higgsfield MCP server on your own Higgsfield account.

How it works:
- **Interview first.** About ten questions, then it picks the closest
  format: music video, ad or promo, narrated short, character cartoon,
  or custom.
- **You approve every stage.** After each stage it runs a QA check,
  shows you what it made and what it cost, and waits for your OK or
  your notes.
- **Hard budget.** You set a credit cap before anything is generated.
  It never goes past the cap and stops to ask at 80%.
- **Cheap by design.** Every shot is tagged still, loop, or animated,
  and only the shots that need real motion become video. One 2:37
  narrated episode cost 110 credits this way.

## 1. Connect Higgsfield (your own account)

You need a Higgsfield account with credits (higgsfield.ai). Sign-in
happens in your browser. There is no API key to copy, and the skill
will never ask you for one.

Server URL: `https://mcp.higgsfield.ai/mcp`

| App | How to connect |
|---|---|
| Claude Code | `claude mcp add --scope user --transport http higgsfield https://mcp.higgsfield.ai/mcp`, then run `/mcp` in a session, pick `higgsfield`, and sign in |
| claude.ai or Claude Desktop | Settings, Connectors, Add custom connector, paste the URL, Connect, sign in. Turn it on in the chat's tools menu |
| ChatGPT | Install the official Higgsfield plugin at chatgpt.com/plugins/higgsfield and sign in, or add a custom connector with the URL in developer mode |
| Codex | Add `[mcp_servers.higgsfield]` with `url = "https://mcp.higgsfield.ai/mcp"` to `~/.codex/config.toml`, then run `codex mcp login higgsfield` |

Check it worked: ask "what's my Higgsfield credit balance?". More detail
and troubleshooting: [references/setup-higgsfield.md](references/setup-higgsfield.md).

## 2. Install the skill

**Claude Code**
```bash
git clone https://github.com/ChaseGould/play-it-back ~/.claude/skills/play-it-back
```

**Codex**
```bash
git clone https://github.com/ChaseGould/play-it-back ~/.codex/skills/play-it-back
```

Update later with `git pull` inside that folder.

**claude.ai:** download this repo as a ZIP (green Code button, Download
ZIP), then upload it under Settings, Capabilities, Skills.

**ChatGPT:** if your plan supports skills, upload the ZIP. If not, make
a Project, paste `SKILL.md` into the project instructions, and add the
`references/` and `templates/` files to the project.

Menu names change often; use the closest current label.

## 3. Use it

Start a new chat (in Claude Code, open it in an empty folder) and say
what you want, attaching your song, photos, or logo if you have them:

> Make a music video for this song. Moody, neon, mostly my character
> walking through a city at night.

> Help me make a 30 second vertical ad for my coffee truck.

It checks your Higgsfield connection, interviews you, asks for a
budget, and goes from there.

## What works where

| | Claude Code, Codex | claude.ai, ChatGPT |
|---|---|---|
| Interview, script, shot list | yes | yes |
| Voice, images, video clips | yes | yes |
| Subagents per role | yes | no, one assistant plays every role in turn |
| Lip sync, audio splicing, frame checks | yes (needs ffmpeg) | limited, see [references/no-code.md](references/no-code.md) |
| Final edit | yes (needs ffmpeg) | you get a shot-by-shot edit list to assemble in CapCut or any editor |

## Costs

You pay Higgsfield directly in credits. Video is most of the spend: a
mostly-stills video can run tens of credits for a minute or more, while
30 seconds of all-video clips can run several hundred. Prices change;
the skill quotes every generation before running it.

## Formats

| Format | Status |
|---|---|
| Narrated short | Proven on a finished episode |
| Music video | Proven on two finished clips |
| Character cartoon | Proven on a finished episode, includes kids rules |
| Ad or promo | Untested, built from the others |
| Custom | Built with you from the interview |

Each format file has a "Lessons from use" section that grows as
projects finish.
