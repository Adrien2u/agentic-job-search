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
