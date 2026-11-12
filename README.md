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

### Cursor

```bash
git clone https://github.com/tday-com/tday-plugins.git ~/.cursor/plugins/local/tday
```

Then run **Developer: Reload Window** in Cursor.

### Only the MCP server, in one click

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=tday&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyItLXByZWZpeCIsIn4vIiwiLXkiLCJAdGRheS1jb20vbWNwQDAuNC4xOCIsInNlcnZlIl19) [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_tday-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%257B%2522name%2522%253A%2522tday%2522%252C%2522type%2522%253A%2522stdio%2522%252C%2522command%2522%253A%2522npx%2522%252C%2522args%2522%253A%255B%2522--prefix%2522%252C%2522~%252F%2522%252C%2522-y%2522%252C%2522%2540tday-com%252Fmcp%25400.4.18%2522%252C%2522serve%2522%255D%257D)

These add the `tday` MCP server alone (no skill or commands) to Cursor or VS Code, pinned to this
version. Use them or the plugin, not both.

### Codex

```bash
codex plugin marketplace add tday-com/tday-plugins
codex plugin add tday@tday
```

### Grok Build

```bash
grok plugin marketplace add tday-com/tday-plugins
grok plugin install tday
```

## First use

Ask your agent to record a demo. The first time, it calls `tday_sign_in`, which shows you a link
and a code. Open the link on any device where you are signed in to tday (it opens by itself when
this computer has a browser), check the code matches and choose **Authorize**; the agent carries
on. It works the same from a sandbox, a cloud machine or over SSH. The sign-in is
saved in `~/.tday/config.json` on your computer, readable only by you, and every coding agent on
the computer uses it. It lasts 90 days.

In Claude Code you can also type `/tday:demo` (optionally with a feature name) or
`/tday:demos-needed` to see which features have no demo yet.

## What it runs and what it sends

- **The tday MCP server.** The plugin adds one MCP server, `tday`, which your agent starts with
  `npx --prefix ~/ -y @tday-com/mcp@0.4.18 serve`: the [`@tday-com/mcp`](https://www.npmjs.com/package/@tday-com/mcp)
  package from npm, pinned to that version. It runs on your computer over stdio, in your repo; npx
  resolves it from your home directory so your repo's own package.json is never read. The package is
  published by tday's release workflow only, under its own license.
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
