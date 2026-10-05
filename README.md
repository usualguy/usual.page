# usual.page

The holding page for [usual.page](https://usual.page). Two files, no build
step, no dependencies — `index.html` is the entire site.

| File | What it is |
|---|---|
| `index.html` | The page. A header table, `COMING SOON/` with a blinking cursor, a footer. |
| `CNAME` | The custom domain. GitHub Pages reads it at the published root and serves the site for that host. |

## Serving it

Settings → Pages → Source: branch `main`, folder `/`. The `CNAME` above fills
in the custom domain by itself; the DNS records go in at the registrar, and
GitHub's own Pages settings page lists the values once the domain is entered.

## The CSS

The page carries its stylesheets inline rather than linking them, so it owes
the network nothing but the webfont. They come from
[the-monospace-web](https://github.com/usualguy/the-monospace-web), a fork of
[Oskar Wickström's design](https://github.com/owickstrom/the-monospace-web),
concatenated in load order — `reset.css`, `index.css`, `tokens.css`,
`a11y.css` — with `index.css`'s `@import` of the webfont hoisted to the top of
the `<style>`, the only place a browser still honours it. The upstream MIT
notice sits above them, because inlining the code is redistributing it.

**This is a snapshot.** Editing a stylesheet in that repository does not reach
this page; the CSS here has to be re-inlined by hand.

## The grid

Everything sits on whole multiples of the 1.20rem line unit, and the two hero
columns are whole numbers of character cells. `tools/check-grid.js` in the
design-system repository measures this and reports every element that drifts —
worth re-running against this file after any change to it.
