# Riftbound Flex Sheet

Live: https://shizukaziye.github.io/riftbound-flex-sheet/

A Riftbound "what do I need to own, and what do I build" page. The sample is
every event on riftdecks.com with 100 or more players in the last month, cut
to a depth that scales with the field:

| players | placings counted |
|---|---|
| 100+ | top 4 |
| 200+ | top 8 |
| 400+ | top 16 |
| 800+ | top 32 |
| 1600+ | top 64 |

A legend is listed when it has at least two placings inside those cuts. Right
now that is 23 legends: Kennen, Master Yi, Rengar, Irelia, Azir, Diana,
LeBlanc, Rek'Sai, Ezreal, Fiora, Jayce, Kha'Zix, Draven, Ornn, Akali, Vex,
Viktor, Nasus, Lux, Kai'Sa, Lillia, Lucian and Mel. Sett and Teemo placed once
each and are left out. The "Events in the sample" dropdown under the title
lists every event with its date, field, cut, and how many placings inside the
cut posted a list.

## Three modes

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
with the flex slots marked, editable, saveable and shareable.

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
  sideboard. Hover a cell for the main / side split. The last number on the
  row is the average placing of the lists that ran at least that many copies,
  green or red when a point or more better or worse than the sample average.
  The header carries the mean over every copy you have picked, next to the
  generic list's figure once you edit.
- **Adjusting the list.** Every row has controls: − drops a copy, + adds one
  (up to 3 in total), ▾S / ▴M move a copy between main and sideboard, +M / +S
  on the "next in line" rows or the add box bring a card in, and battlefields
  swap the same way. Anything dropped below its generic count shows under
  "Removed" with add-back buttons. The header counts turn red when the list
  is off 40 / 10 / 3. Edits are kept per legend in the browser until Reset.
- **Flex choices** pairs the weakest slots in the list ("cut first") with the
  next cards in line that did not make it ("next in line", 10% or more),
  each with its share and average placing.
- **Saving.** Save keeps a named copy of the current list under its legend;
  each save is a chip with Load, Link and delete. Link copies a URL with the
  whole list encoded in the hash, so it opens on any machine and can be
  bookmarked or shared; opening one drops it into the editor as the working
  copy. Export in the control bar copies every save as JSON and Import merges
  that JSON back in, for moving saves between browsers.
- **Copy list** puts the current list on the clipboard as plain text, grouped
  by Champion, Units, Spells, Gear, Battlefields, Runes and Sideboard, with
  the list's market total as a trailing note.
- **Prices.** Every row in both modes shows the TCGplayer market price of the
  cheapest printing of that card (base, alternate art, promo or overnumbered,
  whichever is lowest); hover for the printing and the lowest single listing,
  click to open TCGplayer. Prices over $20 are red. The generic-list header
  totals the whole list including the legend card and 12 runes, and shows the
  generic list's total beside it once you edit. Prices come from the daily
  scrape behind tcg-price-tracker and are baked in with their date; refresh
  them by re-running the price step when rebuilding `P` (`P.prices`,
  `P.meta.prices_asof`).

**Buy list.** A shopping list built from whatever each legend's list is right
now on the page.

- Tiles turn legends on and off. For every legend that is on, the list uses
  your edited or loaded working copy if you have one, otherwise the generic
  list under the current event-size and placing filters, plus 0 / 5 / 10 /
  all of its next-in-line flex slots (your choice). Legend cards and the 12
  runes are included.
- **One at a time** needs the most copies any single deck uses; **All at
  once** sums every deck. Columns: price (cheapest printing), copies needed,
  line total, one column per legend that is on (flex copies marked), the
  printing, and the lowest listing. Headers sort.
- Tick a card as bought and it drops off the list and out of the total;
  "Everything" shows ticked rows struck through. Which legends are on, the
  flex setting and ticked cards are remembered in the browser.
- **Copy buy list** puts the still-to-buy rows on the clipboard as text with
  quantity, card, unit price and printing.

## Filters and detail

- **Event size**: any, or only events with 200+ / 400+ / 800+ / 1600+
  players.
- **Placing**: any, winners only, or lists that placed top 4 / 8 / 16 / 32.
  Every table and every generic list recomputes on the fly.
- Click any card row (in either mode) for the copy split: how many lists ran it
  at 3, 2 or 1 copies or not at all, their share, and the average placing of
  each group. Average placing mixes deep cuts (down to 64th) with shallow ones
  (top 4), so a card common at small events reads better than it is; the
  event-size filter compares like with like.
- Each list link is event and place. Hover one for the date, field size and
  the cut counted. Placings that never posted a list, or posted an empty one,
  are named under "placed but no list on the site".

## Data

Pulled from riftdecks.com on 9–10 Sep 2026: 40 events dated 9 Aug to 9 Sep
2026, 499 placings inside the cuts, 269 lists for the 23 legends. The three
biggest events are the Singapore and Barcelona Regional Qualifiers (top 64
each) and the S4 Wuhan Regional Open (top 32); the Barcelona Pre-Regional
(2058 players) also counts to 64 but only a handful of its placings posted
lists. Most of the rest are S4 City Challenges in China plus the Barcelona and
Singapore side events, Speyer, the US Showdown Series and a few 5k/10k events.

Every list is checked at 40 main, 12 runes and 3 battlefields. A dozen
smaller-event lists are posted incomplete on riftdecks (39 main cards, or no
battlefields, or an 8-card sideboard); they are kept as posted, which can only
under-count. Deck pages that exist but hold no cards are treated as no list.
Card types and domains come from the riftdecks card database.

Every list's card counts are baked into `index.html` as the `P` object and all
tallies are computed in the browser, so refreshing after another event means
rebuilding `P` (per legend: `decks` with `m` main counts, `s` sideboard
counts, `bf` battlefields, `r` runes, `rank`, event name, date, field size,
cut and URL; plus `events` and `meta` for the header). Deck pages on
riftdecks.com sit behind a Cloudflare challenge and rate-limit to roughly one
page every few seconds, so fetch them from a real browser session, not curl.

The page is one self-contained `index.html`. Fonts come from Google Fonts; the
two `loseii.com` scripts add the shared site nav and can be dropped without
affecting the sheet.

Unofficial fan tool, not affiliated with Riot Games.
