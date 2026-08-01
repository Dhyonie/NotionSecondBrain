# Gameplan

Eight phases, 15–30 minutes each. Nothing rolls into the next phase without Dio saying go.

## The principle it rests on

Systems don't die from being too simple. They die because filing costs more effort than
capturing, so filing stops — and then the system lies to you about what's in it. So the capture
path gets built first, end to end, before any structure exists. Structure comes later, shaped by
what actually accumulated rather than by what we guessed would.

## Phases

**✓ Foundations** — operating card, standing context, capture skill, protocol agreed.

**✓ Interview** — seven areas, one question at a time. Output: `docs/interview.md` and the spec.

**✓ Phase 1 · Notion as a user** — page, database, property, view, relation. Enough to never feel
lost in his own system; not enough to build one.

**Phase 2 · Inbox + capture channels** — one database, seeded with examples, plus every route into
it. *Why one box and not six:* with a single destination, capture can never be filed wrongly, so
there's no hesitation — and hesitation is what kills capture. Splitting capture from sorting is
**capture-then-clarify**, from GTD. The inbox is meant to be unsorted.

**Phase 3 · Prove the loop** — he dumps ten real things, messy, no editing. Claude files all ten
and shows every assumption. *Why real data:* fields get designed from what turned up. Fields
invented in advance and never filled are the commonest reason a Notion setup gets abandoned.

**Phase 4 · Triage + the 05:30 brief** — the scheduled sweep that sorts the inbox and asks only
about genuine forks. *Why this decides everything:* an inbox with no review becomes a junkyard in
about two weeks, and once he stops trusting it he stops using it. This is the **review** half of
GTD — the part nearly everyone skips, and the reason nearly everyone's system dies.

**Phase 5 · Structure** — Tasks, Projects, Notes, Habits, and the relations between them. *Why
here and not earlier:* by now real data tells us the shape, so we're describing rather than
guessing. Doing it at phase 2 would be **premature optimisation**.

**Phase 6 · Mission control** — the dashboard. Built once there's something worth showing, though
a simple version exists from phase 2 so he's never staring at an empty shell.

**Phase 7 · App project workspace** — decisions log, open questions, spec pages for the automation
app. *Why the decisions log above all:* on a build project the expensive thing to forget isn't a
task, it's a decision you already made and the reason behind it. Professional teams keep exactly
this and call it an **ADR** — architecture decision record. `decisions.md` in this repo is one.

**Phase 8 · Automate the edges** — and set limits from evidence, if any turn out to be needed.
*Why last and open-ended:* automating a workflow he hasn't lived with just locks in a guess.

## How control works

After each phase Claude stops, shows what exists, and waits. If a phase turns out wrong, we redo
that one — never the whole thing. At the end of any phase, if something has come up he wants to
dig into properly, the build stops and we go into it.

Phases 2–4 are the ones that matter. If he never gets past phase 4, the forgetting problem is
still solved.
