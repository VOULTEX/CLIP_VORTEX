# Clip Vortex ✂️ — long video → ready-to-post clips, in your browser

**Live site:** `https://<your-username>.github.io/clipvortex/` (after step 3 below)

Paste a YouTube link (or drop in a video) and Clip Vortex:

- finds the best moments (loud, lively, fast-talking parts, with hook words and questions)
- trims each clip so it starts and ends on a full sentence
- reframes it to **9:16** (Shorts / Reels / TikTok), **1:1**, **4:5** or **16:9**, using a crop you can slide toward the speaker or a fit over a blurred background
- adds **animated word-by-word captions** in your style, or none
- can cut out pauses (jump cuts) and add a progress bar
- gives you each clip + `.srt` subtitles + a ready post caption with hashtags, or everything as one ZIP

You choose **how many clips**, **how long**, and **with or without captions**: font, size, colors, outline, background box, position, words on screen, UPPERCASE, word highlight and animation.

**The editing runs entirely inside your browser tab: no API keys, no accounts, and your video is never uploaded anywhere. YouTube links need a small free helper on your computer (see below).**

---

## Put it on your GitHub (3 steps)

1. Create a new repository on GitHub called `clipvortex` (Public).
2. Click **Add file → Upload files**, drag in **all files from this folder** (including `index.html`), then click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment* choose **Source: Deploy from a branch**, **Branch: `main` / `(root)`**, then **Save**.

After about a minute your site is live at `https://<your-username>.github.io/clipvortex/`.

---

## How to use

1. **Your video**: either
   - **Paste YouTube link**: paste a video link (`youtube.com/watch?v=…`, `youtu.be/…` or `/shorts/…`). A preview of the video appears right away, and Clip Vortex downloads it automatically when you click **Generate clips**. This needs the free **Clip Vortex Helper**; see below.
   - **Upload video file**: drop an MP4, MOV or WebM. This needs nothing else.
2. **Clips**: pick how many and how long.
3. **Captions**:
   - **Auto**: an AI speech model (Whisper) runs in your browser. The first time, it downloads about 80 MB, then it's cached. It supports Hindi, English and many more, and can translate captions to English.
   - **Subtitle file**: use an `.srt` / `.vtt` you already have.
4. **Format**: choose the aspect ratio and framing, then click **Generate clips**.

---

## 🔗 YouTube links: turn on the Clip Vortex Helper (one time, about 5 minutes)

A website can't download from YouTube by itself; browsers and YouTube block it. Free public "downloader APIs" are blocked by YouTube too. So Clip Vortex uses a small helper that runs **on your own computer** and downloads the video for the website.

**Windows**
1. Install **Python** from python.org (tick *"Add python.exe to PATH"*).
2. Open PowerShell and run:
   ```
   winget install Gyan.FFmpeg
   winget install DenoLand.Deno
   ```
   Then close PowerShell.
3. Open the `server-version` folder and **double-click `run.bat`**. Leave that black window open while you use the site. The first start installs things and takes a few minutes.
4. Open your Clip Vortex site. **⚙ Download settings** should say **"Helper connected ✓"**. If Chrome asks to allow access to devices on your local network, click **Allow**.

**Mac / Linux:** `brew install ffmpeg deno python` (Mac), then run `./run.sh` inside `server-version`.

Now just paste a link and click **Generate clips**. The helper downloads the video and the website makes the clips.

> **Alternative:** if you host your own **cobalt** downloader (for example the one-click Railway template), put its URL in ⚙ Download settings → *Cobalt downloader API*. Clip Vortex tries the Helper first, then cobalt.

---

### Good to know

- Clips are recorded in **real time** (a 30-second clip takes about 30 seconds). **Keep the tab open and visible** while it works.
- Best browsers are **Chrome or Edge** on a computer. They give MP4 (H.264) files that upload anywhere.
- Auto captions are fastest on browsers with WebGPU (recent Chrome / Edge).
- Very long or huge videos (over ~1.5 GB) can run out of memory. Pick 720p or 480p download quality for long podcasts.
- The YouTube link must be a single video, not a channel or playlist.

---

## `server-version/` (optional)

This folder is the **Clip Vortex Helper** that the website uses to download YouTube links. It is also a full app of its own at `http://localhost:8000`, which can take whole **channel** links and adds face-tracking. See `server-version/README.md`.

---

Only clip videos you own or have permission to repost. MIT licensed.
