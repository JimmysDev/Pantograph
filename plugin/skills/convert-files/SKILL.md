---
name: convert-files
description: Convert and shrink photos and PDFs on the person's Mac with Pantograph. Use when someone wants HEIC photos as JPEG (or PNG, TIFF), PDF pages as images, photos or scans combined into a PDF, a PDF made smaller to email or upload, or photos resized, cropped, straightened, rotated or adjusted in bulk.
---

# Convert files

Uses the `pantograph` tools. Most take several files at once and report each one separately, so one bad
file doesn't stop the rest: check `failed` and each result's `error`. New files go beside the originals
(or into an existing folder given as `out`); originals are never replaced unless asked.

## Which tool

| The person wants… | Tool |
| --- | --- |
| HEIC → JPEG (or PNG, HEIC, TIFF) | `convert` with `to`; date, location and colour profile are kept |
| PDF pages as pictures | `pdf_to_images` (`format` png or jpeg, `dpi` 150; 300 for print) |
| photos or scans → one PDF | `images_to_pdf` (in the order given; `page_size` a4, letter or image) |
| a smaller PDF | `compress` (`level` screen for email; high keeps picture resolution) |
| smaller photos | `resize` with `max` (longest side) or `width`/`height` |
| fix photos | `crop` (with `angle` to straighten), `rotate`, `flip`, `adjust`, `effect` |
| join or split PDFs | `merge`, `extract_pages` |

## Good practice

- For many files, say how many you'll convert and where the results will go before starting.
- Afterwards report what came out: file names, sizes (`info`), and anything skipped or failed and why
  (`compress` skips PDFs it can't make smaller; `convert` skips files already in that format).
- JPEG is lossy: `quality` defaults to 0.92, which looks the same as the original. Expect a HEIC to come
  out about twice the size as a JPEG.

If the tools are missing, Pantograph isn't installed: it's free from
https://github.com/JimmysDev/Pantograph/releases/latest (open the .dmg, drag to Applications).
