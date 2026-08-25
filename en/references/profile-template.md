# User Profile Format

The format of `~/.claude/dcea/profile.md`. Follow this structure when creating it for the first time.

**Do not write empty fields.** Fill in only what has been learned, and do not write an unknown field at all.

---

```markdown
# Coffee Extraction Profile

## Equipment
- Grinder:
- Machine:
- Dripper:
- Basket:

## Baseline
Promote only values the user has confirmed 2 or more times. Write the number of confirmations on each item.

- e.g. no astringency at 1:15, slight from 1:16 (confirmed 2 times)
- e.g. 93°C by default, 96°C for beans past 3 weeks (confirmed 3 times)

## Preferences
- e.g. prefers sweetness over acidity
- e.g. especially sensitive to astringency

## Diagnosis History
The 5 most recent. Delete the oldest first. Keep only entries whose result was confirmed.

| Date | Situation | Prescription | Result |
|---|---|---|---|
| 2026-08-25 | Ethiopia at 3 weeks, flat and washed-out · barley tea | pours 3→4 | effective |
```

---

## Logging Rules

- **Write only what the user said.** Do not carry the author's numbers or general principles over as the user's values
- **Do not leave a prescription whose result was not confirmed in the history.** If a prescription was given but the result is unknown, it is not a subject for logging
- When a prescription in the same direction proves effective **2 or more times**, remove it from the history and promote it to the baseline
- If a result contradicts the baseline, roll back the confirmation count or delete the item. A wrong baseline is worse than none
