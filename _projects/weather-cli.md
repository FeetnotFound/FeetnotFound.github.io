---
title: "weather-cli"
summary: "A terminal weather forecaster that reads your shell theme and matches its output colors to it."
status: "Shipped"
date: 2025-11-02
stack: [Rust, clap, ratatui]
tags: [cli, rust, terminal]
repo: https://github.com/yourname/weather-cli
demo:
---

## What it does

`weather-cli` is a small command-line tool that fetches a forecast and
renders it as an ANSI weather panel directly in the terminal, matching
whatever color scheme the user's shell is already using.

## Why I built it

I wanted a weather check that didn't require opening a browser tab, and
I wanted an excuse to learn `ratatui` for terminal UI rendering in Rust.

## How it works

- Pulls a forecast from a public weather API
- Detects the terminal's background/foreground colors
- Renders a compact panel with `ratatui`, falling back to plain text
  when piped to a file

```bash
cargo install weather-cli
weather-cli --city "Reno"
```

## Notes

The trickiest part was color detection across different terminal
emulators — iTerm2, Alacritty, and Windows Terminal all report their
theme differently, so there's a small compatibility shim for each.
