# Self-Improvement, `.learnings`, and Document Intake Implementation Plan

> **For Hermes:** Use the `subagent-driven-development` skill to implement this plan task-by-task.

**Goal:** Equip the no-code job search system with a `.learnings/` persistent memory store, a dedicated user document upload/intake directory (`workspace/documents/`), and an agent self-improvement workflow (`prompts/11-self-improvement.md`) that continuously learns a user's career past, present, future, and application patterns from conversations and uploaded documents to automatically adapt scoring, search, and application tailoring without modifying repository code.

**Architecture:** 
A dedicated `workspace/documents/` folder provides a drop zone for non-coders to upload existing resumes, performance reviews, transcripts, and portfolios, which the agent ingests into a privacy-protected `.learnings/` directory (mirrored by templates in `templates/.learnings/`). This memory store houses `career-journey.md` (past/present/future), `application-learnings.md` (market signals, win/loss patterns), and `system-adaptations.md` (calibrated rubric weights, search term overrides, tone tweaks). Existing workflows (`00-kickoff`, `02-role-scoring`, `04-resume-tailor`, and `10-weekly-review`) and a new workflow `11-self-improvement.md` continuously read, ingest, and calibrate the search engine without code.

**Tech Stack:** Plain Markdown, CSV, POSIX bash shell scripts / git for verification (strictly zero runtime code or third-party dependencies for end users).

---

### Task 1: Update `.gitignore` for `.learnings/` and `workspace/documents/`

**Objective:** Ensure user data in `.learnings/` and uploaded files in `workspace/documents/` are ignored by git by default (preventing accidental disclosure of personal career files), while tracking directory structure and explanatory READMEs.

**Files:**
- Modify: `.gitignore:1-15`

**Step 1: Write the updated `.gitignore`**

Replace `.gitignore` content with:

```gitignore
# Your job search data stays local by default.
# Delete the next four lines if you WANT to version your own search
# (recommended only if the repo is private).
workspace/**/*
config.md
!workspace/**/
!workspace/**/.gitkeep
!workspace/README.md
!workspace/documents/README.md

# Continuous learning and self-improvement data stays local
.learnings/**/*
!.learnings/**/
!.learnings/**/.gitkeep
!.learnings/README.md

# OS / editor noise
.DS_Store
Thumbs.db
*.swp
.idea/
.vscode/
```

**Step 2: Verify `.gitignore` rules via git check-ignore**

Run:
```bash
git check-ignore -v workspace/documents/my_resume.pdf .learnings/career-journey.md workspace/documents/README.md .learnings/README.md
```
Expected output:
```
.gitignore:4:workspace/**/*	workspace/documents/my_resume.pdf
.gitignore:12:.learnings/**/*	.learnings/career-journey.md
```
(Both personal files are ignored; both `README.md` files are NOT ignored due to negative patterns.)

**Step 3: Commit**

```bash
git add .gitignore
git commit -m "chore: update .gitignore with .learnings and workspace/documents privacy rules"
```

---

### Task 2: Create `workspace/documents/` Intake Directory and Documentation

**Objective:** Create the intake folder where users can drop their existing documents (resumes, reviews, writing samples, portfolios) for the agent to inspect, complete with `.gitkeep` and a user-facing `README.md`.

**Files:**
- Create: `workspace/documents/.gitkeep`
- Create: `workspace/documents/README.md`

**Step 1: Write `workspace/documents/.gitkeep`**

Create an empty file at `workspace/documents/.gitkeep`.

**Step 2: Write `workspace/documents/README.md`**

```markdown
# workspace/documents/

This is your personal drop folder for any documents you want the agent to read.

## What you can put here

- **Existing resumes & CVs:** Previous versions, older comprehensive resumes.
- **Performance reviews & evaluations:** Prior manager feedback, peer reviews, promo packets.
- **Work & writing samples:** Project briefs, design docs, published articles, code snippets.
- **Transcripts & certifications:** Degrees, licenses, course completions.
- **Reference letters & recommendations:** Recommendation texts, quotes from mentors/colleagues.
- **Job descriptions / target postings:** Postings saved as `.txt` or `.md` files.

## Supported formats

Plain text (`.txt`, `.md`), Word docs (`.docx`), PDF (`.pdf`), or images (`.png`, `.jpg`).

## Privacy

Everything placed in this folder (except this README and `.gitkeep`) is ignored by git by default. Your uploaded files will never be committed to GitHub unless you intentionally change `.gitignore`.

## How to use

Drop your files here, then tell the agent:
> "Read the documents in `workspace/documents/` and update my profile."
```

**Step 3: Verify `workspace/documents/` tracked files**

Run:
```bash
git status --short workspace/documents/
```
Expected output:
```
A  workspace/documents/.gitkeep
A  workspace/documents/README.md
```

**Step 4: Commit**

```bash
git add workspace/documents/.gitkeep workspace/documents/README.md
git commit -m "feat: add workspace/documents intake drop zone"
```

---

### Task 3: Create `.learnings/` Structure and Documentation

**Objective:** Create the `.learnings/` folder, its tracking `.gitkeep`, and a `.learnings/README.md` explaining privacy and purpose for non-coders and agents.

**Files:**
- Create: `.learnings/.gitkeep`
- Create: `.learnings/README.md`

**Step 1: Write `.learnings/.gitkeep`**

Create an empty file at `.learnings/.gitkeep`.

**Step 2: Write `.learnings/README.md`**

```markdown
# .learnings

This directory holds the agent's evolving knowledge about you and your search.

## What lives here

- `career-journey.md`: Your career narrative — past achievements, unwritten skills, current realities, and future aspirations (2-5 years out).
- `application-learnings.md`: What the market is telling you — feedback from applications, recruiter signals, resonance vs rejection patterns.
- `system-adaptations.md`: How the system tunes itself to you — calibrated rubric weights, customized search terms, tone preferences, and experiment logs.

## Privacy

Everything in this directory (except this README and `.gitkeep`) is ignored by git by default. Your reflections, private notes, and career aspirations remain strictly on your local machine.

## How it works

You do not need to edit these files by hand. The AI agent automatically updates them as you run workflows (`02-role-scoring`, `04-resume-tailor`, `10-weekly-review`, or `11-self-improvement`). You can inspect or edit them whenever you want.
```

**Step 3: Verify `.learnings/` tracked files**

Run:
```bash
git status --short .learnings/
```
Expected output:
```
A  .learnings/.gitkeep
A  .learnings/README.md
```

**Step 4: Commit**

```bash
git add .learnings/.gitkeep .learnings/README.md
git commit -m "feat: initialize .learnings directory and documentation"
```

---

### Task 4: Create Template for Career Journey (`templates/.learnings/career-journey.md`)

**Objective:** Provide a structured blank template to capture the user's past, present, and future career context without requiring manual repo edits.

**Files:**
- Create: `templates/.learnings/career-journey.md`

**Step 1: Write `templates/.learnings/career-journey.md`**

```markdown
# Career Journey & Personal Context

_Last updated: {{DATE}}_

This file captures who you are beyond what fits on a single-page resume. The agent reads this to ground tailoring, interview framing, and role alignment in your authentic trajectory.

---

## 1. Career Past — Roots & Unwritten Context

### Formative Chapters
- **Core background:** {{PAST_BACKGROUND_SUMMARY}}
- **Key inflection points:** {{KEY_TRANSITIONS_AND_WHY}}
- **Environments where you thrived:** {{PAST_THRIVING_ENVIRONMENTS}}
- **Environments that drained you:** {{PAST_DRAINING_ENVIRONMENTS}}

### Unwritten Competencies & Hidden Strengths
Things you are good at that might not have a formal job title or bullet point yet:
- {{UNWRITTEN_SKILL_1}}: {{CONTEXT_OR_EVIDENCE}}
- {{UNWRITTEN_SKILL_2}}: {{CONTEXT_OR_EVIDENCE}}

### Lessons & Hard Boundaries
- **Things you never want to do again:** {{HARD_BOUNDARIES}}
- **Management / leadership lessons learned:** {{LEADERSHIP_LESSONS}}

---

## 2. Career Present — Current Reality & State of Mind

### Current Energy & Bandwidth
- **Job search capacity:** {{HOURS_PER_WEEK}} hours/week
- **Search posture:** {{SEARCH_POSTURE}} <!-- e.g., active urgent, selective exploration, discreet transition -->
- **Current confidence & friction points:** {{CONFIDENCE_AND_FRICTION}}

### Authentic Voice & Self-Description
- **How you describe your work to peers (plain words, no jargon):**
  > {{AUTHENTIC_VOICE_DESCRIPTION}}
- **Phrases you dislike / reject:** {{DISLIKED_JARGON}}

---

## 3. Career Future — Direction & Horizon

### Next Role (1–2 Years)
- **Primary goal of the immediate search:** {{IMMEDIATE_GOAL}} <!-- e.g., compensation step-up, title bump, domain shift, better culture, hands-on craft -->
- **Must-haves in the daily day-to-day:** {{DAILY_MUST_HAVES}}
- **Growth areas you want this next role to stretch:** {{GROWTH_EDGES}}

### Medium-to-Long Horizon (3–5 Years)
- **Where you want this role to position you:** {{LONG_TERM_POSITIONING}}
- **Track preference:** {{TRACK_PREFERENCE}} <!-- e.g., deep individual contributor, executive leadership, entrepreneurial/consulting, advisory -->
- **Ideal work-life integration:** {{WORK_LIFE_IDEALS}}

---

## 4. Agent Observation Log

Chronological entries added by the agent during sessions or from uploaded documents in `workspace/documents/`:

- **{{DATE}} (Source: {{WORKFLOW_OR_DOCUMENT}}):** {{AGENT_OBSERVATION}}
```

**Step 2: Verify file creation**

Run:
```bash
test -f templates/.learnings/career-journey.md && echo "EXISTS"
```
Expected output:
```
EXISTS
```

**Step 3: Commit**

```bash
git add templates/.learnings/career-journey.md
git commit -m "feat: add career-journey template for past, present, and future tracking"
```

---

### Task 5: Create Template for Application Learnings (`templates/.learnings/application-learnings.md`)

**Objective:** Create a structured template to record real-world market signals, feedback from recruiters, and win/loss patterns from jobs applied to.

**Files:**
- Create: `templates/.learnings/application-learnings.md`

**Step 1: Write `templates/.learnings/application-learnings.md`**

```markdown
# Application Learnings & Market Feedback

_Last updated: {{DATE}}_

The market gives signals with every application, screener, interview, and rejection. The agent logs and clusters those signals here to find what converts and what stalls.

---

## 1. Resonance & Conversion Patterns

### What's Landing
- **Resume angles that generated recruiter screens:**
  - {{ANGLE_OR_HEADLINE}}: converted at {{COMPANY_OR_SECTOR}}
- **STAR stories that resonated strongly in interviews:**
  - {{STORY_TITLE}}: received positive feedback on {{COMPETENCY}}
- **Outreach hooks with highest reply rate:**
  - {{OUTREACH_HOOK_TYPE}}: {{REPLY_OBSERVATION}}

### What's Falling Flat
- **Positioning angles that produced ghosting/rejections:**
  - {{ANGLE_OR_KEYWORD}}: {{OUTCOME_OBSERVATION}}
- **Questions that exposed preparation gaps:**
  - {{DIFFICULT_QUESTION}}: {{WHAT_WAS_MISSING}}

---

## 2. Elimination & Pass Analysis

Patterns discovered across roles passed on or rejected:

| Role Type / Sector | Common Elimination Reason | Root Signal | Action Taken |
|---|---|---|---|
| {{ROLE_TYPE}} | {{ELIMINATION_REASON}} | {{ROOT_SIGNAL}} | {{SYSTEM_ADJUSTMENT}} |

---

## 3. Recruiter & Hiring Manager Intelligence

Direct feedback or implicit signals received from live processes:

- **{{DATE}} — {{COMPANY}} ({{ROLE}}):**
  - **Stage reached:** {{STAGE}}
  - **Signal / feedback received:** {{FEEDBACK_OR_OBSERVATION}}
  - **Lesson for future applications:** {{ACTIONABLE_TAKEAWAY}}

---

## 4. Market Hypotheses & Findings

- **Hypothesis:** {{HYPOTHESIS_STATEMENT}} <!-- e.g., "Seed-stage startups value X over Y" -->
  - **Evidence gathered:** {{EVIDENCE_NOTES}}
  - **Verdict:** {{CONFIRMED_DISPROVED_INCONCLUSIVE}}
```

**Step 2: Verify file creation**

Run:
```bash
test -f templates/.learnings/application-learnings.md && echo "EXISTS"
```
Expected output:
```
EXISTS
```

**Step 3: Commit**

```bash
git add templates/.learnings/application-learnings.md
git commit -m "feat: add application-learnings template for market feedback"
```

---

### Task 6: Create Template for System Adaptations (`templates/.learnings/system-adaptations.md`)

**Objective:** Create a template where the agent stores automated system self-improvements (calibrated rubric weights, search term refinements, tone adjustments) without requiring the non-coder user to edit repo files.

**Files:**
- Create: `templates/.learnings/system-adaptations.md`

**Step 1: Write `templates/.learnings/system-adaptations.md`**

```markdown
# System Adaptations & Self-Improvement

_Last updated: {{DATE}}_

This file contains active calibrations the agent applies to workflows. When the agent scores a role, searches for jobs, or drafts a cover letter, it checks these adaptations first to override defaults.

---

## 1. Calibrated Rubric Overrides

When scoring roles in `prompts/02-role-scoring.md`, apply these calibrated weight adjustments over `config.md` / `reference/scoring-rubric.md`:

| Criterion | Base Weight | Calibrated Weight | Reason for Calibration | Date Calibrated |
|---|---:|---:|---|---|
| Role-type match | {{BASE_W1}} | {{CAL_W1}} | {{REASON_1}} | {{DATE_1}} |
| Skill adjacency | {{BASE_W2}} | {{CAL_W2}} | {{REASON_2}} | {{DATE_2}} |
| Comp fit | {{BASE_W3}} | {{CAL_W3}} | {{REASON_3}} | {{DATE_3}} |
| Location / work mode | {{BASE_W4}} | {{CAL_W4}} | {{REASON_4}} | {{DATE_4}} |
| Mission alignment | {{BASE_W5}} | {{CAL_W5}} | {{REASON_5}} | {{DATE_5}} |
| Org health | {{BASE_W6}} | {{CAL_W6}} | {{REASON_6}} | {{DATE_6}} |
| Growth trajectory | {{BASE_W7}} | {{CAL_W7}} | {{REASON_7}} | {{DATE_7}} |
| Culture signals | {{BASE_W8}} | {{CAL_W8}} | {{REASON_8}} | {{DATE_8}} |

---

## 2. Refined Search Strings & Queries

Tuned search terms for `prompts/01-role-discovery.md`:

- **High-yield terms (keep using):**
  - `"{{HIGH_YIELD_QUERY_1}}"` — yielded {{OUTCOME_1}}
- **Negative / noise terms (exclude):**
  - `-{{EXCLUDE_TERM_1}}` — eliminates {{NOISE_DESCRIPTION}}
- **Title nuances discovered:**
  - When the market says `"{{MARKET_TITLE}}"`, it usually means `"{{REAL_RESPONSIBILITY}}"`.

---

## 3. Communication & Tailoring Voice Preferences

Tuned instructions for `04-resume-tailor`, `05-cover-letter`, and `06-outreach`:

- **Tone calibration:** {{TONE_CALIBRATION_NOTES}} <!-- e.g., "lean factual and technical; avoid narrative fluff" -->
- **Framing priorities:** {{FRAMING_PRIORITIES}} <!-- e.g., "always emphasize scale and system ownership first" -->
- **Vocabulary rules:**
  - Prefer: `{{PREFERRED_WORDS}}`
  - Avoid: `{{AVOIDED_WORDS}}`

---

## 4. Active Experiments

| Experiment | Target Workflow | Hypothesis | Status | Results / Decision |
|---|---|---|---|---|
| {{EXP_NAME}} | {{WORKFLOW}} | {{HYPOTHESIS}} | {{STATUS}} | {{RESULTS}} |

---

## 5. Self-Improvement Changelog

Chronological log of system self-calibrations made by the agent:

- **{{DATE}}:** {{CHANGE_SUMMARY}} (Trigger: {{TRIGGER_REASON}})
```

**Step 2: Verify file creation**

Run:
```bash
test -f templates/.learnings/system-adaptations.md && echo "EXISTS"
```
Expected output:
```
EXISTS
```

**Step 3: Commit**

```bash
git add templates/.learnings/system-adaptations.md
git commit -m "feat: add system-adaptations template for automated calibration"
```

---

### Task 7: Create Reference Document for Self-Improvement and Ingestion (`reference/self-improvement.md`)

**Objective:** Document the conceptual framework and operational rules for how the agent ingests uploaded documents, learns, synthesizes, and adapts within this no-code architecture.

**Files:**
- Create: `reference/self-improvement.md`

**Step 1: Write `reference/self-improvement.md`**

```markdown
# Self-Improvement & Continuous Learning Reference

How the agentic job search system learns about the candidate, diagnoses market signals, ingests source documents, and self-tunes over time without code changes or manual configuration overhead.

---

## 1. The Learning Loop: Ingest → Capture → Synthesize → Calibrate → Apply

The system continuously executes an empirical learning loop:

```
  [ workspace/documents/ ]  ───►  1. INGEST DOCUMENTS
                                       │
  [ User Conversations   ]  ───►  2. CAPTURE SIGNALS
                                       │
                                       ▼
                              3. SYNTHESIZE PATTERNS
                           (.learnings/career-journey.md &
                          .learnings/application-learnings.md)
                                       │
                                       ▼
                             4. CALIBRATE SYSTEM
                         (.learnings/system-adaptations.md)
                                       │
                                       ▼
                               5. APPLY IN FLIGHT
                       (01-discovery, 02-scoring, 04-tailor)
```

1. **Ingest Documents:** Check `workspace/documents/` for user-uploaded resumes, reviews, transcripts, or portfolio samples.
2. **Capture Signals:** Extract facts, achievements, tone preferences, and rejection feedback from conversations and workflows.
3. **Synthesize Patterns:** Distill insights into `.learnings/career-journey.md` (past/present/future) and `.learnings/application-learnings.md`.
4. **Calibrate System:** Convert patterns into calibrated weights and query rules in `.learnings/system-adaptations.md`.
5. **Apply in Flight:** Active workflows read `.learnings/` to deliver personalized, calibrated results.

---

## 2. Document Ingestion Protocol (`workspace/documents/`)

When a user drops files into `workspace/documents/`:
1. **Inventory:** List all files present in `workspace/documents/`.
2. **Extract & Corroborate:** Read text, extract achievements, metrics, roles, and dates. Compare against `workspace/profile/master-resume.md`.
3. **No Overwrites of Truth:** Never overwrite `master-resume.md` without explicit permission. Instead, propose new additions or record unwritten competencies into `.learnings/career-journey.md`.
4. **Mark Ingested:** Note in `.learnings/career-journey.md` under the observation log which document was read, on what date, and what facts were absorbed.

---

## 3. Three Pillars of Learning

### Pillar A: The Person & Career Journey (`career-journey.md`)
- **Past:** The unwritten story behind the resume, formative lessons, toxic environments avoided, implicit competencies.
- **Present:** Search capacity, real-time energy, authentic voice, current confidence.
- **Future:** 2-year and 5-year trajectories. The job search is not just about getting *a* job; it is about steering toward the user's intended horizon.

### Pillar B: Market Feedback & Application Signals (`application-learnings.md`)
- Application outcomes are empirical data.
- Clustered elimination reasons reveal whether targeting or calibration is misaligned.
- Screener and interview questions expose gaps in positioning or narrative.

### Pillar C: System Self-Adaptation (`system-adaptations.md`)
- The non-coder never needs to edit the repository or rewrite prompt files.
- The agent records explicit overrides:
  - Scoring rubric weights (e.g., boosting culture signal weight after a bad interview experience).
  - Search query modifiers (e.g., excluding misleading titles).
  - Writing style calibrations (e.g., adjusting resume verbosity or tone).

---

## 4. Non-Negotiable Guardrails

1. **Never fabricate learnings:** Every recorded learning must trace to a direct statement by the user, an uploaded document in `workspace/documents/`, or an observed event in `tracker.csv`.
2. **User confirmation for major shifts:** If learnings suggest changing `{{TARGET_ROLES}}`, `{{COMP_FLOOR}}`, or `{{WORK_MODE}}`, the agent must propose this to the user in conversation before making it an active rule.
3. **Additive and non-destructive:** Never wipe out previous context; append with dates and distill into active summaries.
4. **Zero code:** All memory is plain Markdown stored locally in `.learnings/` and `workspace/documents/`.
```

**Step 2: Verify file creation**

Run:
```bash
test -f reference/self-improvement.md && echo "EXISTS"
```
Expected output:
```
EXISTS
```

**Step 3: Commit**

```bash
git add reference/self-improvement.md
git commit -m "docs: add self-improvement and document ingestion reference guide"
```

---

### Task 8: Create Workflow 11 (`prompts/11-self-improvement.md`)

**Objective:** Add a dedicated workflow that the user or agent can run anytime to ingest uploaded documents, reflect on career trajectory, review market learnings, and calibrate the system.

**Files:**
- Create: `prompts/11-self-improvement.md`

**Step 1: Write `prompts/11-self-improvement.md`**

```markdown
# 11 — Self-Improvement & Learnings

On-demand or milestone-driven calibration. Ingest uploaded documents, reflect on career past/present/future, synthesize market signals, and tune the job search system without touching code.

**When to run:**
- When the user uploads new files to `workspace/documents/`
- Every 3–5 applications submitted or rejected
- After any recruiter screen or interview round
- When feeling stuck, frustrated, or misaligned
- Whenever career goals or life constraints evolve

**Inputs:**
- Files in `workspace/documents/` (if any uploaded)
- `.learnings/career-journey.md`
- `.learnings/application-learnings.md`
- `.learnings/system-adaptations.md`
- `workspace/applications/tracker.csv`
- `config.md`

**Outputs:**
- Ingestion of new files from `workspace/documents/`
- Updated files under `.learnings/`
- One to three concrete system calibrations (rubric weights, search queries, or pitch adjustments)
- Updated `config.md` (if parameters shifted with user consent)

---

## Step 0 — Ingest Uploaded Documents

Check `workspace/documents/`:
1. List any documents present (excluding README.md and .gitkeep).
2. For each document:
   - Read and extract key career facts, metrics, and accomplishments.
   - Cross-reference with `workspace/profile/master-resume.md` and `.learnings/career-journey.md`.
   - Log extracted insights in `.learnings/career-journey.md` under Section 4 (Agent Observation Log).
   - If significant new achievements or credentials are found, offer:
     > "I found these new accomplishments in `<filename>`. Should I draft updates to your `master-resume.md` or `star-stories.md`?"

---

## Step 1 — Check In: Past, Present, and Future

Ask the user one or two targeted questions based on recent activity:

1. **Energy & Alignment:** "Looking at your recent applications or interviews, what felt energizing, and what felt like a forced fit?"
2. **Horizon Check:** "Has anything shifted in what you want your next role to achieve for your 2–5 year career trajectory?"
3. **Unwritten Context:** "Did any past experience or hidden skill come up recently that we don't have documented in your career journey?"

Log responses into `.learnings/career-journey.md` under Section 4 (Agent Observation Log) and update Sections 1–3 as appropriate.

---

## Step 2 — Review Market Signals

Analyze the latest entries in `workspace/applications/tracker.csv`:

1. **Conversion inspection:**
   - How many applications are awaiting response beyond ghosting thresholds?
   - What resume angle or positioning was used for the ones that got screens?
2. **Elimination cluster review:**
   - If 3+ roles were passed on for the same reason (e.g. `comp-below-floor`, `skills-gap-too-wide`, `culture-signals`), what does this say about the current search queries?
3. **Interview debrief (if applicable):**
   - What questions did the interviewer ask that felt tricky?
   - Which STAR stories landed with visible impact?

Append new findings to `.learnings/application-learnings.md`.

---

## Step 3 — Propose System Adaptations

Based on the evidence from Steps 0, 1, and 2, formulate 1–3 specific system improvements:

| Adaptation Area | Current Setting | Proposed Calibration | Evidence / Justification |
|---|---|---|---|
| **Rubric Weight** | e.g. Culture Signals: 10 | Culture Signals: 20 | User passed on 3 roles due to aggressive on-call culture |
| **Search Queries** | e.g. `"Product Manager"` | `"Technical Product Manager" -crypto` | Yielding too many non-technical marketing PM roles |
| **Writing Tone** | e.g. Standard executive | Direct, metrics-first IC tone | Feedback showed recruiters wanted specific hands-on depth |

Present the proposed adaptations to the user:
> "Based on what we've seen, I suggest tuning the system in these ways. Would you like me to lock these calibrations into `.learnings/system-adaptations.md`?"

---

## Step 4 — Lock and Apply

Once confirmed by the user:
1. Update `.learnings/system-adaptations.md` with the new calibrations and log the change in the changelog.
2. If core parameters changed (e.g. target locations, compensation floor), update `config.md` directly.
3. State the exact downstream impact:
   > "Saved. Next time we score a role (02) or discover openings (01), these calibrations will take effect automatically."

---

## Tone

Reflective, practical, unburdening. This workflow exists so the user feels heard and the system gets visibly sharper, without burdening the user with technical maintenance.
```

**Step 2: Verify file creation**

Run:
```bash
test -f prompts/11-self-improvement.md && echo "EXISTS"
```
Expected output:
```
EXISTS
```

**Step 3: Commit**

```bash
git add prompts/11-self-improvement.md
git commit -m "feat: add workflow 11 for self-improvement, document intake, and learnings"
```

---

### Task 9: Update `CLAUDE.md` Standing Rules

**Objective:** Instruct every agent operating in this repository to recognize `workspace/documents/` for file uploads, read `.learnings/` on start, and continuously update learnings.

**Files:**
- Modify: `CLAUDE.md:1-50`

**Step 1: Update `CLAUDE.md`**

In `CLAUDE.md`:
1. Under `## Read first`:
   - Add `.learnings/` files (`career-journey.md`, `application-learnings.md`, `system-adaptations.md`) if present.
   - Mention checking `workspace/documents/` for user-uploaded background materials.
2. Under `## Always`:
   - "Apply calibrated adjustments from `.learnings/system-adaptations.md` whenever scoring roles or drafting materials."
   - "Capture new insights about the candidate's career past, present, future, or application outcomes in `.learnings/` so the system improves without manual configuration edits."
   - "Inspect `workspace/documents/` whenever the user mentions uploaded materials or updates."
3. Under `## File layout`:
   - Add `.learnings/` and `workspace/documents/`.

Apply exact unified diff:

```diff
--- a/CLAUDE.md
+++ b/CLAUDE.md
@@ -7,4 +7,6 @@
 `config.md` at the repo root is the single source of truth for who this user is and what they want. Read it before doing anything. If it doesn't exist, the system hasn't been set up — run `SETUP.md`.
 
+Also read `.learnings/` (`career-journey.md`, `application-learnings.md`, `system-adaptations.md`) if present. Check `workspace/documents/` for any user-uploaded source documents.
+
 If a fact isn't in `config.md` or `workspace/profile/`, you don't know it. Ask.
 
@@ -29,4 +31,7 @@
 - Update `workspace/applications/tracker.csv` whenever a status changes. Stale trackers are worse than no tracker.
 - Cite sources for company facts — Glassdoor, filings, the org's own site, news. Company research without sources is rumor.
+- Apply calibrated adjustments from `.learnings/system-adaptations.md` whenever scoring roles or drafting materials.
+- Record new insights about the candidate's career past, present, future, or application outcomes in `.learnings/` so the system improves without manual configuration edits.
+- Inspect `workspace/documents/` when onboarding or when the user mentions uploaded materials.
 - Respect confidentiality if `{{EMPLOYMENT_STATUS}}` is `employed`: personal email, no public signals, careful about who gets contacted.
 
@@ -36,7 +41,9 @@
 | `config.md` | user's parameters — read every session |
+| `.learnings/` | continuous personal context, market feedback & system adaptations |
 | `prompts/` | the workflows; each is self-contained |
 | `templates/` | blank structures to copy |
 | `reference/` | rubric, cadence, personas, glossary |
 | `workspace/profile/` | the user's durable material |
+| `workspace/documents/` | uploaded source documents (resumes, reviews, samples) |
 | `workspace/applications/` | per-application artifacts + tracker |
 | `workspace/research/` | company research briefs |
```

**Step 2: Verify `CLAUDE.md` changes**

Run:
```bash
grep -n "workspace/documents" CLAUDE.md
```
Expected output:
Matches in `CLAUDE.md`.

**Step 3: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: add .learnings and workspace/documents rules to CLAUDE.md"
```

---

### Task 10: Update `workspace/README.md` to Document `documents/` Folder

**Objective:** Ensure `workspace/README.md` documents `workspace/documents/` alongside `profile/`, `applications/`, `research/`, and `interviews/`.

**Files:**
- Modify: `workspace/README.md:1-15`

**Step 1: Update `workspace/README.md`**

In `workspace/README.md`, update the folder table to include `documents/`:

```diff
--- a/workspace/README.md
+++ b/workspace/README.md
@@ -6,4 +6,5 @@
 | Folder | Holds |
 |---|---|
+| `documents/` | uploaded source documents (past resumes, reviews, writing samples, portfolios) |
 | `profile/` | `profile.md`, `master-resume.md`, `star-stories.md`, `outreach-log.md`, deep-module outputs |
 | `applications/` | `tracker.csv`, `weekly-log.md`, and one folder per application with the tailored resume, cover letter, saved posting, and notes |
```

**Step 2: Verify `workspace/README.md`**

Run:
```bash
grep -n "documents/" workspace/README.md
```
Expected output:
Shows line with `documents/`.

**Step 3: Commit**

```bash
git add workspace/README.md
git commit -m "docs: document workspace/documents in workspace/README.md"
```

---

### Task 11: Update `SETUP.md` for Document Ingestion and `.learnings/` Initialization

**Objective:** Allow users running setup to drop existing documents into `workspace/documents/` to accelerate the setup interview, and initialize `.learnings/` upon completion.

**Files:**
- Modify: `SETUP.md:25-50`
- Modify: `SETUP.md:320-366`

**Step 1: Update `SETUP.md`**

In `SETUP.md`:
1. In `## 1. Opening`, add note:
   `"If you have an existing resume, prior reviews, or notes, you can drop them into workspace/documents/ at any time — I will read them so you don't have to retype your history."`
2. Under file generation (Tier 1 Generation / Hand-off), instruct the agent to:
   - Create `.learnings/career-journey.md` (pre-filled with persona and origin/target roles).
   - Create `.learnings/application-learnings.md` (clean headers).
   - Create `.learnings/system-adaptations.md` (pre-filled with initial calibrated weights).
   - Read any files in `workspace/documents/` and incorporate their data into `workspace/profile/master-resume.md` and `.learnings/career-journey.md`.

**Step 2: Verify `SETUP.md`**

Run:
```bash
grep -n "workspace/documents" SETUP.md
```
Expected output:
Shows matching line in `SETUP.md`.

**Step 3: Commit**

```bash
git add SETUP.md
git commit -m "feat: integrate workspace/documents intake and .learnings into SETUP.md"
```

---

### Task 12: Update `prompts/00-kickoff.md` Menu and Loading Sequence

**Objective:** Wire `prompts/00-kickoff.md` to load `.learnings/`, check `workspace/documents/` for newly added files, and present Workflow 11 in the kickoff menu.

**Files:**
- Modify: `prompts/00-kickoff.md:7-73`

**Step 1: Update `prompts/00-kickoff.md`**

In `prompts/00-kickoff.md`:
1. In `## Agent: load this first`, add:
   `5. .learnings/system-adaptations.md and .learnings/career-journey.md (if present) — calibrated weights and career context.`
   `6. Check workspace/documents/ for any newly added files to ingest.`
2. In `## Menu`, add:
   `11. **Self-improvement & learnings** — review career past/present/future, market feedback, and tune system`
   and renumber "Update my profile" to 12 and "Run a deep module" to 13.
3. In `## Routing` table, add row for 11 (`prompts/11-self-improvement.md`) and adjust 12 and 13.

Apply exact diff:

```diff
--- a/prompts/00-kickoff.md
+++ b/prompts/00-kickoff.md
@@ -12,4 +12,6 @@
 3. `workspace/profile/profile.md` — positioning.
 4. `workspace/applications/tracker.csv` — the current pipeline.
+5. `.learnings/system-adaptations.md` and `.learnings/career-journey.md` (if present) — calibrated weights and career context.
+6. Check `workspace/documents/` for any newly added files to ingest.
 
 Then, before saying anything else, check for anything overdue: rows where `next_action_date` has passed. Lead with those. A menu is not useful if three follow-ups are three days late.
@@ -46,4 +48,5 @@
 > 9. **Think through an offer** — evaluate it, frame a counter
 > 10. **Weekly review** — what's stalled, what's next, is this working
+> 11. **Self-improvement & learnings** — review career past/present/future, market feedback, and tune system
-> 11. **Update my profile** — resume, STAR stories, positioning
-> 12. **Run a deep module** — career change, exec positioning, comp, portfolio, relocation, re-entry, clearance
+> 12. **Update my profile** — resume, STAR stories, positioning
+> 13. **Run a deep module** — career change, exec positioning, comp, portfolio, relocation, re-entry, clearance
 >
 > Or just say what you need.
@@ -65,4 +68,5 @@
 | 9 | `prompts/09-offer-negotiation.md` |
 | 10 | `prompts/10-weekly-review.md` |
+| 11 | `prompts/11-self-improvement.md` |
-| 11 | the relevant `templates/` file, edited in place |
-| 12 | `SETUP.md` § 4 |
+| 12 | the relevant `templates/` file, edited in place |
+| 13 | `SETUP.md` § 4 |
```

**Step 2: Verify `prompts/00-kickoff.md`**

Run:
```bash
grep -n "11-self-improvement" prompts/00-kickoff.md
```
Expected output:
Matches in `prompts/00-kickoff.md`.

**Step 3: Commit**

```bash
git add prompts/00-kickoff.md
git commit -m "feat: wire .learnings, workspace/documents, and self-improvement into 00-kickoff"
```

---

### Task 13: Update Role Scoring (`02-role-scoring.md`) and Resume Tailoring (`04-resume-tailor.md`)

**Objective:** Enable `02-role-scoring.md` and `04-resume-tailor.md` to check `.learnings/` for calibrated rubric overrides and unwritten achievements/authentic voice, and check `workspace/documents/` for relevant work samples.

**Files:**
- Modify: `prompts/02-role-scoring.md:1-35`
- Modify: `prompts/04-resume-tailor.md:1-30`

**Step 1: Update `prompts/02-role-scoring.md`**

Add `.learnings/system-adaptations.md` and `.learnings/application-learnings.md` to Inputs in `prompts/02-role-scoring.md`. In Step 2 (Score each criterion), add explicit instruction:
`Check .learnings/system-adaptations.md for calibrated weight overrides before using default weights. Note if an elimination pattern from .learnings/application-learnings.md applies.`

**Step 2: Update `prompts/04-resume-tailor.md`**

Add `.learnings/career-journey.md`, `.learnings/system-adaptations.md`, and `workspace/documents/` to Inputs in `prompts/04-resume-tailor.md`. Add instruction:
`Consult .learnings/career-journey.md for unwritten competencies and authentic voice preferences, .learnings/system-adaptations.md for tone/vocabulary rules, and workspace/documents/ for deeper source evidence or portfolio details.`

**Step 3: Verify changes**

Run:
```bash
grep -n "\.learnings" prompts/02-role-scoring.md prompts/04-resume-tailor.md
```
Expected output:
Shows matching lines in both files.

**Step 4: Commit**

```bash
git add prompts/02-role-scoring.md prompts/04-resume-tailor.md
git commit -m "feat: integrate .learnings and workspace/documents into scoring and tailoring"
```

---

### Task 14: Update Weekly Review (`prompts/10-weekly-review.md`) to Feed the Learning Loop

**Objective:** Connect Step 5 (Read the elimination reasons) and Step 7 (Next week: one system fix) of `prompts/10-weekly-review.md` directly into `.learnings/` and trigger Workflow 11 when patterns emerge.

**Files:**
- Modify: `prompts/10-weekly-review.md:55-95`

**Step 1: Update `prompts/10-weekly-review.md`**

In `prompts/10-weekly-review.md`:
1. Under **Inputs**, add `.learnings/system-adaptations.md` and `.learnings/application-learnings.md`.
2. Under **5. Read the elimination reasons**, add instruction:
   `Append recurring elimination patterns to .learnings/application-learnings.md.`
3. Under **7. Next week**, add instruction:
   `Record the single system fix in .learnings/system-adaptations.md under § 5 (Changelog) and calibrate weights or search terms accordingly.`
4. At the end of the review, offer:
   `"Would you like to run 11-self-improvement to do a deeper calibration on your career goals and market fit?"`

**Step 2: Verify changes**

Run:
```bash
grep -n "\.learnings" prompts/10-weekly-review.md
```
Expected output:
Shows matching lines in `prompts/10-weekly-review.md`.

**Step 3: Commit**

```bash
git add prompts/10-weekly-review.md
git commit -m "feat: wire weekly review findings into .learnings and self-improvement"
```

---

### Task 15: Update `skill/SKILL.md` to Expose Self-Improvement and Ingestion

**Objective:** Keep the Claude/Hermes skill definition synchronized with the new workflow, document intake directory, and file structure.

**Files:**
- Modify: `skill/SKILL.md:15-40`

**Step 1: Update `skill/SKILL.md`**

In `skill/SKILL.md`:
1. Add `.learnings/` and `workspace/documents/` to the "Before anything else" section:
   `Read .learnings/ (career-journey.md, application-learnings.md, system-adaptations.md) for personal context and system adaptations. Check workspace/documents/ for user-uploaded source files.`
2. In the Routing table, add:
   `| review learnings / self-improve the system | ../prompts/11-self-improvement.md |`
3. In the reference list, add `../reference/self-improvement.md`.

**Step 2: Verify `skill/SKILL.md`**

Run:
```bash
grep -n "11-self-improvement" skill/SKILL.md
```
Expected output:
Shows the new routing entry.

**Step 3: Commit**

```bash
git add skill/SKILL.md
git commit -m "feat: add self-improvement and document intake routing to skill/SKILL.md"
```

---

### Task 16: Update `README.md` System Documentation

**Objective:** Document `workspace/documents/`, `.learnings/`, and Workflow 11 in `README.md` so non-coders and contributors understand the entire intake and self-improvement architecture.

**Files:**
- Modify: `README.md:15-50`

**Step 1: Update `README.md`**

In `README.md`:
1. In the file tree under `## What you get`, add:
```
.learnings/
  career-journey.md           past context, present bandwidth, future horizon
  application-learnings.md    market feedback, resonance vs rejection patterns
  system-adaptations.md       calibrated weights, query overrides, tone rules
workspace/
  documents/                  drop folder for your uploaded resumes, reviews, samples
  profile/
...
```
2. In the workflow table, add:
```
| 11 | self-improvement | capture career learnings, refine system adaptations |
```
3. Under `## Where to look next`, add `- reference/self-improvement.md — how continuous learning, document ingestion, and calibration works`.

**Step 2: Verify `README.md`**

Run:
```bash
grep -n "workspace/documents" README.md
```
Expected output:
Shows line with `workspace/documents`.

**Step 3: Commit**

```bash
git add README.md
git commit -m "docs: update README with .learnings and workspace/documents structure"
```

---

### Task 17: Run Full Verification Suite & Link Integrity Checks

**Objective:** Verify that all template, intake, prompt, and reference files exist, that no broken relative links exist across workflows, and that `.gitignore` correctly protects user data.

**Files:**
- None modified; validation pass only.

**Step 1: Run comprehensive presence check**

Run:
```bash
bash -c '
files=(
  "workspace/documents/.gitkeep"
  "workspace/documents/README.md"
  ".learnings/.gitkeep"
  ".learnings/README.md"
  "templates/.learnings/career-journey.md"
  "templates/.learnings/application-learnings.md"
  "templates/.learnings/system-adaptations.md"
  "reference/self-improvement.md"
  "prompts/11-self-improvement.md"
)
missing=0
for f in "${files[@]}"; do
  if [ ! -f "$f" ]; then
    echo "MISSING: $f"
    missing=$((missing + 1))
  else
    echo "OK: $f"
  fi
done
exit $missing
'
```
Expected output:
`OK` for all 9 files, exit code 0.

**Step 2: Verify git ignore privacy rules**

Run:
```bash
git check-ignore -v workspace/documents/my_resume.pdf .learnings/career-journey.md .learnings/application-learnings.md .learnings/system-adaptations.md
```
Expected output:
All four personal files show matched by `.gitignore` rules.

**Step 3: Verify git status is clean**

Run:
```bash
git status
```
Expected output:
Working tree clean, on branch `main`.

---

## Risks, Tradeoffs, and Open Questions

1. **Risk: Handling various binary document formats (PDFs, DOCX, scans).**
   - *Risk:* Non-coders upload formatted PDFs or Word docs that plain text readers cannot parse natively without tools.
   - *Mitigation:* The system documentation instructs agents to use standard document-reading tools (such as native agent docx/pdf readers or `read_file` document extractors) and provides plain-text/markdown fallback guidance.
2. **Risk: Information duplication between `workspace/documents/`, `master-resume.md`, and `career-journey.md`.**
   - *Risk:* Conflicts between an old resume PDF in `workspace/documents/` and the live `master-resume.md`.
   - *Mitigation:* `master-resume.md` remains the active source of truth for applications; `workspace/documents/` is an intake archive; `career-journey.md` captures formative background and future trajectory.
3. **Tradeoff: Local privacy vs cloud portability.**
   - *Tradeoff:* By ignoring `workspace/documents/` and `.learnings/` in git by default, uploads stay private to the user's local machine.
