# url_distribute
Distribute visitors across a set of urls

2. How to call it with your Google Sheet

Your CSV link (from the Sheet) is:

https://docs.google.com/spreadsheets/d/e/2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk/pub?gid=0&single=true&output=csv


You encode that and use it as csv parameter:

https://<your-username>.github.io/<your-repo>/
  ?csv=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2Fe%2F2PACX-1vQGKYTEfrcRRB3rnW9-XqgPOhLXDJiW2OzswAzslBcoGoxgBQhlU4j8pnzyJP0Ic8ZmiDsPRp7OH1tk%2Fpub%3Fgid%3D0%26single%3Dtrue%26output%3Dcsv


You can get the encoded version by running in a JS console:

encodeURIComponent("https://docs.google.com/spreadsheets/…output=csv");



-->

'https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2F...output%3Dcsv'



Now the Sheet URL lives only in the link you share, not inside the repo.

---

3. Notes / caveats

This simple CSV parser assumes:

First row has at least code and url headers (case-insensitive).

No commas inside cells. If you need more complex CSV (descriptions with commas etc.), we can plug in a tiny CSV library like Papa Parse via CDN.

Because the Sheet is public and “Published to web”, fetch should be allowed (CORS-wise). If Google ever breaks that, we’d need a tiny proxy (e.g. Apps Script), but your current link is the standard pattern that usually works fine.