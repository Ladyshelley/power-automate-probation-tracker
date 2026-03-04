# SharePoint List Schema — Probationary Checklist

## List Name

KSCC Newbie Probationary Check List (or your equivalent name)

## Purpose

Tracks each new employee's probationary stage check-in status.
The Power Automate flow reads and writes to this list daily.

## Columns

| Column Name | Type | Required | Notes |
|---|---|---|---|
| NewbieName | Person | Yes | Employee being tracked |
| StageCode | Choice | Yes | Stage identifier e.g. W1, W2, M1, M3 |
| DueDate | Date | Yes | Date the check-in is due |
| CompleteTime | Date/Time | No | Null until employee submits the form |
| FirstReminderSentTime | Date/Time | No | Written by flow after 17:00 reminder |
| FinalReminderSentTime | Date/Time | No | Written by flow after 18:00 reminder |
| IsNewbie | Yes/No | Yes | Set to No after final reminder cycle |

## Notes

- DueDate must use date-only format (yyyy-MM-dd) to match the flow filter
- CompleteTime is populated by Flow B (form submission handler) — not manually
- IsNewbie = No signals the end of the automated reminder cycle for that stage
