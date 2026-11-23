# The World in One Day — Sunday 22 November 2026

[![make.fun · news-image-20261122](https://make.fun/badge/news-image-20261122.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![rank](https://make.fun/badge/news-image-20261122/ucupverz/world-in-one-day-20261122/rank.svg)](https://make.fun/bounty/news-image-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)
[![reward](https://make.fun/badge/news-image-20261122/ucupverz/world-in-one-day-20261122/reward.svg)](https://make.fun/bounty/news-image-20261122?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261122)

One page that sums up the world's news of **Sunday 22 November 2026**. Thirty-five stories from
seven regions, a world map with a pin for each place, and every caption carrying the name of the
outlet that reported it.

## What this is

A single 1024 by 1024 image, laid out the way a newspaper front page is laid out, but built from
horizontal bands that run edge to edge rather than from a grid of boxes. The masthead is a navy
block carrying the date at the largest size on the page. Three lead bands follow, each one part
photograph and part type, alternating left and right so the eye is pulled down the page. Then a
four-up picture row, then a strip of six more stories, then the world map with a pin for every
place, and a navy footer that repeats the date.

Ten of the stories wear a photograph. Each was lifted from the report that carried the story,
from that page's own `og:image` metadata, so the picture shows the thing the caption describes.
Nothing is drawn or generated, because an illustration of a story is a claim about what happened
and a wrong picture is a factual error. Where a report carried no usable photograph the story is
set in type alone, at a size that still reads, rather than filled with an image that does not
show it.

The type sizes are chosen so the page still reads at thumbnail scale. The leads use a 30-pixel
serif and survive being shrunk to 300 pixels across, and that is the test that decided most of
the layout. A story that could not be read at that size was moved into the briefs, and a brief
that could not be read at that size was cut rather than left on the page as noise.

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
