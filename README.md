# Feast on Olympus - AR Menu POC

Flow: scan QR on printed menu -> phone opens AR page -> camera finds the artwork ->
video plays pinned to it -> tap -> menu page.

## Required structure (exactly this)
ar-menu-poc/
  index.html      AR viewer
  menu.html       printable menu
  test.html       camera+video smoke test (already passed)
  targets.mind    compiled image target (included)
  libs/           aframe + mindar bundled locally (no CDN needed)
  assets/
    artwork.png
    feast.mp4

## Run locally
cd ~/ar-menu-poc
python3 -m http.server 8080
Open http://localhost:8080 in Chrome -> Begin -> allow camera.
First start takes ~5-10s. Green text top-left shows status; it should read
targets.mind: 200 OK / feast.mp4: 200 OK / AR READY, then clear itself.
Show artwork.png on your phone to the webcam -> video snaps on -> click -> menu.

## Ship it (before 7/10)
1. Push this folder to a public GitHub repo, enable Pages (Settings -> Pages -> main).
2. Open the Pages URL in Chrome -> share icon in address bar -> Create QR code -> save.
3. Put the QR image in this folder as qr.png and in menu.html replace
   the qr-slot placeholder text with: <img src="./qr.png">
4. Print menu.html in color (matte paper), test in the dinner room's lighting.

## Tuning
- Cover artwork exactly: change a-video height 1.333 -> 1.5 in index.html.
- Jitter: add filterMinCF: 0.001; filterBeta: 0.01 to the mindar-image attribute.
