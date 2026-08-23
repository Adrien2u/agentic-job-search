# Personas

Six archetypes. `{{PERSONA}}` is set in SETUP Q1 and every workflow reads it. This file is the full spec of what each one changes — SETUP carries an abbreviated version.

Nobody is purely one of these. Use `{{PERSONA_SECONDARY}}` when two apply, follow the primary where they conflict, and let the user overrule both.

---

## `entry-level` — student, new grad, first professional role

**The real problem:** not a lack of ability, a lack of *legible evidence*. Postings ask for 2–3 years for jobs that don't need it.

| Dimension | Setting |
|---|---|
| Achievement sources | coursework, capstone, internships, volunteering, club leadership, part-time work, personal projects |
| Metrics | preference, not requirement — many are genuinely unmeasured |
| Resume length | 1 page, always |
| Resume order | Education first until first full-time role is done |
| Rubric adds | training / mentorship quality, weight 10 |
| Discovery | university career center, alumni network, campus recruiting cycles, entry-tagged boards, professional association student rates |
| Cover letter | more weight than for any other persona — it's where the evidence gap gets closed |
| Comp | "I don't know" is expected; use published ranges to calibrate later |
| Common trap | applying only to postings that ask for zero experience. Apply at 60% match — the requirements are a wish list |

**Discovery note the agent should say out loud:** most entry-level hiring runs on cycles and referrals, not on continuous posting. Ask about timing.

---

## `early-career` — 2 to 7 years, next level up in the same lane

**The real problem:** they have real outcomes and describe them as duties.

| Dimension | Setting |
|---|---|
| Achievement sources | last 2–3 roles, weighted to the most recent |
| Metrics | push hard — this is where numbers exist and go unused |
| Resume length | 1 page |
| Rubric | defaults, unchanged |
| Discovery | job boards work here; also former colleagues who've moved on |
| Cover letter | short, evidence-dense |
| Common trap | "responsible for" bullets. Every one should be rewritten as an outcome |

---

## `career-changer` — different field, function, or industry

**The real problem:** a screener spends six seconds and sees a mismatch. The whole system's job is to close that gap before the six seconds are up.

| Dimension | Setting |
|---|---|
| Extra artifact | `## Transferable Skills Map` in profile.md — origin skill, target-language equivalent, the evidence |
| Resume format | functional-hybrid: a skills-grouped block above the chronology, chronology still present |
| Rubric | skill adjacency 25 (from 15), role-type match 10 (from 20) |
| Cover letter | the change is the opening hook. It leads. It is never apologized for |
| Discovery | roles adjacent to the origin field first — the bridge is shorter and the story lands |
| Outreach | disproportionately important. Referral beats resume screen, and the screen is what's working against them |
| Common trap | hiding the change. It reads as confusion. Naming it in one confident sentence reads as intent |

**Vocabulary is the whole job here.** A teacher's "differentiated instruction across 140 students" and a UX researcher's "user segmentation" are the same competence in two dialects. The Key Reframing Guide table (in `templates/interview-prep.md`) is the tool.

---

## `senior-ic` — experienced specialist, wants to stay hands-on

**The real problem:** the market keeps trying to promote them into management, and the titles are unreliable.

| Dimension | Setting |
|---|---|
| Achievement framing | technical depth, systems owned end to end, influence without authority, what they were the last line of defense on |
| STAR adds | "Technical Judgment & Tradeoffs" |
| STAR optional drop | "Leadership & Influence" — only if genuinely no examples; usually there are, they're just informal |
| Rubric | skill adjacency 20 (from 15), growth trajectory 5 (from 10) |
| Resume length | 1 page, 2 if 15+ years |
| Discovery | specialist communities, conference speaker lists, open source, niche boards over aggregators |
| Common trap | scoring on title. A "Senior Engineer" posting at one org is a "Staff" at another. Score the described responsibilities |

**The agent should warn about this explicitly:** many postings labeled for an IC describe a manager's job. Read the responsibilities before scoring.

---

## `people-leader` — manages or wants to manage

| Dimension | Setting |
|---|---|
| Achievement framing | team size, retention, hiring throughput, promotions grown, outcomes delivered *through others* |
| STAR adds | "Hiring & Team Building", "Performance & Difficult Conversations" |
| Rubric | culture signals 15 (from 10) — a leader inherits the culture and can't outrun it |
| Resume length | 1–2 pages |
| Interview prep | expect scenario questions on underperformance, conflict, and layoffs. Have real answers |
| Common trap | describing the team's work as their own. The framing is "I built the conditions for X," not "I did X" |

**First-time managers:** if the user is moving from IC to manager, treat as `people-leader` primary with `career-changer` layered — the transferable-skills logic applies to informal leadership evidence.

---

## `executive` — Director, VP, C-level

**The real problem:** the roles they want are mostly not posted.

| Dimension | Setting |
|---|---|
| Achievement framing | scope. Org size, budget / P&L owned, revenue influenced, geographies, board and investor exposure, what changed under them |
| Bullets | outcomes at the org level, not project level |
| STAR adds | "Board & Investor Communication", "Org Design & Transformation" |
| Resume length | 2 pages |
| Rubric | org health 20 (from 10), comp fit 20 (from 15), role-type match 10 (from 20) |
| Discovery | executive search firms, board and advisory networks, portfolio-company introductions, direct outreach to the hiring principal. Boards are the *last* channel, not the first |
| Volume | half the applications, double the outreach |
| Comp | total package — equity, severance, change-of-control, not base |
| Confidentiality | usually critical. Assume the search is quiet unless told otherwise |
| Common trap | a resume that reads like a longer manager resume. If it's a list of what they oversaw rather than what changed, it's wrong |

---

## Cross-cutting situations

These aren't personas. They layer on top of any of them, and they map to deep modules.

| Situation | Module | Layered effect |
|---|---|---|
| Returning after 6+ months out | `re-entry-after-gap` | one-sentence gap framing, no apology; skills-refresh evidence; returnship channels |
| Needs visa sponsorship | `visa-and-relocation` | filter for sponsors early — it's a hard gate, not a soft preference. Facts only, no legal advice |
| Relocating | `visa-and-relocation` | local-address question, relocation-cost worksheet, timing |
| Clearance or license required | `security-clearance-or-licensure` | credential inventory, portability, renewal dates. Verify with the issuing body |
| Portfolio-dependent field | `portfolio-and-work-samples` | the portfolio outranks the resume; NDA-safe redaction |
| Currently employed, confidential | — | personal email, no public signals, careful reference handling |
