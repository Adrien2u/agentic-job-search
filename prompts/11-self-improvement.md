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
