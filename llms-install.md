# Installing the tday MCP server

These steps are for an AI agent installing tday for a developer. tday records narrated demo
videos of the app in the developer's repo: the agent runs the app on the developer's computer and
records it, and tday adds the voice, cursor, camera and style.

## Requirements

- Node.js 18.17 or later (`node --version`).
- Google Chrome, or Playwright's Chromium.
- `ffmpeg` on the `PATH`, for demo videos.
- A tday account (https://tday.com). No API key is needed: the server signs the computer in itself.

## 1. Add the server

Add this entry to the MCP settings file of the client you run in (for Cline,
`cline_mcp_settings.json`; Cursor, `~/.cursor/mcp.json`; Claude Code,
`claude mcp add --scope user tday -- npx --prefix ~/ -y @tday-com/mcp@0.4.18 serve`):

```json
{
  "mcpServers": {
    "tday": {
      "command": "npx",
      "args": [
        "--prefix",
        "~/",
        "-y",
        "@tday-com/mcp@0.4.18",
        "serve"
      ]
    }
  }
}
```

It starts the [`@tday-com/mcp`](https://www.npmjs.com/package/@tday-com/mcp) package from npm, pinned to
version 0.4.18, over stdio. `--prefix ~/` (npm expands the `~/` itself, on every OS) makes npx
resolve it from the home directory, so the repo's own package.json, whose `overrides` could fail npx,
is never read. Keep any other servers already in the file.

## 2. Sign in

Reload the client's MCP servers. The `tday` server lists one tool, `tday_sign_in`, until
the computer is signed in. Call it: it answers a link and a code. Give the developer both: they open
the link on any device where they are signed in to tday, check the code matches and choose
**Authorize**. Call it again until it says the computer is signed in. The sign-in is saved in
`~/.tday/config.json`, readable only by the developer, and the server's tools then appear.

## 3. Check it

Call `tday_whoami`. It names the developer's tday account and brands. To check the browser, ffmpeg
and the connection from a terminal instead:

```bash
npx --prefix ~/ -y @tday-com/mcp@0.4.18 doctor
```

## Use

Ask for a demo: "record a tday demo of the newest feature". Call `demo_guide` first; it says how
tday wants the demo made. Nothing is uploaded until the developer confirms the review page with the
code it shows.
