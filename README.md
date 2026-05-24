<div align="center">

<pre>
<span style="color:#4DA3FF">

██╗  ██╗██╗     ██╗██████╗       ████████╗██╗   ██╗██╗
██║ ██╔╝██║     ██║██╔══██╗      ╚══██╔══╝██║   ██║██║
█████╔╝ ██║     ██║██████╔╝█████╗   ██║   ██║   ██║██║
██╔═██╗ ██║     ██║██╔═══╝ ╚════╝   ██║   ██║   ██║██║
██║  ██╗███████╗██║██║              ██║   ╚██████╔╝██║
╚═╝  ╚═╝╚══════╝╚═╝╚═╝              ╚═╝    ╚═════╝ ╚═╝

</span>
</pre>

# 🚀 KLIP-TUI

### A terminal-first dashboard for Klipper 3D printers

Fast. Minimal. Keyboard-driven.  
Built for controlling and monitoring Klipper printers through Moonraker directly from your terminal.

</div>

---

# ✨ Features

- 📊 Real-time printer dashboard
- ⌨️ Fully keyboard-driven interface
- 🖥️ Console mode for direct interaction
- 🚨 Emergency stop support
- ⚡ Lightweight and fast startup
- 🔌 Moonraker integration
- 🧭 Clean terminal UX designed for daily use

---

# 🖼️ Philosophy

KLIP-TUI is designed around a simple idea:

> Your terminal should be enough.

No heavy web UI.  
No unnecessary overhead.  
Just a fast and responsive interface that feels native inside the command line.

---

# 📦 Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/klip-tui.git
cd klip-tui
```

Install dependencies:

```bash
uv sync
```

---

# ⚙️ Configuration

Open:

```bash
src/klippertui/config.py
```

Set your Moonraker server address:

```python
MOONRAKER_URL = "http://192.168.1.50:7125"
```

Example:

```python
MOONRAKER_URL = "http://192.168.1.50:7125"
```

---

# ▶️ Running

Start KLIP-TUI:

```bash
uv run klippertui
```

---

# ⌨️ Keybinds

| Key | Action |
|------|---------|
| `D` | Open dashboard |
| `C` | Open console |
| `ESC` | Return home |
| `E` | Emergency stop |
| `Q` | Quit application |

---

# 🛰️ Requirements

- A Klipper-powered 3D printer
- Moonraker running and accessible on your network
- Python + `uv`

---

# 🛠️ Development Goals

KLIP-TUI aims to become a polished terminal experience for Klipper users by focusing on:

- Better real-time monitoring
- Improved websocket handling
- Rich terminal layouts
- Responsive TUI components
- Stable Moonraker communication
- Efficient keyboard workflows

---

# ⚠️ Notes

- Ensure your printer is powered on before launching KLIP-TUI.
- Verify your Moonraker IP and port if connection errors occur.
- Websocket connectivity is required for live printer updates.

---

<div align="center">

## Built for the terminal.

**Klipper × Moonraker × TUI**

</div>
