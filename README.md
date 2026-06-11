# Ethereum Library

A single-page reading library for Ethereum, cryptography, and decentralized systems. A fork of Erik's [cypherpunkbooks.com](https://www.cypherpunkbooks.com/), with a different shelf. Built by Riely.

## Features

- **Animated hero** — staggered rise-in title set in AlphaLyrae.
- **3D bookshelf** — perspective-tilted shelf that drifts continuously; hover a book to pop it forward, click to open its page.
- **Per-book pages** — each book has its own detail page (`#book/<slug>`) with cover, blurb, and a Read link.
- **Searchable collection** — live filtering across titles and authors, with grid and list views.
- **Light / dark themes** — toggle in the nav, full palette swap via CSS variables.
- **Responsive** — adapts from mobile to desktop.
- **Zero build step** — everything is in one `index.html`. Fonts (AlphaLyrae, Inter) are self-hosted in `fonts/`.

## Running

Open `index.html` directly in a browser, or serve the folder locally:

```bash
# --bind 127.0.0.1 keeps the server on your machine only,
# not exposed to others on your network.
python3 -m http.server 8000 --bind 127.0.0.1
# then visit http://localhost:8000
```

> Note: GitHub labels this repo "100% HTML" only because the CSS and
> JavaScript live inside `index.html`. It's a single-file site, not a
> CSS-less one.

## Contributing — add a book

Anyone is welcome to add a book to the shelf. It's a single edit to one array, no build step.

1. **Fork** this repo and create a branch.
2. Open `index.html` and find the `BOOKS` array (near the bottom, in the `<script>` block).
3. Add an entry following this shape:

```js
{
  title:  "The Book Title",
  author: "Author Name",
  year:   2008,                 // number, or a string like "c. 400 BC"
  section:"Computing History",  // see sections below
  color:  "#16243f",            // cover/spine color, see palette below
  h: 360,                       // shelf book height in px (~280–440)
  t: 22,                        // shelf book thickness in px (~18–38)
  url:   "https://...",         // OPTIONAL: a free/legal Read link
  blurb: "One or two sentences on what the book is and why it belongs here."
},
```

4. Open a **Pull Request** describing the book and the source of the Read link.

### Field reference

| Field | Required | Notes |
|-------|----------|-------|
| `title` | yes | Used for the page URL slug (auto-generated). |
| `author` | yes | |
| `year` | yes | Number, or a string for ancient dates. |
| `section` | yes | One of: `Fiction`, `Cypherpunk`, `Computing History`, `Public Goods`, `Crypto Spirituality`. |
| `color` | yes | Hex cover color. Use one from the palette below for visual consistency. |
| `h` | yes | Spine height on the 3D shelf, roughly 280–440. |
| `t` | yes | Spine thickness on the shelf, roughly 18–38. |
| `url` | no | If omitted, the page shows a "find at a library" link instead of a Read button. |
| `blurb` | recommended | Short description shown on the book's page. |

### Read-link policy

Only link to **free or legal** sources. Good options:

- Author- or publisher-hosted free copies (e.g. the Bitcoin/Ethereum whitepapers).
- [Nakamoto Institute Library](https://nakamotoinstitute.org/library/), Project Gutenberg, arXiv.
- [Internet Archive](https://archive.org) **controlled-lending borrow pages** (one borrower at a time) for in-copyright books.
- [OpenLibrary](https://openlibrary.org) records.

Please do **not** link to pirated copies, shadow-library aggregators, or direct full-PDF dumps of in-copyright works. If no legal Read source exists, leave `url` off — the site will show a library/bookshop link automatically.

### Cover palette

The shelf uses the cover palette from cypherpunkbooks.com. Pick a hex from this set:

```
#7a1f2b  #16243f  #14532d  #c2410c  #1f2733  #b51d22  #0f3d3e
#7a5512  #3a1d52  #0b1f3a  #8b1e3f  #5b3a29  #2a1f5e  #2e3a40
#10402c  #4a1d2a  #4a3713  #1f3a4d  #4a1538  #f7931a  #1a1a1a
```

## Structure

```
index.html    # markup, styles, and logic in one file
fonts/        # AlphaLyrae + Inter (woff2)
README.md
```

## Credits

Design forked from Erik's [cypherpunkbooks.com](https://www.cypherpunkbooks.com/). Book selection by Riely and contributors.

## License

MIT.
