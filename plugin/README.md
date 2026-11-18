# Pantograph plugin for Claude

Lets Claude fill in, edit, convert and check PDFs and photos on your Mac using
[Pantograph](https://github.com/JimmysDev/Pantograph), a free, native macOS image and PDF viewer.
Everything happens on your Mac; no file is uploaded anywhere.

## What Claude can do with it

**Fill in forms** (skill: `fill-pdf-forms`)
- Fillable PDFs: list the fields and fill them by name: text, checkboxes, radio buttons, choices.
- Flat and scanned forms: find labels (read with text recognition on scans), find the printed boxes,
  and write answers beside labels, on printed lines, or one letter per box in any font.

**Edit PDFs** (skill: `edit-pdfs`)
- Rotate, delete, move, duplicate and insert pages; split and merge; make a PDF from photos.
- Add text, logos, stamps or a signature picture you supply; watermark every page; set the title,
  author and keywords; list and remove markup; flatten before sending.

**Convert files** (skill: `convert-files`)
- HEIC to JPEG (or PNG, TIFF), keeping date, location and colour; PDF pages to PNG or JPEG.
- Make PDFs smaller for email; resize, crop, straighten, rotate and adjust photos, many at once.

**Check its own work** (skill: `check-your-work`)
- Compare before and after to see exactly what an edit changed, with the changes marked in red.
- Zoom in on any part of a page with a ruler; read text back; list what's been added and whether it prints.

Under the hood these are Pantograph's 29 tools (`form_fields`, `fill_form`, `find_text`, `find_boxes`,
`add_text`, `add_image`, `pdf_pages`, `compare`, `render`, `compress`, `convert`, …). The skills tell Claude
when to use them and how to check the result.

## Requirements

- A Mac with the Pantograph app: download the latest `.dmg` from
  [the releases page](https://github.com/JimmysDev/Pantograph/releases/latest), open it and drag
  Pantograph to Applications. Pantograph updates itself.
- Claude Code, or Claude Cowork running on your Mac. The tools run as a local program on your Mac, so
  they aren't available in claude.ai chat in a browser.

## Install

- **Claude Code:** `/plugin marketplace add JimmysDev/Pantograph`, then `/plugin install pantograph@pantograph`.
- **Claude Desktop and Cowork:** download `Pantograph-plugin.zip` from
  [the latest release](https://github.com/JimmysDev/Pantograph/releases/latest), then in Claude choose
  Customize › Plugins › Add › Upload plugin.
- **The Claude Directory:** search for Pantograph, once it's listed.

## What this plugin runs, sends and fetches

- **Runs:** `server/pantograph`, a short shell script, starts the Pantograph app already installed on
  your Mac (`/Applications/Pantograph.app/Contents/MacOS/Pantograph mcp`) as a Model Context Protocol
  server over stdin and stdout. If Pantograph isn't in `/Applications` or `~/Applications`, the script
  asks macOS (`osascript`) where the app with identifier `com.jimmysdev.pantograph` is. The plugin
  contains no copy of Pantograph.
- **Reads and writes:** only the files Claude passes to the tools. Results are written beside the
  original under a new name and never replace a file unless asked.
- **Sends and fetches:** nothing. Neither this plugin nor Pantograph's tools make network requests.
  (The Pantograph app checks GitHub for its own updates once a day; that's the app, not the tools.)

## Support

Questions and problems: [github.com/JimmysDev/Pantograph/issues](https://github.com/JimmysDev/Pantograph/issues).
