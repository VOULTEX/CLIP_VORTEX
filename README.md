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

## ⚡ Turbo mode: the Clip Vortex Helper (strongly recommended)

The website works on its own (**browser mode**), but browsers are slow at video. They have to download the whole video and record clips in real time. For anything longer than a few minutes, start the free **Clip Vortex Helper** on your computer. The site detects it automatically and switches to **⚡ Turbo mode**:

| | Browser mode | ⚡ Turbo mode |
|---|---|---|
| YouTube links | – | ✅ video, **channel** and playlist links |
| Downloads the whole video | yes | **no**: it reads only the 30-second parts it needs, straight from YouTube |
| Finding the best moments | listens with AI in the browser | uses YouTube's **"Most replayed"** data and YouTube's **own captions** (instant even for 10 hours), with AI only as a backup |
| Making clips | real time, one by one | many at once, uses all CPU cores, plus your **graphics card's video encoder** if it has one |
| Face tracking | – | ✅ |
| Test result: **40 × 30 s clips from a 10-hour stream** | not realistic | **≈ 2–6 minutes** (on a 2-core test machine) |

Speed tips: choose **720p output** (about 2× faster) and **Speed: Fastest**. In Turbo mode you can switch to another tab while it works, and clips appear as soon as each one is ready.

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

**Linux (Ubuntu / Debian / Mint): one command.** Open a terminal in the `server-version` folder (right-click inside the folder → *Open in Terminal*) and run:
```
bash install-linux.sh
```
It installs everything, then starts the helper. If your Python is older than 3.11 (Ubuntu 22.04 has 3.10), it automatically fetches Python 3.12 just for Clip Vortex, without changing your system. Next time, just run `./run.sh` in that folder.

If apt shows errors about some *other* package (for example `rtbth-dkms`), that's a separate problem with your system. The script carries on as long as ffmpeg and Python got installed.

**Mac:** `brew install ffmpeg deno python`, then run `./run.sh` inside `server-version`.

While the helper runs you can also simply open **http://localhost:8000**. That's Clip Vortex served by the helper itself, already connected.

Now just paste a link and click **Generate clips**. The helper downloads the video and the website makes the clips.

> **Alternative:** if you host your own **cobalt** downloader (for example the one-click Railway template), put its URL in ⚙ Download settings → *Cobalt downloader API*. Clip Vortex tries the Helper first, then cobalt.

---

### Good to know

- Clips are recorded in **real time** (a 30-second clip takes about 30 seconds). **Keep the tab open and visible** while it works.
- Best browsers are **Chrome or Edge** on a computer. They give MP4 (H.264) files that upload anywhere.
- Auto captions use your graphics card (WebGPU) when the browser supports it, and otherwise switch to the CPU automatically. On the CPU, the "Listening to moment…" step takes longer, but it works.
- Very long or huge videos (over ~1.5 GB) can run out of memory. Pick 720p or 480p download quality for long podcasts.
- The YouTube link must be a single video, not a channel or playlist.

---

## `server-version/` (optional)

This folder is the **Clip Vortex Helper** that the website uses to download YouTube links. It is also a full app of its own at `http://localhost:8000`, which can take whole **channel** links and adds face-tracking. See `server-version/README.md`.

---

Only clip videos you own or have permission to repost. MIT licensed.
