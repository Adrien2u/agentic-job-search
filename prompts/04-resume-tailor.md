# 04 — Resume Tailor

Cut one posting-specific resume from the master. Never edit the master.

**Inputs:** the posting text, `workspace/profile/master-resume.md`, `config.md`
**Output:** `workspace/applications/{{COMPANY}}-{{ROLE}}/resume.md`

---

## The line that matters

Tailoring changes **which** true things you say, **in what order**, and **in whose vocabulary**. It never changes what's true.

Allowed: reordering, cutting, re-emphasizing, swapping your term for theirs where they mean the same thing, promoting a buried project into a bullet.

Not allowed: adding a skill, inflating a title, extending a date, inventing a number, upgrading "contributed to" into "led."

If the honest tailored version is weak, that's information about the fit — surface it, don't paper over it.

---

## I. Guiding principles

**Tone.** Plain, active, specific. No "passionate," "results-driven," "dynamic," "synergy," "thought leader." Every bullet starts with a verb.

**Keywords.** Pull the 15–20 terms the posting leans on — repeated phrases, the must-have list, the exact tool and methodology names. Use the ones that honestly describe the user's work, in the posting's wording. This is how a recruiter's keyword search finds the resume. It is not stuffing: a term that doesn't describe real work doesn't go in.

**Evidence density.** Every bullet earns its line. If it doesn't show capability relevant to *this* posting, it's cut — no matter how proud they are of it.

**Length.** `{{RESUME_LENGTH}}` — one page for most, two for `executive` or 15+ years. Going over means cutting, not shrinking the font.

**Proofread.** Consistent tense (present for current role, past for everything else), consistent date format, consistent punctuation at bullet ends. Spell the company name right — this fails more often than anyone expects.

## II. Format

- Reverse chronological, unless `{{PERSONA}}` is `career-changer` (see below)
- Standard section headers — "Professional Experience," not "My Journey." Applicant tracking systems parse by heading
- No tables, no text boxes, no columns, no headers/footers, no images. They parse badly or not at all
- One standard font, 10–12pt body, 0.5–0.75" margins
- Submit as PDF unless the posting says otherwise
- Filename: `Lastname_Firstname_Role.pdf`

## III. Sections, in order

**Header** — name, city and state, phone, email, LinkedIn, portfolio if relevant. No street address, no photo, no date of birth.

**Professional summary** — 2–4 sentences, rewritten for this posting. Their top need in the first clause. This is the highest-leverage twenty seconds on the page.

**Core competencies** — 9–15 terms in 3 groups, drawn from the posting's language where honest.

**Professional experience** — 3–5 bullets per recent role, fewer as you go back. Shape: **[verb] [what] [for whom] [result]**.

**Education** — below experience, except `entry-level`.

**Certifications, technical skills, extras** — only what's relevant to this posting.

## IV. Persona adjustments

```
IF PERSONA = entry-level THEN
  Education first, including GPA if 3.5+, relevant coursework, capstone, honors.
  Projects, internships, volunteering, and club leadership are experience — treat them as such.
  A metric per bullet is a preference here, not a rule.

IF PERSONA = career-changer THEN
  Functional-hybrid: a "Relevant Experience" block grouped by capability, using the
  TARGET field's vocabulary, above the standard reverse-chronological history.
  Pull the groupings from the Transferable Skills Map in profile.md.
  Do NOT hide the chronology — a purely functional resume reads as concealment.
  The summary names the target field in the first clause.

IF PERSONA = senior-ic THEN
  Depth over breadth. Systems owned end to end, technical judgment, the hard problems.
  Do not pad with management-adjacent language to look promotable — it works against
  someone who wants to stay hands-on.

IF PERSONA = people-leader THEN
  Team size and outcomes delivered through others. Retention, hiring, promotions grown.
  Framing is "built the conditions for X," not "did X."

IF PERSONA = executive THEN
  2 pages. Lead with scope — org size, budget/P&L, revenue influenced, geography.
  Bullets are org-level outcomes, not project deliverables.
  Consider a 3-line scope summary block directly under the header.
```

## V. Procedure

1. **Extract requirements.** Split must-have from nice-to-have. List the 15–20 keywords.
2. **Match against the master.** For each must-have: what's the evidence, and how strong?
3. **Report the gaps to the user before writing.** If three must-haves have no evidence, say so — that's a scoring conversation, not a writing one.
4. **Rewrite the summary** around their top need.
5. **Select and reorder bullets.** Most relevant first within each role, regardless of chronology inside the role.
6. **Swap vocabulary** where their term and the user's term mean the same thing.
7. **Cut to length.** Oldest and least relevant goes first.
8. **Proof.** Tense, dates, spelling, company name.
9. **Show the user what changed and why** — a short diff summary against the master, not just the finished file.

## Quality check

- [ ] Every claim traces to `master-resume.md`
- [ ] No invented numbers, dates, titles, or tools
- [ ] Their top 3 requirements are each visibly addressed
- [ ] Summary rewritten for this posting, not reused
- [ ] Every bullet starts with a verb
- [ ] Most bullets have a number, or are marked `[TBD: quantify]` for the user to fill
- [ ] Fits `{{RESUME_LENGTH}}`
- [ ] Company name spelled correctly
- [ ] Master resume untouched

## Then

Cover letter: `prompts/05-cover-letter.md`. Log `resume_version` in `tracker.csv`.

If the user has no referral at this org yet, say so before they submit — `prompts/06-outreach.md`, and it is worth more than another hour of tailoring.
