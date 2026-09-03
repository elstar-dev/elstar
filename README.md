# elstar

**Everything you can't do with Xcode alone, from your terminal. Or let your AI agent do it.**

elstar is a single compiled binary for iOS simulator development: drive a live app, inspect its UI and network traffic, hot-reload Swift without rebuilding, and evaluate code in the running process — from your shell, your CI, or an AI agent over MCP.

No SDK to embed. No proxy certificates. No GUI app that has to stay open. Works on any app you can launch in the simulator.

> This repository hosts **releases, the issue tracker, and public documentation**. Website: [elstar.dev](https://elstar.dev) · What's new: [Releases](../../releases)

## Install

```bash
brew install elstar-dev/elstar/elstar
```

or without Homebrew:

```bash
curl -fsSL https://elstar.dev/install.sh | bash
```

Requires macOS 15 or later and Xcode 26 or later. A 7-day trial starts on first use — `elstar license activate <key>` to unlock.

## Quick start

```bash
elstar state                  # app info + screen size + elements + screenshot, one JSON call
elstar tap "Sign In" --wait   # tap by accessibility label, polling until it appears
elstar hot Sources/HomeView.swift   # hot-reload a SwiftUI/UIKit file into the running app
elstar net                    # live HTTPS traffic of the foreground app — no proxy, no certs
elstar eval 'UIApplication.shared.windows.count'   # run code in the live process
```

## For AI agents

```bash
elstar mcp install    # register the MCP server (32 tools) with your agent
elstar skills install # bundled skills: ios-setup, ios-test, ios-audit, ios-debug
elstar hook install   # Claude Code hook: hot-reload on edit; --a11y adds an accessibility audit
```

Every command supports `--json` with structured errors, `elements --compact` for token-efficient output, and `state` for a single-round-trip snapshot designed for agent loops. The MCP session pins itself to one simulator, so booting another never retargets your agent.

## What it does

- **Hot reload** — SwiftUI views, UIKit view controllers, pure-Swift classes, XIBs, and assets injected into the running app in about a second. No rebuild, no relaunch, no SDK.
- **Network** — capture and decrypt the foreground app's HTTPS traffic with zero setup; mock endpoints for testing.
- **Runtime** — evaluate Swift/ObjC expressions in the live process; walk the view hierarchy.
- **UI automation** — native tap/swipe/drag/type and hardware buttons via the simulator's own input path; generate XCUITest code from the live screen.
- **Inspection** — accessibility tree, view hierarchy, element queries by role/label, `wait`/`assert` for agent loops, screenshots, display topology.
- **Simulator control** — boot and shut down, install and launch, list devices and apps, set privacy permissions and location.

38 commands in the current release. Commands ship behind a stability gate and appear as they're verified on the current Xcode — `elstar --help` is the authoritative list.

## Reporting issues

Bug reports and feature requests are welcome in [Issues](../../issues), or run `elstar feedback` from the terminal. For crashes or misbehavior, attach the output of `elstar diagnose --out bug.txt` — it collects versions, device state, and recent logs (no source code or secrets).

## License

Commercial software with a free 7-day trial. One license covers one developer on two machines. See [elstar.dev](https://elstar.dev) for pricing.
