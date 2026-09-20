# agentic-job-search

A complete job search system that an AI agent sets up for you by asking about ten questions.

No code. No accounts. No subscriptions. No spreadsheet you have to learn. Everything is plain markdown and one CSV file, sitting on your own machine, and an agent that knows how to use them.

It works for a nursing student applying to their first hospital job, a teacher moving into UX, a staff engineer who wants to stay hands-on, and a VP who never touches a job board. The setup interview routes on which one you are, and every downstream workflow adapts.

---

## What you get

After setup, you have:

```
config.md                       everything the agent knows about your search
.learnings/
  career-journey.md             past context, present bandwidth, future horizon
  application-learnings.md      market feedback, resonance vs rejection patterns
  system-adaptations.md         calibrated weights, query overrides, tone rules
workspace/
  documents/                    drop folder for uploaded resumes, reviews, samples
  profile/
    profile.md                  who you are, positioning, strengths
    master-resume.md            your full history — the source of truth
    star-stories.md             interview stories, organized by competency
    outreach-log.md             who you talked to and when
  applications/
    tracker.csv                 the pipeline
    weekly-log.md               volume and outcomes, week by week
    <company>-<role>/           tailored resume, cover letter, notes
  research/                     company briefs
  interviews/                   prep docs
```

And twelve workflows you invoke by name:

| | Workflow | What it does |
|---|---|---|
| 00 | kickoff | start a session, pick what you're doing |
| 01 | role discovery | where to look and what to search for, tuned to you |
| 02 | role scoring | a weighted 0–100 score and a real go/no-go |
| 03 | company research | a sourced brief before you apply or interview |
| 04 | resume tailor | a version aimed at one posting, without lying |
| 05 | cover letter | five-part structure, then cut to 280 words |
| 06 | outreach | recruiter, hiring manager, warm intro, alumni |
| 07 | interview prep | phone screen through final round |
| 08 | follow-up | when to nudge, what to say, when to let go |
| 09 | offer & negotiation | evaluate the whole package, frame a counter |
| 10 | weekly review | what's stalled, what's next, is this working |
| 11 | self-improvement | capture career learnings, refine system adaptations |

---

## Quick start

### If you use a coding agent (Claude Code, Cursor, etc.)

```
git clone https://github.com/Adrien2u/agentic-job-search.git
cd agentic-job-search
```

Open it with your agent and say:

> Read SETUP.md and set up my job search system.

Answer the questions. You're done in five minutes.

### If you just use chat (claude.ai, ChatGPT, etc.)

You don't need a filesystem. Every file here is self-contained and copy-pasteable.

1. Open `SETUP.md`, paste the whole thing into a new chat, and add: *"Run this setup with me."*
2. Answer the questions. The agent will output the contents of your files as text — save them wherever you like (a doc, a note, a folder).
3. For any later task, paste the relevant `prompts/` file plus your `config.md` and `master-resume.md`, then say what you want.

The tradeoff: you're doing the file management by hand. Everything else is identical.

### If you use Claude Skills

`skill/SKILL.md` packages the whole system as a skill. Drop the repo into your skills directory and Claude will pull it in when you talk about your job search.

---

## Design rules

Four rules, held throughout:

1. **The agent never invents a fact about you.** Not a date, not an employer, not a percentage. If something's missing it says `[TBD]` and asks. A resume with a made-up number is a resume that ends an interview badly.
2. **The agent drafts, you decide.** Nothing is submitted, sent, or posted on your behalf. Ever.
3. **No paid dependencies.** Every step has a free path. Assessments like CliftonStrengths are supported if you have them and completely optional if you don't.
4. **No code.** Nothing to install, nothing to run, nothing to break in six months.

---

## Setup depth

The quick path is ten questions and gives you a working system. Seven optional deep modules go further when your situation calls for it — career change narrative, executive positioning, compensation strategy, portfolio, relocation, re-entry after a gap, clearance and licensure. The agent recommends the ones your situation implies; you can run any of them later by saying so.

---

## Where to look next

- `SETUP.md` — the setup interview (written for the agent, readable by you)
- `CLAUDE.md` — the standing rules the agent follows every session
- `reference/self-improvement.md` — how continuous learning, document ingestion, and calibration works
- `reference/personas.md` — the six archetypes and how the system shifts for each
- `reference/scoring-rubric.md` — how roles get scored, and how to change the weights
- `reference/cadence.md` — follow-up timing
- `reference/glossary.md` — ATS, STAR, and the rest of the jargon

---

## Privacy

Your data lives in `workspace/`, `.learnings/`, and `config.md`, and all three are gitignored by default. If you fork this to a private repo and *want* your search versioned, delete those lines from `.gitignore`.

---

MIT licensed. Fork it, change the rubric, rewrite the templates — that's the point.
