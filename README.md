# Klip-TUI
A 3D Printer Klipper CLI/TUI for controlling your 3D Printer.

[settings_and_dashboard_mockup.html](https://github.com/user-attachments/files/26405473/settings_and_dashboard_mockup.html)
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: monospace; font-size: 12px; background: transparent; }
.screen { background: #0a0a0f; border: 1px solid #2a2a3a; margin-bottom: 20px; }
.hdr { background: #0d0d14; border-bottom: 1px solid #2a2a3a; padding: 6px 16px; display: flex; align-items: center; gap: 16px; color: #39d353; font-weight: bold; }
.hdr-mid { flex: 1; text-align: center; color: #39d353; }
.hdr-host { color: #3a3a4a; }
.hdr-div { color: #3a3a4a; }
/* Settings */
.s-title { color: #39d353; font-weight: bold; padding: 8px 16px; border-bottom: 1px solid #1a1a26; }
.s-body { padding: 8px 16px; }
.s-row { display: flex; gap: 12px; margin-bottom: 8px; }
.card { background: #1f1f2d; border: 1px solid #2a2a3a; flex: 1; }
.card-hdr { background: #12121a; border-bottom: 1px solid #2a2a3a; padding: 5px 12px; color: #39d353; font-weight: bold; }
.card-body { padding: 10px 12px; }
.kv { display: flex; gap: 0; margin-bottom: 4px; }
.kk { color: #5a5a6a; min-width: 80px; }
.vv { color: #e0e0e6; }
.badge-ok { color: #39d353; font-weight: bold; }
.badge-off { color: #e05050; }
.kbd-row { display: flex; align-items: center; gap: 10px; margin-bottom: 5px; }
.kbd { background: #39d353; color: #0a0a0f; font-weight: bold; padding: 1px 6px; min-width: 60px; text-align: center; font-size: 11px; }
.kdesc { color: #7a7a8a; font-size: 11px; }
.kdiv { color: #2a2a3a; font-size: 10px; margin: 6px 0 4px; }
/* Dashboard */
.dash { display: flex; height: 420px; }
.left { width: 190px; border-right: 1px solid #2a2a3a; background: #171722; display: flex; flex-direction: column; }
.center { flex: 1; background: #1a1a26; padding: 8px; }
.right { width: 160px; border-left: 1px solid #2a2a3a; background: #171722; }
.panel { background: #1f1f2d; border: 1px solid #2a2a3a; margin: 6px; }
.phdr { background: #12121a; border-bottom: 1px solid #2a2a3a; padding: 4px 10px; color: #39d353; font-weight: bold; font-size: 11px; }
.pbody { padding: 8px 10px; }
.temp-row { margin-bottom: 6px; }
.temp-name { color: #e0e0e6; font-weight: bold; }
.temp-val { color: #39d353; font-weight: bold; }
.temp-tgt { color: #7a7a8a; }
.bar-g { color: #39d353; letter-spacing: -1px; font-size: 10px; }
.bar-e { color: #2a2a3a; letter-spacing: -1px; font-size: 10px; }
.badge-ht { color: #f0a500; font-size: 10px; }
.sec-lbl { color: #5a5a6a; font-weight: bold; font-size: 10px; margin: 5px 0 3px 2px; }
.btn-row { display: flex; gap: 4px; margin-bottom: 4px; }
.btn { background: #12121a; border: 1px solid #2a2a3a; color: #e0e0e6; padding: 3px 6px; font-size: 10px; font-family: monospace; flex: 1; text-align: center; }
.btn-g { background: #121a12; border-color: #2a3a2a; color: #39d353; }
.btn-r { background: #1a1212; border-color: #3a1a1a; color: #e05050; }
.btn-a { background: #1a1508; border-color: #3a2a0a; color: #f0a500; }
.ps-hdr { background: #12121a; border-bottom: 1px solid #2a2a3a; padding: 4px 12px; color: #39d353; font-weight: bold; }
.ps-body { padding: 10px 14px; }
.fn { color: #e0e0e6; font-weight: bold; }
.st { color: #39d353; font-weight: bold; }
.ph { color: #39d353; font-weight: bold; font-size: 11px; margin: 6px 0 2px; }
.br { color: #39d353; letter-spacing: -1px; }
.be { color: #2a2a3a; letter-spacing: -1px; }
.rv { display: flex; gap: 0; margin-bottom: 2px; }
.rl { color: #5a5a6a; min-width: 68px; font-size: 11px; }
.rr { color: #e0e0e6; font-size: 11px; }
.mbtn { display: block; background: #12121a; border: 1px solid #2a2a3a; color: #e0e0e6; padding: 5px 10px; margin: 0 6px 4px; font-family: monospace; font-size: 11px; }
.footer { background: #12121a; border-top: 1px solid #2a2a3a; padding: 3px 12px; color: #5a5a6a; font-size: 10px; display: flex; gap: 16px; }
.fk { color: #39d353; }
</style>

<div style="font-family:monospace; font-size:12px; padding: 8px 0;">

<div style="color:#5a5a6a; font-size:10px; margin-bottom:6px; padding-left:4px;">SETTINGS SCREEN</div>
<div class="screen">
  <div class="hdr">
    <span style="color:#39d353;font-weight:bold;">✦ klip-tui</span>
    <span class="hdr-div">|</span>
    <span style="color:#e0e0e6;">My Printer</span>
    <span class="hdr-mid">● Ready</span>
    <span class="hdr-host">10.0.0.18:7125</span>
  </div>
  <div class="s-title">  Settings</div>
  <div class="s-body">
    <div class="s-row">
      <div class="card">
        <div class="card-hdr">  Connection</div>
        <div class="card-body">
          <div class="kv"><span class="kk">Host</span><span class="vv">10.0.0.18</span></div>
          <div class="kv"><span class="kk">Port</span><span class="vv">7125</span></div>
          <div class="kv"><span class="kk">TLS</span><span class="badge-off">○ Disabled</span></div>
          <div class="kv"><span class="kk">API Key</span><span class="badge-off">Not set</span></div>
        </div>
      </div>
      <div class="card">
        <div class="card-hdr">  Printer</div>
        <div class="card-body">
          <div class="kv"><span class="kk">Name</span><span class="vv">My Printer</span></div>
          <div class="kv"><span class="kk">Endpoint</span><span class="vv">10.0.0.18:7125</span></div>
          <div style="margin-top:8px;color:#5a5a6a;font-size:11px;">Edit via --host / --port CLI flags</div>
        </div>
      </div>
    </div>
    <div class="card" style="margin:0 0 8px 0;">
      <div class="card-hdr">  Keyboard Shortcuts</div>
      <div class="card-body" style="display:flex;gap:32px;">
        <div>
          <div class="kdiv">─── Navigation ──────────</div>
          <div class="kbd-row"><span class="kbd">1</span><span class="kdesc">Dashboard</span></div>
          <div class="kbd-row"><span class="kbd">2</span><span class="kdesc">Files</span></div>
          <div class="kbd-row"><span class="kbd">3</span><span class="kdesc">Settings</span></div>
          <div class="kdiv">─── Dashboard ───────────</div>
          <div class="kbd-row"><span class="kbd">`</span><span class="kdesc">Toggle console</span></div>
        </div>
        <div>
          <div class="kdiv">─── Printer ─────────────</div>
          <div class="kbd-row"><span class="kbd">E</span><span class="kdesc">Emergency stop</span></div>
          <div class="kbd-row"><span class="kbd">Ctrl+R</span><span class="kdesc">Reconnect</span></div>
          <div class="kdiv">─── App ─────────────────</div>
          <div class="kbd-row"><span class="kbd">Ctrl+C</span><span class="kdesc">Quit</span></div>
        </div>
      </div>
    </div>
  </div>
  <div class="footer"><span><span class="fk">1</span> Dashboard</span><span><span class="fk">2</span> Files</span><span><span class="fk">3</span> Settings</span><span><span class="fk">Ctrl+C</span> Quit</span></div>
</div>

<div style="color:#5a5a6a; font-size:10px; margin: 12px 0 6px 4px;">DASHBOARD — with corrected button colours</div>
<div class="screen">
  <div class="hdr">
    <span style="color:#39d353;font-weight:bold;">✦ klip-tui</span>
    <span class="hdr-div">|</span>
    <span style="color:#e0e0e6;">My Printer</span>
    <span class="hdr-mid">● Ready</span>
    <span class="hdr-host">10.0.0.18:7125</span>
  </div>
  <div class="dash">
    <div class="left">
      <div class="panel">
        <div class="phdr">  Temperatures</div>
        <div class="pbody">
          <div class="temp-row">
            <div><span class="temp-name">Extruder   </span><span class="temp-val">245.0°</span><span class="temp-tgt"> / 250°</span></div>
            <div><span class="bar-g">███████████████</span><span class="bar-e">░░░</span> <span class="temp-tgt">98%</span> <span style="color:#f0a500;font-size:10px;">ALMOST</span></div>
          </div>
          <div class="temp-row">
            <div><span class="temp-name">Bed        </span><span class="temp-val" style="color:#39d353;">60.0°</span><span class="temp-tgt"> / 60°</span></div>
            <div><span class="bar-g">██████████████████</span> <span class="temp-tgt">45%</span> <span style="color:#39d353;font-size:10px;">AT TEMP</span></div>
          </div>
          <div style="color:#2a2a3a;font-size:10px;margin:4px 0;">─────────────────────</div>
          <div><span style="color:#5a5a6a;">MCU Temp   </span><span style="color:#4aa8e8;font-weight:bold;"> 42.3°</span></div>
        </div>
      </div>
      <div class="panel" style="flex:1;">
        <div class="phdr">  Controls</div>
        <div class="pbody">
          <div class="sec-lbl">PRINTER</div>
          <div class="btn-row">
            <div class="btn btn-g">Home All</div>
            <div class="btn btn-r">⚠ E-Stop</div>
            <div class="btn btn-a">⏸ Pause</div>
          </div>
          <div class="sec-lbl">PART FAN</div>
          <div class="btn-row">
            <div class="btn">−10%</div><div class="btn">Fan Off</div><div class="btn">+10%</div>
          </div>
          <div class="sec-lbl">SPEED</div>
          <div class="btn-row">
            <div class="btn">−10%</div><div class="btn btn-g">Reset</div><div class="btn">+10%</div>
          </div>
          <div class="sec-lbl">FLOW</div>
          <div class="btn-row">
            <div class="btn">−5%</div><div class="btn btn-g">Reset</div><div class="btn">+5%</div>
          </div>
        </div>
      </div>
    </div>
    <div class="center">
      <div class="panel" style="height:100%;">
        <div class="ps-hdr">  Print Status</div>
        <div class="ps-body">
          <div class="fn">benchy_0.2mm_pla.gcode</div>
          <div style="margin-left:2px;margin-bottom:6px;"><span class="st">● PRINTING</span></div>
          <div class="ph">  Progress</div>
          <div style="margin:2px 0 6px;"><span class="br">████████████████████████</span><span class="be">░░░░░░░░░░</span> <span style="color:#39d353;font-weight:bold;">71.2%</span></div>
          <div class="ph">󱑋  Time</div>
          <div class="rv"><span class="rl">Elapsed    </span><span class="rr">1:22:14</span></div>
          <div class="rv"><span class="rl">Remaining  </span><span class="rr">0:32:06</span></div>
          <div class="rv"><span class="rl">ETA        </span><span class="rr">1:54:20</span></div>
          <div class="ph">󰆧  Toolhead</div>
          <div style="color:#e0e0e6;font-size:11px;margin-left:2px;"><span style="color:#5a5a6a;">X</span> 112.4  <span style="color:#5a5a6a;">Y</span>  88.1  <span style="color:#5a5a6a;">Z</span>  7.200</div>
        </div>
      </div>
    </div>
    <div class="right">
      <div class="panel" style="height:calc(100% - 12px);">
        <div class="phdr">  Macros</div>
        <div style="padding:6px 0;">
          <div class="mbtn">▸  CANCEL_PRINT</div>
          <div class="mbtn">▸  LOGO_BLUE</div>
          <div class="mbtn">▸  LOGO_GREEN</div>
          <div class="mbtn">▸  LOGO_LIME</div>
          <div class="mbtn">▸  LOGO_MAGENTA</div>
        </div>
      </div>
    </div>
  </div>
  <div class="footer"><span><span class="fk">1</span> Dashboard</span><span><span class="fk">2</span> Files</span><span><span class="fk">3</span> Settings</span><span><span class="fk">`</span> Console</span><span><span class="fk">Ctrl+C</span> Quit</span></div>
</div>

</div>
