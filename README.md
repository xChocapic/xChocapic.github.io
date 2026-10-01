# xchocapic.github.io

Personal site of Alex Matei. Plain HTML + one CSS file, no build step, no JavaScript.
Served by GitHub Pages from `main`.

## Work on it

```sh
git clone https://github.com/xChocapic/xChocapic.github.io.git
cd xChocapic.github.io
python3 -m http.server 8000   # open http://localhost:8000
```

Edit, commit, push. Pages redeploys within a minute.

## Layout

```
index.html            bio, project list, work, education, skills
projects/*.html       one page per project, same layout
style.css             the only stylesheet
media/<project>/      photos and videos for that project
cv.pdf                linked from the index, downloads on click
```

## Adding media

Each placeholder (`<div class="ph">`) has an HTML comment above it naming the file it expects.
Replace the placeholder with:

```html
<img src="../media/smart-lamps/build.jpg" alt="The three lamps">
<video src="../media/smart-lamps/demo.mp4" controls preload="metadata"></video>
```

Keep videos small (GitHub rejects files over 100 MB; aim for under 15 MB):

```sh
ffmpeg -i input.MOV -t 60 -vf "scale=-2:720" -c:v libx264 -crf 28 -preset slow \
       -c:a aac -b:a 96k -movflags +faststart media/<project>/demo.mp4
```

Photos: resize to about 1600 px wide before committing.

### Where the source footage is (from the 30 Sep 2026 inventory)

| Project | File | Source |
| --- | --- | --- |
| Smart Lamps | `demo.mp4` | T7 `Alex/University/S2/Project One/mihaialexandrumatei-SmartLamps.mp4` (46 s) |
| Smart Lamps | `build.jpg`, `circuit.jpg` | `frontcover.jpg` and `main.jpg` (hand-drawn wiring) in the Project One folder |
| Immersive room | `demo.mp4` | T7 `Alex/University/S4/USB Team project/Demo_Video.MOV` (4 min, HEVC: cut to ~60 s) |
| Immersive room | `panorama-1.jpg`, `panorama-2.jpg` | T7 `Alex/uni_mac/Uni/USB Team project/ErgoGroup1FinalVersion.zip` → `Assets/GeneratedPanoramas/panorama_20260127_161838.png`, `panorama_20260114_123145.png` (8192×4096, downscaled to 1600) |
| Immersive room | `diffuser.jpg` | still at 0:26 of `media/immersive-room/demo.mp4` (no separate photo on the T7) |
| Airfield | `drone-demo.mp4` | Industry project `final_source/frontend/assets/drone-demo.mp4` |
| Airfield | `drone-demo.mp4` notes | 6x speed, top 48 px cropped to remove the DJI filename/timestamp overlay. No health map: it would show the real airfield layout |
| Warehouse robot | `demo.mp4` | needs recording |
| Couple lamps | `demo.mp4`, photos | needs recording |

## Rules

- Oblivion Labs and Kurkumama work is described only: no code, no client names, no screenshots of client data.
- Name teammates only once they have agreed.
