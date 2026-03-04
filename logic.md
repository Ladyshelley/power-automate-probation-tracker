Start
├── Get current hour (Taipei time)
├── Get today's date (Taipei time)
├── Set Form Link
├── Query SharePoint: items where DueDate = Today AND CompleteTime = null
│
├── IF hour ≤ 17  →  First Reminder loop
│   └── For each overdue item:
│       ├── Post Teams message (Stage + Name + Form link)
│       ├── Send Email (Chinese) — polite first reminder
│       └── Update SharePoint: write FirstReminderSentTime
│
└── ELSE IF hour ≥ 18  →  Final Reminder loop
    └── For each overdue item:
        ├── Post Teams message (Email + Name + Stage)
        ├── Send Email (Chinese) — urgent final reminder + weekend encouragement 🔋
        └── Update SharePoint: write FinalReminderSentTime + set IsNewbie = No