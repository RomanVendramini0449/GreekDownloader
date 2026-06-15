# GreekDownloader

Downloads a variety of content from the web, primarily YouTube videos.

A simple Qt desktop front-end for [yt-dlp](https://github.com/yt-dlp/yt-dlp), with a light/dark mode, a queue, per-item progress, and clear error messages.

![GreekDownloader screenshot](https://i.imgur.com/nkI327O.png)

![GreekDownloader screenshot](https://i.imgur.com/NHxqADA.png)

## Setup (important)

The app doesn't download anything by itself — it drives `yt-dlp`. Two small programs must sit in the **same folder as `GreekDownloader.exe`**:

1. **`yt-dlp.exe`** — the downloader. Get it from https://github.com/yt-dlp/yt-dlp/releases
2. **`ffmpeg.exe`** — merges separate video + audio streams (needed for "Best quality" and MP3). Get the "essentials" build from https://www.gyan.dev/ffmpeg/builds/

Without these, downloads won't run — the app will tell you `yt-dlp` is missing. Keep `yt-dlp` updated (`yt-dlp -U`), since YouTube changes often and an out-of-date copy is the usual cause of "unable to extract" errors.

## Features

- Paste multiple URLs (one per line) and download them as a queue.
- Quality presets: best, 1080p / 720p / 480p / 360p, or audio-only MP3.
- Per-item progress with status, speed, ETA, and size.
- Plain-English error messages with hints (missing ffmpeg, out-of-date yt-dlp, age-restricted video, network issues, etc.).
- Light and **dark mode** toggle, remembered between sessions.
- "Open download folder" link, plus double-click a finished row to open its folder or a failed row to see the full error.
- Cancelling a download cleans up the leftover `.part` files.
- Remembers your save folder and format choice.

## Building

Requires Qt 6 (or Qt 5) with the Widgets and Network modules.

```bash
cmake -B build
cmake --build build
```

On Windows with MinGW:

```bat
cmake -B build -G "MinGW Makefiles" -DCMAKE_BUILD_TYPE=Release
cmake --build build
windeployqt --release build\GreekDownloader.exe
```

Then drop `yt-dlp.exe` and `ffmpeg.exe` into the `build` folder next to `GreekDownloader.exe`.
