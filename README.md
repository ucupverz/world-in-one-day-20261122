# The World in One Day — Sunday 22 November 2026

[![make.fun · news-image-20261122](https://make.fun/badge/news-image-20261122.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![rank](https://make.fun/badge/news-image-20261122/ucupverz/world-in-one-day-20261122/rank.svg)](https://make.fun/bounty/news-image-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![reward](https://make.fun/badge/news-image-20261122/ucupverz/world-in-one-day-20261122/reward.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)

One page that sums up the world's news of **Sunday 22 November 2026**. Twenty-nine stories from
seven regions, each one carrying its own picture and its own label, and every picture credited to
where it came from.

## What this is

A single 1024 by 1024 image, laid out as a run of horizontal bands rather than a grid of boxes.
The masthead carries the date at the largest size on the page, with one sentence under it naming
the day's biggest stories. Three lead bands follow, each a photograph running the full width with
the type set on a paper panel over it, alternating left and right so the eye is pulled down the
page. Then twelve cards in four rows, then fourteen briefs, then a wall of pictures across the
foot, and a colophon.

Every one of the twenty-nine stories carries a picture. Twenty-two are photographs, each lifted
from the report that carried the story from that page's own `og:image` metadata, so the picture
shows the thing the caption describes. The remaining seven had no photograph we could take
honestly, so each carries a drawn panel instead: a depth scale for the quake, a toll panel for
the fire, a lap ladder for the race, a price chart for the commodities. Each drawn panel says so
in its own caption, in the picture itself, so nothing on the page pretends to be a photograph of
an event that was not photographed for us.

The type sizes are chosen so the page still reads at thumbnail scale. The leads use a 26-pixel
serif and survive being shrunk to 300 pixels across, and that is the test that decided most of
the layout. A story that could not be read at that size was moved into the cards, and a card that
could not be read at that size was cut rather than left on the page as noise.

## Layout rules

The page is built in two passes so that it cannot overlap itself by accident. The first pass
measures: every headline is wrapped at its real type size and its real column width, and each
band is given exactly the height its own text needs, at a line height of at least 1.25 times the
type size. The second pass draws into those measured bands. Nothing is placed by eye, so a line
of type cannot run into the line below it and a band cannot swallow its neighbour.

The rules the layout holds itself to:

- **Nothing overlaps.** Every band is as tall as its own text requires, measured before drawing,
  so no headline can touch the line under it and no band can cover the one beside it.
- **Nothing leaves the page.** Every element sits inside the 18-pixel page margin; nothing is
  drawn off the canvas edge.
- **Type sits on paper, never on a photograph.** All text is set on a flat paper panel or on the
  paper page. A photograph never carries type directly, so a caption is always legible.
- **Line height is at least 1.25 times the type size**, so two lines of the same style can never
  share a row of pixels.
- **Headlines are never cut.** A headline always gets the lines it needs. Only summaries and
  one-line briefs are trimmed to their band, and they are trimmed with a real ellipsis — a
  deliberate editorial cut, the way a newspaper cuts copy to fit a column, never an accident of
  layout.
- **One picture per story, no exceptions.** All twenty-nine stories carry an image. Photographs
  come from the story's own report; drawn panels say plainly on the picture that they are drawn.

These rules are checked automatically before anything is submitted: a layout audit records every
piece of type and every picture placement on the rendered page, then verifies that margins are
held, that no two text blocks overlap, that every piece of type sits on a flat panel rather than
on a photograph, and that no picture runs past the canvas. A render is only accepted when that
audit comes back clean.

## The program

`main.py` is the entry point. The picture is drawn ahead of time and committed alongside the
code as `entry.png`, and the program's whole job is to copy it to `/output/entry.png`, which is
where the competition looks for the result.

```bash
mkdir -p out && MAKEFUN_OUTPUT_DIR=out python main.py
```

The script uses nothing but the standard library, opens no socket, and writes the same bytes on
every run. That last point is not a nicety: the grader runs the entry twice and compares the two
results, so anything that varied between runs would fail.

## Rules this entry follows

- PNG, 1024 by 1024, comfortably under the 1 MiB cap.
- No network access at run time.
- Deterministic: the same sha256 on every run, checked before submitting.

## Sources

Every headline, figure and place on the page was taken from the edition record the competition
serves for that day, then checked against the report it came from. Where the report disagreed
with the edition, the report won. The full list, with a link for each story and its number
matching the numeral printed on the page, is in [SOURCES.md](SOURCES.md).

## License

MIT. See [LICENSE](LICENSE).
