# Ponder

A static site for browsing and downloading Create mod `.nbt` schematics.

## Folder layout

```
ponder/
├── index.html        the site
├── manifest.json      the list of schematics + their search terms
└── schematics/
    ├── your_file_1.nbt
    ├── your_file_2.nbt
    └── ...
```

## Adding a schematic

1. Drop the `.nbt` file into `schematics/`.
2. Add an entry for it in `manifest.json`:

```json
{
  "file": "your_file_1.nbt",
  "name": "Display name shown on the card",
  "author": "your name",
  "description": "What it does, what version of Create, anything worth knowing.",
  "tags": ["farm", "automatic", "0.5.1"]
}
```

Only `file` and `name` are required — `description`, `author`, and `tags` are
optional but make the card and search much more useful. `tags` is what the
search box matches against, along with the name, author, and description.

To remove a schematic, delete its entry from `manifest.json` (and optionally
delete the `.nbt` file too).

There's no upload form and no login — the only way to add or remove a
schematic is to edit these files directly, so access is controlled by
whoever has access to the folder / repository, not by a password.

## Running it

This site needs to be served over HTTP — opening `index.html` directly as a
local file (`file://...`) will fail, because browsers block `fetch()` from
local files for security reasons.

**Locally, for testing:**
```
cd ponder
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

**To actually share it with others**, host the folder on any static host:
- GitHub Pages (push this folder to a repo, enable Pages)
- Netlify or Vercel (drag-and-drop the folder)
- Any regular web server / file host that serves static files

Anyone with the link can browse and download. Only you (or whoever has write
access to the folder) can add or remove schematics.
