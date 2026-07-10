# Weblate POT source-location test

Minimal gettext fixture to test whether Weblate can use source string
locations from the `.pot` template file instead of storing them in each
language `.po` file.

## Hypothesis

> An advantage of using Weblate is that we do not need to store the source
> string location in the `.po` files; it can use the information in the
> `.pot` file for all languages.

## Layout

```
po/
├── r-test.pot   # template — HAS #: source references
├── de.po        # German — NO #: references
├── fr.po        # French — NO #: references
└── hu.po        # Hungarian — NO #: references
```

## Source references in `r-test.pot`

The template deliberately mixes reference styles:

| Style | Example |
|-------|---------|
| File + line number | `#: src/library/base/R/quit.R:12` |
| File only (no line) | `#: src/library/stats/R/lm.R` |
| Multiple locations | `#: src/library/grDevices/R/postscript.R:203 src/library/grDevices/R/pdf.R:156` |

The `.po` files contain only `msgid` / `msgstr` pairs — no `#:` lines.
