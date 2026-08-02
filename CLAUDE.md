# Second Brain — project context

You are building and running Dio's second brain. The goal: **capture everything, surface
almost nothing, and take all the organising work off him.**

@docs/spec.md
@docs/interview.md
@decisions.md

---

## Who you're working with

**Explaining things to Dio**
- Give the reason, not just the conclusion. He stalls when he doesn't know *why* something
  is the way it is.
- Show how the parts connect. Naming pieces isn't enough — he needs relationships and flow.
- Tell him what things are officially called. He's self-taught, so he often grasps a concept
  without knowing its proper name or the standard professional method. That's usually the
  missing piece, not the idea.
- Don't simplify the substance. His gaps are vocabulary and formal structure, not ability.
  Drop correct terms into normal conversation instead of staging a lesson.
- He is strongly visual. Build diagrams, flowcharts, tables or charts on your own initiative
  whenever something is complex, has moving parts, or needs an overview — actual visuals, not
  descriptions of them. If unsure whether one helps, make it anyway.
- If he says he doesn't get it, find the missing link between steps rather than rephrasing.

**Working with Dio**
- Work in phases. Plan first, his go-ahead, then one phase at a time, with a short
  "where we are, what's next" between each.
- Match effort to the ask: small reversible things just do and state your assumptions.
  Projects, hard-to-undo or research-heavy work get a plan and his confirmation first.
- When he's vague, ask 2–3 questions or offer to interview him. Don't guess.
- Push back when he's wrong and say what shape would work better.
- Reply in whatever language he wrote in.

**Context**
- Solo. Building personal automation tools for his own workflows, not a product.
- New to Notion. He uses it; he never builds or maintains it.
- He forgets things. Assume anything unwritten is lost, and tell him when something is
  worth keeping.
- Often on mobile. Capture must work from a phone in one step.
- Diagnosed ADHD. Context only — don't mention it or frame answers around it.

---

## The eight rules

1. **Push is rationed, pull is generous.** What the system *sends* him is cut to almost
   nothing. What he *opens* can show everything.
2. **Many ways in, one place it lands.** Chat, Notion quick-add, dictation, forwarded mail —
   all routes end in the same Inbox. The destination is the single source of truth.
3. **He uses it, he never maintains it.** Ticking something done is use. Deciding where it
   belongs, naming, tagging, tidying — never his.
4. **Reminding comes to him at 05:30.** One brief, timed for his commute. Short enough to
   listen to, since he may be driving.
5. **The day arrives as an order, not a list.** Overview, then today in a decided sequence.
6. **Every filed item shows the assumption.** One visible line: what you guessed.
7. **Two-way doors yours, one-way doors his.**
8. **Architecture is planned upfront; limits wait for evidence.** The full workflow gets
   designed on paper and approved by Dio before building — that's how he works. Only numeric
   limits (caps, quotas) must wait for real usage evidence.

---

## Permissions

**Do without asking (two-way doors)**
File, sort, name, tag, link, re-file, tidy. Build and maintain views and the dashboard.
Draft messages and leave them waiting. Propose structural changes.

**Wait for an explicit yes (one-way doors)**
Anything another person sees. Deleting or archiving. Changing how the system is structured.
Calendar writes — batched into one confirmation, never one per item.

---

## Current state (updated 2026-08-02)

- **Phases 0–5 are COMPLETE.** Protocol, interview, spec v2, Notion basics, Inbox, loop
  proven with real data, triage + brief, and the full structure (Areas, Projects, Tasks,
  Habits + log, Notes, mission control).
- **Phase 5 closed 2026-08-02.** Structure built in Claude Code and approved by Dio
  ("shape is ok"); automations v2 installed, end-to-end tested and re-enabled from Cowork
  (D16). **The system is feature-complete in staging.**
- **Still open before go-live**: (a) the aesthetic pass on mission control — deferred at
  Dio's call, owner not yet decided; (b) Dio's four manual view-filter taps; (c) the
  go-live checklist below.

### Phase 5 build record (2026-08-01)

All under the "Second brain — system" page (`3afa4e35-74a0-8122-996a-e9bff8e2b500`),
except Mission control which is top-level (`3afa4e35-74a0-8104-808c-dd3a10cf35b5`).

| Database | Data source ID |
|---|---|
| Areas (7 pillars seeded) | `7cf4fea9-14ae-43a8-aaf8-7f3e4817f726` |
| Projects (4 seeded) | `5b8f20be-6b78-4ad0-8cff-10bad42ef39b` |
| Tasks (4 seeded) | `97e8055f-fd08-4c77-8838-ca8565631357` |
| Habits (5 seeded) | `12cacfce-4a76-43fd-b91e-edff361ae6c9` |
| Habit log (empty until briefs run) | `537878eb-3cc4-4f21-b4ee-3b80d871a883` |
| Notes (4 seeded) | `d8c3d520-cd48-47ba-8842-a5e59f15e5f0` |

- Relations: Task→Project ('Tasks' synced), Task→Area, Project→Area, Habit→Area,
  Habit log→Habit ('Log' synced), Note→Project ('Notes' synced), Note→Pillar.
  Projects.Progress = rollup percent_checked of Tasks.Done. Habits."Days done" = rollup
  checked of Log.Done. Habits.Streak = number, computed by triage v2, never typed.
- Tasks."Today order" (number): triage writes the day's sequence; Today views sort by it.
- Views: Tasks (Today / By pillar board / Calendar / Waiting on / Parked), Habits (Streaks),
  Inbox default renamed "Capture" filtered Status=new + "Receipts" view (Status≠new).
  Mission control: Today / Pillars / Projects / Streaks / Waiting on / Coming up / Parked.
- All 24 Inbox rows are receipts: Status=sorted, "→ Filed:" link in My assumption.
- **API limitation found**: view DSL silently drops FILTER on relation properties (grouping
  works). The four "Notes — <project>" views embedded in project pages are therefore
  UNFILTERED until Dio adds the one-tap filter in the app (goes on the D13 manual-finish
  list), or until the aesthetic pass finds a better shape. Also: no relative-date filters,
  so "Coming up" shows all undone dated admin, not a rolling fortnight — triage keeps it
  honest instead.
- Scheduled tasks were PAUSED during the build per blueprint step 0; re-enabled 2026-08-02
  after the end-to-end test (see "Automations v2" below).

### Automations v2 — LIVE (verified 2026-08-02, from Cowork)

- Triage v2 and brief v2 prompts (drafted here as `docs/prompts/*.md`) are installed on the
  scheduled tasks and RE-ENABLED after a passed end-to-end test: dummy Inbox item → routed
  to Tasks (Kind set, "on Monday" parsed to 2026-08-03, Area relation linked, assumption
  written) → Inbox row became a receipt with a Filed link → ledger incremented to triaged=1.
  **Headless Notion auth works — fix 2 closed.**
- Ledger lives at the bottom of the Morning Brief page: "TRIAGE LEDGER: triaged=N" plus
  "QUESTIONS:" — currently holding the 4 done-when questions from the audit, to be answered
  at go-live, not before (staging).
- Hourly triage at :36; brief daily 03:30 UTC. DST: shift both an hour in late October.
- Verified from Claude Code 2026-08-02: E2E task row and ledger both present in Notion.

### Go-live checklist (when Dio says the system works AND looks right)

1. Dio approves function + look.
2. Archive the test content (his job — the connector cannot archive).
3. He loads his real life in.
4. Delete the ⚠️ STAGING blocks from BOTH trigger prompts — this is what turns pushes,
   deadline-chasing and "Needs your yes" back on.
5. Answer the done-when questions sitting on the ledger.
6. Re-time the brief if his commute has changed.

### Live infrastructure

- **Inbox database**: `d8aa86c5-ab1e-471f-bfcd-bcf735d8cf92`, data source
  `ad464194-0f80-4cff-8894-3b1941bfc2ee`. Type select now includes `area` (added when
  Dio's pillars arrived — real data forced the schema change). ~24 items filed, each with
  an assumption line.
- **Seven pillars** exist as `area` items: Faith, Family, Health, Finances & admin,
  Learning & research, Work & business, Order-flow trading (its own pillar at Dio's
  explicit request — it sits beside his business, not inside it).
- **Morning Brief page**: `3afa4e35-74a0-812a-bf64-ce962680d18f` — rewritten daily.
- **Scheduled tasks** (server-side, run without any session):
  - `trig_01UdbAS9Dh2Hz21SMDTK4Wwq` — overnight triage, 02:30 UTC (04:30 NL summer).
  - `trig_0177BfPT4WgxvxkDozg6Crvk` — morning brief, 03:30 UTC (05:30 NL summer),
    push notification carries the single most important line.
  - **DST warning**: schedules are UTC. When NL switches to winter time (late October),
    both fire an hour early local — shift them then.
- Notion workspace still contains Notion's starter templates; Dio may bin them himself.
  **The Notion connector has no delete tool.** Never promise to delete anything in Notion.

### ⚠️ STAGING MODE — read this first

Dio's explicit instruction (2026-08-01): **everything currently in the system is TEST DATA.**
The 24 Inbox items, the tasks, the dates, the onderneming, the habits — treat them as sample
content for building and testing, NOT as live commitments. Do not chase him about deadlines,
do not ask for done-when dates on his real projects, do not surface "Needs your yes" items
about his personal life. The job right now is exactly two things: make the system WORK the
way he specified, and make it LOOK the way he wants. When both are true, he declares
**go-live**: sample content gets archived, he loads his real life in, and only then do
deadlines, briefs and nagging become real. The seven pillars stay — they're architecture,
not content.

### Phase 5 — APPROVED, build it (this is your job if you're reading this in Claude Code)

Blueprint approved by Dio 2026-08-01 with three amendments (D11–D13):

0. **BOTH SCHEDULED TASKS ARE PAUSED** (fix 1 — race prevention). Do not re-enable them;
   that happens from the Cowork session after the build, when their prompts are rewritten
   for the new structure. Until then, chat captures are filed live and quick-adds wait.
1. **Databases to create**: Areas (7 pillars, promoted from Inbox items), Projects
   (required "done-when" field; progress = rollup % of tasks done; decisions log inside
   each page), Tasks (incl. dated admin + commitments; relations to Projects and Areas),
   Habits (his 5 practices + a daily-log database behind them; streaks computed, never typed).
   **Notes = one Notes database** (fields: note, project relation, pillar relation), but
   every project page embeds a linked view of it filtered to that project — so notes READ
   in-place, per Dio's wish, while staying queryable, linkable from two projects, and safe
   from agent-edit/manual-layout collisions (D12 as amended by D14).
2. **Inbox becomes a buffer**: keeps its schema; triage routes items OUT to their homes and
   leaves the Inbox row as a receipt (status sorted + link to destination). Drains hourly.
3. **Relations**: Task→Project (optional), Task→Area (required if no project), Project→Area
   (required), Habit→Area. Progress and streaks are rollups/computed — never typed by anyone.
4. **Views**: Today, By pillar (board), Calendar, Waiting on, Parked, Streaks. Plus on the
   Inbox: a default view filtered to Status = new (so receipts are invisible), and a
   "Receipts" view of sorted rows for the monthly archive sweep (fix 3).
5. **Migration**: route the ~24 existing Inbox items. Ask Dio for each real project's
   done-when — that's his decision, not a guess.
6. **Mission control**: one page, blocks = Today / Pillars health / Projects with progress /
   Streaks / Waiting on / Coming up / Parked. Dio wants it BEAUTIFUL — icons, covers,
   callouts, clean layout. Do a dedicated aesthetic pass; Canva is available for cover art.
   Whatever the API can't style, leave crisp and tell Dio the two manual drags that finish it.
7. **After the build**: tell Dio to return to the Cowork session so the triage + brief
   scheduled prompts get rewritten to route into the new structure (schedulers live there),
   tested end-to-end (one dummy "new" item, fire the trigger manually, verify it routed —
   this is the headless-Notion-auth test, fix 2), and re-enabled.

### Triage v2 / brief v2 spec (rewritten in Cowork after build — fixes 2–7)

- **Heartbeat**: the brief ALWAYS opens with "Triaged N since yesterday." A missing brief
  or missing number is itself the alarm that automation broke.
- **Habit recovery**: the brief asks one question — "Yesterday's habits: which happened?" —
  because streaks must not depend on Dio remembering to tick (that contradicts the premise).
- **Urgency escape hatch**: triage batches ambiguity into "Needs your yes", EXCEPT items
  both ambiguous and possibly dated within 48h — those push to his phone immediately.
- **Done-when audit**: every triage pass checks for projects missing done-when (hand-created
  ones will lack it; Notion can't enforce required fields) and queues them for his yes.
- **Receipt sweep**: on the 1st of each month the brief asks Dio to archive the Receipts
  view — 30 seconds, manual, his job only because the connector cannot delete/archive.

### Open items (all deferred to go-live per D15)

- The onderneming date and done-when answers for the four real projects — they sit on the
  ledger; do NOT chase them during staging.
- Triage runs HOURLY. Ambiguous items: best-guess filing + flag; questions surface in the
  brief's "Needs your yes", never as interruptions (D11).

## Failure signals — stop and raise immediately

- He's organising something → work leaked back to him.
- The brief becomes noise → it's too long or showing the wrong things.
- Capture feels slow → remove the offending step whatever it costs downstream.
- The dashboard goes unopened → it shows what you thought mattered, not what he wants.
- You guessed wrong twice → your inference rules are wrong, not the individual item.
