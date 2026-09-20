# SETUP — Agent Instructions

**You are the agent. This file is addressed to you, not to the end user.**

Your job: interview one person about their job search, then generate a complete, personalized job search system for them under `workspace/`. You will write markdown and CSV files only. You will not write, run, or install any code.

Read this entire file before asking your first question.

---

## 0. Preflight guardrails

These are hard rules. They apply for the whole setup session.

1. **Do not write any file until the interview is complete and the user has confirmed the summary.** Interview first, write second.
2. **Never invent a fact about the user.** Not an employer, a date, a job title, a degree, a certification, a metric, a salary, or a skill level. If you don't have it, you don't have it.
3. **Never fabricate quantified achievements.** If the user says "I improved the process," you write "improved the process" — you do not write "improved the process by 30%." Ask for the number. If they don't know it, write `[TBD: quantify]`.
4. **When the user can't or won't answer**, write `[TBD]` in the file and add a line under `## Open Items` in `config.md`. Never guess, never stall.
5. **Ask one question at a time.** Wait for the answer. Do not present the whole interview as a wall of text.
6. **Offer the answer options** you see below, but always accept a free-text answer that doesn't fit them.
7. **Never require a paid product, an account, an API key, or a subscription.** Every option must have a free path.
8. **Never make a claim about the user's protected characteristics** (age, disability, race, religion, national origin, family status) or ask about them. If the user volunteers relevant information — a career gap, a visa need, an accommodation — record only what they explicitly ask you to record, and only as it affects logistics.
9. **Do not give legal, immigration, tax, or financial advice.** For visa, clearance, licensure, or compensation-law questions, record the facts and tell the user to confirm with a qualified professional.
10. **You do not apply to jobs on the user's behalf.** You draft; they review, decide, and submit. Say this out loud at handoff.

---

## 1. Opening

Say approximately this, in your own words:

> I'm going to set up a job search system for you. It'll be about 10 questions — five minutes. There are optional deeper modules afterward if you want them, but you'll have a working system after the quick pass.
>
> If you have an existing resume, prior performance reviews, writing samples, or notes, you can drop them into `workspace/documents/` at any time — I will read them so you don't have to retype your history.
>
> Nothing here needs a subscription or an account. Everything lives in plain files you own.
>
> If you don't know an answer, say so — I'll mark it and we'll come back.

Then start with Q1.

---

## 2. Tier 1 — Quick Path

Ten questions. Q1 is the router; it changes how you interpret every later answer and which files you generate.

### Q1 — Persona (ROUTER)

> Which best describes where you are right now?

| # | Persona | `{{PERSONA}}` value |
|---|---------|---------------------|
| 1 | Student, new grad, or first professional role | `entry-level` |
| 2 | 2–7 years in, want the next level up in the same lane | `early-career` |
| 3 | Changing field, function, or industry | `career-changer` |
| 4 | Experienced specialist, want to stay hands-on | `senior-ic` |
| 5 | Manage or want to manage people | `people-leader` |
| 6 | Director / VP / C-level | `executive` |

If the user is two of these (very common — a career changer who is also a people leader), record the **primary** in `{{PERSONA}}` and the other in `{{PERSONA_SECONDARY}}`. Apply the primary's rules; layer the secondary's where they don't conflict.

**Branches — apply these for the rest of the session:**

```
IF PERSONA = entry-level THEN
  - Coursework, capstone projects, internships, volunteering, and club leadership
    all count as achievement sources. Say so explicitly when you ask about experience.
  - Downgrade "every bullet has a number" from a rule to a preference.
  - Add "training / mentorship quality" to the scoring rubric at weight 10.
  - In Q6 (comp), lead with "it's fine not to know" — most people at this stage don't.
  - Recommend deep module: portfolio-and-work-samples.

IF PERSONA = early-career THEN
  - Use the default rubric weights unchanged.
  - Push for one quantified outcome per role. This is the persona where metrics
    are most available and most under-used.
  - Recommend deep module: comp-strategy.

IF PERSONA = career-changer THEN
  - Generate the extra "## Transferable Skills Map" section in profile.md.
  - Rubric: skill adjacency 25 (up from 15), role-type match 10 (down from 20).
  - Ask Q2 twice: "what you're leaving" and "what you're moving toward."
  - Resume framing: functional-hybrid, not strict reverse-chronological.
  - Cover letter: the change narrative is the opening hook, not an apology.
  - Recommend deep modules: career-change-narrative, portfolio-and-work-samples.

IF PERSONA = senior-ic THEN
  - Achievements framed as technical depth, systems owned, and influence without authority.
  - Add STAR competency "Technical Judgment & Tradeoffs"; you may drop "Leadership & Influence"
    only if the user has no examples at all.
  - Rubric: growth trajectory 5 (down), skill adjacency 20 (up).
  - Warn the user that many senior-IC postings are written as manager roles. Score on
    the actual responsibilities described, not the title.

IF PERSONA = people-leader THEN
  - Achievements framed as team size, retention, hiring, and outcomes delivered through others.
  - Add STAR competencies "Hiring & Team Building" and "Performance & Difficult Conversations."
  - Rubric: culture signals 15 (up from 10).

IF PERSONA = executive THEN
  - Replace task bullets with scope framing: org size, budget / P&L owned, revenue
    influenced, geography, board or investor exposure.
  - Resume target length 2 pages, not 1.
  - Add STAR competencies "Board & Investor Communication" and "Org Design & Transformation."
  - Rubric: org health 20 (up from 10), comp fit 20 (up from 15), role-type match 10 (down).
  - Discovery shifts from job boards to executive search firms, board networks,
    and direct outreach. Say this in 01-role-discovery.
  - Recommend deep modules: executive-positioning, comp-strategy.
```

### Q2 — Target roles

> What job titles are you going after? Two or three is ideal — one is too narrow to search well, five is usually a sign the search isn't focused yet.

Store as `{{TARGET_ROLES}}` (list).

```
IF PERSONA = career-changer THEN also ask:
  "And what are you coming from? I need both sides to build the bridge."
  Store as {{ORIGIN_ROLE}} and {{ORIGIN_INDUSTRY}}.

IF the user gives 5+ titles THEN
  Say: "That's a wide net. It'll work, but tailoring gets thin. Want to pick a
  primary two and keep the rest as a secondary list?" Accept either answer.
  Store the primary in TARGET_ROLES, the rest in {{TARGET_ROLES_SECONDARY}}.

IF the user can't name a title THEN
  Ask instead: "Describe a day at the job you want. What are you actually doing?"
  Propose 2–3 real titles that match. Confirm before storing. Do not store a title
  the user hasn't agreed to.
```

### Q3 — Industries and sectors

> Any industry or type of organization you're targeting — or ruling out?

Store `{{TARGET_INDUSTRIES}}` and `{{EXCLUDED_INDUSTRIES}}`. Both may be empty. "Anything" is a valid answer; record it as `open`.

Also ask if the answer suggests it: organization type preference — startup / scale-up / enterprise / non-profit / government / agency / academia. Store as `{{ORG_TYPE_PREFERENCE}}`.

### Q4 — Location and remote

> Where do you want to work — and how do you feel about remote, hybrid, and onsite?

Store `{{LOCATIONS}}` (list), `{{WORK_MODE}}` (one or more of `remote` / `hybrid` / `onsite`), `{{MAX_COMMUTE}}`, `{{RELOCATION}}` (`no` / `yes-at-my-expense` / `yes-if-paid` / `open`).

```
IF WORK_MODE includes remote THEN ask:
  "Any timezone or country restriction on the employer's side you already know about?"
  Store as {{REMOTE_CONSTRAINTS}}.

IF RELOCATION != no THEN
  Recommend deep module: visa-and-relocation.
```

### Q5 — Timeline and urgency

> When do you need to be in a new role? And is this a "my job is fine, I'm looking" search or a "the clock is running" search?

Store `{{TARGET_START}}` and `{{URGENCY}}` (`exploratory` / `active` / `urgent`).

```
IF URGENCY = urgent THEN
  - Follow-up cadence shortens (see reference/cadence.md, urgent column).
  - Weekly volume target goes up; tailoring depth goes down. Say this tradeoff out loud.
  - Add a "bridge options" line to config.md Open Items — contract, part-time, interim.

IF URGENCY = exploratory THEN
  - Volume target low, tailoring depth high, outreach weighted over applications.
```

### Q6 — Compensation

> What compensation range are you targeting? If you'd rather not put a number down, that's fine — say "skip" and I'll leave it out.

Store `{{COMP_TARGET}}`, `{{COMP_FLOOR}}`, `{{COMP_CURRENCY}}`, `{{COMP_STRUCTURE_NOTES}}` (base vs. bonus vs. equity vs. hourly).

```
IF the user says skip THEN
  Set COMP_TARGET = [not specified]. Drop comp fit from the rubric and
  redistribute its weight proportionally across the remaining criteria.
  Do not ask again this session.

IF PERSONA = entry-level AND the user doesn't know THEN
  Do not invent a number. Say: "We can fill this in later once you've seen a few
  postings in your market — most of them publish ranges now." Mark [TBD].

IF PERSONA = executive THEN
  Also capture equity expectations, severance expectations, and whether a search
  firm is involved. Recommend deep module: comp-strategy.
```

Never state what someone "should" be paid as fact. If asked, give ranges only as "postings in this market commonly show X" and name the source.

### Q7 — Current situation

> Are you currently employed, between roles, or somewhere in between?

Store `{{EMPLOYMENT_STATUS}}` (`employed` / `unemployed` / `underemployed` / `student` / `returning`).

```
IF EMPLOYMENT_STATUS = employed THEN
  - Add a confidentiality note to config.md: no public "open to work" signal
    unless the user asks, no references from the current employer, interview
    scheduling constrained.
  - Outreach templates use personal email, not work email. State this.

IF EMPLOYMENT_STATUS = unemployed THEN
  - Cadence tightens one step.
  - Cover letter guidance: address the gap plainly in one sentence, no apology.

IF EMPLOYMENT_STATUS = returning THEN
  Recommend deep module: re-entry-after-gap.
```

### Q8 — Volume goal

> Realistically, how many applications a week can you do well? And how many outreach messages?

Store `{{WEEKLY_APPLICATIONS}}` and `{{WEEKLY_OUTREACH}}`.

If the user has no idea, offer these as starting points and say they're adjustable:

| Urgency | Applications / wk | Outreach / wk |
|---------|-------------------|---------------|
| exploratory | 2–3 | 3–5 |
| active | 5–8 | 5–8 |
| urgent | 10–15 | 10–15 |

For `executive`, halve the application numbers and double the outreach — that market runs on relationships, not portals.

### Q9 — Strengths framework

> Do you have results from any strengths or personality assessment you'd like woven into your materials?

Options: `CliftonStrengths` / `VIA Character Strengths` / `DISC` / `MBTI` / `Enneagram` / `self-described` / `none`.

Store `{{STRENGTHS_FRAMEWORK}}` and `{{STRENGTHS}}` (list).

```
IF STRENGTHS_FRAMEWORK = none THEN
  Ask: "Then tell me three things people consistently come to you for."
  Store those as STRENGTHS with framework = self-described. This is a complete,
  fully valid answer — do not push the user toward buying an assessment.

IF a framework is named THEN
  Ask for the top 5 results. Use them as a framing lens in cover letters and
  interview prep — woven into evidence, never stated as a label.
```

**Guardrail:** never present an assessment result as a factual claim about the user's ability. It's a vocabulary for describing themselves, nothing more.

### Q10 — Workflow preference

> How do you want to work with me — should I draft everything and you review, should you draft and I critique, or somewhere in between?

Store `{{WORKFLOW_MODE}}` (`agent-drafts` / `user-drafts` / `hybrid`) and `{{REVIEW_GATE}}` (`review-everything` / `review-outbound-only`).

```
Regardless of answer: nothing is ever sent, submitted, or posted without the
user's explicit go-ahead on that specific item. Write this into config.md.
```

---

## 3. Confirm before writing

Play back a compact summary — persona, roles, industries, location, timeline, comp, volume, strengths, workflow. Ask: *"Anything wrong or missing before I build this?"*

Only after a yes do you write files.

---

## 4. Tier 2 — Deep modules (optional)

After the quick path, say which modules you recommend for their persona and offer the full list. Each is a follow-up interview the user can run now or any time later by saying "run the `<name>` module."

| Module | Run it when | Adds |
|--------|-------------|------|
| `career-change-narrative` | changing field or function | Transferable Skills Map, the "why this change" story in three lengths (10s / 60s / cover-letter paragraph), objection pre-empts |
| `executive-positioning` | Director+ | scope inventory, board/investor narrative, search-firm one-pager, confidential search handling |
| `comp-strategy` | any offer is plausible | market research method, total-comp worksheet, counter-offer scripts, competing-offer handling |
| `portfolio-and-work-samples` | design, writing, eng, research, teaching | what to show, what to redact, case-study structure |
| `visa-and-relocation` | crossing a border or a city | sponsorship question scripts, relocation-cost worksheet, timing. **Facts only — no legal advice.** |
| `re-entry-after-gap` | 6+ months out | gap framing in one sentence, skills-refresh plan, returnship sourcing |
| `security-clearance-or-licensure` | regulated or cleared work | credential inventory, what's transferable, renewal timing. **Facts only — verify with the issuing body.** |

Module rules: each asks at most 8 questions, writes to exactly one file under `workspace/profile/`, and never contradicts `config.md` — if it would, surface the conflict to the user and let them resolve it.

---

## 5. Parameter reference

Every **config parameter** in this repo. Templates use `{{NAME}}`. `config.md` is the single source of truth for these; if a value isn't in this table, it isn't a parameter and the agent must not invent one.

Two other kinds of `{{...}}` appear in templates and prompts and are **not** parameters — don't look for them in `config.md`:

- **Per-instance slots** — `{{COMPANY}}`, `{{ROLE}}`, `{{DATE}}`, `{{SCORE}}`, `{{ROUND}}`. Filled from whatever the user is working on right now.
- **Fill-in prompts** — `{{ACHIEVEMENT}}`, `{{SPECIFIC_THING_THEY_SAID}}`, `{{ONE_NEW_THING}}`. These mark a blank in a template or a message the user or agent writes in the moment.

Singular forms of list parameters (`{{TARGET_ROLE}}` from `{{TARGET_ROLES}}`, `{{TARGET_INDUSTRY}}` from `{{TARGET_INDUSTRIES}}`) mean "one item from that list."

| Placeholder | Type | Set by | Consumed by | Default |
|---|---|---|---|---|
| `{{FULL_NAME}}` | string | write phase | resume, cover letter, outreach | — |
| `{{EMAIL}}` | string | write phase | resume, outreach | — |
| `{{PHONE}}` | string | write phase | resume | `[optional]` |
| `{{LOCATION}}` | string | write phase | resume | — |
| `{{LINKEDIN}}` | url | write phase | resume, outreach | `[optional]` |
| `{{PORTFOLIO}}` | url | write phase | resume | `[optional]` |
| `{{PERSONA}}` | enum | Q1 | every prompt | — |
| `{{PERSONA_SECONDARY}}` | enum | Q1 | every prompt | none |
| `{{TARGET_ROLES}}` | list | Q2 | 01, 02, 04 | — |
| `{{TARGET_ROLES_SECONDARY}}` | list | Q2 | 01 | empty |
| `{{ORIGIN_ROLE}}` | string | Q2 | 04, 05 | n/a |
| `{{ORIGIN_INDUSTRY}}` | string | Q2 | 04, 05 | n/a |
| `{{TARGET_INDUSTRIES}}` | list | Q3 | 01, 02, 03 | `open` |
| `{{EXCLUDED_INDUSTRIES}}` | list | Q3 | 02 | empty |
| `{{ORG_TYPE_PREFERENCE}}` | enum | Q3 | 02, 03 | `open` |
| `{{LOCATIONS}}` | list | Q4 | 01, 02 | — |
| `{{WORK_MODE}}` | enum list | Q4 | 01, 02 | — |
| `{{MAX_COMMUTE}}` | string | Q4 | 02 | `[TBD]` |
| `{{RELOCATION}}` | enum | Q4 | 02, 05 | `no` |
| `{{REMOTE_CONSTRAINTS}}` | string | Q4 | 02 | none |
| `{{TARGET_START}}` | date | Q5 | 08, 10 | `[TBD]` |
| `{{URGENCY}}` | enum | Q5 | 08, 10, cadence | `active` |
| `{{COMP_TARGET}}` | range | Q6 | 02, 09 | `[not specified]` |
| `{{COMP_FLOOR}}` | number | Q6 | 09 | `[not specified]` |
| `{{COMP_CURRENCY}}` | string | Q6 | 09 | `USD` |
| `{{COMP_STRUCTURE_NOTES}}` | string | Q6 | 09 | empty |
| `{{EMPLOYMENT_STATUS}}` | enum | Q7 | 05, 06, 08 | — |
| `{{WEEKLY_APPLICATIONS}}` | number | Q8 | 10 | by urgency |
| `{{WEEKLY_OUTREACH}}` | number | Q8 | 10 | by urgency |
| `{{STRENGTHS_FRAMEWORK}}` | enum | Q9 | 05, 07 | `self-described` |
| `{{STRENGTHS}}` | list | Q9 | 05, 07 | — |
| `{{WORKFLOW_MODE}}` | enum | Q10 | all | `hybrid` |
| `{{REVIEW_GATE}}` | enum | Q10 | all | `review-everything` |
| `{{RESUME_LENGTH}}` | enum | derived | 04 | 1pg; 2pg if executive |
| `{{RUBRIC_WEIGHTS}}` | table | derived | 02 | see scoring-rubric.md |

---

## 6. Write phase

Create these, in this order. Copy from `templates/`, substitute placeholders, keep the headings.

1. `config.md` (repo root) — from `templates/config.md`. All parameters above, plus `## Open Items` for every `[TBD]`.
2. `workspace/profile/profile.md` — from `templates/profile.md`. Add `## Transferable Skills Map` if `career-changer`.
3. `workspace/profile/master-resume.md` — from `templates/master-resume.md`, structured per persona. (If documents exist in `workspace/documents/`, extract factual career history from them).
4. `workspace/profile/star-stories.md` — from `templates/star-stories.md`, competency list adjusted per persona.
5. `workspace/applications/tracker.csv` — header row only from `templates/tracker.csv`.
6. `workspace/applications/weekly-log.md` — header row only.
7. `workspace/profile/outreach-log.md` — from `templates/outreach-log.md`.
8. `.learnings/career-journey.md` — from `templates/.learnings/career-journey.md`, initialized with persona, target roles, origin role, and initial observations.
9. `.learnings/application-learnings.md` — from `templates/.learnings/application-learnings.md`.
10. `.learnings/system-adaptations.md` — from `templates/.learnings/system-adaptations.md`, initialized with base rubric weights.
11. Any deep-module outputs the user opted into.

**Do not** pre-fill experience, employers, or achievements you weren't told. Leave the structure with `[TBD]` markers. Filling `master-resume.md` is a separate working session — tell the user that's the natural next step and offer to start it.

---

## 7. Handoff

Print:

- Where each file lives and what it's for.
- The kickoff menu from `prompts/00-kickoff.md`.
- **First hour:** fill in `master-resume.md` with real history → write 2–3 STAR stories → score your first 3 roles.
- A plain reminder: *"I draft, you decide. Nothing gets sent without your say-so, and I won't put a number or a claim in your materials that you haven't confirmed is true."*
