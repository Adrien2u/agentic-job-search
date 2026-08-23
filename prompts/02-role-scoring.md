# 02 — Role Scoring

Turn a posting into a 0–100 score and a decision with a reason attached.

**Inputs:** the posting text, `config.md`, `workspace/profile/profile.md`, `reference/scoring-rubric.md`
**Output:** a score, a verdict, and an updated `tracker.csv` row

---

## Ask for

The full posting text. Not a link — links rot and the agent may not be able to read them. If the user only has a URL, ask them to paste the text.

## Step 1 — Hard gates

Check these first. Any one of them ends the scoring.

| Gate | Pass condition |
|---|---|
| Credential / license / clearance | user has it, or can get it before the start date |
| Work authorization | user has it, or the posting states sponsorship |
| Comp ceiling | at or above `{{COMP_FLOOR}}`, where a range is published |
| Location | compatible with `{{LOCATIONS}}` / `{{WORK_MODE}}` / `{{RELOCATION}}` |
| Excluded industry | not in `{{EXCLUDED_INDUSTRIES}}` |

If a gate fails: verdict is Pass. Record `hard-gate-<reason>` and stop. Do not score the rest — a 92 on a role the user legally cannot take is noise.

If a gate is *uncertain* (comp not published, sponsorship not stated), do not fail it. Score it, and add "confirm in screen" to the notes.

## Step 2 — Score each criterion 0–10

Read `reference/scoring-rubric.md` for weights, including `{{PERSONA}}` overrides.

**1. Role-type match** — compare the described *responsibilities* to `{{TARGET_ROLES}}`. Ignore the title. A "Program Manager" posting that describes event production is an event role.

**2. Skill adjacency** — of the stated requirements, how many can the user evidence today from `master-resume.md`? Count "must haves" separately from "nice to haves," and score against the must-haves. 70% of must-haves is a strong 8, not a 7 — requirement lists are wish lists.

**3. Comp fit** — published range against `{{COMP_TARGET}}`. If unpublished, look at what similar roles at similar orgs publish and say that's what you did. Never present an estimate as the employer's number.

**4. Location / work mode** — against `{{LOCATIONS}}`, `{{WORK_MODE}}`, `{{MAX_COMMUTE}}`, `{{REMOTE_CONSTRAINTS}}`. Watch for "remote" postings with a quiet onsite requirement buried in paragraph six.

**5. Mission alignment** — does the user actually care about what this org does? A 5 is fine and honest.

**6. Org health** — from `prompts/03-company-research.md` if it's been run; otherwise a quick pass on funding, layoffs, ratings, and leadership churn. Score 5 and flag it if you genuinely don't know.

**7. Growth trajectory** — where does this leave them in two years? Look at the level above this one in the org, and whether it exists.

**8. Culture signals** — review patterns, tenure, how the posting is written, how the interview process is designed. A seven-stage process for a mid-level role is a signal.

**9. Effort penalty (−0 to −10)** — take-home length, number of rounds, custom application essays, portfolio requirements. Weigh against likelihood. A four-hour take-home for a 45% match is a −8.

## Step 3 — Compute and band

`Σ (score ÷ 10 × weight) − effort penalty`

| Score | Verdict |
|---|---|
| 80+ | Strong fit — apply, full tailoring, find a human |
| 65–79 | Good fit — apply, standard tailoring |
| 50–64 | Marginal — apply if the pipeline is thin; note what would move it |
| <50 | Pass — record the reason |

## Step 4 — Write the verdict

Not just the number. Format:

> **{{COMPANY}} — {{ROLE}} · {{SCORE}}/100 · {{BAND}}**
>
> **Strongest fit:** the two or three criteria that scored highest, and why.
> **Weakest:** what scored low and whether it's fixable.
> **What would change this:** the one thing — a referral, a published range, a clarifying answer in a screen — that would move the score most.
> **Decision:** apply / pass, and the reason in one sentence.

The "what would change this" line is the useful one. A 61 that becomes a 78 with one conversation is a different situation from a 61 that's structurally a 61.

## Step 5 — Record

Update the `tracker.csv` row: `score`, `status` (`Researched` or `Passed`), and `elimination_reason` if passed. Reasons come from the vocabulary in `reference/scoring-rubric.md`.

---

## Calibration

If more than about a third of scored roles land above 80, the scoring is inflated. Say so plainly and re-score a few. Anxiety makes everything look like a fit, and an inflated pipeline wastes the user's scarcest resource — the energy to tailor well.

If almost nothing clears 65, the opposite: either the targeting is off (wrong level, wrong market) or the user is scoring themselves out of roles they'd get. Check criterion 2 first — that's where perfectionism hides.

## When the gut disagrees

If the user says "the score says pass but I want to apply," don't fudge the number. Ask which criterion is wrong. Either a weight is miscalibrated for them — fix it in `config.md`, it'll pay off across every future role — or they're reacting to something the rubric doesn't capture, which is worth naming out loud. Both outcomes are better than a quietly adjusted score.
