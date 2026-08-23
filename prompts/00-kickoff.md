# 00 — Kickoff

Start of any working session. Orients the agent, then hands the user a menu.

---

## Agent: load this first

1. `config.md` — who this is and what they want. If missing, run `SETUP.md` instead.
2. `CLAUDE.md` — the standing rules.
3. `workspace/profile/profile.md` — positioning.
4. `workspace/applications/tracker.csv` — the current pipeline.

Then, before saying anything else, check for anything overdue: rows where `next_action_date` has passed. Lead with those. A menu is not useful if three follow-ups are three days late.

**Working in plain chat with no filesystem?** Ask the user to paste `config.md` and `master-resume.md`, and work from those. Everything below is unchanged.

---

## Agent: open with this

> **{{FULL_NAME}} — {{PERSONA}} · targeting {{TARGET_ROLES}} · {{URGENCY}}**
>
> Pipeline: {{N}} active · {{N}} awaiting response · {{N}} interviewing
> Overdue: {{LIST_OR_NONE}}
> This week: {{X}}/{{WEEKLY_APPLICATIONS}} applications · {{Y}}/{{WEEKLY_OUTREACH}} outreach

Then the menu.

---

## Menu

> What are we doing?
>
> 1. **Find roles** — search for openings that fit
> 2. **Score a role** — is this one worth applying to
> 3. **Research a company** — sourced brief before applying or interviewing
> 4. **Tailor my resume** — a version aimed at one posting
> 5. **Write a cover letter** — draft, then cut it down
> 6. **Reach out to someone** — recruiter, hiring manager, warm intro, alumni
> 7. **Prep for an interview** — any round
> 8. **Follow up** — thank-you, nudge, or close something out
> 9. **Think through an offer** — evaluate it, frame a counter
> 10. **Weekly review** — what's stalled, what's next, is this working
> 11. **Update my profile** — resume, STAR stories, positioning
> 12. **Run a deep module** — career change, exec positioning, comp, portfolio, relocation, re-entry, clearance
>
> Or just say what you need.

## Routing

| Choice | File |
|---|---|
| 1 | `prompts/01-role-discovery.md` |
| 2 | `prompts/02-role-scoring.md` |
| 3 | `prompts/03-company-research.md` |
| 4 | `prompts/04-resume-tailor.md` |
| 5 | `prompts/05-cover-letter.md` |
| 6 | `prompts/06-outreach.md` |
| 7 | `prompts/07-interview-prep.md` |
| 8 | `prompts/08-follow-up.md` |
| 9 | `prompts/09-offer-negotiation.md` |
| 10 | `prompts/10-weekly-review.md` |
| 11 | the relevant `templates/` file, edited in place |
| 12 | `SETUP.md` § 4 |

## Session rules

- Accept a plain-language request over a menu number. "Can you look at this posting" is choice 2.
- Update `tracker.csv` at the end of any session that changed a status. Don't wait for the weekly review.
- If the user seems stuck rather than task-focused, offer choice 10 — a weekly review usually surfaces what's actually wrong faster than another application does.
- End by naming the next concrete action and its date.
