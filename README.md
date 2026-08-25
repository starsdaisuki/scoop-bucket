# scoop-bucket

A personal [Scoop](https://scoop.sh) bucket.

```powershell
scoop bucket add stars https://github.com/starsdaisuki/scoop-bucket
scoop install stars/starpaper
```

---

## StarPaper

**Turn a local video into a Windows live wallpaper.** A lightweight alternative to
Lively Wallpaper — written from scratch in C++17 + Win32 + Direct3D 11 + Media Foundation,
shipped as **one 3.2 MB exe** that needs no runtime at all.

### Features

- **Fills the whole screen by default** — scales up and crops the overflow, so a 16:9 video
  on a 16:10 display shows no black bars
- **Manual framing** — drag the frame right on the preview, scroll to zoom, the desktop
  follows live
- **15 colour controls** on a custom D3D11 shader: exposure, brightness, contrast,
  highlights, shadows, gamma, saturation, vibrance, temperature, tint, blur, sharpen,
  vignette, vignette radius, dim
- **Video library** — keep your wallpapers in one place and click a thumbnail to switch
- **Auto-advance** — on end or on a timer, optionally shuffled
- **Day / night schedule** — two videos swapped by time of day, midnight-crossing supported
- **Four independent pause rules** — when covered by a window, on lock screen, on battery,
  in system power-saving mode
- **One window per display**, each with its own playback and its own resolution; topology
  changes (new monitor, projector, resolution switch) rebuild automatically
- Settings window with **dark / light theme** and **English / 中文**
- Loops mp4, mov, mkv, avi, wmv with hardware decoding
- Mute toggle and volume slider; only the primary display outputs sound
- Mouse events pass through — desktop right-click and double-click still work
- Runs from the tray; optional launch at login
- Settings live in `HKCU\Software\StarPaper`. **No files are written anywhere.**

### Why not just strip Lively down

Lively is good software, but it is a *general-purpose wallpaper platform*: 17 projects,
~48k lines, four separate player processes (CefSharp, WebView2, VLC, WMF), gRPC IPC,
a WinUI 3 interface, depth-map AI, Steam Workshop import, a screensaver mode, 40 languages.

Looping one mp4 is 191 lines of that. Cutting the rest away costs more than rewriting it:

| | Stripping Lively | Rewriting |
|---|---|---|
| Licence | GPL-3.0, derivatives stay GPL | **MIT, entirely my own** |
| .NET 9 desktop runtime | cannot be removed | **not needed** |
| Resident processes | Core + UI + Watchdog + Player | **1** |
| Native ARM64 | blocked upstream for two years | one `make arm64`, 2.4 s |
| Size | 100–200 MB | **3.2 MB** |

StarPaper shares no code with Lively and is not a fork of it.

### Builds

Both **x64** and **native ARM64** are published; Scoop picks the right one automatically.
Installing puts StarPaper in the Start menu, so Windows search finds it like any other app.

## License

Manifests in this repository are MIT. Each published archive carries its own `LICENSE`.
