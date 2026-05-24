<div align="center">

   ```
                     ██╗  ██╗██╗     ██╗██████╗       ████████╗██╗   ██╗██╗
                     ██║ ██╔╝██║     ██║██╔══██╗      ╚══██╔══╝██║   ██║██║
                     █████╔╝ ██║     ██║██████╔╝         ██║   ██║   ██║██║
                     ██╔═██╗ ██║     ██║██╔═══╝          ██║   ██║   ██║██║
                     ██║  ██╗███████╗██║██║              ██║   ╚██████╔╝██║
                     ╚═╝  ╚═╝╚══════╝╚═╝╚═╝              ╚═╝    ╚═════╝ ╚═╝
```

**Terminal 3D Printer Control**

A full-featured TUI for Klipper / Moonraker — live in your terminal, no browser needed.

[![Python](https://img.shields.io/badge/Python-3.11+-3776ab?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Textual](https://img.shields.io/badge/Textual-0.80+-000000?style=flat-square&logo=python&logoColor=white)](https://github.com/Textualize/textual)
[![Moonraker](https://img.shields.io/badge/Moonraker-API-orange?style=flat-square)](https://github.com/Arksine/moonraker)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

</div>

---

## What is klip-tui?

`klip-tui` is a keyboard-driven terminal interface for your Klipper 3D printer. SSH into your Pi, run `klippertui`, and you have full control — temperatures, print status, GCode console, file management, bed mesh, job queue, and more — all without leaving the terminal.

---

## Features

<table>
<tr>
<td width="50%">

### 🖥️ Dashboard
Live temperatures, print progress, toolhead position, extruder controls, macros, and machine commands — all on one screen.

### 💻 GCode Console
Full terminal with timestamped output, command history (↑↓), and instant feedback on every command sent.

### 📂 Files
Browse your gcode library and start a print in two keystrokes.

### 🔧 Machine
File browser + in-app editor for your printer's config files. Create, edit, and delete without leaving the TUI.

### 📜 History
Complete print job log with status, duration, and totals. Delete old records in-place.

</td>
<td width="50%">

### 🗂️ Job Queue
Queue up prints, reorder jobs, start and pause the queue — all from the keyboard.

### ⚡ Power
Toggle Moonraker power devices (relays, smart plugs) on and off.

### 📐 Bed Mesh
Color-coded ASCII visualization of your active mesh profile. Trigger calibration or clear the mesh with one key.

### 🌡️ Temperature Presets
Save and apply hotend + bed temp combos instantly.

### 🎯 Exclude Objects
Exclude or re-include individual model objects during a running print.

### ⚙️ Settings
Change your Moonraker URL and poll interval from inside the app — no manual config editing required.

</td>
</tr>
</table>

---

## Requirements

- **Python** 3.11+
- **[uv](https://github.com/astral-sh/uv)** — fast Python package manager
- A running **[Moonraker](https://github.com/Arksine/moonraker)** instance (standard Klipper setup)

---

## Getting Started

**1. Clone the repo**
```bash
git clone https://github.com/yourname/klip-tui.git
cd klip-tui
```

**2. Install dependencies**
```bash
uv sync
```

**3. Point it at your printer**

Edit `src/klippertui/config.py`:
```python
MOONRAKER_URL = "http://192.168.1.100:7125"  # your printer's IP
POLL_INTERVAL = 2.0
```

> **Tip:** You can also change this from inside the app via the **Settings** screen (`S`) — it writes the config file for you.

**4. Launch**
```bash
uv run klippertui
```

---

## Keybinds

### Home Menu

| Key | Screen | Description |
|:---:|---|---|
| `D` | Dashboard | Temperatures, status & controls |
| `C` | Console | GCode terminal |
| `F` | Files | Browse & start prints |
| `A` | Machine | Edit config files |
| `H` | History | Print job log |
| `J` | Job Queue | Manage print queue |
| `P` | Power | Toggle power devices |
| `M` | Bed Mesh | Mesh visualization & calibration |
| `T` | Presets | Temperature presets |
| `X` | Exclude | Exclude print objects |
| `S` | Settings | Configure connection |
| `Q` | — | Quit |

### Universal

| Key | Action |
|:---:|---|
| `ESC` | Back / return home |
| `Q` | Quit from anywhere |
| `R` | Refresh current screen |

### Screen-Specific

| Screen | Key | Action |
|---|:---:|---|
| Dashboard | `E` | 🚨 Emergency stop |
| Console | `↑` / `↓` | Scroll command history |
| Console | `Ctrl+L` | Clear log |
| Machine | `Enter` | Open file / navigate directory |
| Machine | `E` | Edit selected file |
| Machine | `N` | New file |
| Machine | `D` | Delete selected file |
| History | `D` | Delete selected job |
| Job Queue | `A` | Add file to queue |
| Job Queue | `D` | Remove selected job |
| Bed Mesh | `C` | Run `BED_MESH_CALIBRATE` |

---

## Project Structure

```
src/klippertui/
├── main.py              # Entry point
├── app.py               # App root, Moonraker client, screen registration
├── config.py            # MOONRAKER_URL · POLL_INTERVAL
├── styles.tcss          # Global Textual CSS
│
├── screens/             # One module per screen
│   ├── home.py          # Navigation hub
│   ├── dashboard.py     # Main control panel
│   ├── console.py       # GCode terminal
│   ├── files.py         # File browser + print launcher
│   ├── machine.py       # Config file browser + editor
│   ├── history.py       # Print history
│   ├── queue.py         # Job queue manager
│   ├── power.py         # Power device control
│   ├── mesh.py          # Bed mesh viewer
│   ├── presets.py       # Temperature presets
│   ├── exclude.py       # Object exclusion
│   └── settings.py      # App settings
│
└── widgets/             # Reusable UI components
    ├── header_bar.py    # Connection status bar
    ├── temperatures.py  # Live temp display
    ├── print_status.py  # Progress + job info
    ├── toolhead.py      # Position + movement
    ├── extruder.py      # Extrusion controls
    ├── macros.py        # Macro buttons
    ├── machine.py       # Machine action buttons
    ├── bed_mesh.py      # Mesh widget
    ├── power_controls.py
    ├── temp_presets.py
    ├── file_editor.py   # In-app text editor
    └── miscellaneous.py
```

---

## Dependencies

| Package | Version | Purpose |
|---|---|---|
| [`textual`](https://github.com/Textualize/textual) | `≥ 0.80` | TUI framework |
| [`httpx`](https://github.com/encode/httpx) | `≥ 0.27` | Async HTTP for Moonraker API |
| [`websockets`](https://github.com/python-websockets/websockets) | `≥ 12.0` | WebSocket support |

---

## License

MIT — see [LICENSE](LICENSE) for details.

<div align="center">

Made for the Klipper community &nbsp;·&nbsp; Built with [Textual](https://github.com/Textualize/textual)

</div>
