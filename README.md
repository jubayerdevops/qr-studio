# Signal Tag — QR Label Studio

A single-file, self-contained QR code generator with a distinctive "lab specimen tag" visual style: a dark technical interface, viewfinder-style corner brackets, and a teal scan-line animation that sweeps the tag on generation.

Live version: https://claude.ai/artifact/Qae8oEL1fzhTU6kKbH52GQ

## Features

- **Four content types** — encode a URL, plain text, Wi-Fi credentials, or a phone number, switchable via tabs
- **Live preview** — the tag regenerates as you type, no submit button needed
- **Adjustable size** — 160–480px via slider
- **Custom colors** — pick module and background colors, with a contrast reminder for scannability
- **Error correction levels** — L / M / Q / H, selectable to trade pattern density for damage tolerance
- **PNG download** — exports the generated code at its current size and colors
- **Animated empty state** — a pulsing reticle icon with a looping scan-line when there's no content yet, instead of a blank square
- **Runs entirely client-side** — nothing typed is sent to a server

## Tech stack

- Plain HTML, CSS, and vanilla JavaScript — no build step, no framework
- [qrcodejs](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js) (davidshimjs) loaded from cdnjs for QR rendering
- Google Fonts: [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) (display) and [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono) (data/labels)

## Usage

1. Open `qr-studio.html` in any modern browser — no install or server required.
2. Pick a content type (URL, Text, Wifi, or Phone) and fill in the field.
3. Adjust size, colors, and error correction as needed.
4. Click **Download PNG** to save the generated tag.

## Content encoding reference

| Type  | Encoded as |
|-------|------------|
| URL   | `https://...` (scheme added automatically if missing) |
| Text  | Raw text, unmodified |
| Wifi  | `WIFI:T:<security>;S:<ssid>;P:<password>;;` |
| Phone | `tel:<digits>` |

## Project structure

```
qr-studio.html   # everything — markup, styles, and script in one file
README.md        # this file
```

## Customization

Color tokens, fonts, and spacing are defined as CSS custom properties near the top of the `<style>` block (`--void`, `--panel`, `--signal`, `--amber`, `--paper`, `--ink`, etc.), so the palette can be restyled without touching layout code.

## Browser support

Works in any modern evergreen browser (Chrome, Firefox, Safari, Edge). QR rendering uses `<canvas>` where supported.
