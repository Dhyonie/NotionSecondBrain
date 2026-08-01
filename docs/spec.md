# System spec v2

Approved 2026-08-01. Everything here traces back to `interview.md`.

## What this is

A second brain where **Notion is the place Dio looks and acts**, and Claude is the thing that
fills it, sorts it, and keeps it clean. He never designs a database, decides a field, files an
item, or tidies a backlog. Capture reaches it from wherever he happens to be.

## The eight rules

1. **Push is rationed, pull is generous.** What the system *sends* him is cut to almost nothing.
   What he can *go and open* may show everything, because he chose to open it. This is what lets
   mission control be rich without recreating the overwhelm — the pile only hurt when it arrived
   uninvited.
2. **Many ways in, one place it lands.** Message Claude, quick-add in Notion, dictate, forward an
   email. All routes end in the same Inbox — the single source of truth.
3. **He uses it, he never maintains it.** Ticking done is use. Deciding where something belongs,
   naming it, tagging it, tidying it — never his.
4. **Reminding comes to him at 05:30.** One brief, timed for his commute, short enough to work if
   he's driving. Nothing depends on him remembering to check.
5. **The day arrives as an order, not a list.** Short overview, then today in a decided sequence.
   Wrong order, he says so and Claude re-sorts. He never sorts.
6. **Every filed item shows the assumption.** One visible line: what Claude guessed. A wrong guess
   costs five seconds instead of rotting silently.
7. **Two-way doors are Claude's, one-way doors are his.** Reversible without asking; irreversible,
   structural, or visible to another person waits for his yes. Claude does the thinking and all
   the labour — he makes the call in one tap.
8. **Architecture is planned upfront; limits wait for evidence.** The full workflow and
   infrastructure get designed on paper and approved by Dio before anything is built — that's how
   he works. What may NOT be invented in advance are numeric limits (caps, quotas, "max N
   projects"): those only get set once real usage shows they're needed.

## The daily loop

```
capture (chat · Notion quick-add · dictation · forwarded mail)
                        ↓
                   ONE INBOX
                        ↓
        Claude triages overnight — he's asleep
                        ↓
              05:30 · the brief  (push, short, already ordered)

     Mission control  (pull, open any time, shows everything)
```

## The Inbox

One database. Every field populated by Claude.

| Field | Type | Why it exists |
|---|---|---|
| What it is | Title | His words, near verbatim. Rewriting loses what helps him recognise it later. |
| Type | Select | task, idea, note, commitment, dated admin, habit, question, area. Drives everything downstream. ("area" added when Dio's pillars arrived.) |
| Belongs to | Text → relation later | Project or area. Empty allowed — an unattached thought is still worth keeping. |
| When | Date | Only if stated or clearly implied. Never invented. |
| My assumption | Rich text | What Claude guessed. A field rather than a chat message, because chat scrolls away. |
| Status | Select | new, sorted, parked, done. Four states, no more. |
| Captured | Created time | Automatic. Tells fresh from stale. |

## Mission control

One Notion page, built and kept current by Claude. It grows as the system fills — a simple
version exists from phase 2 rather than arriving finished at the end.

| Block | Purpose |
|---|---|
| Today | The same ordered list the brief sent, so the two never disagree. |
| Projects | Each with visible progress, computed by rollup — never typed. |
| Habits | A streak view. Seeing the run of days is itself the motivation. |
| Waiting on | What others owe him and what he owes them. The category that costs trust. |
| Coming up | Dated admin in the next fortnight. His most expensive category. |
| Parked | Everything not active. Visible so he can trust it exists, out of the way so it can't shout. |

## Permissions

**Without asking:** file, sort, name, tag, link, re-file, tidy; build and maintain every view and
the dashboard; draft messages and leave them waiting; propose structural changes.

**Waits for his yes:** anything another person sees; deleting or archiving; changing how the system
is structured; calendar writes, batched into one confirmation rather than one per item.

## Failure signals

| Signal | Response |
|---|---|
| He's organising | Stop and raise it. Work leaked back to him; find out how. |
| Brief becomes noise | Too long or wrong contents. Cut it — don't let him start ignoring it. |
| Capture feels slow | Remove the offending step, whatever it costs downstream. |
| Dashboard goes unopened | It shows what Claude thought mattered, not what he wants. Rebuild. |
| Two wrong guesses | The inference rules are wrong, not the individual item. Change them. |

## Phases

| # | Phase | Status |
|---|---|---|
| 0 | Foundations — protocol, context, capture skill | done |
| — | Interview and spec | done |
| 1 | Notion as a user | done |
| 2 | Inbox + capture channels | done — built via Claude Code, verified |
| 3 | Prove the loop with real data | done — 24 items incl. 7 pillars; schema gained "area" |
| 4 | Triage + the 05:30 brief | done — both live as scheduled tasks (see CLAUDE.md) |
| 5 | Structure — full architecture, planned on paper first, then built | **next** |
| 6 | Mission control | folded into the phase-5 blueprint |
| 7 | App project workspace — decisions log, open questions, specs | |
| 8 | Automate the edges; set numeric limits from evidence if needed | |

## Known constraints

- The Notion connector can create, edit and move, but **cannot delete**. Never promise deletion.
- Capture must work in one step from a phone. Any design that needs a computer at capture time
  is wrong.
