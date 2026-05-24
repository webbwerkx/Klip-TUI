<div align="center">

                                           
```                                           
██ ▄█▀ ██     ██ █████▄   ██████ ██  ██ ██ 
████   ██     ██ ██▄▄█▀ ▄▄▄ ██   ██  ██ ██
██ ▀█▄ ██████ ██ ██         ██   ▀████▀ ██
 
```                                           

**A terminal-first UI for Klipper 3D printers via Moonraker**

A clean, keyboard-driven dashboard for monitoring and controlling your printer from the command line.

</div>

---

## What it does

KLIP-TUI gives you a simple terminal interface for interacting with a Klipper-powered printer through Moonraker. It is designed to be fast, lightweight, and easy to navigate without leaving your shell.

## Features

- Dashboard view for quick printer status
- Console view for command-driven interaction
- Keyboard-first navigation
- Emergency stop support
- Simple, minimal setup

## Setup

Install dependencies with:

```bash
uv sync
```

## Configuration

Open `src/klippertui/config.py` and set `MOONRAKER_URL` to your printer's Moonraker endpoint.

Example:

```python
MOONRAKER_URL = "http://192.168.1.50:7125"
```

## Run

Start the application with:

```bash
uv run klippertui
```

## Keybinds

| Key | Action |
| --- | --- |
| `D` | Dashboard |
| `C` | Console |
| `ESC` | Back to home |
| `E` | Emergency stop |
| `Q` | Quit |

## Notes

- Make sure your printer is powered on and reachable on the network before launching the app.
- If the connection fails, verify the Moonraker IP address and port.

## Project goal

This project aims to provide a polished terminal interface for Klipper users who want a fast, reliable, and pleasant workflow inside the terminal.

---

<div align="center">

Built for Klipper • Powered by Moonraker

</div>
