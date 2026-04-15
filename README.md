# QR.

A minimal, futuristic QR code tool — scan, read, and create QR codes entirely in the browser. No backend, no installs, no tracking.

**Last updated:** 15 Apr 2025 · v1.2  
**Author:** [@arookiecoder-ip](https://github.com/arookiecoder-ip)

---

## Features

### Scanner
- Live camera feed using `getUserMedia` (works on mobile and desktop)
- Auto-detects the rear camera on mobile devices
- Frame-by-frame decode loop via `requestAnimationFrame` — low latency, no polling
- Decoded URLs are auto-linked and openable in one tap

### Reader
- Drag-and-drop or tap-to-browse image upload
- Decodes QR codes from PNG, JPG, GIF, WebP
- Multi-scale decode (tries 1×, 2×, 0.5×) — handles screenshots, tiny QR codes, and large photos
- Shows a preview of the uploaded image alongside the result

### Creator
- **Content types:** plain text, URL, email address, phone number, Wi-Fi credentials
- **Size:** 128 – 512 px (slider)
- **Error correction:** L / M / Q / H
- **Custom colors:** separate foreground and background color pickers
- **Export:** PNG download, SVG download, or copy image to clipboard

---

## Usage

Just open `index.html` in any modern browser. No build step, no dependencies to install.

```
open index.html
```

For camera scanning, the browser will ask for camera permission. On mobile, it defaults to the rear (environment-facing) camera.

> **Note:** Camera access requires a secure context (`https://` or `localhost`). If you're serving over plain `http://` on a remote host, the camera tab will show a permission error — use HTTPS or serve locally.

---

## Tech stack

| Purpose | Library |
|---|---|
| QR scanning / reading | [@zxing/library](https://github.com/zxing-js/library) 0.18.6 |
| QR code generation | [qrcodejs](https://github.com/davidshimjs/qrcodejs) 1.0.0 |
| Styling | Vanilla CSS (no framework) |
| Logic | Vanilla JS (no framework) |

Everything runs client-side. No data leaves your device.

---

## Browser support

| Browser | Scanner | Reader | Creator |
|---|---|---|---|
| Chrome / Edge 90+ | ✓ | ✓ | ✓ |
| Firefox 90+ | ✓ | ✓ | ✓ |
| Safari 15+ (iOS/macOS) | ✓ | ✓ | ✓ |
| Samsung Internet | ✓ | ✓ | ✓ |

---

## Changelog

### v1.2 — 15 Apr 2025
- Fixed camera scanner: replaced broken `listVideoInputDevices` with direct `getUserMedia` + RAF decode loop
- Fixed image reader: decode now uses canvas pixel data instead of `decodeFromImageUrl` (resolves blob URL failures on mobile)
- Multi-scale decode for reader (handles screenshots and unusual image sizes)
- Mobile-optimized layout (responsive padding, full-width scanner, tighter tabs)
- Switched from blue/cyan theme to warm amber/charcoal

### v1.1
- Added Wi-Fi QR code generation
- SVG export for created QR codes
- Copy image to clipboard

### v1.0
- Initial release: scanner, reader, creator

---

## License

MIT — do whatever you want with it.
