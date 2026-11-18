---
name: edit-pdfs
description: Edit PDFs on the person's Mac with Pantograph. Use when someone wants to add text, a logo, stamp or signature picture to a PDF; rotate, delete, reorder, duplicate or insert pages; split out or merge pages; watermark; remove or fix existing markup; or change a PDF's title, author or keywords.
---

# Edit a PDF

Uses the `pantograph` tools. Positions are points from the top-left of the page as shown (`render`
reports `points_per_pixel` to convert a spot on a picture). Every edit writes a new file beside the
original unless `in_place` is set; keep it that way unless the person asks to change the original.

## Which tool

| The person wants to… | Tool |
| --- | --- |
| rotate, delete, move, duplicate pages, add a blank page | `pdf_pages` (`action`, `pages`, `degrees`, `to`) |
| keep only some pages, or split a PDF | `extract_pages` |
| join PDFs, or make one from photos | `merge`, `images_to_pdf` |
| write text somewhere | `add_text` (use `find_text` to position it next to existing words) |
| put a logo, stamp or signature picture on a page | `add_image` (`x`, `y`, `width`; the height follows) |
| mark every page CONFIDENTIAL, DRAFT, a logo… | `watermark` (`position: "tile"` across the page) |
| see or undo what's been added | `annotations`, `remove_annotations` |
| change the title, author, keywords, Where From | `metadata` |
| make it uneditable before sending | `flatten` |

## Good practice

- Look before you place: `render` the page (with `grid`) or `find_text` the nearby words.
- A signature picture only goes on a document when the person gave it to you for that document. Never
  reuse one from elsewhere.
- After each edit, check it (the check-your-work skill): `compare` the original and the result and make
  sure the only changes are the ones intended.
- Tell the person what you changed and where the new file is; `open` shows it to them.

If the tools are missing, Pantograph isn't installed: it's free from
https://github.com/JimmysDev/Pantograph/releases/latest (open the .dmg, drag to Applications).
