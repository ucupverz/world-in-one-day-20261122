# The World in One Day — Sunday 22 November 2026

One page that sums up the world's news of **Sunday 22 November 2026**: 35 stories,
7 regions, a world map, and every story carrying the name of the outlet that
reported it.

## What this is

A single 1024x1024 image laid out like a front page: three leads across the top,
a world map with one pin per region beneath them, ten picture cards, and 22 short
briefs filling the columns. The date sits at the top so the day can never be
mistaken, and a footer repeats it.

## The program

`main.py` is the entry point. The picture is drawn ahead of time and committed as
`entry.png`; the program copies it to `/output/entry.png`, which is what the
competition runs.

```bash
mkdir -p out && MAKEFUN_OUTPUT_DIR=out python main.py
```

It uses only the standard library, opens no socket, and produces the same bytes
on every run, because the grader runs it twice and compares.

## Rules this entry follows

- PNG, 1024x1024, under 1 MiB.
- No network at run time.
- Deterministic: identical sha256 across runs.

## Sources

Every headline, figure and place on the page comes from the edition record the
competition serves for that day, and each is attributed on the page itself. The
full list with links is in [SOURCES.md](SOURCES.md).

## License

MIT, see [LICENSE](LICENSE).
