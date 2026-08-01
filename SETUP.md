# Second Brain — start here

This folder is the whole project. Drop it somewhere permanent on your computer
(Documents, a code folder, wherever) and open Claude Code inside it.

---

## One-time setup

**1. Install Claude Code** (macOS, Linux, or Windows via WSL):

```
curl -fsSL https://claude.ai/install.sh | bash
```

Windows has its own PowerShell installer — see https://code.claude.com/docs/en/quickstart

Check it worked:

```
claude --version
```

**2. Open Claude Code in this folder:**

```
cd path/to/second-brain
claude
```

**3. Connect Notion.** Claude Code needs its own connection to Notion — the one in the app
doesn't carry over.

```
claude mcp add --transport http notion https://mcp.notion.com/mcp
```

Then inside the session type `/mcp`, pick `notion`, and choose **Authenticate**. Your browser
opens and you sign in to Notion.

⚠️ That URL is the one Notion publishes, but I couldn't verify it against Anthropic's own docs.
If the command fails, check Notion's MCP page for the current address, or ask Claude Code
"help me connect the Notion MCP server" — it can look it up.

---

## What happens automatically

`CLAUDE.md` loads at the start of every session, and it imports the spec, the interview and
the decision log. So you don't need to explain anything, ever. Just open Claude Code and say
what you want.

You can confirm what got loaded by typing `/context` in a session.

---

## Your first message in Claude Code

Copy this:

> Read CLAUDE.md and confirm you understand the project. Then build phase 2 — the Inbox
> database in Notion — and show me what you made before doing anything else.

---

## What's in here

| File | What it is |
|---|---|
| `CLAUDE.md` | Loaded every session. How to work with you, the eight rules, permissions, current state, and what to build next. |
| `decisions.md` | The decision log. Every choice that would be expensive to re-argue, with the reasoning. Claude appends to this as you go. |
| `docs/spec.md` | The full system spec — rules, the Inbox schema, mission control, failure signals. |
| `docs/interview.md` | The raw interview findings. Everything in the spec traces back to here. |
| `docs/gameplan.md` | The phases, with where you are now. |
| `docs/marketing-program.md` | The marketing system broken into eight ordered projects. |

---

## The one rule for you

If you ever catch yourself tidying, re-tagging, or reorganising anything — stop and say so.
That's not you being diligent, it's the system failing the same way the last four did.
