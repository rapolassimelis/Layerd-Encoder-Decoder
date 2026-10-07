# Cipher Notebook

A small, single-file, client-side tool for stacking classic text ciphers — Base64, Hex, Binary, ROT13, URL encoding, Morse, ASCII85, Caesar shift, Unicode escapes, and string reversal — in whatever order you like.

**[Live demo →](#)** *(enable GitHub Pages on this repo to get a link here, or just open `index.html` locally)*

## What it does

Pick a sequence of ciphers, run your text through them one after another, and get the result back. Switch to decode mode and it reverses the same chain to unscramble it. Handy for:

- Learning how these encodings work and how they compose
- Quick one-off encode/decode tasks (CTF practice, puzzles, debugging an encoded string)
- Teaching how encoding chains work

## Features

- 10 ciphers, chainable in any order, up to 12 steps
- Encode and decode modes (decode runs the chain in reverse automatically)
- A running size estimate as you build the chain, so you can see ahead of time if a combination is going to produce something huge
- A hard runtime cap so a bad chain fails cleanly instead of freezing the tab
- No dependencies, no network calls — everything runs locally in your browser
- One HTML file, no build step

## Usage

Open `index.html` in any modern browser. Nothing to install.

```bash
git clone https://github.com/<your-username>/cipher-notebook.git
cd cipher-notebook
open index.html
```

Or host it free with [GitHub Pages](https://pages.github.com/): Settings → Pages → Deploy from branch → `main` → `/ (root)`.

## The ciphers

| Cipher | Notes |
|---|---|
| Base64 | Standard Base64, UTF-8 safe |
| Hex | Space-separated byte values |
| Binary | Space-separated 8-bit values |
| ROT13 | Classic letter substitution, self-reversing |
| URL | `encodeURIComponent` / `decodeURIComponent` |
| Morse | Letters, digits, and spaces |
| ASCII85 | Compact binary-to-text encoding |
| Reverse | Flips the string, self-reversing |
| Caesar (3) | Classic Caesar shift of 3 |
| Unicode | `\uXXXX` escape sequences |

## Why the size warnings?

A few of these ciphers expand text a lot per step — Binary roughly 9x, Unicode roughly 6x, Hex and Morse roughly 3x. Stack several of those and a short sentence can turn into megabytes of output, which is enough to freeze a browser tab. The notebook estimates this as you build your chain and caps things at 12 steps with a hard runtime limit, so a bad combination fails with a clear note instead of hanging.

## License

MIT — see [LICENSE](LICENSE).
