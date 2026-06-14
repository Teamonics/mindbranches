# MindBranches

Paste markdown, get an interactive mind map, save it as a high-resolution image. A single-file web app built on [markmap](https://markmap.js.org/).

## Features

- **Live preview** — the map re-renders as you type (300 ms debounce)
- **Save PNG** — exports the *entire* map (not just the visible viewport) at 2×–8× resolution
- **Save SVG** — exports the full map as a vector file (best viewed in a web browser)
- **Light / Dark theme** — dark mode flips the whole app and exports inverted images: black background, white text
- **Save HTML** — downloads a standalone interactive mind map you can share
- **Wrap text** — one click caps node width at 300px (inserts editable markmap settings into your markdown)
- **Autosave** — your markdown is kept in the browser's localStorage
- Folding branches, pan/zoom, fit-to-view — everything markmap offers

## How it works

`index.html` is the whole app, with its four library dependencies (d3, markmap-lib, markmap-view, html-to-image) bundled locally in `vendor/` — fully self-contained, no CDN, works offline. There is no build step, no dependencies to install, no server. See `THIRD-PARTY-LICENSES` for the bundled libraries' licenses.

Two features still reach the network when used: markdown with math or syntax-highlighted code loads KaTeX/Prism assets on demand, and files saved via **Save HTML** load their scripts from CDN (so they work standalone wherever you send them).

PNG export works by temporarily resizing the SVG to the map's natural bounds, snapshotting it with html-to-image at the chosen `pixelRatio` (this handles markmap's `<foreignObject>` HTML labels, which break naive SVG serialization), then restoring your view.

## Deploy

Any static host works:

- **Open from disk** — double-click `index.html`
- **Netlify Drop** — drag this folder onto <https://app.netlify.com/drop>
- **GitHub Pages** — push this folder to a repo, enable Pages
- **Anything else** — `python3 -m http.server` in this folder, Vercel, S3, …

## License

The Teamonics MindBranches build is licensed under the [Apache License 2.0](LICENSE).

This repository includes third-party open-source libraries: [markmap](https://github.com/markmap/markmap) (MIT), [html-to-image](https://github.com/bubkoo/html-to-image) (MIT), and [d3](https://github.com/d3/d3) (ISC). Their full license texts are in [`THIRD-PARTY-LICENSES`](THIRD-PARTY-LICENSES).

MindBranches, Teamonics, associated logos, domain names, visual identity, and related branding are trademarks or brand assets of Teamonics LLC. The software license applies to the code only and does not grant permission to use Teamonics or MindBranches branding in a way that suggests endorsement, affiliation, sponsorship, or an official Teamonics product. See [`TRADEMARKS.md`](TRADEMARKS.md).
