# Mission control — design brief

Paste this into the Claude design app together with your reference screenshots.
When a design comes back, bring it here (image, description or file) and it gets
built into Notion — within the limits listed at the bottom.

---

## The prompt to paste

I want a design for the home dashboard of my personal "second brain". I'm attaching
screenshots of a dashboard whose look I want something similar to — match that feel,
not my description of it.

**What it is.** One page I open on my phone and my laptop. It is the front door to a
system that captures everything I throw at it and sorts it automatically overnight.
It is the calm place where I see where I stand — I never edit or organise anything
here, I only read it and tick things off.

**Who it's for.** Me, one person. Not a team, not a product. I open it in the morning
after a short brief has already told me the day's order, and again in odd moments
during the day.

**The one idea the design must carry.** What the system *sends* me is cut to almost
nothing — a single short message a day. What I *open* is allowed to show everything,
because I chose to open it. So this page can be rich and full, but it must feel quiet.
Nothing on it should shout or nag.

**The seven blocks, in this order of importance:**

1. **Today** — a short numbered list, at most five things, already in the right order.
   This is the reason I opened the page. It should be the first and strongest thing.
2. **Projects** — a handful of projects, each with a progress bar that fills itself.
3. **Streaks** — five daily habits with a run-of-days number each. Seeing the run is
   the motivation, so make the number feel earned.
4. **Coming up** — dated things ahead: renewals, deadlines, appointments.
5. **Waiting on** — what I owe people and what they owe me.
6. **Pillars** — my seven life areas (Faith, Family, Health, Finances & admin,
   Learning & research, Work & business, Order-flow trading). A health check: is one
   being starved?
7. **Parked** — things not active. Visible so I trust they exist, quiet so they can't
   shout at me.

**Requirements.**
- Phone first. It must be readable one-handed, and Today must be visible without
  scrolling on a phone.
- Laptop second: use the extra width for a calm multi-column layout, never a wall.
- Light and dark, both designed properly — I use both.
- Give me: colours as hex values, the type treatment, spacing, an icon per block, and
  a cover image idea for the top of the page.
- Show me the phone layout and the laptop layout.

**Please avoid:** anything that looks like a busy analytics dashboard, gradient-heavy
"SaaS" styling, or big empty hero images that push the actual content below the fold.

---

## What can actually be built in Notion (read before falling in love with a design)

The Notion API can do:
- page cover image and page icon
- an emoji or custom icon per database row and per section
- coloured callout blocks, headings, dividers, quotes
- multi-column layouts (side-by-side blocks)
- toggles to fold long sections away
- database views: table, board, calendar, gallery, list — with chosen visible fields

The Notion API cannot do:
- custom fonts, custom colours outside Notion's fixed palette, or custom spacing
- progress bars styled differently from Notion's built-in ones
- charts, widgets, or anything embedded that Notion doesn't natively support
- moving blocks by pixel — layout is columns and stacking only

So: a design that is about **layout, hierarchy, icons, covers, colour-through-callouts
and what's shown vs hidden** can be built almost exactly. A design that depends on
custom typography or pixel-level styling will be approximated, and I'll tell you
honestly which parts got lost.

---

## Files you can attach as context

- `docs/spec.md` — what the system is and the rules behind it
- `docs/user-guide.html` — how it's used day to day
- `docs/spec-artifact.html` — the visual identity already in use for this project
  ("Raster 05:30": off-white ground, near-black ink, one rationed red for anything
  pushed at me, blue for anything I pull, Archivo + Fragment Mono, printed grid)

Or point the design app at the repo: `Dhyonie/NotionSecondBrain`.
