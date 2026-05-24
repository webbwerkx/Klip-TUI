A terminal UI for controlling Klipper 3D printers via Moonraker — no browser required.


 ██╗  ██╗██╗     ██╗██████╗       ████████╗██╗   ██╗██╗
 ██║ ██╔╝██║     ██║██╔══██╗      ╚══██╔══╝██║   ██║██║
 █████╔╝ ██║     ██║██████╔╝         ██║   ██║   ██║██║
 ██╔═██╗ ██║     ██║██╔═══╝          ██║   ██║   ██║██║
 ██║  ██╗███████╗██║██║              ██║   ╚██████╔╝██║
 ╚═╝  ╚═╝╚══════╝╚═╝╚═╝             ╚═╝    ╚═════╝ ╚═╝


Built with [Textual](https://github.com/Textualize/textual). Connects to your printer's Moonraker API over HTTP/WebSocket.

---

## Features

| Screen | What it does |
|---|---|
| **Dashboard** | Temperatures, print status, toolhead position, extruder, macros, machine controls |
| **Console** | GCode terminal with command history and timestamped output log |
| **Files** | Browse and start gcode files |
| **Machine** | Full file browser and editor for printer config files (create, edit, delete) |
| **History** | Print job log with completion stats and delete support |
| **Job Queue** | Add, remove, start, and pause the print queue |
| **Power** | Toggle Moonraker power devices on/off |
| **Bed Mesh** | Color-coded ASCII visualization of the active mesh, calibrate and clear |
| **Presets** | One-key application of saved hotend + bed temperature combos |
| **Exclude Objects** | Exclude or re-include individual objects mid-print |
| **Settings** | Configure Moonraker URL and poll interval from inside the UI |

---

## Requirements

- Python 3.11+
- [uv](https://github.com/astral-sh/uv)
- A running [Moonraker](https://github.com/Arksine/moonraker) instance

---

## Installation

```bash
git clone https://github.com/yourname/klip-tui.git
cd klip-tui
uv sync
```

---

## Configuration

Edit `src/klippertui/config.py` and point `MOONRAKER_URL` at your printer:

```python
MOONRAKER_URL = "http://192.168.1.100:7125"
POLL_INTERVAL = 2.0
```

You can also change these from inside the app via the **Settings** screen (`S`), which writes the file for you.

---

## Running

```bash
uv run klippertui
```

---

## Keybinds

### Global (Home screen)

| Key | Action |
|---|---|
| `D` | Dashboard |
| `C` | Console |
| `F` | Files |
| `A` | Machine |
| `H` | History |
| `J` | Job Queue |
| `P` | Power |
| `M` | Bed Mesh |
| `T` | Presets |
| `X` | Exclude Objects |
| `S` | Settings |
| `Q` | Quit |

### In any screen

| Key | Action |
|---|---|
| `ESC` | Back to previous screen |
| `Q` | Quit |
| `R` | Refresh (where applicable) |

### Dashboard

| Key | Action |
|---|---|
| `E` | Emergency stop |

### Console

| Key | Action |
|---|---|
| `Enter` | Send GCode command |
| `↑` / `↓` | Navigate command history (last 100 commands) |
| `Ctrl+L` | Clear the log |

### Machine

| Key | Action |
|---|---|
| `Enter` | Open file or directory |
| `E` | Edit selected file |
| `N` | New file |
| `D` | Delete selected file |

### History

| Key | Action |
|---|---|
| `D` | Delete selected job |

### Job Queue

| Key | Action |
|---|---|
| `A` | Add file to queue |
| `D` | Remove selected job |

### Bed Mesh

| Key | Action |
|---|---|
| `C` | Run `BED_MESH_CALIBRATE` |

---

## Project Structure

```
src/klippertui/
├── main.py          # Entry point
├── app.py           # Textual app, Moonraker client, screen registration
├── config.py        # MOONRAKER_URL and POLL_INTERVAL
├── styles.tcss      # Textual CSS styles
├── screens/         # One file per screen
│   ├── home.py
│   ├── dashboard.py
│   ├── console.py
│   ├── files.py
│   ├── machine.py
│   ├── history.py
│   ├── queue.py
│   ├── power.py
│   ├── mesh.py
│   ├── presets.py
│   ├── exclude.py
│   └── settings.py
└── widgets/         # Reusable UI components
    ├── header_bar.py
    ├── temperatures.py
    ├── print_status.py
    ├── toolhead.py
    ├── extruder.py
    ├── macros.py
    ├── machine.py
    ├── bed_mesh.py
    ├── power_controls.py
    ├── temp_presets.py
    ├── file_editor.py
    └── miscellaneous.py
```

---

## Dependencies

| Package | Purpose |
|---|---|
| `textual >= 0.80.0` | TUI framework |
| `httpx >= 0.27.0` | Async HTTP client for Moonraker API |
| `websockets >= 12.0` | WebSocket support |

---

## License

MIT

