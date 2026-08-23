# Cadence

When to follow up, how many times, and when to stop. This was the biggest gap in most job search setups: people either never follow up or follow up in a way that reads as pressure.

All timing in **business days**. Columns key off `{{URGENCY}}`.

---

## After applying

| Event | exploratory | active | urgent |
|---|---|---|---|
| Find and message a human at the org | +3 | +2 | same day |
| First status nudge (if no response) | +12 | +8 | +5 |
| Second and final nudge | +25 | +18 | +12 |
| Mark `Ghosted`, stop | +35 | +28 | +20 |

Two nudges. Not three. A third does not produce a response; it produces a reputation.

If the posting states a timeline ("interviews begin in March"), that timeline overrides this table. Follow up one week after their stated date, not before.

---

## After any interview

| Event | Timing | Non-negotiable? |
|---|---|---|
| Thank-you note to each interviewer | within 24 hours | **Yes.** Every round, every person. |
| Nudge if their stated deadline passes | +2 after the date they gave | Yes |
| Nudge if they gave no date | +7 | Yes |
| Second nudge | +14 | Optional |
| Mark `Ghosted` | +21 | — |

Always leave an interview knowing two things: what the next step is and when they expect to decide. If the user doesn't have both, the closing question in `prompts/07-interview-prep.md` failed — fix it for next time.

---

## After outreach (cold or warm)

| Event | exploratory | active | urgent |
|---|---|---|---|
| First follow-up | +7 | +5 | +4 |
| Second follow-up | +18 | +14 | +10 |
| Stop | after 2 | after 2 | after 2 |

Two attempts on a cold contact. A warm introduction gets one follow-up, then it goes back to the introducer — chasing past that costs the introducer's relationship, not just the user's.

---

## Employment-status adjustment

```
IF EMPLOYMENT_STATUS = unemployed OR underemployed THEN
  tighten one column (exploratory reads active; active reads urgent)

IF EMPLOYMENT_STATUS = employed AND the search is confidential THEN
  - never follow up from a work address or a work device
  - do not accept daytime calls that require an unexplained absence
  - keep the pace but not the urgency in the wording
```

---

## Persona adjustment

```
IF PERSONA = executive THEN
  - Everything runs slower. Add roughly 50% to every interval.
  - Search-firm processes have their own clock; the recruiter sets it. Ask, then follow it.
  - Follow up with the search partner, not the hiring company, while a firm is engaged.

IF PERSONA = entry-level THEN
  - Campus and cycle-based hiring has fixed dates. The posted timeline always wins.
  - Large-employer programs genuinely take weeks. Slow is not rejection here.
```

---

## Weekly rhythm

Once a week, same day, run `prompts/10-weekly-review.md`:

1. Anything past its nudge date — send or close it out.
2. Anything past its ghost date — mark it, record the reason, move on.
3. Log the week's volume against `{{WEEKLY_APPLICATIONS}}` and `{{WEEKLY_OUTREACH}}`.
4. Look at the elimination-reason cluster. Is the search aimed where it should be?

---

## Tone rules for every follow-up

- One short paragraph. Three sentences is plenty.
- Add something — a relevant article, a thought about their problem, a new credential. Never just "checking in."
- No guilt, no urgency theater, no "I haven't heard back." State the interest, offer the next step, stop.
- Reply in the existing thread. A new email restarts a conversation they were already having.
- Silence is information, not insult. Recruiters carry 30 to 60 open roles.

---

## When to stop

Mark `Ghosted` at the interval above and mean it. A closed row is not a failure; it's capacity returned to the pipeline. Roles have reopened months later — that's the second-nudge close-out's job:

> Understood — I'll assume the timing didn't line up. If things change, I'd still be glad to talk.

That sentence has restarted more processes than any third nudge ever has.
