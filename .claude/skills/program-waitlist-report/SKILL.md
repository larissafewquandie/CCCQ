---
name: program-waitlist-report
description: Builds the Program Waitlist Report for CatholicCare CQ (MBC, SAB, Counselling and Lorena's Child Counsellor waitlist for Emerald and Rockhampton) by pulling data out of CSNet exports, reports, screenshots or pasted lists. Use when Larissa asks for "program stats", a "stats update", "who's on the waitlist", waitlist contact counts, intake or group start dates, or SAB participant numbers.
---

# Program Waitlist Report

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

**Counselling team numbers:** after the waitlist table, give one row per
counselling worker and a team total row:

| Worker | Site(s) | Waitlist | Waitlist contacted | Waitlist not contacted | Caseload | Total open |
|---|---|---|---|---|---|---|

- **Waitlist**: clients with status Waitlist.
- **Waitlist contacted**: waitlisted clients with at least one contact or
  session date recorded. **Not contacted** is the rest, including clients
  whose contact data is missing; add "(N not recorded)" for those.
- **Caseload**: clients with status Initial establishment or Full
  establishment. Leave out placeholder clients, groups and admin activities.
- **Total open** = Waitlist + Caseload.
- **Site(s)**: from the Site column. If it isn't in the data, write "Not
  recorded".
- Name the source report for each worker's numbers. If a worker's caseload
  comes from the Worker Activity List, add "(clients with an October session
  only)" or the matching date range, because that report misses clients with
  no session in the period.
- Workers in the team: every worker the "Workers and programs" table lists
  as Counselling or Counselling team.

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
PROGRAM WAITLIST REPORT as at DD/MM/YYYY

SUMMARY
- MBC: X on waitlist (QPS X | InfoX X); X contacted; X intakes booked
- SAB: X on waitlist; X active participants
- Counselling: X on waitlist; longest wait X days; X start dates booked;
  team caseload X; total open X
- Child Counsellor (Lorena): X on waitlist (Emerald X | Rockhampton X); X contacted; X start dates booked

MBC
  QPS referrals    [table]
  InfoX referrals  [table]
  Flags

SAB                [table] + active participant count
  Flags

COUNSELLING        [waitlist table]
  Team numbers     [table]
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
| Client name | PRIMARY CLIENT (Worker Activity List by Funding) | Yes |
| CSNet client ID | IDENTIFIER (Worker Activity List by Funding) | Yes |
| Worker | PRINCIPAL WORKER (Worker Activity List by Funding) | Yes |
| On waitlist | CURRENT ACTIVITY STATUS = "Waitlist" | Yes |
| Referral / waitlist date | Commencement (Activity search). Activity start date, used as the waitlist date | Use, confirm |
| Most recent contact | Last session (Activity search). One date only, not a count | Yes |
| Location | Site (Activity search) | Yes |
| Referral source (QPS / InfoX) | REFERRAL SOURCE (Client List). Values seen so far are agency types such as Internal or Community services agency, not QPS / InfoX | Not yet |
| Referral / waitlist date | | No |
| Contact entries | CSNet admin notes (team asked on 29/10/2026 to record every contact attempt there with date, method and outcome) | Yes |
| Intake date | | No |
| Next group start date | | No |
| Engagement / support start date | | No |
| SAB active status | | No |
| Child Counsellor location (Emerald / Rockhampton) | | No |

## Known CSNet reports

**Worker Activity List by Funding**: one row per activity, with the columns
IDENTIFIER, PRIMARY CLIENT, PRINCIPAL WORKER and CURRENT ACTIVITY STATUS. The
Parameters sheet holds the worker, funding tag, activity types and date range.

- Status values seen: Waitlist, Initial Establishment, Full Establishment,
  Closed. Count Initial and Full Establishment as engaged.
- The report only lists activities where a session took place in the date
  range, so a waitlisted client with no session in that period won't be on
  it. Say so whenever this report is the only source for a waitlist.
- It has no referral dates, contact dates, start dates or locations. Every
  one of those fields is "Not recorded in CSNet" unless another report
  supplies it.
- Leave out rows that aren't a client from client counts: rows with no
  PRIMARY CLIENT (admin activities, groups such as "Shark Cage - Group 5")
  and placeholder clients such as "Contact Brief". Mention them separately.

**Client List (Excel) with contact details**: one row per client on each
activity, so a family can take up several rows under the same ACTIVITY ID.
The useful columns are ACTIVITY ID, ACTIVITY TYPE, REFERRAL SOURCE, LAST
NAME, FIRST NAME, ROLE, PRINCIPAL USER, SITE, ACTIVITY STATUS, ACTIVITY
FUNDING TAG, COMMENCEMENT DATE and ACTIVITY CLOSED DATE. The date range
applies to session start time.

- Count activities, not rows: one per ACTIVITY ID. The primary client is the
  row with ROLE Aggrieved (or Respondent). Rows with ROLE Other are family
  members, usually children. Rows with ROLE Participant belong to group
  activities (ACTIVITY TYPE "DV Groups - case managed"), so report those as
  groups.
- Some activities are listed twice for the same person. Count them once.
- Status values: Waitlist, Initial Establishment, Full Establishment,
  Inactive, Not Accepted, Closed. Caseload = Initial + Full Establishment.
- COMMENCEMENT DATE is the waitlist date. There are no contact dates, so the
  1st, 2nd and 3rd contacts and attempt counts are "Not recorded in CSNet".
- The report includes addresses, phone numbers, DOB and cultural details.
  Don't copy any of those into the report.
- The T320 DV Counselling funding tag covers the whole DFV service's
  workers, not just the counselling team. Report the counselling team rows
  under Counselling, then give every worker in a separate "Whole T320
  service" table (worker, sites, waitlist, initial, full, caseload) with
  a by-site total.
- Flag Initial Establishment activities that commenced more than 90 days ago.

**Activity search** (CSNet search screen, pasted as text): the columns are
Identifier, Type, Client, Commencement, Last session, Worker, Site and Status.
The filter line above the results names the activity types, sites, statuses
and worker or team.

- Commencement gives the waitlist date, so days on waitlist can be worked out.
- Last session is the most recent contact only. It can't give an attempt
  count or the 1st, 2nd and 3rd contacts; show it as "Last contact" and mark
  the attempt count "Not recorded in CSNet".
- "Worker is, or Team includes" brings in other workers' clients (for example
  Trinity Allan's under a Georgia Stein search). Report each client under
  their own Worker.
- Dates come as "14 Oct 2026 (Wed)". Drop the weekday and any trailing
  number (e.g. "28 Oct 2026 (Wed)1"), then write the date as DD/MM/YYYY.
- Flag engaged (Full or Initial establishment) clients and waitlisted
  clients whose last session was more than 28 days ago.
- Flag identifiers that don't match the client's surname.

**Workers and programs** (as confirmed):

| Worker | Program | Funding tag seen |
|---|---|---|
| Trinity Allan | Counselling | DFV - T320 DV Counselling |
| Lorena Contreras | Child Counsellor (Emerald / Rockhampton) | DFV enhancement - T320 DV Counselling |
| Georgia Stein | Counselling team (DV clients, not funded under Counselling T320) | Not T320 |

## Change log

- 28/10/2026: First version covering MBC (QPS and InfoX waitlists), SAB,
  Counselling and Lorena's waitlist.
- 28/10/2026: Named Lorena's waitlist as the Child Counsellor waitlist and
  split it by location (Emerald and Rockhampton).
- 29/10/2026: Added the Worker Activity List by Funding report, its column
  names, and the worker-to-program table, after the first run.
- 29/10/2026: Added the CSNet Activity search screen (Commencement, Last
  session, Site) and the 28-day no-session flag.
- 29/10/2026: Added the Counselling team numbers table (waitlist, contacted,
  caseload, total open per worker) and listed Georgia Stein as part of the
  Counselling team.
- 29/10/2026: Contact attempts now come from CSNet admin notes. Count each
  dated note of a call, SMS, email or letter as one attempt.
- 29/10/2026: Renamed from program-stats-update to program-waitlist-report.
- 29/10/2026: Added the Client List (Excel) with contact details report:
  count one per activity, leave out contact details, and flag Initial
  Establishment activities older than 90 days.
