# elstar

**Everything you can't do with Xcode alone, from your terminal. Or let your AI agent do it.**

elstar is a single compiled binary for iOS simulator development: drive a live app, inspect its UI and network traffic, hot-reload Swift without rebuilding, and evaluate code in the running process — from your shell, your CI, or an AI agent over MCP.

No SDK to embed. No proxy certificates. No GUI app that has to stay open. Works on any app you can launch in the simulator.

> This repository hosts **releases, the issue tracker, and public documentation**. Website: [elstar.dev](https://elstar.dev)

## Install

```bash
brew install elstar-dev/elstar/elstar
```

or without Homebrew:

```bash
curl -fsSL https://elstar.dev/install.sh | bash
```

Requires macOS 15+ and Xcode. A 7-day trial starts on first use — `elstar license activate <key>` to unlock.

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
elstar mcp install    # register the MCP server with your agent
elstar skills install # bundled skills: ios-setup, ios-test, ios-audit, ios-debug, ios-perf
elstar hook install   # Claude Code hooks: hot-reload-on-edit, crash detection, a11y audit
```

Every command supports `--json` with structured errors, `elements --compact` for token-efficient output, and `state` for a single-round-trip snapshot designed for agent loops.

## What it does

- **Hot reload** — SwiftUI views, UIKit view controllers, pure-Swift classes, XIBs, and assets injected into the running app in about a second. No rebuild, no relaunch, no SDK.
- **Network** — capture and decrypt the foreground app's HTTPS traffic with zero setup; mock endpoints for testing.
- **Runtime** — evaluate Swift/ObjC expressions in the live process, dump classes and ivars, attach a persistent debug REPL.
- **UI automation** — native tap/swipe/drag/type via simulator HID; generate XCUITest code from recorded interactions.
- **Inspection** — accessibility tree, view hierarchy, element queries by role/label, screenshots.
- **Performance** — launch time, hitches, gauges, leaks — instrumented from the CLI, usable in CI.
- **Simulator control** — boot, install, launch, push notifications, permissions, privacy state, app data.

Full command reference: `elstar --help` or [elstar.dev](https://elstar.dev).

## Reporting issues

Bug reports and feature requests are welcome in [Issues](../../issues). For crashes or misbehavior, attach the output of `elstar diagnose --out bug.txt` — it collects versions, device state, and recent logs (no source code or secrets).

## License

Commercial software with a free 7-day trial. One license covers one developer on two machines. See [elstar.dev](https://elstar.dev) for pricing.
