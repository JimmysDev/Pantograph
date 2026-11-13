# Pantograph plugin for Claude

Lets Claude fill in, check and edit PDFs and photos on your Mac using
[Pantograph](https://github.com/JimmysDev/Pantograph), a free, native macOS image and PDF viewer.
Everything happens on your Mac; no file is uploaded anywhere.

With it, Claude can:

- fill in PDF forms: real form fields by name, or flat and scanned forms by finding a label (read with
  text recognition on scans) and writing beside it, or putting one letter in each printed box;
- look at a page, zoom in to check alignment, fix mistakes, and flatten the result before it's sent;
- read and search the text of PDFs and scans;
- watermark, merge, split and render PDFs, and turn photos into a PDF;
- convert HEIC to JPEG and resize, crop, straighten, rotate, flip or adjust photos;
- read or change a photo's or PDF's information (title, date taken, keywords…) and Finder's Where From.

## Requirements

- A Mac with the Pantograph app installed: download the latest `.dmg` from
  [the releases page](https://github.com/JimmysDev/Pantograph/releases/latest), open it and drag
  Pantograph to Applications. Pantograph updates itself.
- Claude Code, or Claude Cowork running on your Mac. The tools run as a local program, so they aren't
  available in claude.ai chat in a browser.

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

## Install

- **Claude Code:** `/plugin marketplace add JimmysDev/Pantograph`, then `/plugin install pantograph@pantograph`.
- **From the Claude Directory:** search for Pantograph, once it's listed.
- **Claude Desktop:** Pantograph › Settings › Command line and AI agents › Add to Claude Desktop also
  installs the tools as a Desktop extension.

## Support

Questions and problems: [github.com/JimmysDev/Pantograph/issues](https://github.com/JimmysDev/Pantograph/issues).
