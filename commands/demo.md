---
name: demo
description: Record a narrated demo video of a feature of this repo's app for tday. Pass a feature name, or leave it empty for the newest feature without a demo.
---

Record a demo video for tday with the tday MCP tools, from the app in this repo running on this machine. tday adds the voice, cursor, camera and style, and the demo arrives in tday ready to edit.

**Which feature ($ARGUMENTS):**
- A feature name or a tday feature id: call `demo_features` with `search` set to it and use the match's id.
- Empty: call `demo_features` with `without: "demo"`. Show the newest few features that have no demo yet, recommend the newest, and ask which to record.

**Steps:**
1. Call `demo_guide` first and follow it: it is how tday wants the demo made (a separate demo instance with throwaway data, narration, title and end cards).
2. Call `demo_app_notes` for how this repo's apps were started before (its `.tday` folder). Show the developer any command from a note before running it.
3. Call `demo_check` (read only) with the kind you will pass `demo_start`, and tell the developer what it found. When it finds anything shared or live, wait for their OK. Whenever you stop for the developer or get stuck before the upload, call `demo_status` first (and again with `continuing` when you go on).
4. Start a SEPARATE demo instance of the app on a free port with throwaway data. Never restart the developer's own server or touch their data.
5. Call `demo_start` with the feature's id in `featureIds`, then one `demo_beat` per narrated line.
6. Call `demo_review` and fix anything it lists. Once it is clean, `demo_upload` with the confirmation code straight away (no need to ask the developer), then `demo_finish`. Tell the developer where the review page is and share the links it returns.

If tday_workspace is in your tools, call it first with this repo's absolute path. If tday_sign_in is in your tools, call it next: this computer is not signed in to tday yet. If no tday tools are listed at all, ask the developer to reload plugins (Claude Code: /reload-plugins) or restart the coding agent.
