---
name: pantograph
description: Fill in, check and edit PDFs and photos on the person's Mac with Pantograph's tools. Use when someone wants to fill in or complete a PDF form (fillable, flat or scanned), write text on a PDF, put letters in the boxes of a form, find or read text in a PDF or scan, flatten a filled form, watermark, merge or split PDFs, turn photos into a PDF, convert HEIC to JPEG, or resize, crop, straighten, rotate or adjust photos, or change a file's title, date or Where From.
---

# Pantograph

Pantograph is a free macOS app whose tools edit PDFs and photos locally. Files never leave the Mac.
The tools appear as `pantograph` MCP tools (`form_fields`, `fill_form`, `find_text`, `find_boxes`,
`add_text`, `render`, `flatten`, …). The server's own instructions, sent when it connects, describe
every tool; this page is the short version.

## If the tools aren't there

The tools need the Pantograph app on the Mac. If they're missing or fail to start, tell the person:
"Pantograph is a free Mac app. Download it from https://github.com/JimmysDev/Pantograph/releases/latest,
open the .dmg, drag Pantograph to Applications, then start a new conversation." Don't try to edit the
PDF some other way without saying so.

## House rules

- Give absolute paths. Results are written beside the original under a new name, never over it,
  unless `in_place` (or `out` with `overwrite`) is set. Every result gives its output path.
- Positions on PDF pages are points from the top-left of the page as shown, in every tool.

## Filling in a PDF form

1. `form_fields`. If it lists fields, fill them by name with `fill_form` and stop there.
2. Otherwise the form is flat, often a scan:
   - `find_text` finds labels ("Surname", "Date of birth") with their positions, reading scanned pages
     with text recognition.
   - `find_boxes` finds printed boxes: rows of one-letter boxes (cells, count, pitch) and answer boxes.
   - `render` shows the page; `region` zooms in and `grid` adds a ruler in points.
3. `add_text` writes the answers, several at once with `boxes`. For one-letter boxes pass the row's
   `cells` from `find_boxes`: one character is centred in each. Otherwise write just right of the label,
   with `anchor: "baseline"` to sit on a printed line. A tick is `add_text` with "✓" or "X".
4. `render` the region again to check. `annotations` and `remove_annotations` fix mistakes.
5. `flatten` before the form is sent, so answers can't be moved. Keep the unflattened copy for edits.
6. `open` shows the finished file to the person in Pantograph.

Ask the person for any answer you don't know rather than guessing, and show them the result before
anything is sent or submitted on their behalf.
