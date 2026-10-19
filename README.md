# Hudson Valley & Catskills Short-Term Rental Permit Dataset

Town-by-town short-term rental permit rules for 147 municipalities across seven New York counties: Ulster, Greene, Sullivan, Delaware, Dutchess, Columbia and Orange.

**Scoped to the question investors actually ask: can a non-resident owner still get a permit here?**

## Why this exists

Published summaries of these laws contradict each other regularly, and several contradict the town's own code. Shandaken's cap appears as 150 in its codified law and 100 on the town website. Woodstock's cap has been reported as both 340 and 285. Woodstock, Vermont rules circulate widely as though they were Woodstock, New York.

So 136 of these municipalities were read directly from the local law text rather than from anyone's summary.

## Files

| File | Rows | Contents |
|---|---|---|
| `hudson-valley-str-permits.csv` | 139 | One row per municipality with a full entry |
| `hudson-valley-str-permits.json` | 139 | Same data, JSON |
| `watch-list.csv` | 8 | Municipalities with no law yet but regulation in motion |

139 + 8 = 147.

## Columns

| Column | Values |
|---|---|
| `municipality` | Official name, e.g. "Town of Rosendale" |
| `county` | One of the seven counties |
| `also_covers` | Hamlets and clarifications, e.g. "includes Tillson", "not the Village" |
| `tier` | `open`, `one_condition`, `effectively_closed` |
| `tier_label` | Human-readable tier |
| `confidence` | `verified` or `reported`, applying to `summary` (see below) |
| `summary` | The entry text at the confidence level above |
| `caveat_confidence` | Confidence level of `caveat`, where one exists. Always the opposite of `confidence` |
| `caveat` | Text held at the other confidence level. Empty for most rows |

## Confidence

**`verified`** means the municipality's own local law text was read directly. 136 meet that standard. Every row in the main files is now `verified`, counting municipalities where the full local-law index or code was read and no short-term rental law was found.

Three entries carry `verified` on a different basis and are flagged in the summary text rather than buried:

- **City of Kingston:** source is the city's published short-term rental fact sheet, not the law.
- **Town of Kingston:** the law's existence and adoption record are documented, but no operative term is readable in any published copy, and no filing of it appears in the state's local-law database.
- **Town of Lexington:** source is the town's own short-term rental page and summary, because the law is posted only as scanned images.

**`reported`** means secondary sources and local reporting. Treat with care: this is exactly where published summaries disagree with each other.

**Rows with a `caveat`** hold two confidence levels at once, which is why the text is split across two fields rather than run together. Nine rows do this.

Town of Kingston is the clearest case. Its `summary` is `verified`: Chapter 314 provably exists, created by Introductory Local Law 1 of 2023, with the state environmental review notice published 3 January 2024. Its `caveat` is `reported`: not one operative term of it could be read, because the only published copy is a scanned image with no readable text.

If you are filtering this dataset, filter on `confidence` for the main claim and read `caveat` before relying on any row that has one.

## Known limits

- Municipal law changes without notice and this is a snapshot. **Last updated 16 October 2026.**
- Several entries have open questions documented in the source guide, including Woodstock §260-56, Marlborough §155-32.3 and Town of Kingston Chapter 314, all of which are published only as scanned images with no readable text.
- Zoning laws are sometimes filed with the state without their text. Clermont filed its 2025 zoning law that way; its short-term rental section was read from the copy the town posts. Where a "no law" row rests only on state filings, read it as no law in the filed text.
- An absence of law is harder to prove than a presence. Entries reading "no law found" mean no law was found, not that none exists.
- **Nothing here is legal advice.** Confirm with the municipality before relying on any of it.

## Source and attribution

Compiled and maintained by **Ryan Rooney**, Licensed Real Estate Salesperson, Stevens Real Estate at eXp Realty, New Paltz NY.

The canonical version, with full detail, sources and correction notes, is at:
**https://realtorrooney.com/short-term-rental-rules-hudson-valley**

Free to use with attribution. If you find an error, say so and it gets corrected on the page with credit.

## How to cite

> Hudson Valley & Catskills Short-Term Rental Permit Dataset, compiled by Ryan Rooney, Stevens Real Estate at eXp Realty. https://realtorrooney.com/short-term-rental-rules-hudson-valley

## Licence

CC BY 4.0. Use it, adapt it, build on it, commercially or otherwise. Just credit it and link back. See `LICENSE`.

## Corrections

If an entry is wrong, open an issue or email rrooney@stevensre.com. Corrections get made on the source page with credit to whoever found them. Several entries have already been corrected, and those corrections are shown on the page rather than quietly swapped.

## Changelog

- **16 October 2026.** Columbia County completed: twenty municipalities added to the main files, all `verified` from their own law, online code or Department of State filings: the Towns of Ancram, Austerlitz, Canaan, Chatham, Claverack, Clermont, Copake, Gallatin, Ghent, Greenport, Kinderhook, Livingston, New Lebanon, Stockport, Stuyvesant and Taghkanic, and the Villages of Chatham, Kinderhook, Philmont and Valatie. Germantown added to the watch list (a 2023 draft law went to hearing in 2024 and was never filed; a January 2026 zoning rewrite draft adds a short-term rental section). Three gaps elsewhere closed: the Town of Ashland (Greene), the Village of Woodridge (Sullivan) and the Village of Pawling (Dutchess, capped at 15 and limited to primary residents). The Town of Pawling row now points to the village.
- **15 October 2026.** Twenty-eight Delaware County municipalities added, all `verified` from the laws they have filed with the New York Department of State: the Towns of Andes, Bovina, Colchester, Davenport, Delhi, Deposit, Franklin, Hamden, Hancock, Harpersfield, Kortright, Masonville, Meredith, Middletown, Sidney, Stamford, Tompkins and Walton, and the Villages of Delhi, Deposit, Fleischmanns, Franklin, Hancock, Hobart, Margaretville, Sidney, Stamford and Walton. Every row that was `reported` was re-read from the law and is now `verified`. Corrections: Hardenburgh moves from the main files to the watch list (a 2025 moratorium on short-term rental applications, with special permits in its zoning); East Fishkill moves from `effectively_closed` to `open` (no cap or owner-occupancy rule in Local Law 4 of 2023); Hillsdale's law is Local Law 2 of 2019, not 2 of 2022; Jewett's reported local-manager rule is not in its laws. Village of Catskill is now read from its zoning text rather than its application (contact rule is one hour, not 20 minutes; 4% village occupancy tax since 2025).
- **14 October 2026 (night).** Fifteen Sullivan County municipalities added, all `verified`: the Towns of Fallsburg, Forestburgh, Fremont, Liberty, Lumberland, Mamakating, Neversink, Rockland, Thompson and Tusten, and the Villages of Bloomingburg, Jeffersonville, Liberty, Monticello and Wurtsboro. Twelve have no short-term rental law; for most, the check was a full-text search of every local law filed with the New York Department of State. Two findings matter: the Village of Monticello banned short-term rentals in its residential districts with Local Law 4 of 2026, filed 30 September 2026, and the Town of Rockland adopted Chapter 144 in 2023 (permits limited to primary or seasonal owners).
- **14 October 2026 (evening).** Twenty-one Dutchess County municipalities added, all `verified`: the Towns of Amenia, Beekman, Clinton, Dover, Fishkill, Hyde Park, Milan, North East, Pawling, Pine Plains, Pleasant Valley, Poughkeepsie, Stanford, Union Vale, Wappinger and Washington, the City of Poughkeepsie, and the Villages of Fishkill, Millbrook, Millerton and Wappingers Falls. LaGrange added to the watch list.
- **14 October 2026 (later).** Sixteen municipalities added: in Greene County the Towns of Durham, Athens, Cairo, Coxsackie, Greenville, Halcott, Lexington, New Baltimore and Prattsville and the Villages of Athens, Catskill, Coxsackie, Hunter and Tannersville; in Ulster County the Town of Plattekill and the Village of Saugerties. Fifteen are `verified`, Prattsville is `reported`. Lexington is the notable one: its 62 non-resident permits are all issued.
- **14 October 2026.** Town of Rhinebeck: the hospitality moratorium was adopted on 14 September 2026 as Local Law 3 of 2026, and the adopted version excludes short-term rentals; a proposed 3% occupancy tax reaching short-term rentals added. City of Kingston: cap updated to 112 as of September 2026, with the December 2025 reopening (correction made on the page 12 October 2026). Town of Kingston caveat updated to match.
