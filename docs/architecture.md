# Architecture Notes — Power Automate Probation Tracker

## Design Goals
1. Zero manual intervention — HR touches nothing daily
2. Full audit trail — every reminder timestamped back to SharePoint
3. Bilingual operation — flow logic in English, email content in Traditional Chinese
4. Graceful exit — if no items match the filter, flow ends cleanly

## Trigger Design
Single recurrence fires at both 17:00 and 18:00 TST. Same flow runs twice; 
internal time-branching decides which reminder block executes.
Why not two flows? Single flow = easier maintenance, one version to update.

## Known Limitations
1. No retry logic on Teams/email failure mid-loop
2. Hardcoded to Taipei Standard Time — parameterise for multi-region use
3. No deduplication guard against manual triggers outside schedule
4. IsNewbie closes at 18:00 regardless of actual completion

## Future Improvements
- [ ] Error handling scope around For Each loops
- [ ] Parameterise SharePoint site URL and list ID
- [ ] Add 09:00 morning advance warning
- [ ] Connect Flow B to set CompleteTime automatically
- [ ] Power BI dashboard on top of SharePoint list