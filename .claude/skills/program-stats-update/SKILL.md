---
name: program-stats-update
description: Builds the Program Stats Update for CatholicCare CQ (MBC, SAB, Counselling and Lorena's Child Counsellor waitlist for Emerald and Rockhampton) by pulling data out of CSNet exports, reports, screenshots or pasted lists. Use when Larissa asks for "program stats", a "stats update", "who's on the waitlist", waitlist contact counts, intake or group start dates, or SAB participant numbers.
---

# Program Stats Update

Turns CSNet data into one waitlist and engagement update per program. This
skill only covers **pulling the data out and reporting it**. Data entry tasks,
such as uploading waitlisted clients into CSNet, are outside it.

This skill will grow. New programs, fields or rules go in the
"Programs" section using the same layout, and get a line in the change log at
the bottom.

## Inputs

Accept whatever Larissa provides from CSNet:

- CSV or Excel exports, or saved reports
- Screenshots of CSNet screens or lists
- Text pasted from CSNet, case notes or the referral queue

If something a section needs is not in the data, write **"Not recorded in
CSNet"** for it. Never guess or fill in a date, a count or a name. If you can't
tell which program a client belongs to, put them under **"Needs checking"**
rather than picking a program.

Field names change between CSNet screens. Before you report anything, match
each column to the fields below. If a match is unclear, ask once and add the
confirmed column name to the "CSNet field names" table so you don't have to ask
next time.

## Shared rules

- **Today**: use the date of the request for every "days on waitlist" figure,
  and state that date at the top of the update.
- **Days on waitlist** = today minus the referral or waitlist entry date, in
  whole days.
- **Contact attempts** = the number of separate dated contact entries:
  calls, SMS, emails and letters, whether or not the client answered. Count
  entries on the same day separately only if CSNet logs them separately.
- **Dates** use DD/MM/YYYY.
- **Names**: keep client names exactly as CSNet has them, and add the CSNet
  client ID if there is one. This is confidential client data, so keep it in
  the internal update and don't put it anywhere outside it.
- **Flags**, shown after each program's table:
  - No contact recorded yet
  - 3 or more attempts with no successful contact
  - On the waitlist with no start, intake or group date
  - A start date that has already passed, but no engagement recorded

## Programs

### 1. MBC (Men's Behaviour Change)

**Sources:** two referral streams. Report them separately and then give a
combined total.

- **QPS referrals**: the waitlist built from Queensland Police Service referrals
- **InfoXchange referrals** ("InfoX")

**For each client on the waitlist:**

| Field | Notes |
|---|---|
| Client name / CSNet ID | |
| Referral source | QPS or InfoX |
| Referral / waitlist date | |
| Contact attempts | Count, plus the date of each contact |
| Contacted? | Yes / No (whether any successful contact has happened) |
| Intake date | When their intake begins |
| Next group start date | The next MBC group intake they are due to join |

**Totals:** waitlist count for QPS, for InfoX and combined; how many have been
contacted and how many haven't; how many have an intake booked.

### 2. SAB (Supporting Adolescent Boys)

**For each client on the waitlist:**

| Field | Notes |
|---|---|
| Client name / CSNet ID | |
| Referral / waitlist date | |
| Days on waitlist | |

**Active participants:** the number currently engaged in SAB. List their names
only if Larissa asks for them.

**Totals:** waitlist count and active participant count.

### 3. Counselling

**For each client on the waitlist:**

| Field | Notes |
|---|---|
| Client name / CSNet ID | |
| Referral / waitlist date | |
| Days on waitlist | |
| 1st contact date | |
| 2nd contact date | |
| 3rd contact date | If there are more than three, add "+N more" |
| Engagement start date | When their sessions with the counselling team are scheduled to begin |

**Totals:** waitlist count; average and longest days on the waitlist; how many
have a start date booked.

### 4. Child Counsellor waitlist (Lorena): Emerald and Rockhampton

Lorena's waitlist covers two locations. Report **Emerald** and **Rockhampton**
separately, then give a combined total.

**For each client on the Child Counsellor waitlist:**

| Field | Notes |
|---|---|
| Client name / CSNet ID | |
| Location | Emerald or Rockhampton |
| Referral / waitlist date | |
| Contact attempts | Count, plus the date of each contact |
| Support start date | When they are due to begin support |

**Totals:** waitlist count for Emerald, for Rockhampton and combined; how many
have been contacted; how many have a start date.

Every client on this waitlist has to be uploaded into CSNet. That is a data
entry task and not part of this extraction, so don't check it and don't
report on it.

## Output layout

```
PROGRAM STATS UPDATE as at DD/MM/YYYY

SUMMARY
- MBC: X on waitlist (QPS X | InfoX X); X contacted; X intakes booked
- SAB: X on waitlist; X active participants
- Counselling: X on waitlist; longest wait X days; X start dates booked
- Child Counsellor (Lorena): X on waitlist (Emerald X | Rockhampton X); X contacted; X start dates booked

MBC
  QPS referrals    [table]
  InfoX referrals  [table]
  Flags

SAB                [table] + active participant count
  Flags

COUNSELLING        [table]
  Flags

CHILD COUNSELLOR (LORENA)
  Emerald          [table]
  Rockhampton      [table]
  Flags

NEEDS CHECKING     clients with an unclear program or missing key data
```

Default to plain text that can be pasted into an email or Teams message. If
Larissa asks for a spreadsheet or a document, give each program its own tab or
section and put the summary first.

## CSNet field names

Fill this in as columns are confirmed with Larissa.

| Skill field | CSNet column / screen | Confirmed |
|---|---|---|
| Referral source (QPS / InfoX) | | No |
| Referral / waitlist date | | No |
| Contact entries | | No |
| Intake date | | No |
| Next group start date | | No |
| Engagement / support start date | | No |
| SAB active status | | No |
| Child Counsellor location (Emerald / Rockhampton) | | No |

## Change log

- 28/10/2026: First version covering MBC (QPS and InfoX waitlists), SAB,
  Counselling and Lorena's waitlist.
- 28/10/2026: Named Lorena's waitlist as the Child Counsellor waitlist and
  split it by location (Emerald and Rockhampton).
