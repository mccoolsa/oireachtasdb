# OireachtasDB

**[https://mccoolsa.github.io/oireachtasdb/](https://mccoolsa.github.io/oireachtasdb/)** **HTML Homepage**

Search over the Official Report of the Houses of the Oireachtas — every Dáil and Seanad debate
from 2020 onward, and every recorded vote. From the use of the Oireachtas API.

Going live at **[oireachtasdb.ie](https://oireachtasdb.ie)**. `index.html` in this repo is a
static snapshot of the home page. Updated weekly Monday 01:00 GMT.

**This current database is yet to go live - so figures, contributions and other metrics are valid from 2020 to 01-08-2026.**

## What it does

Every speaker carries the party they belonged to on the day
they spoke. Members change party, and most archives quietly relabel their old speeches with
their current one. A contribution from 2020 here keeps its 2020 party, resolved by a dated
join and written onto the record when it is parsed.

**Search.** Full text of 318,530 contributions. Words are combined with AND by default, with
quoted phrases, `OR`, exclusion and prefix matching. Filter by party, chamber and date; sort by
relevance or date; page through the whole result set.

**Votes.** All 2,470 divisions with the complete Tá/Níl roll — 186,260 individual votes —
grouped by the party each member held that day, with tellers and the other divisions taken in
the same debate.

**Debates.** 18,237 debates, each stored with a bag-of-words / TF-IDF profile so the terms
surfaced are the ones distinguishing that debate rather than the vocabulary common to all
parliamentary language. Each carries a short summary and, where it went to a division, the
result.

**Members.** A page per member: everything they said, how they voted, and their party history.

**Citations.** Every result downloads with the record URI and the timestamp it was fetched. The
Official Report is revised after publication, so a citation without a timestamp cannot be
checked later.

## Scale (for demonstration)

| | |
|---|---:|
| Sittings | 1,190 |
| Contributions | 318,530 |
| Recorded votes | 2,470 |
| Individual votes cast | 186,260 |
| Members | 318 |
| Speakers resolved to a named member | 99.6% |

## Caveats of note

**Written answers are not included.** They are not in the debate record at all — the Oireachtas
publishes them separately, with a different attribution model (an asking member and an
answering minister). Adding them means a separate ingest.

**Committee transcripts are not included.** Committee votes are; their debates are not.

**Coverage starts in 2020.** The source archive goes back to 1919 and the pipeline is
date-parameterized, so widening it is configuration rather than a rewrite. Earlier material is
also poorer: sampling the whole 1919–2026 archive, speaker-to-member linkage runs from 84% in
the 1920s to 99.8% in the 2020s.

**Summaries are extractive, not written.** Sentences are scored on how distinctive their
wording is and the best few are quoted back verbatim, in the order spoken. Every word in a
summary was said in the chamber. For a record people may want to cite, that is the safer
trade: a generated summary can smooth over or invent detail.

**Some vote outcomes are calculated, not published.** For a small number of divisions the
Oireachtas recorded no result but the tallies survived. Where those differ the outcome follows
arithmetically and is shown, labelled as derived.

**No age or gender breakdowns.** The source API publishes no date of birth and returns an empty
gender field for every member in this period. Showing such a breakdown would mean inventing it.

**Party colours are not official branding.** They are chosen so parties stay distinguishable in
greyscale and to colour-blind readers. Several parties genuinely share a colour family — Fianna
Fáil, Sinn Féin, the Greens and Aontú are all shades of green — so the abbreviation on each chip, not the
colour, identifies the party.


## Source and licence

Data is the Official Report of the Houses of the Oireachtas, licensed
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), retrieved from their open data API.
No Oireachtas data is redistributed in this repository.
