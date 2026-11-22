# Paper Crane AR: scan the picture, watch the folding video

Point your phone at the printed crane card ([`target.png`](target.png), the pink crane). When it is recognised, the paper-crane folding video
([ONLY-CRANE](https://github.com/naomirajwanshi02/ONLY-CRANE)) plays right on the card in AR. Bottom bar: **play / pause**, **back 10 s**,
**forward 10 s** and a seek bar. If the card leaves the view, the video floats over the camera so you keep your place.
Desktop keys: Space = play/pause, ← / → = ∓10 s.

**Play locally:** `powershell -ExecutionPolicy Bypass -File tools/serve.ps1` then `http://localhost:8142/`
· **Without the card:** `?demo=1` · **Without any camera:** `?preview=1` · **Other video:** `?video=<url>`

| File | What it is |
|---|---|
| `index.html`, `js/app.js` | The flow: camera permission → scan → note → watch |
| `js/scan.js` | MindAR image tracking; draws the `<video>` as a three.js plane glued to the card |
| `js/player.js` | Play/pause, ±10 s, seek bar (drives the same `<video>`) |
| `js/data.js` | Video URL (ONLY-CRANE on GitHub Pages) and the bundled fallback |
| `assets/paper-crane-720.mp4` | Fallback copy of the video (used if the Pages link is unreachable) |
| `target.png` / `targets.mind` | The printable card and its compiled MindAR target |
| `tools/make-target.html`, `tools/serve.ps1` | Draw the card + compile the target (`?build=1`); local server with Range support |

**Rebuild the card/target:** start `tools/serve.ps1`, open `http://localhost:8142/tools/make-target.html?build=1` in desktop Chrome and wait for `DONE`.

Look: [Anatomy](https://github.com/wheresryan22/anatomy) sepia theme (`vendor/anatomy/`, skill in `../.claude/skills/anatomy`).
Pins: `mind-ar@1.2.5` with `three@0.160.0`. Phones need HTTPS (e.g. GitHub Pages) for the camera.
