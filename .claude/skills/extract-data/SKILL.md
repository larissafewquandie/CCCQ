---
name: extract-data
description: Turn pasted "Activities and Clients" search results from the client management system into a sorted, filterable Excel spreadsheet. Use when Larissa pastes a search result list (lines like "Searching for Activities and Clients where Client is ...", followed by SURNAME-123456 / DV / client name / dates / worker / location / status) and asks to extract, tabulate, log or put it into a spreadsheet.
---

# Extract Data: client search results to .xlsx

## What the input looks like

A copy-paste from the system's Activities and Clients search. Each result is a vertical block:

```
Searching for Activities and Clients where Client is JANE. Sorting by Commencement descending.
|
SMITH-000001        Activity ID
DV                  Program
Jane SMITH          Client
17 Apr 2026 (Fri)   Commencement
22 Apr 2026 (Wed)   Last session (can end in a footnote digit, or read "No sessions")
Worker Name         Worker
Rockhampton         Location
Closed              Status
```

Stray `|` lines and blank lines are ignored.

## Steps

1. Save the pasted text exactly as given to a temporary file in the scratchpad directory (never in the repo: it's client data).
2. Run:
   ```bash
   python3 .claude/skills/extract-data/scripts/extract_activities.py <paste.txt> <scratchpad>/<Name>_activities_<YYYY-MM-DD>.xlsx --match <searched first name>
   ```
   `--match` takes the name from the "where Client is X" line. It marks each row as an **Exact** first-name match or a **Variant** (e.g. a search for Kristy also returns Kristyn and Kristy-Lee), so the right client can be filtered out.
3. Send the .xlsx to Larissa. In the reply give:
   - the number of records, and how many are open vs closed
   - the variant-name rows, which are probably different people
   - every warning the script printed, especially an **incomplete last record**, which means the paste was cut off. Ask for the rest if so.
   - footnote digits (e.g. `27 Oct 2026 (Tue)1`): the script keeps the digit in a Footnote column. Say what it means only if Larissa has explained it.

## Output

- **Activities** sheet: Activity ID, Program, Client, Commencement, Last Session (real dates), Days Open, No Sessions, Footnote, First Name Match, Issues. Formatted as an Excel table with filters; rows with issues are highlighted yellow.
- **Summary** sheet: the search criteria and sort, the record count, and counts by status, location and worker.

## Rules

- This is DV client data. Don't commit it, publish it as an artifact, or send it to any external service. Keep outputs in the scratchpad unless Larissa names another location.
- Don't fix or guess missing values. Show them as blank and flag them.
- If the paste has a different layout (other columns, another search type), don't force it through the script. Read it by hand and build the sheet with the same columns plus whatever is new, then offer to extend the script.
