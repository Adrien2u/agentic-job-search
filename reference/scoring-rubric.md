# Scoring rubric

A role gets a 0–100 score and a written go/no-go. The score exists to make the decision fast and to make the *pattern* visible after twenty roles — not to be precise. Treat 71 and 74 as the same number.

Weights are defaults. Change them. They're supposed to be argued with.

---

## Criteria and default weights

| # | Criterion | Weight | Scored 0–10 on |
|---|---|---:|---|
| 1 | Role-type match | 20 | Does the *described work* match `{{TARGET_ROLES}}`? Read the responsibilities, not the title. |
| 2 | Skill adjacency | 15 | Of the stated requirements, how many can the user evidence today? |
| 3 | Comp fit | 15 | Posted or inferred range vs. `{{COMP_TARGET}}` and `{{COMP_FLOOR}}`. |
| 4 | Location / work mode fit | 10 | Against `{{LOCATIONS}}`, `{{WORK_MODE}}`, `{{MAX_COMMUTE}}`, `{{RELOCATION}}`. |
| 5 | Mission / values alignment | 10 | Does the user care about what this org does? Honest answers only. |
| 6 | Org health | 10 | Funding, layoffs, growth, leadership churn, financial disclosures, ratings. Sourced. |
| 7 | Growth trajectory | 10 | Where does this leave them in two years? |
| 8 | Culture signals | 10 | Review patterns, tenure, how the posting is written, interview process design. |
| 9 | Effort vs. likelihood | −0 to −10 | A penalty. Four-hour take-home for a 40% match is a subtraction. |

**Score** = Σ (criterion score ÷ 10 × weight) − effort penalty.

---

## Persona weight overrides

| Criterion | entry | early | changer | sr-IC | leader | exec |
|---|---:|---:|---:|---:|---:|---:|
| Role-type match | 20 | 20 | **10** | 20 | 20 | **10** |
| Skill adjacency | 15 | 15 | **25** | **20** | 15 | 15 |
| Comp fit | 15 | 15 | 15 | 15 | 15 | **20** |
| Location fit | 10 | 10 | 10 | 10 | 10 | 10 |
| Mission | 10 | 10 | 10 | 10 | 10 | 10 |
| Org health | 10 | 10 | 10 | 10 | 10 | **20** |
| Growth | 10 | 10 | 10 | **5** | 10 | 5 |
| Culture | 10 | 10 | 10 | 10 | **15** | 10 |
| Training/mentorship | **10** | — | — | — | — | — |

Weights are normalized to 100 after any override. If the user skipped comp in SETUP, drop criterion 3 and redistribute its 15 proportionally.

---

## Bands

| Score | Verdict | Action |
|---|---|---|
| 80–100 | Strong fit | Apply. Full tailoring. Find a human to talk to before or right after. |
| 65–79 | Good fit | Apply. Standard tailoring. |
| 50–64 | Marginal | Apply only if pipeline is thin, or if one outreach conversation could move it up. Note what would change the score. |
| below 50 | Pass | Record the elimination reason. Do not apply out of anxiety. |

**Hard gates** — these override the score outright:
- Requires a credential, clearance, or license the user does not have and cannot get in time.
- Requires work authorization the user does not have and the employer won't sponsor.
- Compensation ceiling is below `{{COMP_FLOOR}}` and stated as firm.
- Location is incompatible and remote isn't offered.
- Sits in `{{EXCLUDED_INDUSTRIES}}`.

A hard gate is a pass regardless of a 90 on everything else. Say which gate it was.

---

## Recording the reason

Every scored role goes into `tracker.csv` with its score, and every pass gets an elimination reason. This is the highest-value habit in the system: after three weeks the reasons cluster, and the cluster tells the user something their gut hadn't articulated — that they keep passing on the industry they said they wanted, or that comp is the real blocker and not fit.

Elimination reason vocabulary (extend freely): `comp-below-floor`, `location-incompatible`, `role-type-mismatch`, `seniority-mismatch`, `skills-gap-too-wide`, `org-health-concern`, `culture-signal`, `mission-mismatch`, `effort-not-justified`, `hard-gate-credential`, `hard-gate-authorization`, `posting-stale`, `applied-already`.

---

## Scoring honestly

Three failure modes the agent should actively resist:

**Inflation.** When someone is anxious, every role looks like a fit. If the score comes out above 80 more than about a third of the time, the scoring is broken. Say so.

**Deflation.** Perfectionists score themselves out of roles they'd get. Requirements lists are wish lists; the honest question for criterion 2 is "can I evidence enough of this to be credible," not "do I meet every line."

**Score theater.** Do not reverse-engineer the number to match a gut call already made. If the user's gut disagrees with the score, that's real information — ask which criterion is wrong and fix the weight, don't fudge the score.
