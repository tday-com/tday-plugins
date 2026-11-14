---
name: demos-needed
description: List this product's features and docs pages that have no demo video yet in tday, then record the ones you pick.
---

Use the tday MCP tools.

1. Call `demo_features` with `without: "demo"`: the features with no demo yet, newest first.
2. Call `demo_docs`: the docs pages whose sections still need a demo. If tday says the product has no docs connected, skip this list quietly.
3. Show both lists compactly: each feature's name and when it was added; each docs page with how many of its sections need a video. Ask which to record.
4. For a feature, record it as the tday demo command does. For a docs page, follow what `demo_docs` says for that page. Run `demo_features` or `demo_docs` again at the end to show what is left.

If tday_workspace is in your tools, call it first with this repo's absolute path. If tday_sign_in is in your tools, call it next: this computer is not signed in to tday yet. If no demo_* tools are listed, tday's local demo tools are not installed on this computer yet: ask the developer to run `npx -y @tday-com/mcp@latest install` once in a terminal (it signs the computer in to tday and adds them), then type /reload-plugins.
