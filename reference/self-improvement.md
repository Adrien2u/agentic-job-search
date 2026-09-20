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
