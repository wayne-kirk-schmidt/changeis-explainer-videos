# GuruSuite Explainer Video Production Guide

**ChangeIS K.K. / changeis.io**
Version 1.0 — How we made these videos

---

## Overview

Each explainer video is built from three components:

1. **Audio** — AI voiceover generated in ElevenLabs
2. **Video** — Motion graphics built in Canva
3. **Compressed output** — Optimised MP4 for web and mobile

Total production time per video: approximately 45–60 minutes once the template is learned.

---

## Naming Convention

All files follow this pattern:

```
ChangeIS.<Product>.Audio.mp3       — voiceover audio
ChangeIS.<Product>.Explainer.Video.mp4  — final compressed video
<Product>.Logo.png                 — product icon
```

Example:
```
ChangeIS.Maestro.Audio.mp3
ChangeIS.Maestro.Explainer.Video.mp4
Maestro.Logo.png
```

---

## Folder Structure

Each product lives in its own folder:

```
/ProductName/
  ChangeIS.ProductName.Audio.mp3
  ChangeIS.ProductName.Explainer.Video.mp4
  ProductName.Logo.png
  ChangeIS_ProductName.pdf
```

Shared assets live in:
```
/Logos/
  ChangeIS.Background.png   — node network background used in all videos
  ChangeIS.Logo.png         — main ChangeIS logo
  ChangeIS.Small.Logo.png   — small logo for video closing scene

/Products/
  GuruSuite_Video_Scripts.docx   — all 9 scripts
  GuruSuite_Video_Scripts.pdf
```

---

## Step 1 — Audio Production (ElevenLabs)

### Tool
**ElevenLabs** — https://elevenlabs.io
Free tier is sufficient for all 9 videos.

### Voice Settings
| Setting | Value |
|---|---|
| Voice | Adam — Engaging, Friendly and Bright |
| Model | Eleven v3 |
| Stability | 100 (Robust) |
| Similarity | 100 (High) |
| Output Format | MP3 44.1 kHz 128kbps |

### Process
1. Go to **Text to Speech** in the left sidebar
2. Paste the clean script for the product (see Scripts section below)
3. Confirm voice is set to **Adam** and model is **Eleven v3**
4. Click **Generate**
5. Listen to the output — check it feels warm and confident, not rushed
6. If happy, click the **download icon** on the generation
7. Save as `ChangeIS.<Product>.Audio.mp3`

### Tips
- Each script runs approximately 23–26 seconds at Adam's natural pace
- The paragraph breaks in the script create natural breathing pauses
- Do not adjust speed — Adam's default pace is correct for this content

---

## Step 2 — Video Production (Canva)

### Tool
**Canva** — https://canva.com
Free tier works. Note: free tier adds a watermark on video export.
One month of Canva Pro (~$15) removes the watermark.

### Template Structure
Every video uses the same 3-scene structure:

| Scene | Duration | Beat | Content |
|---|---|---|---|
| Scene 1 | 8 seconds | Imagine | Opening hook |
| Scene 2 | 9 seconds | Here is how | Product explanation |
| Scene 3 | 7 seconds | Your future | Product name + closing |

Total: 24 seconds (matches audio length)

### Background
Use `ChangeIS.Background.png` (node network image) on all three scenes.
- Drag from Uploads onto each scene
- Right-click and select **Send to back**

### Scene 1 — "Imagine"
| Element | Size | Position |
|---|---|---|
| "IMAGINE" | ~100pt, white, bold | Upper third, centred |
| Body sentence | ~36pt, white | Middle, centred |
| Three punchy closing lines | ~44pt, white, stacked | Below middle, centred |

### Scene 2 — "Here is how"
| Element | Size | Position |
|---|---|---|
| Product name (e.g. "MAESTRO") | ~70pt, white, bold | Upper third, centred |
| Body paragraph | ~36pt, white | Middle, centred |
| Two closing lines | ~44pt, white, stacked | Below middle, centred |

### Scene 3 — "Your future"
| Element | Size | Position |
|---|---|---|
| Product icon | ~180–200px wide | Upper third, centred |
| "Testing wisdom that grows with you. / See what your team can do." | ~36pt, white | Middle, centred |
| "Amplify Success." / "Amplify You." | ~44pt, white, stacked | Below middle |
| ChangeIS logo | ~80px wide | Bottom, centred |
| "ChangeIS. Because Change... Is." | ~24pt, white | Bottom, next to logo |

### Adding Audio
1. Click **Add audio** in the timeline
2. Upload the ElevenLabs MP3
3. Drag it into the timeline — it sits below the video clips
4. The audio waveform should span all three scenes

### Transitions
Use **Dissolve** between all scenes. Smooth, not flashy.
- Click the transition gap between scenes in the timeline
- Select Dissolve

### Export
1. Click **Share** top right
2. Select **Download**
3. Choose **MP4 Video**
4. Wait 30–60 seconds for render
5. Save the file

---

## Step 3 — Compression

### Tool
**FFmpeg** — command line, free, cross-platform

### Why compress?
Canva exports at ~7000kbps — approximately 28MB for a 33-second video.
After compression: approximately 6–7MB. Same visual quality on mobile.

### Command
```bash
ffmpeg -i InputVideo.mp4 \
  -c:v libx264 \
  -b:v 2000k \
  -maxrate 2500k \
  -bufsize 4000k \
  -c:a aac \
  -b:a 128k \
  -movflags +faststart \
  -y ChangeIS.ProductName.Explainer.Video.mp4
```

### The `-faststart` flag
This moves metadata to the front of the file so videos begin playing immediately on web without waiting to fully download. Important for mobile viewers.

### Expected results
| Metric | Before | After |
|---|---|---|
| File size | ~28MB | ~6–7MB |
| Duration | 33 sec | 33 sec |
| Visual quality | High | High (no visible loss) |
| Web playback | Buffered | Instant start |

---

## The 3-Beat Script Structure

Every script follows this pattern:

**Beat 1 — Imagine (0–8 sec)**
Opens with hope. "Imagine..." followed by the better world this product enables.
Never starts with a problem. Always starts with the possibility.

**Beat 2 — Here is how (8–17 sec)**
Introduces the product by name. Explains what it does in one or two sentences.
The "living library" concept lands naturally here.

**Beat 3 — Your future (17–26 sec)**
Product name. Tagline. Call to action. Closing brand lockup.
Short. Calm. Confident.

---

## Brand Principles

**Tone:** Trustworthy, warm, genuinely excited. Not corporate. Not startup hype.

**Always hope, never fear.**
Fear makes people freeze. Greed makes people chase the wrong thing. Hope makes people lean in, believe, and act.

**Person in the middle.**
The product never replaces the person. It amplifies them.

**The living library.**
Every product builds a library, journal, and newspaper of institutional knowledge that grows smarter over time.

---

## Voice Direction for ElevenLabs

Paste this as a note when setting up the voice:

> Warm, confident, and genuine. Speaks like a trusted colleague who is genuinely excited about something helpful. Not a TV announcer. Not corporate. Measured pace with natural pauses. Slight upward energy on aspirational phrases. Calm and reassuring on closing lines.

---

## Products

| Product | Tagline | Audience word | Colour |
|---|---|---|---|
| Maestro | Testing wisdom | team | Blue-purple |
| Weavr | Knowledge wisdom | organization | Purple |
| Pulse | Monitoring wisdom | team | Orange-red |
| Vigil | Event wisdom | team | Amber |
| Relay | Delivery wisdom | team | Purple-blue |
| Galen | Advisory wisdom | organization | Gold |
| Nexa | DevOps wisdom | team | Blue |
| Haven | Security wisdom | people | Teal |
| Fluid | Collaboration wisdom | team | Teal-cyan |

---

## Colour Scheme — One Word, One Identity

Each video uses a single colour accent to carry the product identity.
Everything else stays white on the dark node network background.

**The rule:** The word "IMAGINE" in Beat 1 Scene 1 is coloured in the product's primary colour.
All other text remains white. One word. Instantly recognisable. Subtly consistent.

Over time viewers subconsciously map each colour to its product — without ever being told.

### Product Colour Reference

| Product | Hex Code | Colour Name |
|---|---|---|
| Maestro | #7B6FDD | Blue-purple |
| Weavr | #7F77DD | Soft purple |
| Pulse | #E85D24 | Orange-red |
| Vigil | #BA7517 | Amber |
| Relay | #5B6FDD | Periwinkle blue |
| Galen | #EF9F27 | Gold |
| Nexa | #378ADD | Sky blue |
| Haven | #0F6E56 | Deep teal |
| Fluid | #5DCAA5 | Teal-cyan |

### How to apply in Canva
1. Click on the "IMAGINE" text box in Scene 1
2. Select all the text
3. Click the colour picker in the top toolbar
4. Enter the hex code for that product
5. Done — everything else stays white

### Optional — extend the accent colour
If you want to go further, the same product colour can also be applied to:
- The product name text in Beat 2 (e.g. "MAESTRO" in blue-purple)
- A subtle coloured line or divider between text blocks
- The tagline in Beat 3 ("Testing wisdom that grows with you.")

Keep it to one or two elements maximum. Restraint is the point.
The dark background does the heavy lifting — the colour just signs the work.

---

## Closing Line (every video)

> Amplify success. Amplify you.
> ChangeIS. Because Change... Is.

---

*GuruSuite — Outcomes that Matter*
*© 2025 ChangeIS K.K.*
