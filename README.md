# URL DISTRIBUTE

Distributes visitors across a set of urls.

---

## USAGE

Simply go to the static 'index.html' by typing the repository pages URL:

```url
https://adrianartacho.github.io/url_distribute/
```

Add the public URL pointing at the .csv table with the url addresses as a query parameter as follows:

```url
https://adrianartacho.github.io/url_distribute/?csv=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2Fe%2F2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk%2Fpub%3Fgid%3D0%26single%3Dtrue%26output%3Dcsv
```

---

## How to encode the Spreadsheet url

You encode that and use it as csv parameter:

https://<your-username>.github.io/<your-repo>/
  ?csv=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2Fe%2F2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk%2Fpub%3Fgid%3D0%26single%3Dtrue%26output%3Dcsv

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

## Notes / caveats

This simple CSV parser assumes:

First row has at least code and url headers (case-insensitive).

No commas inside cells. If you need more complex CSV (descriptions with commas etc.), we can plug in a tiny CSV library like Papa Parse via CDN.

Because the Sheet is public and “Published to web”, fetch should be allowed (CORS-wise). If Google ever breaks that, we’d need a tiny proxy (e.g. Apps Script), but your current link is the standard pattern that usually works fine.
