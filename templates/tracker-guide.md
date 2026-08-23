# Tracker guide

`tracker.csv` is one row per role. Open it in any spreadsheet app, or let the agent maintain it. It is the only file that must stay current — a stale tracker is worse than none, because you start trusting it.

## Columns

| Column | What goes in it |
|---|---|
| `date_added` | YYYY-MM-DD, the day you found it |
| `company` | organization name |
| `role` | exact posted title |
| `source` | where you found it — board name, referral, recruiter, direct |
| `url` | the posting. **Save the text too** — postings vanish and you'll want it before the interview |
| `status` | see legend below |
| `score` | 0–100 from `prompts/02-role-scoring.md` |
| `resume_version` | filename of the tailored resume |
| `cover_letter` | filename, or `none` |
| `contact_name` | the human, if you have one |
| `contact_role` | recruiter / hiring manager / referrer / employee |
| `last_action_date` | last thing you did on this row |
| `next_action` | the actual next move — "nudge recruiter", "prep panel", "send thank-you" |
| `next_action_date` | from `reference/cadence.md` |
| `elimination_reason` | required when status is Passed, Rejected, or Ghosted |
| `comp_posted` | the range if published |
| `location` | city, or Remote |
| `work_mode` | remote / hybrid / onsite |
| `notes` | everything else — benefits, red flags, who you spoke to, what they said |

## Status legend

| Status | Meaning |
|---|---|
| `Researched` | found and scored, not applied |
| `Passed` | decided not to apply. **Elimination reason required** |
| `Applied` | submitted |
| `Screen` | recruiter screen scheduled or done |
| `Interview` | with the hiring manager or team |
| `Final` | final round or panel |
| `Offer` | offer received |
| `Negotiating` | terms in discussion |
| `Accepted` | done |
| `Declined` | you turned it down. **Reason required** |
| `Rejected` | they turned you down. Reason if you have it |
| `Ghosted` | no response past the cadence limit |
| `Withdrawn` | you pulled out mid-process |

## Rules

1. **Every closed row has a reason.** Passed, Rejected, Ghosted, Declined — no exceptions. The clustered reasons are the most valuable output this system produces.
2. **`next_action` is never empty on an open row.** If you can't name the next move, the row should be closed.
3. **Save the posting text** somewhere in `workspace/applications/<company>-<role>/`. Postings get taken down the day before your interview surprisingly often.
4. **Update on status change, not on schedule.** A weekly sweep catches what you missed; it isn't the update mechanism.

## Weekly log

`weekly-log.md` sits alongside the tracker:

```markdown
| Week of | Apps sent | Outreach sent | Responses | Screens | Interviews | Offers | Notes |
|---------|----------:|--------------:|----------:|--------:|-----------:|-------:|-------|
```

The `Notes` column is the important one. Write what you noticed — which channel produced responses, which elimination reason keeps repeating, what stalled. After three weeks that column is a strategy document.

## Reading the funnel

Rough healthy conversion, cold applications, no referral:

| Stage | Typical |
|---|---|
| Applications → any response | 10–20% |
| Response → screen | 50% |
| Screen → interview | 40–50% |
| Interview → final | 40% |
| Final → offer | 25–35% |

Referrals run several times better at the first step, which is why outreach is not optional.

**Where it's stuck tells you what's broken:**

| Symptom | Likely cause |
|---|---|
| Applications, no responses | targeting too senior, resume keywords not matching, or no referrals |
| Responses but no screens | resume and posting are mismatched — the recruiter looked and moved on |
| Screens, no interviews | the pitch isn't landing, or comp misalignment surfaces there |
| Interviews, no finals | STAR stories are thin, or the role fit is genuinely off |
| Finals, no offers | competing against internal candidates, or closing badly |

Under ~20 applications, none of these numbers mean anything. Don't redesign the search on a sample of six.
