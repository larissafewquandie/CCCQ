---
name: follow-up-tracker
description: Organises and prioritises Larissa's follow up tasks inside an executive functioning system, keeps one live tracker table in "Follow Ups/Follow Up Tracker.md", moves finished items to a Done log and writes a summary of what was achieved. Use whenever Larissa adds follow ups ("add this to my list", "I need to follow up with", pastes a list of tasks or meeting actions), marks something complete ("done", "finished", "sent it", "ticked off"), asks what to do next ("what should I work on", "what's my focus today", "I'm stuck/overwhelmed"), or asks for a summary of what she did ("what did I get done", "weekly wrap up", "end of day summary"). Also trigger on "update my follow ups", "run my follow up tracker" or /follow-up-tracker.
---

# Follow Up Tracker (Executive Functioning System)

This skill runs Larissa's follow up list as an external brain. The goal is to take
the load off working memory, make the next step obvious, and show progress so
wins are visible. Every run reads the tracker, updates it, re-prioritises it and
rewrites the summary.

The single source of truth is `Follow Ups/Follow Up Tracker.md` (repo root). If it
does not exist, create it from the structure in "Tracker file layout" below.

## House style

- Australian spelling (organise, prioritise, behaviour).
- Dates as DD/MM/YYYY with the weekday, e.g. Fri 23/10/2026. Always convert
  relative dates ("next Tuesday", "end of week", "in 2 days") into real dates using
  today's date. Business days are Monday to Friday.
- No em dashes. Short, plain, kind sentences. No guilt language about overdue items
  ("carried over" not "failed", "still open" not "behind").
- De-identify clients. Use initials or a file reference, never full client names
  of PUVs, victim survivors or children in the tracker.

## The executive functioning principles the system follows

1. **Capture everything, decide later.** Anything Larissa mentions goes into the
   table first. Sorting happens after capture so nothing is lost.
2. **Every task gets a Next Step.** A concrete, physical first action that can be
   started in under 2 minutes of thinking, starting with a verb
   ("Email Tennille asking for the CSNet result", not "Sort out CSNet"). Big tasks
   are chunked: the task row stays, the Next Step is only the very next chunk.
3. **Limit the focus list.** Only 3 items go in Today's Top 3. Everything else is
   visible but out of the way. This protects against overwhelm and task switching.
4. **Match tasks to energy.** Each task is tagged High, Medium or Low energy so
   Larissa can pick a Low energy task when depleted instead of stalling.
5. **Make time visible.** Each task has a time estimate. Under 15 minutes is a
   Quick Win and gets batched.
6. **Separate waiting from doing.** Tasks blocked on someone else move to Waiting
   On with the person and a chase date, so they stop taking up attention.
7. **Show the wins.** Completed items are never deleted. They move to the Done log
   with what was actually done, and the summary celebrates progress.

## Priority system

Score each open task, then assign the priority band.

**Urgency**
- 3 = overdue, due today or next business day, or has a safety, risk, court,
  Child Safety, HRT or compliance deadline
- 2 = due within the next 5 business days
- 1 = no hard date or more than 5 business days away

**Impact**
- 3 = client safety, risk management, legal or funding obligation, or someone else
  is blocked until this is done
- 2 = team, supervision, reporting or stakeholder work
- 1 = admin, nice to have, personal tidy up

**Score = Urgency + Impact** (add 1 if the task has been open more than 10 business
days, so old items do not quietly rot).

| Band | Rule | Meaning |
|---|---|---|
| P1 Do Now | Score 5 or more, or any safety or risk item | Goes into Today's Top 3 first |
| P2 Schedule | Score 4 | Book a time block for it this week |
| P3 Quick Win | Time estimate 15 min or less and not P1 | Batch them together in one sitting |
| P4 Park | Score 3 or less | Visible but not for this week, or delegate |

Tie breakers inside a band: earlier due date first, then higher impact, then
longest open.

Never downgrade a safety, risk or suicidal ideation follow up below P1, whatever
the score.

## What to do on each run

1. **Read** `Follow Ups/Follow Up Tracker.md` and note today's date.
2. **Capture new items** Larissa gave. For each one create a row with the next
   free ID (FU-001, FU-002 and so on, never reuse an ID), and fill every column. If
   something essential is missing (who it involves, or the due date when it sounds
   time critical) make the best sensible guess, mark it with `(?)` and list it under
   "Check with Larissa" in the summary instead of stopping to ask.
3. **Mark completions.** When Larissa says something is done, match it to the row
   (by ID, keyword or person). Remove it from Active or Waiting On and add it to the
   Done log with the completion date and a one line "What I did" outcome written
   from what she said. If the completion creates a new follow up (e.g. "sent the
   email, now waiting for a reply"), add that as a new row, usually in Waiting On.
   If a match is ambiguous, pick the closest and say which one you ticked off.
4. **Update Waiting On.** If a chase date has arrived, move the item back to Active
   with Next Step "Chase [person] about [thing]".
5. **Re-score and sort** every open task using the priority system. Re-check the
   Next Step is still the real next action.
6. **Rewrite the Summary section** at the top of the file (see layout).
7. **Save the file**, then reply in chat with:
   - what changed this run (added, completed, moved), in 1 to 4 short lines
   - Today's Top 3 with their Next Steps
   - one encouraging line about progress, grounded in the Done log
   - any "Check with Larissa" questions
   Keep the chat reply short. The file holds the detail.
8. If the repo is a git checkout, commit the tracker with a message like
   "Follow ups: completed FU-004, added FU-009" and push to the working branch.

## Summary requests

When Larissa asks what she did (end of day, end of week, a date range or for line
management or supervision), build it from the Done log:

- Group completed items by theme (Client and risk, Stakeholders and agencies,
  Team and supervision, Reporting and admin, Other).
- One dot point per item using the "What I did" text, with the date.
- Close with counts: completed in the period, still open, P1 items still open, and
  items waiting on others.
- Write it so it can be pasted into a line management record or email.

## Overwhelm mode

If Larissa says she is stuck, overwhelmed, foggy or does not know where to start:
offer only ONE task, the highest P1 that fits Low or Medium energy, show its Next
Step, its time estimate, and suggest a 15 minute timer. Do not show the whole list.

## Tracker file layout

The file uses these sections in this order. Keep the table columns exactly as
below so the file stays consistent between runs.

```markdown
# Follow Up Tracker

_Last updated: Fri 23/10/2026_

## Summary

**Today's Top 3**
1. FU-00X Task, Next Step (time, energy)
2. ...
3. ...

**Quick Wins batch** (15 min or less): FU-00X, FU-00Y
**Overdue / carried over:** FU-00X (due DD/MM)
**Waiting On, chase today:** FU-00X Person
**Done this week:** N items. Highlight of the most meaningful one.
**Check with Larissa:** anything marked (?)

## Active

| ID | Priority | Task | Next Step | Who / Where | Due | Energy | Time | Added |
|---|---|---|---|---|---|---|---|---|

## Waiting On

| ID | Task | Waiting on | Since | Chase on |
|---|---|---|---|---|

## Done

| ID | Task | Completed | What I did |
|---|---|---|---|
```

Active rows are sorted P1, P2, P3, P4 then by the tie breakers. The Done log is
newest first. Done rows are kept forever so summaries can cover any period.
