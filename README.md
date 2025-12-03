# URL DISTRIBUTE

Distributes visitors across a set of urls.

---

## USAGE

Simply go to the static 'index.html' by typing the repository pages URL:

```url
https://adrianartacho.github.io/url_distribute/
```

Add the [public URL pointing at the .csv table with the url addresses](https://docs.google.com/spreadsheets/d/1e6XpShTIiDQWFWPk5WJ0pEAEcygZh6ZYEFjzxiLhGYs/edit?gid=0#gid=0) as a query parameter as follows:

```url
https://adrianartacho.github.io/url_distribute/?csv=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2Fe%2F2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk%2Fpub%3Fgid%3D0%26single%3Dtrue%26output%3Dcsv
```

---

## How to encode the Spreadsheet url

You encode that and use it as csv parameter:

```url
https://USERNAME.github.io/REPO/
  ?csv=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2Fe%2F2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk%2Fpub%3Fgid%3D0%26single%3Dtrue%26output%3Dcsv
```

You can get the encoded version by running in a JS console:

```js
encodeURIComponent("https://docs.google.com/spreadsheets/…output=csv");
```

Alternatively, you may just use the stativ URI encoder page:

```url
https://adrianartacho.github.io/url_distribute/encode.html
```

Now the Sheet URL lives only in the link you share, not inside the repo.

---

## Timer

There is an optional query parameter (`t`) that:

* `?t=5` → auto-clicks after 5 seconds if the user does nothing

* `?t=0` → auto-clicks immediately (invisible forwarding, as soon as the CSV is loaded)

If t is omitted → behaves exactly like now (no auto-click)
Example:

```url
https://USERNAME.github.io/REPO/?csv=ENCODED_CSV_URL&t=5
```

or for instant invisible forwarding:

```url
https://USERNAME.github.io/REPO/?csv=ENCODED_CSV_URL&t=0
```

---

## Default forwarding

The query parameter allows to set up the default behaviour of a specific url:

* `?default=random` or no default at all → behaves like now (balanced random)

* `?default=purple` (where purple is a valid code in the CSV) → the default behavior is to redirect to purple’s URL

---

## Notes / caveats

This simple CSV parser assumes:

First row has at least code and url headers (case-insensitive).

No commas inside cells. If you need more complex CSV (descriptions with commas etc.), we can plug in a tiny CSV library like Papa Parse via CDN.

Because the Sheet is public and “Published to web”, fetch should be allowed (CORS-wise). If Google ever breaks that, we’d need a tiny proxy (e.g. Apps Script), but your current link is the standard pattern that usually works fine.
