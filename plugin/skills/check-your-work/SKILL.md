---
name: check-your-work
description: Check edits to PDFs and photos with Pantograph before handing them over. Use after filling in a form, adding text or pictures, rearranging pages, watermarking or converting, and whenever someone asks to check, verify, review, compare or proofread a PDF or image, or to see what changed between two versions.
---

# Check your work

Don't report an edit as done until you've looked at it. Pantograph's tools show you the result.

## After every edit

1. **`compare`** the file before and after. You get the changed areas (in points for PDFs) and a picture
   with the changes marked in red. Confirm the changes are exactly the ones intended, and that nothing
   else moved. `identical: true` means the edit didn't take.
2. **`render`** the changed areas up close: `region` (x, y, width, height in points) and `grid` (a ruler
   every 10 or 20 points). Check text sits on its line or inside its box, isn't clipped, and doesn't run
   into printed text.
3. **Read it back:** `text` or `find_text` to confirm words landed and are spelled right. On a flattened
   PDF, answers should still be searchable.
4. **`annotations`** lists everything added to each page, and whether it prints.

## Before handing over

- Every question on a form answered (compare against the form's `text`), or left blank on purpose and
  said so.
- For a form that will be sent: a `flatten`ed copy, checked with `render`.
- `info` for the final page count and size; `compress` if it's too big to email.
- Tell the person what changed, what you're unsure of, and the output path; `open` shows it to them.

## Fixing mistakes

`annotations` gives each item's page and index; `remove_annotations` with `page` and `indexes` (or a
`type` such as text) removes them. Indexes shift after a removal, so list again before removing more.
Then add again and check again.
