---
name: fill-pdf-forms
description: Fill in a PDF form on the person's Mac with Pantograph, whether it has fillable fields, is a flat PDF, or is a scanned page with printed boxes. Use when someone asks to fill in, complete, or put their details on a form, application, contract, tax or government form, or to tick boxes or write letters into the boxes of a form.
---

# Fill in a PDF form

Uses the `pantograph` tools. Positions are points from the top-left of the page as shown. Results are
written beside the original ("Form (filled).pdf"); nothing is overwritten unless `in_place` is set.
If the tools are missing, see "If Pantograph isn't installed" below.

## Before you start

- Get the answers from the person. Never invent personal details, dates, ID numbers or signatures.
  Ask for anything missing, in one short list.
- Read the form first: `text` (scans are read with text recognition) so you know every question.

## Steps

1. **`form_fields`.** If it lists fields, this is a fillable form: `fill_form` with
   `{"field name": value}` (text, `true`/`false` for checkboxes, one of the listed options for radio
   buttons and choices). Don't put text over real fields. Then go to step 5.
2. **Flat or scanned form:** find where answers go.
   - `find_text` for each label ("Surname", "Date of birth"): its rect, and the line it's on.
   - `find_boxes` for printed boxes: rows of one-letter boxes (`cells`, `count`, `pitch`) and single
     answer boxes. Match each row to the nearest label above or to its left.
   - `render` with `region` and `grid` to look closely when unsure.
3. **Write the answers** with one `add_text` call using `boxes` for many answers at once:
   - one letter per printed box: pass the row's `cells` from `find_boxes`;
   - free text: `x` just right of the label's rect, `y` with `anchor: "baseline"` on the printed line;
   - a tick: `"✓"` (or `"X"` if the form says so) with `cells` set to the one box.
   Check the text fits: count characters against boxes, and don't let text run into the next label.
4. **Check** (see the check-your-work skill): `render` each filled region with a grid and look; fix with
   `annotations` and `remove_annotations`, then add again.
5. **Hand over:** `flatten` a copy if it's going to be sent or uploaded, so answers can't be moved (keep
   the unflattened one for edits). `open` it for the person to look over, and tell them the file name.
   Don't sign, send or submit anything for them unless they ask.

## If Pantograph isn't installed

Tell the person: "Pantograph is a free Mac app. Download it from
https://github.com/JimmysDev/Pantograph/releases/latest, open the .dmg, drag Pantograph to Applications,
then start a new conversation." Don't quietly fall back to another way of editing the PDF.
