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
