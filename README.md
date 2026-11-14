# tday for coding agents

Record narrated demo videos of your app with the coding agent you already use. Ask your agent to
"record a tday demo of the newest feature": it starts a separate demo copy of your app on your
computer, walks through the feature one narrated line at a time, checks the take for anything
private on screen, and uploads it. tday adds the voice, the cursor, the camera moves and the
style, and the demo arrives in tday ready to edit and share.

It works with web apps, desktop apps built on Electron, terminal tools, iPhone apps in the iOS
Simulator, Android apps on the emulator and Mac apps. You need a tday account
([tday.com](https://tday.com)).

## Install

### Claude Code

```bash
claude plugin install tday --marketplace tday-com/tday-plugins
```

Or inside a session: `/plugin marketplace add tday-com/tday-plugins`, then `/plugin install tday@tday`.

## First use

The plugin connects Claude Code to tday's hosted MCP server, `https://tday.com/api/mcp`. The first time,
Claude Code opens tday in your browser to sign in and approve it.

Recording runs on your computer, so the demo tools are a separate one-time install. In a terminal:

```bash
npx -y @tday-com/mcp@latest install
```

It signs this computer in to tday and adds the local `tday` server to Claude Code (and Cursor and
Codex if you use them); then type `/reload-plugins`. Ask your agent to record a demo, or type
`/tday:demo` (optionally with a feature name) or `/tday:demos-needed` to see which features have no
demo yet.

## What it runs and what it sends

- **The MCP servers.** The plugin adds one, `tday-connector`: tday's hosted server at
  `https://tday.com/api/mcp`, signed in with OAuth in your browser (your brands, credits and product
  screens). The demo tools come from the installer above, which adds the
  [`@tday-com/mcp`](https://www.npmjs.com/package/@tday-com/mcp) package from npm as a local
  server that runs on your computer over stdio, in your repo. The package is published by tday's
  release workflow only, under its own license.
- **What leaves your computer.** The demo footage and the screens you choose to upload, and
  metadata about them (the feature, the steps, the narration). Never your source code, `.env`
  values or secrets: a take with a possible secret on screen is held back until it is fixed. See
  [what leaves your machine](https://docs.tday.com/capture-privacy) and [demo safety](https://docs.tday.com/demo-safety).
- **Who it talks to.** tday (`tday.com`), with your sign-in. The npm registry, once a day, to see
  whether a newer version is out. GitHub's or GitLab's public API, without a token, to check whether
  your repo is public before a note is saved in it (sending only the repo's name). For a terminal
  demo, a symbols font from `cdn.jsdelivr.net`.
- **On your computer.** A separate demo instance of your app with throwaway data (your own server
  and data are never touched), a browser or simulator to record it in, and scratch files under
  `~/.tday/capture`, removed at the end. Notes on how your app was started go in your repo's
  `.tday` folder, and nothing is committed for you.

The plugin also carries a skill with the steps the agent follows, and the two commands above.

## Links

- [Docs](https://docs.tday.com/coding-agents)
- [Support](https://tday.com/support)
- [Privacy policy](https://tday.com/privacy)
- [Terms](https://tday.com/terms)

## License

The files in this repository are licensed under the MIT license (see [LICENSE](LICENSE)). The
`@tday-com/mcp` package they start is distributed on npm under its own license.

The tday name, the tday logo and Cali (the icon in `assets/`) are tday's trademarks. The license does
not grant permission to use them.
