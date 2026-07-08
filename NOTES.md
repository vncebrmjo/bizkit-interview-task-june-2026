# Notes

### Fix explained
`dates_overlap` only checked if the new booking's start fell inside the existing range, missing cases where it starts earlier and runs into it. Fix checks both directions:

```python
start_a <= end_b and start_b <= end_a
```

### Failure example
Existing booking: **Jan 10–15**
Original code wrongly allowed: **Jan 5–12** (overlaps Jan 10–12)
Fix now correctly **rejects** it.

### AI use
Used Claude to find root causes and draft fixes for each bug. Verified by reproducing each bug on the original code first, then re-testing the same scenarios after the fix via the UI and `bookings.json`.