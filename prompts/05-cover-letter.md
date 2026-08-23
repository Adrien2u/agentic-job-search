# 05 — Cover Letter

Draft in five parts, then cut hard.

**Inputs:** the posting, the tailored resume, `workspace/profile/profile.md`, `workspace/research/{{COMPANY}}.md`
**Output:** `workspace/applications/{{COMPANY}}-{{ROLE}}/cover-letter.md`

---

## Should there be one at all?

| Situation | Answer |
|---|---|
| Required | yes |
| "Optional" | yes — most people skip it, which is exactly why it works |
| No upload field at all | skip, and put the substance into outreach instead |
| Career change, gap, relocation, or any explaining to do | **yes, always.** This is the only place to control that narrative |
| A generic one you'd send to twenty orgs | no. It reads worse than nothing |

## Part 1 — Opening hook

One short paragraph. Never "I am writing to apply for the position of…"

Open on **why them specifically** — something from the research that is actually true and actually specific. A program they run, a recent development, a problem the posting reveals they have. Then connect it to the user in one clause.

```
IF PERSONA = career-changer THEN
  The change IS the hook. Lead with it, confidently, no apology:
  "After eight years teaching high-school chemistry, I'm moving into instructional
  design — and this role is the specific reason I started looking at {{COMPANY}}."
  Not: "Although my background is in education..."
```

## Part 2 — Evidence

One short paragraph of framing, then **three to five bullets**. Each bullet maps to one of their stated needs and carries a real outcome.

Bullets are the point. A wall of prose here doesn't get read — the bullets do.

Every number traceable to `master-resume.md`. No exceptions, not even for a draft.

## Part 3 — Why this organization

The paragraph that separates a real letter from a mail merge. Specific enough that it could not be sent to any other employer.

Weak: "I've long admired your commitment to innovation."
Strong: "Your shift to a two-year grant cycle is the kind of operational change I spent last year implementing at a similar scale — and it's the reason I think I could be useful here quickly."

If this paragraph can't be written specifically, the research isn't done. Go back to `prompts/03-company-research.md`.

## Part 4 — Strengths, woven

`{{STRENGTHS}}` appear as evidence, never as labels.

Not: "My top CliftonStrength is Strategic."
Instead: "I tend to work backward from the outcome — which is how the volunteer program went from three weeks of onboarding to five days."

Same for a self-described strength. The label is for the user's own clarity; the reader only ever sees the behavior.

## Part 5 — Close

Two sentences. Plain statement of interest, a concrete next step, done. No "I look forward to hearing from you at your earliest convenience."

## The elephant

If there's something needing explanation — gap, change, short tenure, relocation, overqualification — one sentence, factual, no apology, then move on. Placed in Part 1 or 3, not the close.

- Gap: "I took eighteen months to care for a family member; I've been back in the field since March."
- Relocation: "I'm relocating to {{CITY}} in {{MONTH}} at my own expense and will be available onsite from then."
- Overqualified: "I'm deliberately looking for a hands-on role — the scope here is the appeal, not a compromise."

## The cut

**Draft long, then cut to: 280 words, 4 paragraphs, 3 bullets.**

A hiring manager scans this in six to ten seconds before deciding whether to read it. Everything that survives the cut has to earn its place at that speed.

Cutting order:
1. Every adverb.
2. Every sentence that restates the resume.
3. Every clause about what the user wants, keeping what the user offers.
4. Any bullet without a number or a concrete outcome.
5. The weakest of the remaining bullets, until three are left.

Then read it out loud. Anything you stumble over is a sentence to rewrite.

## Format

- Their letterhead conventions don't apply — this is usually pasted into a box or attached as PDF
- Address a person by name if findable. "Dear Hiring Team" if not. Never "To Whom It May Concern"
- Match the org's register: a 90-year-old foundation and a 40-person startup are different rooms
- Same font and header as the resume if attached

## Quality check

- [ ] Under 280 words
- [ ] Could not be sent to any other employer unchanged
- [ ] Every number traces to the master resume
- [ ] Opens on them, not on "I am writing to apply"
- [ ] 3–5 bullets, each mapped to a stated need
- [ ] Strengths shown as behavior, never named as labels
- [ ] The elephant addressed in one sentence, if there is one
- [ ] Company and person's name spelled correctly
- [ ] Read out loud once

## Then

Log `cover_letter` in `tracker.csv`. Set the follow-up date from `reference/cadence.md` — the letter is not the last action on this application.
