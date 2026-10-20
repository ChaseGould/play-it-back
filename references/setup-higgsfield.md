# Connecting Higgsfield

Every user connects their own Higgsfield account. Generation uses their
credits. Sign-in happens in the browser (OAuth); there is no API key to
copy, and nobody should ever paste a key or token into the chat.

Server URL: `https://mcp.higgsfield.ai/mcp`

1. Make a Higgsfield account at higgsfield.ai. Using it from an AI app
   needs an active paid Higgsfield plan, and every generation spends
   credits. Higgsfield has no spending cap of its own; the project
   budget is a rule the assistant follows, and the only hard limit is
   the credits on the account.
2. Connect it in the app you're using:

**Claude Code** (terminal or the desktop app's Code tab)
- Run: `claude mcp add --scope user --transport http higgsfield https://mcp.higgsfield.ai/mcp`
  (`--scope user` makes it work in every folder, not just one project)
- Then in a `claude` session run `/mcp`, pick `higgsfield`, and sign in
  in the browser.

**claude.ai or Claude Desktop (chat)**
- Settings, Connectors, Add custom connector. Name `Higgsfield`, URL
  `https://mcp.higgsfield.ai/mcp`. Click Connect and sign in.
- Turn the connector on in the chat (the tools menu) before starting.

**ChatGPT**
- Go to higgsfield.ai/mcp and click Add Higgsfield plugin, or open the
  Plugins directory in ChatGPT and find Higgsfield. Click Add, then sign
  in to Higgsfield and authorize.
- Only add Higgsfield from Higgsfield's site or ChatGPT's directory; a
  connector with any other URL is not Higgsfield.
- In the chat, ChatGPT uses the plugin when it fits, or type
  `@Higgsfield`.
- Limits in ChatGPT (Higgsfield help center, October 2026): no audio or
  voice generation, and the assistant can't read images attached to the
  chat, so photos and logos go in through the Higgsfield upload window.

**Codex (OpenAI's coding agent)**
- Add to `~/.codex/config.toml`:
  ```toml
  [mcp_servers.higgsfield]
  url = "https://mcp.higgsfield.ai/mcp"
  ```
- Then run `codex mcp login higgsfield` and sign in.

**Anything else** that supports remote MCP servers: add the URL above
as a streamable HTTP server and sign in when prompted.

3. Check it works: ask "what's my Higgsfield credit balance?". The
   assistant should answer from the Higgsfield tool, not from memory.

## Troubleshooting
- **"Unauthorized" mid-project:** the sign-in expired. Reconnect
  (`/mcp` in Claude Code, or reconnect the connector) and continue.
- **Cloud or sandboxed sessions** may block outbound connections to
  `mcp.higgsfield.ai`. Run locally or allow that domain.
- **Rate limits (429):** the request was refused and not charged. Wait
  a little and resubmit unchanged.
- **Tool names change.** List the server's tools at the start of each
  session rather than assuming names.

These steps were current in October 2026. Apps rename menus often; if a
step doesn't match what the user sees, use the closest current label.
