# Host Seating Drill

Two training pages for Hojokban hosts, built on the real floor plan and on
August 2026 (1,511 seated parties from the GuestCenter export).

| Page | Link | What it drills |
|---|---|---|
| **Next Party Up** | [`/`](https://einsteinpark.github.io/host-drill/) | One party at a time. You see only the next 30 minutes, capped at 10 parties. Quick mode ends when the room fills; Standard runs to close. |
| **Fill the Room** | [`/advanced.html`](https://einsteinpark.github.io/host-drill/advanced.html) | The full version — plan the whole book, then work the door with late arrivals, part-parties and walk-ins. |

Both are single self-contained HTML files. No build step, no server, no data
leaves the page. Open on an iPad in Safari, or **Share → Add to Home Screen**
for a full-screen icon at the host stand.

## The rules being taught

**Fill order** — the middle block runs `33 42 31 44 32 41 34 43`; the banquettes
run `21 12 23 14 22 11 24 13 26 16 25 15`, staggered across the two rows so
nothing gets double-seated. The 50s come last because they are at the door.

**Occasions** — birthdays and anniversaries want `11 16 21 26`, the ends of the
banquette runs, or a two-top given a whole 30s/40s table. Never the 50s, never
the bar.

**Combinations** — as configured in GuestCenter. `15/16` and `25/26` are the
house sevens, so don't burn `15` or `25` on a deuce. `14/15` is deliberately not
a legal pair.

**The bar** — `B1`–`B8` plus `51/52/53` belong to the bartender, and 80% of bar
seatings in August were walk-ins. It is the relief valve, not book capacity.

## Dial these if they're wrong

Everything tunable sits in one `F` object at the top of `index.html`:

- `dine` — how long a table sits, by party size. Currently 1–2: 60–105 min,
  3: 75–120, 4: 90–120, 5–6: 90–150, 7+: 120–180, then 15 minutes to reset.
  **This is the one input the export could not give us** — it has no departure
  time — so these are set to match the room's observed throughput.
- `nights` — the volume tiers, set from how the room actually feels rather
  than the raw spread of the book: **slow 60-80 covers, mid 80-110, busy 110+**
  (capped at 220, which is what August's biggest nights ran). Walk-ins count
  inside the tier, not on top of it. Across August those thresholds split the
  month 2 slow / 8 mid / 19 busy, median night 135.
- `lookaheadMin` / `lookaheadMax` — 30 minutes and 10 parties. The single dial
  that sets difficulty.
- `tables`, `combos`, `sections` — the room itself.

## Sharing a night

Every night is generated from a seed. Tap the `#4821` chip, type a number, and
every trainee who enters that number gets the identical room — useful for
comparing two hosts on the same book.
