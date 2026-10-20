# Play It Back

Make a music video, an ad, a story video, or a cartoon with Claude or
ChatGPT. Tell it what you're picturing, drop in your songs, photos, or
videos, and it pitches ideas built on yours, asks before spending
anything, and shows you each step.

You need a paid [Higgsfield](https://higgsfield.ai) plan with some
credits. Higgsfield makes the pictures, voices, and video, on your own
account. Then follow the steps for the app you use:
[Claude](#set-it-up-in-claude-about-3-minutes) or
[ChatGPT](#set-it-up-in-chatgpt-about-3-minutes).

## Set it up in Claude (about 3 minutes)

You need a [Claude](https://claude.ai) account.

**1. Download the skill**

[Download play-it-back.zip](https://github.com/ChaseGould/play-it-back/releases/latest/download/play-it-back.zip)
(don't unzip it)

**2. Add it to Claude**

In Claude, go to **Settings**, then **Capabilities**, then **Skills**.
Click **Upload skill** and pick the file you just downloaded. Make sure
the skill is switched on.

Don't see **Skills**? On the same Capabilities page, turn on **Code
execution and file creation** first; skills need it.

**3. Connect Higgsfield**

In Claude, go to **Settings**, then **Connectors**, then **Add custom
connector**.
- Name: `Higgsfield`
- URL: `https://mcp.higgsfield.ai/mcp`

Click **Connect** and sign in to Higgsfield. You'll never need to copy
a password or key into the chat.

**4. Make something**

Start a new chat and begin your message with **Use Play It Back**, so
Claude knows to use the skill. Then say what you're picturing (even
roughly) and drop in whatever you've got: songs, photos, videos, voice
memos, a logo. For example:

> Use Play It Back. Make a music video for this song. Moody, neon, kind
> of lonely.

> Use Play It Back. Here's a song and some photos of my car. I want
> something funny, like a fake documentary about it.

> Use Play It Back. Help me make a 30 second ad for my coffee truck.

If you just send files, Claude will ask what you have in mind first.
Then it looks through everything, pitches a few ideas built on yours,
and asks only what it still needs, including how many credits you
want to spend at most. After that it checks with you after every step.

Menu names change sometimes. If a button isn't exactly where this says,
look for the closest match.

## Set it up in ChatGPT (about 3 minutes)

You need a paid ChatGPT plan that includes Skills.

**1. Download the skill**

[Download play-it-back.zip](https://github.com/ChaseGould/play-it-back/releases/latest/download/play-it-back.zip)
(don't unzip it)

**2. Add it to ChatGPT**

Open **Skills** (in the sidebar or your profile menu), click
**Create**, then **Upload from your computer**, and pick the file you
just downloaded.

**3. Connect Higgsfield**

Go to [higgsfield.ai/mcp](https://higgsfield.ai/mcp) and click **Add
Higgsfield plugin** (or find Higgsfield in ChatGPT's **Plugins**
directory). Click **Add**, then sign in to Higgsfield and allow access.
Only add Higgsfield from Higgsfield's own site or ChatGPT's directory.

**4. Make something**

Start a new chat and begin your message with **Use Play It Back**,
the same way as in Claude. Then say what you're picturing and add your
files.

**Two differences in ChatGPT:**
- Higgsfield can't make voices in ChatGPT. Music videos and ads with
  on-screen text work fine. For a narrated video, record the voiceover
  yourself on your phone and attach it, or use Claude.
- Attach your files to the chat so ChatGPT can look at them. When it's
  time to use your photos or logo in the video, it will also open a
  Higgsfield upload window; add them there too.

**No Skills on your plan?** Make a **Project**, open the zip on your
computer, paste the text of `SKILL.md` into the project's
instructions, and add the files from `references` and `templates` to
the project's files. Then chat inside that project.

## Good to know

- **Cost:** you pay Higgsfield in credits. Videos that are mostly still
  pictures cost much less than all-video ones. You pick a limit at the
  start and the assistant stops to check with you before getting close.
  Higgsfield itself has no spending cap, so the only hard limit is how
  many credits you buy.
- **The final edit:** in the Claude and ChatGPT apps, you get a simple
  shot-by-shot list to put together in CapCut or any video editor.
  (Claude Code can do the edit for you.)
- **Music and photos:** use songs and photos you have the right to use.
  It will ask.

---

## For developers

This repo is the skill folder itself.

**Claude Code** (or just ask Claude Code to "install the skill from
github.com/ChaseGould/play-it-back and connect the Higgsfield MCP
server"):
```bash
git clone https://github.com/ChaseGould/play-it-back ~/.claude/skills/play-it-back
```
```bash
claude mcp add --scope user --transport http higgsfield https://mcp.higgsfield.ai/mcp
```
Then run `/mcp` in a session, pick `higgsfield`, and sign in. Start a
project with `/play-it-back` followed by what you're picturing. Claude
Code runs each role as a subagent and does the final edit itself
(needs ffmpeg).

**Codex:** clone into `~/.codex/skills/play-it-back`, add
`[mcp_servers.higgsfield]` with `url = "https://mcp.higgsfield.ai/mcp"`
to `~/.codex/config.toml`, then `codex mcp login higgsfield`.

More detail: [references/setup-higgsfield.md](references/setup-higgsfield.md)
and, for apps that can't run code, [references/no-code.md](references/no-code.md).

| Format | Status |
|---|---|
| Narrated short | Proven on a finished episode |
| Music video | Proven on two finished clips |
| Character cartoon | Proven on a finished episode, includes kids rules |
| Ad or promo | Untested, built from the others |
| Custom | Built with you at kickoff |
