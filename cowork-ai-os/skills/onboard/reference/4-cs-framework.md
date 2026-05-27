# The 4 Cs Framework — Cowork AI OS Audit Rubric

This is the scoring rubric for `/audit`, `/tune-up` Gate 2, and Phase 9 of onboarding.

Score the user's Cowork AI OS on a **0–100 scale**. 25 points per C.

---

## C1 — Context (0–25)
**Question:** How much does Claude actually know about this person and their business?

Context is the foundation. Without it, every skill produces generic output. With it, everything Claude writes sounds like the user wrote it.

| Score | What it means |
|---|---|
| 0–8 | No `about-me/` files, OR files exist but still have `~~placeholder` text unfilled. Claude is working blind. |
| 9–16 | `about-me/about-me.md` and `business-brain.md` are filled in, but `writing-rules.md` has fewer than 3 real writing samples. Voice isn't captured yet. |
| 17–22 | All 4 `about-me/` files complete (`about-me.md`, `business-brain.md`, `writing-rules.md`, `memory.md`). Writing samples are real. `memory.md` has 5+ entries. |
| 23–25 | Everything above, PLUS `business-brain.md` is kept current (updated within the last 30 days) AND `memory.md` gets appended every session (no gaps longer than 7 days). |

**What counts as the 4 about-me/ files:**
1. `about-me/about-me.md` — who they are, what they do, what they care about
2. `about-me/business-brain.md` — offers, ICP, 90-day priorities, time sinks
3. `about-me/writing-rules.md` — voice rules + at least 3 real writing samples
4. `about-me/memory.md` — running log of sessions, pivots, decisions

**Scoring tips:**
- If `~~placeholder` text is found anywhere, cap at 8 regardless of other files.
- One writing sample scores 9–13. Three+ real samples (not the generic ones from the template) scores 17+.
- If `memory.md` was last appended more than 14 days ago, deduct 3 points from wherever they'd otherwise land.

---

## C2 — Connections (0–25)
**Question:** How many of the 7 buckets are actually reachable by Claude?

The 7 buckets: Revenue, Customer, Calendar, Comms, Tasks, Meetings, Knowledge.
See `reference/7-buckets.md` for the full descriptions.

| Score | What it means |
|---|---|
| 0–8 | 0–2 buckets reachable. Gmail and Calendar might be connected — nothing else. |
| 9–16 | 3–4 buckets reachable. Beyond Gmail/Calendar, at least one of Tasks, Meetings, or Customer is connected. |
| 17–22 | 5–6 buckets reachable. A solid stack — most of the user's day is visible to Claude. |
| 23–25 | All 7 buckets reachable, AND write actions are safely configured (reads: act without asking; writes: ask before acting; sends/deletes: blocked or ask). |

**Scoring tips:**
- "Reachable" means the connector is enabled AND Claude can successfully pull live data from it. Ask the user to confirm if you can't verify from Settings.
- A bucket where the connector is installed but broken/disconnected counts as 0.
- If any connector has "send" or "delete" set to "act without asking", deduct 5 points (safety violation).
- Gmail alone = Bucket 4. Google Calendar alone = Bucket 3. These are the two must-haves — at Phase 9 the user should have both.

---

## C3 — Capabilities (0–25)
**Question:** How many things can Claude actually do for this user?

Capabilities measure the breadth of skills and plugins installed and actually used — not just installed and forgotten.

| Score | What it means |
|---|---|
| 0–8 | Only used `/onboard`. No other Cowork AI OS skills have been run. |
| 9–16 | Cowork AI OS skills used regularly (at least `/morning-brief`, `/voice-writer`, or `/audit` run at least once). No additional Anthropic role plugins installed. |
| 17–22 | Cowork AI OS skills + at least 1–2 Anthropic role plugins installed (e.g., productivity, marketing, sales). AND at least 1 custom skill built via `/add-skill`. |
| 23–25 | Everything above, PLUS custom skills are refined on a regular cadence (at least one revision or new skill built in the last 30 days, per `memory.md`). |

**What counts as "Cowork AI OS skills":**
- `/morning-brief`
- `/voice-writer`
- `/audit`
- `/level-up`
- `/tune-up`
- `/browse-skills` and `/browse-connectors`
- `/add-skill`

**Scoring tips:**
- Check `about-me/memory.md` and `about-me/skills-tour.md` for evidence of skill usage.
- A skill installed but never run scores the same as a skill not installed — count only used skills.
- If the user can describe what a custom skill does and when they last used it, it counts.

---

## C4 — Cadence (0–25)
**Question:** How much of this user's AI OS runs automatically vs only when they remember to ask?

Cadence is what separates an AI OS from a chatbot. The morning brief should fire without the user having to ask. The weekly tune-up should happen on a schedule.

| Score | What it means |
|---|---|
| 0–8 | No scheduled tasks. Everything only runs when the user manually triggers it. |
| 9–16 | Morning brief is scheduled and firing. Nothing else. |
| 17–22 | Morning brief + weekly tune-up both scheduled and firing. At least one other custom recurring routine exists. |
| 23–25 | Multiple routines firing reliably. AND the user has a "computer awake" strategy in place so scheduled tasks don't miss (always-on machine, or they've accepted the wake-and-run tradeoff). |

**Scoring tips:**
- "Firing" means the user confirms it ran at least once as scheduled — not just that it was set up.
- If the morning brief is scheduled but the computer sleeps, it doesn't fire → count as 8 or less unless the user has a mitigation strategy.
- The quarterly connector audit (calendar event created in Phase 5) counts as a cadence item — award 1–2 bonus points if it exists.

---

## How to compute the total

1. Score each C independently using the rubric above.
2. Add the four scores: Context + Connections + Capabilities + Cadence = total (0–100).
3. Compare to the most recent entry in `about-me/audit-log.md` to compute the delta.

**Interpreting the total:**
- **0–30:** Foundation phase. Focus on Context first — nothing else works well without it.
- **31–55:** Building phase. At least 2 Cs are solid. Push the lagging C next.
- **56–75:** Operational. The system is working. Tune-up will find the next leverage point.
- **76–90:** Optimized. Rare. Keep refining the custom skill layer.
- **91–100:** Infrastructure-grade. Morning operates itself. Claude is a genuine business partner.

---

## How to find the top leverage gap

**The top gap is NOT automatically the lowest-scoring C.** It's the C where one specific change produces the highest return.

Examples:
- Context = 22/25 (just missing a 3rd writing sample) vs Connections = 11/25 (5 buckets unconnected) → **Connections is the gap**. Adding ClickUp unlocks task pulls in the morning brief — far more leverage than one more writing sample.
- Cadence = 6/25 (nothing scheduled) + everything else solid → **Cadence is the gap**. Getting the morning brief on a schedule is a transformational unlock.
- Capabilities = 14/25 (no custom skills) + user has described a manual process they repeat 5x/week → **Capabilities is the gap**. One `/add-skill` session pays back immediately.

Always lead with the highest-leverage single change. The user can say "too big" and you'll downshift — but lead with the move that compounds most.
