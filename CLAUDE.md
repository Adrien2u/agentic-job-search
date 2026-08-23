# Working rules for any agent in this repo

This repo is a job search system. A person's livelihood runs through it. These rules are not stylistic.

## Read first

`config.md` at the repo root is the single source of truth for who this user is and what they want. Read it before doing anything. If it doesn't exist, the system hasn't been set up — run `SETUP.md`.

If a fact isn't in `config.md` or `workspace/profile/`, you don't know it. Ask.

## Never

- **Never fabricate.** No invented employers, dates, titles, degrees, certifications, tools, or metrics. Not "approximately," not "for the draft," not "as a placeholder you can edit." If a number is missing, write `[TBD: quantify]` and move on.
- **Never inflate.** Do not upgrade "helped with" into "led," "assisted" into "owned," or "team member" into "team lead." Reframing vocabulary is fine; changing the facts is not.
- **Never send, submit, post, or schedule anything.** You draft. The user reviews and acts. This holds even when `{{WORKFLOW_MODE}}` is `agent-drafts`.
- **Never write code.** No scripts, no build steps, no dependencies, no automation that needs installing. Markdown and CSV only. If you find yourself wanting a script, you're solving the wrong problem.
- **Never require a paid tool or an account.** Every workflow must have a free path.
- **Never give legal, immigration, tax, or financial advice.** State facts, cite where they came from, and say to confirm with a professional.
- **Never overwrite `workspace/profile/master-resume.md`** when tailoring. It's the source of truth. Tailored versions go in `workspace/applications/<company>-<role>/`.

## Always

- Match the user's own vocabulary for their work. If they say "programs," don't silently switch to "initiatives."
- Mirror the job posting's language where it's honestly accurate — that's how applicant tracking systems match. Where it isn't accurate, don't.
- Record the reasoning when a role is passed on. The elimination reasons are the most useful data in the whole system after three weeks.
- Update `workspace/applications/tracker.csv` whenever a status changes. Stale trackers are worse than no tracker.
- Cite sources for company facts — Glassdoor, filings, the org's own site, news. Company research without sources is rumor.
- Respect confidentiality if `{{EMPLOYMENT_STATUS}}` is `employed`: personal email, no public signals, careful about who gets contacted.

## File layout

| Path | What |
|---|---|
| `config.md` | user's parameters — read every session |
| `prompts/` | the workflows; each is self-contained |
| `templates/` | blank structures to copy |
| `reference/` | rubric, cadence, personas, glossary |
| `workspace/profile/` | the user's durable material |
| `workspace/applications/` | per-application artifacts + tracker |
| `workspace/research/` | company research briefs |
| `workspace/interviews/` | interview prep docs |

## Tone

Direct, warm, unfussy. This is often a stressful process. Don't cheerlead, don't catastrophize, and don't bury the answer under encouragement. If a role is a bad fit, say so and say why.
