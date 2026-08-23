# 03 — Company Research

Produce a sourced brief before applying or interviewing.

**Inputs:** company name, the posting, `config.md`
**Output:** `workspace/research/{{COMPANY}}.md` from `templates/company-research.md`

---

## The rule

**Every factual claim gets a source.** Unsourced research is rumor, and rumor said out loud in an interview is expensive. If something can't be sourced, write "could not verify" — that is itself a finding.

If the agent has no web access, say so plainly and switch to a question list the user can research themselves. Do not fill the brief from memory. Company facts go stale fast and confidently wrong facts are worse than blanks.

## Where to look, by org type

| Org type | Sources |
|---|---|
| Public company | latest annual report and quarterly filings, investor relations page, earnings call summaries, news |
| Private / startup | Crunchbase or equivalent, funding announcements, the founders' own posts, press, engineering or company blog |
| Non-profit | IRS Form 990 (public in the US), Charity Navigator, GuideStar, the annual report, the board list |
| Government | the agency's published budget, org chart, strategic plan, oversight reports |
| Agency / consultancy | client list, case studies, principal bios, awards |
| Any | employee reviews, LinkedIn headcount trend and tenure, the careers page, recent news |

## What to actually determine

Nine questions. Everything else is decoration.

1. **What do they do, in one sentence a stranger would understand?**
2. **How do they make money, or where does the funding come from?** For a non-profit: the mix of grants, giving, earned revenue, and contracts — a 90%-single-grant org is a different risk than a diversified one.
3. **Are they growing, flat, or shrinking?** Headcount trend, funding, layoffs.
4. **What happened in the last 12 months?** Funding, layoffs, leadership change, launch, acquisition, regulatory action, bad press. Walking in unaware of a bad news cycle is the avoidable mistake.
5. **What do employees repeatedly say?** Patterns only. Read the 3-star reviews.
6. **How long do people stay?** An entire department under 18 months is a signal.
7. **Why is this role open?** New or backfill. Often unanswerable from outside — that's fine, it becomes a screen question.
8. **Who would you work with?** Manager, likely interviewers, anyone in shared network.
9. **Has this posting been up before?** Repeated reposting means something is wrong.

## Reading reviews honestly

- Ignore 5-star and 1-star. Both are usually written in an emotional state.
- Weight 3-star heavily. They're the ones trying to be fair.
- Only repeated complaints count. One person's bad manager is one person's bad manager.
- Recency matters — a bad stretch three years and one CEO ago may be genuinely over.
- Small orgs have small samples. Twelve reviews is an anecdote, not a dataset.

## Culture signals in the posting itself

The posting is a primary source and it's usually read too quickly:

| Phrase | Often means |
|---|---|
| "wear many hats" | understaffed |
| "fast-paced" | reactive, possibly chaotic |
| "work hard, play hard" | long hours |
| "like a family" | boundaries are weak |
| "self-starter, minimal supervision" | little onboarding |
| "competitive salary" (no range) | not competitive |
| "rockstar / ninja / guru" | dated culture |
| a clear range, a clear process, a clear scope | someone thought about this role |

Not deal-breakers. Signals — score them in criterion 8 and ask about them.

## Fit analysis

Pull the top three needs off the posting. For each: what evidence does the user have, and is it strong, partial, or a gap?

Then the gap strategy. A gap is handled with adjacent evidence plus a credible learning path — never by pretending it isn't there. Partial and gap rows are normal; a candidate with zero gaps is usually over-qualified and will be bored.

## Questions to bring

Generate six, grouped by who to ask. The two highest-value ones are almost always:

- *Is this a new role or a backfill — and what happened with the last person?*
- *What does success look like at 90 days?*

## Then

Write the brief. Feed org health and culture signals back into `prompts/02-role-scoring.md` and update the score if research changed it — it often does, in both directions. Note the change and why.

Reuse the brief for interview prep in `prompts/07-interview-prep.md`. Re-check the news section the day before any interview; twelve months of research can be undone by one week's announcement.
