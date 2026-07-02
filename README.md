<div align="center">

# <img src="docs/logo.png" width="40" valign="middle" alt="ClaudeView logo"/> ClaudeView

### A fast, native Windows desktop app for the Claude Code CLI

A pleasant three-pane workspace — **chat · file tree · git** — that idles around **~120 MB**
instead of a full editor's 400 MB+. Plan-mode approvals, slash-command **and `@`-file** autocomplete,
a file tree that lights up with your git changes, inline screenshot paste, **Remote Control from your
phone**, live usage bars, and a tray icon that doubles as a glanceable usage meter.

[![Download](https://img.shields.io/github/v/release/Concept211/ClaudeView?label=download&style=for-the-badge&color=C75F3F)](https://github.com/Concept211/ClaudeView/releases/latest)
&nbsp;
![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-0a0a0a?style=for-the-badge)
&nbsp;
![Free](https://img.shields.io/badge/free%20to%20use-22C55E?style=for-the-badge)

![ClaudeView — light](docs/screenshot-light.png)

</div>

---

## Why

VS Code's Claude Code extension is great, but it drags a whole editor along with it. ClaudeView is
the opposite: a small, focused window for *talking to Claude Code in a project* — see the files, see
the git state, approve plans, and keep an eye on your usage — without the weight.

## Features

- **💬 Chat with Claude Code** — streamed Markdown, tool calls, tool results, and live to-do checklists. **File paths Claude mentions are clickable** — click a generated `.html` and it opens in your browser; URLs open in your default browser too. Every code block gets a hover **Copy** button, and every response gets a small **copy / jump-to-prompt** action row, Claude.ai-style.
- **🔀 Permission modes, one Shift+Tab away** — cycle **Auto · Default · Accept Edits · Plan Mode · Don't Ask · Bypass Permissions** (the same set as Zed), or click the pill for a one-click picker instead of cycling. New sessions start in **Bypass Permissions**.
- **🧠 Model picker that tracks your CLI** — the model dropdown lists exactly what your installed Claude Code offers — Opus, **Sonnet 5**, Fable, Haiku, and Default — with display names and per-model reasoning-**effort** levels pulled straight from the CLI, so a new model shows up the moment you update the CLI, no app update needed. Opus, Sonnet, and Fable run with the **1M-token context window**, and the composer ring shows how much of it you've used — visible at a glance whether or not a turn is running.
- **📥 Never blocked on send** — type your next message while Claude is still working and it queues as an editable, numbered chip instead of waiting; it fires the moment the turn ends. Press **Enter** again to force it out immediately instead of waiting, or pull it back into the composer to revise it first.
- **🔴🟢 Inline diffs** — Edit/Write/MultiEdit tool calls show a real red/green line diff right inside the tool card, not just a filename.
- **⏱️ Never wonder if it's stuck** — the working indicator shows elapsed time and *what* Claude's currently running (e.g. "Editing Foo.cs · 12s"), not just three dots.
- **🛰️ Remote Control** — hand a session off to your phone or claude.ai: flip it on and ClaudeView opens the session link and keeps the transcript **in sync both ways**, so messages you type on your phone show up here (and vice-versa). One session at a time, marked with a violet indicator; it disconnects the moment you close the window.
- **📋 Plan mode, clickable** — `AskUserQuestion` renders as selectable option cards; `ExitPlanMode` as an **Approve / Reject** card. Reject → edit → re-present works end to end.
- **⌨️ Slash commands** — `/` autocomplete over built-ins *and* your own `.claude/commands` and skills — icon-coded so you can tell Anthropic built-ins from your own at a glance — with descriptions **and argument hints** pulled from their frontmatter. No-arg builtins submit on select; fires mid-message too, not just at the start.
- **🔎 `@`-mention files** — type `@` for an inline, filter-as-you-type file picker (Zed-style). Arrow-keys / Tab to insert a path reference into your message. Or right-click any file → **Reference in chat**.
- **📎 Attach & drop** — attach a file with the paperclip button or drag it straight onto the composer; images become inline thumbnails, everything else becomes a reference Claude can read.
- **🗂️ File tree as a change-radar** — lazy-loaded and **tinted live by git status** (green = new · yellow = modified · red = deleted), with a dot on folders that contain changes. **Single-click a changed file to see its diff**; right-click for Reference in chat · View diff · Open · Reveal in Explorer · Open terminal here · Copy path · **Add to `.gitignore`**.
- **🖼️ Inline screenshot paste** — paste an image straight into the composer (Zed-style); hover a thumbnail to enlarge.
- **🔀 Git panel** — status, colored changes, history, and one-box commit (Enter to commit); auto-refreshes after each turn. **Click a changed file to reveal it in the tree and open its diff** — a tinted, side-bar diff view with colored `+`/`−` lines. Not a repo yet? **Initialize one in a click.**
- **🔭 Sessions** — multiple concurrent conversations per project, with a working/awaiting/idle indicator, per-session cost, and how long ago it last ran (hover for the exact time). **Ctrl+1‑9 / Ctrl+Tab** jump straight to a session. **A native toast tells you when a task finishes** while ClaudeView is unfocused, minimized, or closed to the tray.
- **🎨 Theming** — Light / Dark / **System** (follows Windows), switching the chrome, the transcript, *and* the context menus together; immersive dark title bar.
- **📊 Usage at a glance** — status-bar 5h / 7d limit bars, session cost, model, and live RAM.
- **🛎️ Tray meter** — the tray icon *is* a live usage bar chart. Single-click for a usage popup, double-click to restore the window, right-click for a menu (update frequency, close-to-tray, start with Windows).
- **🪟 Polished window** — responsive collapsing layout, restores its size/maximized state, scroll-follows-cursor across panels.
- **♻️ Auto-updating** — self-installs to `%LOCALAPPDATA%`, then updates from GitHub Releases (download → **verify SHA-256** → swap on next launch).

<div align="center">

|  Dark mode  |  Tray usage meter  |
| :---------: | :----------------: |
| ![ClaudeView — dark](docs/screenshot-dark.png) | ![ClaudeView tray popup](docs/tray.png) |

</div>

## Install

1. Download **`ClaudeView.exe`** from the [latest release](https://github.com/Concept211/ClaudeView/releases/latest).
2. Run it. On first launch it copies itself to `%LOCALAPPDATA%\ClaudeView`, extracts its bundled
   sidecar, adds Desktop + Start-Menu shortcuts, and relaunches from there. After that it
   auto-updates itself.
3. **First-run setup checks your prerequisites and installs what's missing for you** — no manual
   `npm install` required. When it's done, click **Start using ClaudeView**.

<div align="center">

|  Auto-installs prerequisites  |  Ready to go  |
| :---------------------------: | :-----------: |
| ![ClaudeView first-run setup](docs/setup-install.png) | ![ClaudeView setup complete](docs/setup-done.png) |

</div>

**Requirements:** Windows 10/11. ClaudeView installs [Node](https://nodejs.org) and the
[Claude Code CLI](https://docs.claude.com/en/docs/claude-code) (`claude`) on first run if they aren't
already present — you just need to be **signed in to Claude** (the app can drive the CLI's sign-in for
you). The WebView2 runtime ships with modern Windows/Edge.

## How it works

A native WPF (.NET 8) shell renders the chat in WebView2 and drives the installed Claude Code CLI
through a small Node sidecar (the official `@anthropic-ai/claude-agent-sdk`). The SDK handles the
parts the raw stream protocol can't — like answering plan-mode questions reliably.

---

<div align="center">

Free to download and use. Built on Anthropic's
[Claude Agent SDK](https://github.com/anthropics/claude-agent-sdk-typescript) — not affiliated with
or endorsed by Anthropic.

</div>
