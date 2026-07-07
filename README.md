<div align="center">

# <img src="docs/logo.png" width="40" valign="middle" alt="ClaudeView logo"/> ClaudeView

### A fast, native Windows desktop app for the Claude Code CLI

A pleasant three-pane workspace — **chat · file tree · git** — that idles around **~120 MB**
instead of a full editor's 400 MB+. A built-in **Assistant workspace** for general chats, a
**click-to-open context & plan-usage panel**, a **live To-Do panel** that mirrors Claude's task
list, plan-mode approvals, slash-command **and `@`-file**
autocomplete, a file tree that lights up with your git changes, a built-in **syntax-highlighted code
viewer & editor**, a **built-in mockup preview**, inline screenshot paste, **Remote Control from your phone**, distinct
**task-done / needs-you alert sounds**, live usage bars, and a tray icon that doubles as a
glanceable usage meter.

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

- **💬 Chat with Claude Code** — streamed Markdown (with **tables rendered as a clean bordered grid**), tool calls, tool results, and live to-do checklists. **File paths Claude mentions are clickable**, and **mockups it builds for you open automatically in a fast built-in preview** — an in-app browser window with **Reload** and **Open in browser** that shrugs off a page crash and reloads itself. A tray menu picks how widely it triggers — **only `_mockups` folders · any mockup-named folder · any HTML file · off** — or you can send mockups to your default browser instead; other URLs open in your default browser too. Every code block gets a hover **Copy** button, every response gets a small **copy / jump-to-prompt** action row, and **your own messages get copy *and* edit buttons** — Claude.ai-style throughout. **Edit a message you've already sent to rewind the conversation to that point and re-run from your revised wording** — the earlier branch is copied, not clobbered, so nothing is lost server-side.
- **✨ Built-in Assistant workspace** — a pinned, always-there general-purpose space (under `Documents\ClaudeView`) for quick questions and one-off tasks that aren't a project. It's non-git, defaults to Bypass, and still has **full filesystem access** — point it at any folder on your machine. Its own blue styling keeps it distinct from your projects, and it sits at the top of both the project picker and the sessions list.
- **🔀 Permission modes, one Shift+Tab away** — cycle **Ask before edits · Edit automatically · Plan mode · Auto mode · Bypass permissions** (the same set as Anthropic's official VS Code extension), or click the pill for a one-click picker instead of cycling. New sessions start in **Bypass permissions**, which runs everything without asking.
- **🧠 Model picker that tracks your CLI** — the model dropdown lists exactly what your installed Claude Code offers — Opus, **Sonnet 5**, Fable, Haiku, and Default — with display names and per-model reasoning-**effort** levels pulled straight from the CLI, so a new model shows up the moment you update the CLI, no app update needed. **Each session remembers its own model and effort** — switch sessions and the picker follows, and every session runs (and live-switches) with its own choice. Opus, Sonnet, and Fable run with the **1M-token context window**, and the composer ring shows how much of it you've used — visible at a glance whether or not a turn is running.
- **📊 Context & usage panel** — click the context ring for the **real `/context` breakdown**: per-category token usage (system prompt · tools · skills · MCP · memory files · messages · free space), plus your **plan-usage bars** (5-hour · weekly) and a one-click **Compact conversation** that updates the numbers live as it runs. It reads the live session **token-free** (no wasted message) and even wakes an idle session to show its baseline.
- **📥 Never blocked on send** — type your next message while Claude is still working and it queues as an editable, numbered chip instead of waiting; it fires the moment the turn ends. Press **Enter** again to force it out immediately instead of waiting, or pull it back into the composer to revise it first.
- **✍️ A composer that keeps up** — **Zed-style numbered lists** (type `1. ` and the markers snap to fixed-width mono + accent so every item lines up, while your text stays regular; `Shift+Enter` continues the list and ends it on an empty item), and **your unsent draft — text and pasted images alike — survives session switches, restarts, and even a crash**.
- **⚡ Quick commands** — one-click buttons in the composer for the things you send constantly (**Continue · Commit · Push** out of the box), each firing its command the moment you click it. **Add, rename, reorder, or remove your own** from a small manager, while the keyboard-shortcut hints tuck behind a **?** so the row stays clean.
- **🔴🟢 Inline diffs** — Edit/Write/MultiEdit tool calls show a real red/green line diff right inside the tool card, not just a filename.
- **⏱️ Never wonder if it's stuck** — the working indicator shows elapsed time and *what* Claude's currently running (e.g. "Editing Foo.cs · 12s"), not just three dots.
- **🛰️ Remote Control** — hand any session off to your phone or claude.ai: flip it on and ClaudeView opens the session link and keeps the transcript **in sync both ways**, so messages you type on your phone show up here (and vice-versa). **Bridge as many sessions as you like at once** — each marked with a violet indicator. Then drive it all from your phone: type **`/remote`** to list every session on that computer, **connect** another one, or **disconnect** any of them (or all) — no need to walk back to the desktop. A bridge drops when you close the window, but **survives an app update or restart** — ClaudeView re-establishes it automatically when the session comes back, so a background update never silently strands your phone. An idle bridged session shows a **dimmed** violet dot (it only pulses while actually working).
- **📋 Plan mode, clickable** — `AskUserQuestion` renders as selectable option cards; `ExitPlanMode` as an **Approve / Reject** card. Reject → edit → re-present works end to end. The cards **wait as long as you need** — take an hour to decide and the turn stays parked for your answer, never timing out behind your back.
- **⌨️ Slash commands** — `/` autocomplete over built-ins *and* your own `.claude/commands` and skills — icon-coded so you can tell Anthropic built-ins from your own at a glance — with descriptions **and argument hints** pulled from their frontmatter. No-arg builtins submit on select; fires mid-message too, not just at the start.
- **🔎 `@`-mention files** — type `@` for an inline, filter-as-you-type file picker (Zed-style). Arrow-keys / Tab to insert a path reference into your message. Or right-click any file → **Reference in chat**.
- **📎 Attach & drop** — attach a file with the paperclip button or drag it straight onto the composer; images become inline thumbnails, everything else becomes a reference Claude can read.
- **🗂️ File tree as a change-radar** — lazy-loaded and **tinted live by git status** (green = new · yellow = modified · red = deleted), with a dot on folders that contain changes. **Double-click any file to open it in the built-in code viewer/editor**; right-click for Reference in chat · View diff · View · Open · Reveal in Explorer · Open terminal here · Copy path · **Add to `.gitignore`**. It **refreshes itself the moment Claude creates or deletes a file**, and you can **drag any file straight into the composer** to reference it.
- **📝 Built-in code viewer & editor** — double-click any file to open it in a themed, **syntax-highlighted** viewer (~40 languages) topped with a **colored brand-logo badge** for the file's language — no more launching an external app just to glance at a file. Click **Edit** to turn it into a full editor powered by **CodeMirror 6**: line-number gutter, undo/redo, **find/replace**, multi-cursor, auto-indent, and bracket matching — save with **Ctrl+S**. **Ctrl+A selects the whole file** so you can copy it straight out, even in read-only view. It opens **read-only by default** and stays safe alongside a live session: it silently reloads when a file changes on disk while you're just viewing, **warns before overwriting** a file Claude changed, and preserves your original line endings.
- **🖼️ Inline screenshot paste** — paste an image straight into the composer (Zed-style); hover a thumbnail to enlarge.
- **🔀 Git panel** — status, colored changes, history, and one-box commit (Enter to commit); auto-refreshes after each turn. **Click a changed file to reveal it in the tree and open its diff** — a tinted, side-bar diff view with colored `+`/`−` lines. It also **spots a placeholder commit identity** (like `Your Name <you@example.com>`) and offers to set your real name and email in one click — pre-filled from your signed-in Claude account, for this repo or globally — so your commits are attributed correctly. Not a repo yet? **Initialize one in a click.**
- **🔭 Sessions** — multiple concurrent conversations per project, with a working/awaiting/idle indicator, per-session cost, and how long ago it last ran (hover for the exact time). **Ctrl+1‑9 / Ctrl+Tab** jump straight to a session, **`+` on any group starts a new one**, **↻ starts a project fresh** (clears all its sessions and opens a clean one in a click), and you can **pin the projects you live in to the top** of the list. **A native toast — with a distinct sound — tells you when a task finishes** (a gentle chime) or **needs your input** (an insistent, looping alert), while ClaudeView is unfocused, minimized, or closed to the tray.
- **✅ Live To-Do panel** — when Claude tracks its work as a task list, it gets its own panel pinned under Sessions and **mirrors that list in real time**: items check off as Claude completes them, the one **currently in progress is marked with a gently breathing Claude logo** so you can see what's being worked on at a glance, topped with an *X of Y done* progress bar. It **appears only when there's a list** (and hands the space back to Sessions otherwise), and the divider between the two **drags to resize · double-clicks to reset**, remembered across restarts.
- **🎨 Theming** — Light / Dark / **System** (follows Windows), switching the chrome, the transcript, *and* the context menus together; immersive dark title bar, set throughout in Anthropic's own **Sans / Serif / Mono** typefaces.
- **📊 Usage at a glance** — status-bar 5h / 7d limit bars, session cost, model, and live RAM.
- **🛎️ Tray meter** — the tray icon *is* a live usage bar chart: 5-hour, weekly, and a **configurable third bar** you pick from **Disk · RAM · CPU · App RAM** right from the menu — and its **hover tooltip carries the same three rows** (with **App RAM** showing the exact MB ClaudeView is using). Single-click for a **usage popup** (now with a live **CPU** row and your core count), double-click to restore the window, right-click for a menu (third-bar metric, update frequency, close-to-tray, start with Windows).
- **🪟 Polished window** — a **responsive collapsing layout** that folds the side panels away as it narrows (down to a phone-width single column), with its **own chat font size for the compact view** kept separate from your desktop size. It restores its size/maximized state, scroll-follows-cursor across panels, and **double-click any panel splitter to reset it**. Panel widths *and* the Explorer/Git and Sessions/To-Do splits are **remembered across sessions and restarts**.
- **🛡️ Subscription-safe — never bills your API account** — ClaudeView runs on your Claude **subscription**, full stop. Even if your machine has an `ANTHROPIC_API_KEY` (or a Bedrock/Vertex/base-URL override) set for other tools, ClaudeView **strips it from every process it launches** so the CLI can *only* use your subscription — it can never silently drain pay-per-token API credits. If you aren't signed in, it asks you to log in instead of quietly spending money, and it shows a one-time notice whenever it detects and ignores a key.
- **🛟 Resilient** — if the underlying CLI ever crashes mid-turn, ClaudeView explains what happened in plain language (not a raw stack trace) and **resumes your conversation on the very next message** instead of hanging or losing it. It also **sizes the CLI's memory to your machine** so long, heavy sessions have the headroom to keep going instead of running out and crashing.
- **♻️ Auto-updating** — self-installs to `%LOCALAPPDATA%`, then updates from GitHub Releases (download → **verify SHA-256** → swap on next launch).

<div align="center">

|  Dark mode  |  Tray usage meter  |
| :---------: | :----------------: |
| ![ClaudeView — dark](docs/screenshot-dark.png) | ![ClaudeView tray popup](docs/tray.png) |

</div>

<div align="center">

**🛰️ Drive every session from your phone** — type **`/remote`** to list the sessions running on that
computer, then **connect** (bridge) or **disconnect** any of them from anywhere.

<img src="docs/remote-control.jpg" width="360" alt="ClaudeView Remote Control — bridging another session from a phone"/>

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
you). ClaudeView always uses that **subscription** — never a pay-per-token API account, even if you
have an `ANTHROPIC_API_KEY` set on your machine. The WebView2 runtime ships with modern Windows/Edge.

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
