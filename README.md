# Clip Vortex ✂️ — long video → ready-to-post clips, in your browser

**Live site:** `https://<your-username>.github.io/clipvortex/` (after step 3 below)

Drop in a video and Clip Vortex:

- finds the best moments (loud, lively, fast-talking parts, with hook words and questions)
- trims each clip so it starts and ends on a full sentence
- reframes it to **9:16** (Shorts / Reels / TikTok), **1:1**, **4:5** or **16:9**, using a crop you can slide toward the speaker or a fit over a blurred background
- adds **animated word-by-word captions** in your style, or none
- can cut out pauses (jump cuts) and add a progress bar
- gives you each clip + `.srt` subtitles + a ready post caption with hashtags, or everything as one ZIP

You choose **how many clips**, **how long**, and **with or without captions**: font, size, colors, outline, background box, position, words on screen, UPPERCASE, word highlight and animation.

**Everything runs inside the browser tab. No server, no install, no API keys, and your video is never uploaded.**

---

## Put it on your GitHub (3 steps)

1. Create a new repository on GitHub called `clipvortex` (Public).
2. Click **Add file → Upload files**, drag in **all files from this folder** (including `index.html`), then click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment* choose **Source: Deploy from a branch**, **Branch: `main` / `(root)`**, then **Save**.

After about a minute your site is live at `https://<your-username>.github.io/clipvortex/`.

---

## How to use

1. **Your video:** drop an MP4, MOV or WebM file.
   *Using a YouTube video?* Browsers can't download from YouTube directly, so download the file first. For your own channel: YouTube Studio → Content → ⋮ → **Download**.
2. **Clips:** pick how many and how long.
3. **Captions:**
   - **Auto:** an AI speech model (Whisper) runs in your browser. The first time, it downloads about 80 MB, then it's cached. It supports Hindi, English and many more languages, and can translate the captions to English.
   - **Subtitle file:** use an `.srt` / `.vtt` you already have (e.g. from YouTube Studio → Subtitles). This is faster.
4. **Format:** choose the aspect ratio and framing, then click **Generate clips**.

### Good to know

- Clips are recorded in **real time**: a 30-second clip takes about 30 seconds. **Keep the tab open and visible** while it works.
- Best browsers are **Chrome or Edge** on a computer. They give MP4 (H.264) files that upload anywhere. Firefox makes WebM files.
- Auto captions are fastest on browsers with WebGPU (recent Chrome / Edge).
- Very long or huge files (over ~1.5 GB) can run out of memory. Trim the video or use a 720p copy.

---

## `server-version/` (optional)

This is the Python version, which **can take YouTube channel links directly** and adds face-tracking. It must run on your own computer (double-click `run.bat`). See `server-version/README.md`. You don't need it for the website.

---

Only clip videos you own or have permission to repost. MIT licensed.
