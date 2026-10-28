# elstar

**Drive, inspect and hot-reload your iOS app in the simulator — from your terminal or your AI agent.**

One compiled binary. No SDK to embed, no proxy certificates, no app that has to stay open. Works on any app you can run in the simulator.

> This repository hosts **releases and the issue tracker**. Website and docs: [elstar.dev](https://elstar.dev) · What's new: [Releases](../../releases)

## Install

```bash
brew install elstar-dev/elstar/elstar
```

or without Homebrew:

```bash
curl -fsSL https://elstar.dev/install.sh | bash
```

Requires Xcode 27.1 or later (macOS 26.6+).

Your first command starts a free 7-day trial — no signup, no card, internet needed once. When it ends, run `elstar license activate <key>`.

## Quick start

Build and run your app from Xcode on a simulator, then:

```bash
elstar state                      # app, screen size, tappable elements and a screenshot in one call
elstar tap "Sign In" --wait       # tap by label, waiting for it to appear
elstar type "hi@example.com"      # type into the focused field
elstar hot Sources/HomeView.swift # hot-reload a file into the running app
elstar net                        # the app's HTTPS traffic, no proxy or certificates
```

## For AI agents

```bash
elstar mcp install       # add elstar's 40 tools to this project for Claude Code
elstar skills install    # skills: ios-setup, ios-test, ios-audit, ios-debug
elstar hook install --all  # hot-reload and accessibility checks after every agent edit
```

Any MCP client can run `elstar mcp` directly. Every command takes `--json`, and `state` returns everything an agent needs in one round trip.

## What it does

- **Hot reload** — SwiftUI views, UIKit view controllers, final Swift classes, XIBs and assets, without rebuilding or relaunching.
- **Network** — capture the app's HTTPS traffic, export it as HAR, and mock endpoints.
- **Runtime** — evaluate Swift or Objective-C in the running app, inspect the view hierarchy and live values.
- **UI automation** — tap, swipe, drag, type, hardware buttons, `wait` and `assert`; generate XCUITest code from the screen.
- **Simulator control** — boot, install, launch, permissions, push notifications, location, appearance.

`elstar --help` lists every command.

## Reporting issues

Open an [issue](../../issues) or run `elstar feedback`. For a crash or wrong behaviour, attach `elstar diagnose --out bug.txt`, and read it before sharing.

## License

Commercial software: a free 7-day trial, then $69/year for one developer on two machines. See [elstar.dev](https://elstar.dev#pricing).
