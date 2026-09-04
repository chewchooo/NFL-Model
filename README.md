# NFL-Model

The NFL prop board and its data feed, served by GitHub Pages.

## Open the board

**https://chewchooo.github.io/NFL-Model/nfl-props/**

Works on a phone: Safari runs the page normally, and Share → Add to Home Screen gives an icon
that opens full-screen.

It is a large page (~3.5 MB, about 500 KB over the wire) because the whole slate's data is
inlined. That is one load; afterwards it polls only `meta.js`, a couple of hundred bytes.

Downloading the HTML and opening it from the iOS Files app does *not* work — Quick Look renders
the markup but never runs the JavaScript, so the board shows its static placeholders.

## Feeds

| feed | served at |
|---|---|
| `nfl-props/meta.js` | https://chewchooo.github.io/NFL-Model/nfl-props/meta.js |
| `nfl-props/data.js` | https://chewchooo.github.io/NFL-Model/nfl-props/data.js |

`meta.js` names the pull `data.js` currently holds. Shared copies poll it and fetch the 3.2 MB
`data.js` only once the stamp moves — the board rebuilds about once a week, so polling the big
file directly would move roughly a gigabyte a day to keep learning nothing had changed.

Written by `publish.ps1` after every rebuild. History is held at a single amended commit.
