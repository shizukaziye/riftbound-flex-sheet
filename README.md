# Nine-Legend Flex Sheet

Live: https://shizukaziye.github.io/riftbound-flex-sheet/

A Riftbound "what do I need to own" sheet for nine legends: Irelia, Kennen,
Master Yi, Rengar, Rek'Sai, Azir, Diana, Jayce and Kha'Zix. For each legend it
lists every card that showed up in a top-cut list, at the highest copy count
any single list ran. Own those copies and you can rebuild any of the sampled
lists, or any mix of them.

## What is in it

- One section per legend with a main-deck table, a sideboard table, a
  battlefields table, rune split chips, and links to every source list.
- The number on each row is the max copies seen. The bar shows how many of
  that legend's lists ran the card at all. Rows tagged *core* were in every
  list.
- A **Separate / Combined** toggle. Separate tallies main deck and sideboard
  on their own. Combined adds each list's main and sideboard copies first,
  then takes the max across lists, so it is the count needed to build any one
  full 40+10 list. The choice is remembered in the browser.
- Legends with a thin sample carry a note. Placings that never posted a list
  are named under "placed but no list on the site".

## Data

Pulled from riftdecks.com on 3 Sep 2026:

- S4 Wuhan Regional Open, top 32 (32 lists).
- Barcelona Regional Qualifier, top 64 (29 lists for these legends; 21 of the
  64 rows had no decklist submitted).

61 lists in total, each checked at 40 main and 12 runes. The numbers are baked
into `index.html`; to refresh after another event, rebuild the `P` object in
the script block.

The page is one self-contained `index.html`. Fonts come from Google Fonts; the
two `loseii.com` scripts add the shared site nav and can be dropped without
affecting the sheet.

Unofficial fan tool, not affiliated with Riot Games.
