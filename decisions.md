# Decision log

Architecture decision records. One entry per decision that would be expensive to re-litigate.
Format: what was decided, why, and what it rules out. Append, never rewrite.

---

## D1 — Notion is the interface and the storage
**2026-08-01**

Claude builds and maintains Notion; Dio uses it. He never designs a database, decides a
field, files an item, or tidies a backlog — but he does open it, read it, and tick things off.

**Why.** An earlier version had Notion as storage only, with chat as the sole interface. Dio
objected. The distinction that was missing: *operating* Notion (designing, filing, maintaining)
versus *using* it (opening a view, ticking a box). Only the first killed his four previous
systems. "Never touch Notion" was an over-correction.

**Rules out.** Any design where the only way to see the system is to ask Claude.

---

## D2 — Many capture channels, one destination
**2026-08-01**

Capture can arrive from anywhere: a message to Claude, Notion quick-add, dictation, forwarded
email. All of them land in one Inbox.

**Why.** The original spec said "one message to Claude" as though it were a principle. It
wasn't — it was the cheapest thing to build first. What must be single is the *destination*
(the single source of truth), not the channel.

**Rules out.** Any second inbox, anywhere, for any reason.

---

## D3 — No project cap until there is data
**2026-08-01**

An active-project limit was proposed and removed. It may return in a later phase, derived
from what actually competes for his time.

**Why.** Dio pointed out it was being decided before a single item had been captured — which
broke the project's own rule about designing from real data. Rule 1 (push rationed) already
solves the overwhelm, because the pain came from *visibility*, not from quantity.

**Rules out.** Imposing any limit, category or structure by guess. This became rule 8.

---

## D4 — Triage overnight, brief at 05:30, short enough to hear
**2026-08-01**

Claude sorts the inbox overnight. One brief lands at 05:30 for the commute. It must work if
he's driving, so it stays short and front-loaded.

**Why.** He wakes at 05:00 and commutes between 05:30 and 06:00. The commute varies day to
day, so the brief can't assume he can read it.

---

## D5 — Fresh Notion workspace
**2026-08-01**

The system is built clean. Existing content was Notion's own starter templates only, nothing
of Dio's. Deletion is his to do — the connector has no delete capability.

---

## D6 — Build in Claude Code, keep Cowork for conversation
**2026-08-01**

Construction happens in Claude Code against a project folder. The Cowork session remains
available for thinking, review, and phone-side work.

**Why.** Claude Code holds a repo, runs scripts, and keeps the whole system in files rather
than in a chat log. Daily *use* still has to work from a phone, so the two aren't in conflict.

---

## D7 — Pillars are first-class, and "area" is a Type
**2026-08-01**

Dio's first real dump wasn't tasks — it was the pillars of his life: Faith, Family, Health,
Finances & admin, Learning & research, Work & business. "area" was added to the Type select
and the seven pillars exist as items. Everything else hangs off a pillar in phase 5.

**Why.** His overwhelm wasn't too many projects — it was work projects competing against
pillars that were never on the board, so the pillars lost silently. You can't defend what
isn't written down.

---

## D8 — Order-flow trading is its own pillar
**2026-08-01**

Trading stands beside Work & business, not inside it. Dio's explicit call.

**Why.** He named it a priority and separately from everything else. A pillar gets defended
in the daily order; a sub-item gets leftovers.

---

## D9 — Triage and brief are live as scheduled tasks
**2026-08-01**

Overnight triage at 02:30 UTC, morning brief at 03:30 UTC (04:30 / 05:30 NL summer time).
The brief is a sequence of ≤5, readable in under 60s, hard-capped because Dio may be driving;
the push notification carries only the single most important line.

**Caveat.** UTC schedules — shift both by an hour when NL returns to winter time (late Oct).

---

## D10 — Rule 8 corrected: plan-first architecture, evidence-first limits
**2026-08-01**

Rule 8 as first written ("no rule before there's data") over-generalised the project-cap
lesson and briefly blocked upfront design. Dio corrected it: he wants the whole workflow and
infrastructure planned and approved on paper BEFORE building — that's his working style. The
narrow lesson stands only for numeric limits: caps and quotas wait for real usage evidence.

**Rules out.** Using rule 8 as an excuse to defer design work; inventing caps without data.

---

## D11 — The Inbox drains hourly, and ambiguity comes back to Dio on his terms
**2026-08-01**

Triage now runs every hour (scheduled tasks can't go faster), so captures rarely sit more
than 60 minutes. Chat captures are filed instantly by whichever Claude receives them.
Ambiguous items are never left unfiled: they get a best-guess filing plus a flag, and the
question reaches Dio through the morning brief's "Needs your yes" section — batched, at a
time he's already reading, not as interruptions. If he doesn't answer, the question simply
reappears; it never blocks the item.

**Why.** Dio asked for the buffer to drain as fast as possible, and for unclear captures to
come back to him — but rescheduled around his time, not shoved at him.

---

## D12 — Notes live inside project pages, not in a Notes database
**2026-08-01**

Dio's call, against Claude's recommendation (recorded per protocol). Notes attach to the
project they belong to as page content; notes with no project land on the pillar's page.

**Trade-off accepted.** Reads better in place; searching across all notes is weaker. If
retrieval starts failing ("I know I wrote that somewhere"), revisit.

---

## D13 — Phase 5 is built in Claude Code, with a dedicated aesthetic pass
**2026-08-01**

Claude Code builds the structure (databases, relations, views, migration). Mission control
gets its own design pass — Dio wants it genuinely beautiful, and he has design taste plus
Canva connected for cover art. The scheduled-task prompts (triage v2, brief v2) are rewritten
from the Cowork session afterwards, since the schedulers live there.

**Honest constraint.** The Notion API can set icons, covers, callouts and layouts, but some
polish (widgets, custom fonts, fine spacing) only exists as manual drag-and-drop in the
Notion app. Plan: Claude Code builds 90%, Dio does the last 10% by hand with guidance —
that 10% is use, not maintenance.

---

## D14 — The blueprint survived a hole-poking pass; seven fixes adopted
**2026-08-01**

Dio asked Claude to attack the gameplan and structure before building. Eight holes found,
fixes 1–7 adopted: (1) both scheduled tasks paused until after the build to prevent
write-races during migration; (2) heartbeat line opens every brief, and headless Notion
auth gets an end-to-end test before re-enabling; (3) Inbox receipts hidden behind a
filtered view + monthly manual archive sweep (connector cannot delete); (4) **D12 amended**:
notes become a Notes database embedded as filtered linked views inside project pages —
reads in-place as Dio wanted, but queryable and safe from agent/manual layout collisions;
(5) the brief asks a daily habit-recovery question so streaks don't depend on remembering
to tick; (6) ambiguous items possibly dated within 48h push immediately instead of waiting
for the brief; (7) triage audits for projects missing done-when, since Notion can't enforce
required fields.

Hole 8 (system-building as productivity procrastination; the undated onderneming) was
explained to Dio and left as his decision.

---

## D15 — Staging first, go-live later
**2026-08-01**

Dio's call: all current content is test data. Build and polish the entire system first —
function and aesthetics — with sample content, then wipe and load his real life at an
explicit go-live moment. Until go-live: no deadline-chasing, no personal "needs your yes"
items, no onderneming reminders. Supersedes hole 8's proposed rule. Pillars remain as
architecture.

**Why.** He wants to judge and shape the machine without his real obligations tangled in
it. Standard staging/production separation, applied to a life system.
