# Hudson Valley & Catskills Short-Term Rental Permit Dataset

Town-by-town short-term rental permit rules for 42 municipalities across seven New York counties: Ulster, Greene, Sullivan, Delaware, Dutchess, Columbia and Orange.

**Scoped to the question investors actually ask: can a non-resident owner still get a permit here?**

## Why this exists

Published summaries of these laws contradict each other regularly, and several contradict the town's own code. Shandaken's cap appears as 150 in its codified law and 100 on the town website. Woodstock's cap has been reported as both 340 and 285. Woodstock, Vermont rules circulate widely as though they were Woodstock, New York.

So 22 of these municipalities were read directly from the local law text rather than from anyone's summary.

## Files

| File | Rows | Contents |
|---|---|---|
| `hudson-valley-str-permits.csv` | 37 | One row per municipality with a full entry |
| `hudson-valley-str-permits.json` | 37 | Same data, JSON |
| `watch-list.csv` | 5 | Municipalities with no law yet but regulation in motion |

37 + 5 = 42.

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

**`verified`** means the municipality's own local law text was read directly. Twenty-two meet that standard.

Two entries carry `verified` on a different basis and are flagged in the summary text rather than buried:

- **City of Kingston** — source is the city's published short-term rental fact sheet, not the law.
- **Town of Kingston** — the law's existence and adoption record are documented, but no operative term is readable in any published copy.

**`reported`** means secondary sources and local reporting. Treat with care: this is exactly where published summaries disagree with each other.

**Rows with a `caveat`** hold two confidence levels at once, which is why the text is split across two fields rather than run together. Three rows do this.

Town of Kingston is the clearest case. Its `summary` is `verified`: Chapter 314 provably exists, created by Introductory Local Law 1 of 2023, with the state environmental review notice published 3 January 2024. Its `caveat` is `reported`: not one operative term of it could be read, because the only published copy is a scanned image with no readable text.

If you are filtering this dataset, filter on `confidence` for the main claim and read `caveat` before relying on any row that has one.

## Known limits

- Municipal law changes without notice and this is a snapshot.
- Several entries have open questions documented in the source guide, including Woodstock §260-56, Marlborough §155-32.3 and Town of Kingston Chapter 314, all of which are published only as scanned images with no readable text.
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

If an entry is wrong, open an issue or email rrooney@stevensre.com. Corrections get made on the source page with credit to whoever found them. Four entries have already been corrected that way, and those corrections are shown on the page rather than quietly swapped.
