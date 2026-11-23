# The World in One Day — Sunday 22 November 2026

One page that sums up the world's news of **Sunday 22 November 2026**. Thirty-five stories from
seven regions, a world map with a pin for each place, and every caption carrying the name of the
outlet that reported it.

## What this is

A single 1024 by 1024 image, laid out the way a newspaper front page is laid out. Three leads
run across the top with the biggest type on the page. Beneath them sits a world map, one pin per
region, so a reader can see at a glance that the day was not one continent's day. Under the map
come ten picture cards, and filling the remaining columns are twenty-two short briefs. The date
sits at the very top where it cannot be missed, and the footer repeats it.

The type sizes are chosen so the page still reads at thumbnail scale: the leads survive being
shrunk to 300 pixels wide, and that is the test that decided most of the layout. A story that
could not be read at that size was moved into the briefs, and a brief that could not be read at
that size was cut rather than left on the page as noise. Ten picture cards carry the stories
that a caption alone would have flattened.

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
