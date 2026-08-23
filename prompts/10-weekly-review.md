# 10 — Weekly Review

Once a week, same day. Twenty minutes. The one habit that keeps a search from drifting.

**Inputs:** `tracker.csv`, `workspace/profile/outreach-log.md`, `workspace/applications/weekly-log.md`, `config.md`
**Output:** an updated weekly log and a concrete plan for next week

---

## 1. Clear the overdue

Every row where `next_action_date` has passed. For each: send it, or close it.

Nothing stays overdue after this review. An open row with no action is the thing that quietly turns a pipeline into a list of regrets.

## 2. Sweep statuses

Anything past its ghost interval (`reference/cadence.md`) gets marked `Ghosted` with a reason. Anything that moved gets its new status. Every open row gets a `next_action` and a `next_action_date`.

## 3. Log the week

```markdown
| Week of | Apps sent | Outreach sent | Responses | Screens | Interviews | Offers | Notes |
```

Against targets: `{{WEEKLY_APPLICATIONS}}` and `{{WEEKLY_OUTREACH}}`.

The `Notes` column is the valuable one. What did you notice? Which channel produced responses? Which elimination reason keeps repeating? What stalled and why? After three weeks that column is a strategy document.

## 4. Read the funnel

Typical cold-application conversion, no referral:

| Stage | Typical |
|---|---|
| Applications → any response | 10–20% |
| Response → screen | ~50% |
| Screen → interview | 40–50% |
| Interview → final | ~40% |
| Final → offer | 25–35% |

**Under about 20 applications, none of this means anything.** Don't redesign a search on a sample of six.

Where it's stuck says what's broken:

| Symptom | Likely cause | Fix |
|---|---|---|
| Applications, no responses | targeting too senior, keywords not matching, or no referrals | re-check scoring calibration; shift effort to `06-outreach` |
| Responses, no screens | resume doesn't match the posting | `04-resume-tailor`, harder |
| Screens, no interviews | the pitch isn't landing, or comp misalignment surfaces there | rehearse "tell me about yourself"; address comp earlier |
| Interviews, no finals | STAR stories thin, or fit genuinely off | `07-interview-prep`; write more stories |
| Finals, no offers | closing badly, or internal candidates | the closing pitch; ask for rejection feedback |
| Offers, none appealing | targeting the wrong roles | revisit `config.md` — this is a search-design problem |

## 5. Read the elimination reasons

Cluster them. This is the highest-value five minutes in the review.

| Pattern | What it's telling you |
|---|---|
| `comp-below-floor` dominates | targeting a level or market that doesn't pay the floor. Adjust one of the two |
| `role-type-mismatch` dominates | search strings are wrong, or the titles in `config.md` don't match what the market calls this |
| `location-incompatible` dominates | the geography is too tight, or remote needs weighting up |
| `skills-gap-too-wide` dominates | targeting a level up. Either close a specific gap or aim at the level that exists |
| `culture-signal` / `org-health` dominates | targeting a sector under stress. Worth naming |
| No pattern | targeting is probably fine. It's a volume and conversion problem |

Also worth noticing: is the user consistently passing on the thing they said they wanted? That's real information about what they actually want, and it belongs in a `config.md` conversation.

## 6. Sanity check the effort

| Question | If the answer is no |
|---|---|
| Hit the application target? | was it unrealistic, or did the week get away? Adjust the target, not the guilt |
| Hit the outreach target? | this is the one that slips first and costs most. Protect it |
| Tailoring properly, or spraying? | volume without tailoring converts near zero. Fewer, better |
| Any conversation with a human this week? | if not, that's next week's first priority |
| Following up, or letting things die? | check §1 honestly |

## 7. Next week

Write it down, concretely:

- **Applications:** which specific roles, from the `Researched` rows
- **Outreach:** which specific people, from the warm-paths table
- **Interviews:** what needs prep, and when
- **Follow-ups:** what's due, by date
- **One system fix:** the single thing from this review worth changing — a rubric weight, a search string, a resume section, a target

One fix. Not five. Five changes at once means you learn nothing from any of them.

## 8. Every four weeks — the bigger question

Once a month, step back:

- Is `config.md` still true? Targets drift, and nobody updates the file.
- Is the target level right? Too high shows as silence; too low shows as offers that don't appeal.
- Is `{{URGENCY}}` still accurate? Runway changes, and cadence should change with it.
- Which channel actually produced conversations? Put more time there and less everywhere else.
- What's the honest read on the timeline against `{{TARGET_START}}`?

```
IF the search has run 8+ weeks with no screens THEN
  Something structural is wrong, not tactical. Do not respond by applying more.
  Check, in order: target level, resume against a posting line by line,
  outreach volume, and whether the target market is actually hiring.

IF URGENCY = urgent AND runway is shortening THEN
  Raise bridge options explicitly — contract, interim, fractional, part-time.
  This is a practical conversation, not a concession, and it's better held early
  than at week eleven.
```

## Tone

This review will sometimes deliver bad news. Deliver it plainly and briefly, then move to what changes. Don't cheerlead through a flat month and don't catastrophize a slow one — job searches are lumpy, and four weeks of nothing followed by three offers in one week is an ordinary shape, not a crisis.
