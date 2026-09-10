# Riftbound Flex Sheet

Live: https://shizukaziye.github.io/riftbound-flex-sheet/

A Riftbound "what do I need to own, and what do I build" page. It covers every
legend that placed at least twice across three top cuts (the Singapore Regional
Qualifier top 64, the Barcelona Regional Qualifier top 64 and the S4 Wuhan
Regional Open top 32) or made a top 4 at any other event with 100 or more
players in the last month. That is 23 legends right now: Kennen, Master Yi,
Irelia, Rengar, Diana, Azir, Ezreal, Kha'Zix, Akali, Fiora, Rek'Sai, Vex,
Jayce, LeBlanc, Lucian, Ornn, Draven, Lux, Mel, Nasus, Kai'Sa, Viktor and
Lillia.

## Two modes

**Flex sheet.** For each legend, every card that showed up in a sampled list,
at the highest copy count any single list ran. Own those copies and you can
rebuild any of the sampled lists, or any mix of them.

- Main-deck table, sideboard table, battlefields, rune split chips, and links
  to every source list.
- The number on each row is the max copies seen. The bar shows how many of
  that legend's lists ran the card at all. Rows tagged *core* were in every
  list.
- **Separate / Combined** toggle. Separate tallies main deck and sideboard on
  their own. Combined adds each list's main and sideboard copies first, then
  takes the max across lists, so it is the count needed to build any one full
  list.

**Generic list.** One consensus 40-card main deck (including the legend's
champion), 10-card sideboard, 3 battlefields and 12-rune split per legend,
with the flex slots marked.

- Main deck and sideboard are one 50-card pool. Every copy of every card is a
  *slot*, scored by the share of lists that ran at least that many copies
  across main + sideboard (over lists that posted a sideboard), so "2nd copy
  of Gust" is its own slot. The 50 best slots make the pool, then the 40 that
  most often sat in the main deck become the main deck and the other 10 the
  sideboard. A card never exceeds 3 copies in total. The legend's own champion
  is always seeded in. Battlefields are the 3 best by share. Runes are the
  most common exact split, with the other splits seen listed beside it.
- Each row shows the pool shares for the 1st, 2nd and 3rd copy. Filled cells
  are *locked* (two thirds of lists or more), outlined cells are *flex* slots
  that made the cut anyway, dotted cells are copies this list keeps in the
  sideboard. Hover a cell for the main / side split.
- **Adjusting the list.** Every row has controls: − drops a copy, ▾S / ▴M
  move a copy between main and sideboard, +M / +S on the "next in line" rows
  or the add box bring a card in, and battlefields swap the same way. The
  header counts turn red when the list is off 40 / 10 / 3. Edits are kept per
  legend in the browser (localStorage) until Reset; Copy list copies the
  edited list.
- **Saving.** Save keeps a named copy of the current list under its legend;
  each save is a chip with Load, Link and delete. Link copies a URL with the
  whole list encoded in the hash, so it opens on any machine and can be
  bookmarked or shared; opening one drops it into the editor as the working
  copy. Export in the control bar copies every save as JSON and Import merges
  that JSON back in, for moving saves between browsers.
- **Flex choices** pairs the weakest slots in the list ("cut first") with the
  next cards in line that did not make it ("next in line", 10% or more),
  each with its share and average placing.
- **Copy list** puts the whole list on the clipboard as plain text, grouped by
  Champion, Units, Spells, Gear, Battlefields, Runes and Sideboard.

## Filters and detail

- **Source**: all lists, the three big cuts only, or only the top-4 finishes
  from the smaller events.
- **Placing**: any, or only lists that placed top 4 / 8 / 16 / 32. Every table
  and every generic list recomputes on the fly.
- Click any card row (in either mode) for the copy split: how many lists ran it
  at 3, 2 or 1 copies or not at all, their share, and the average placing of
  each group. Average placing mixes big cuts (1 to 64) with smaller events
  where every list is a top 4, so treat it as a hint.
- Links under "Top 4 elsewhere" are the top-4 finishes from the smaller
  events, labelled event and place. Hover one for the date and field size.
- Placings that never posted a list are named under "placed but no list on
  the site".

## Data

Pulled from riftdecks.com on 9 Sep 2026:

- Singapore Regional Qualifier, top 64 (33 lists for these legends; 29 of the
  63 ranked rows had no decklist submitted).
- Barcelona Regional Qualifier, top 64 (43 lists; 21 of the 64 rows had no
  decklist submitted).
- S4 Wuhan Regional Open, top 32 (31 lists for these legends).
- Top 4 of every other event with 100+ players dated 9 Aug to 9 Sep 2026 on
  the riftdecks tournament index: 37 events, 129 lists, 17 placings with no
  list. Most are S4 City Challenges in China plus the Barcelona and Singapore
  side events, Speyer, the US Showdown Series and a handful of 5k/10k events.

236 lists in total, each checked at 40 main, 12 runes and 3 battlefields. Ten
of the smaller-event lists are posted incomplete on riftdecks (39 main cards,
or no battlefields, or an 8-card sideboard); they are kept as posted, which
can only under-count. Card types and domains come from the riftdecks card
database.

Every list's card counts are baked into `index.html` as the `P` object and all
tallies are computed in the browser, so refreshing after another event means
rebuilding `P` (per legend: `decks` with `m` main counts, `s` sideboard
counts, `bf` battlefields, `r` runes, `rank`, event tag and URL). Deck pages on
riftdecks.com sit behind a Cloudflare challenge and rate-limit to roughly one
page every few seconds, so fetch them from a real browser session, not curl.

The page is one self-contained `index.html`. Fonts come from Google Fonts; the
two `loseii.com` scripts add the shared site nav and can be dropped without
affecting the sheet.

Unofficial fan tool, not affiliated with Riot Games.
