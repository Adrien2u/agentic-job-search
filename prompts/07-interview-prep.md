# 07 — Interview Prep

Produce a prep doc for one specific conversation.

**Inputs:** the posting, `workspace/research/{{COMPANY}}.md`, the tailored resume, `workspace/profile/star-stories.md`, interview type and interviewer names
**Output:** `workspace/interviews/{{COMPANY}}-{{ROUND}}.md` from `templates/interview-prep.md`

---

## Ask first

- Which round, and what format — phone, video, onsite
- Who's on it, with titles
- How long
- Anything they told the user to prepare

Without the interviewer names, prep is generic and generic prep is barely prep.

## By round

**Recruiter screen (20–30 min).** Filtering for realness, interest, logistics, and comp alignment. Prep: the 90-second "tell me about yourself," a comp answer, availability, and why this role. Do not go deep technically — that isn't what's being assessed, and depth here reads as not listening.

**Hiring manager (45–60 min).** Capability and judgment. Prep: 4–6 STAR stories mapped to the posting's actual responsibilities, a view on what the role's first 90 days should look like, and real questions about the team.

**Peer / team.** "Would I want to work next to this person." Prep: collaboration and conflict stories, genuine curiosity about their work. Warmth matters more than polish here.

**Skip-level or executive.** Judgment, scope, and strategic read. Prep: the broader context of the user's work, opinions held lightly, and a question about where the org is heading.

**Panel.** Answer to whoever asked, then include the room. Assume no shared context between them — repeating yourself across interviewers is expected, not a failure.

**Technical / case / presentation.** Ask what tools are permitted and whether it's live. Narrate the reasoning out loud; a clean answer with silent reasoning scores worse than a rough answer with visible thinking.

**Final round.** Often a decision that's already 80% made. Prep the closing pitch and the questions that show you're evaluating them too.

## Build the doc

### 1. Logistics cheat sheet

Five lines, read right before starting. Link or address, who you're meeting, one-line pitch, comp answer, closing question. Nothing else — this is the panic-prevention page.

### 2. Interviewer profiles

For each: background worth knowing, and what they'll likely probe. Sourced from LinkedIn, the company site, talks or writing. If nothing is findable, say so rather than guessing.

### 3. Five company facts

Five, from memory, from the research brief. Not twenty. **Re-check the news the day before** — twelve months of research is undone by one week's announcement.

### 4. Key Reframing Guide

The most useful table in the doc, and essential for `career-changer`:

| What I've done | How to say it at {{COMPANY}} |
|---|---|

Left column: the user's natural vocabulary. Right: the same fact in the org's dialect, sourced from the posting, their site, and how the recruiter talked. Translation, never exaggeration — if the right column claims more than the left, it's wrong.

### 5. Ten to twelve likely questions, with written answers

Mix: 2 about them and their trajectory, 3–4 behavioral, 2–3 role-specific, 1 comp, 1 why-them, 1 on the hard question.

Write the answers out. They won't be read during the interview — writing them is what makes them available under pressure.

Each answer gets an anchor STAR story from `star-stories.md` and one point it must land.

### 6. Tell me about yourself

Ninety seconds, three beats: what you do now and its scope → the one or two moves that make the path coherent → why this role, this org, now. Ends pointed at them.

Rehearsed out loud. It's the only answer that's guaranteed to come up and the one most often improvised badly.

### 7. The hard question

Everyone has one — gap, change, short tenure, over- or under-qualified, a firing, relocation. Name it and answer in three sentences: acknowledge, explain briefly, pivot to evidence. Answered flatly it costs almost nothing; dodged it becomes the whole interview.

### 8. Six questions to ask

They'll get to three. Never "no, you covered everything."

Always include: **what are the next steps, and when do you expect to decide?** Without both, follow-up becomes guesswork.

Strong ones: what does success look like at 90 days · new role or backfill, and what happened with the last person · what's the team struggling with right now · what would you change if you could · how are decisions made when people disagree.

### 9. Comp handling

Deflect early: *"I'd like to understand the scope better first — do you have a range budgeted?"* If pressed, give a range with `{{COMP_FLOOR}}` at the bottom. Asking for their range is normal and, in many jurisdictions, legally required on request.

### 10. Closing pitch — 20 seconds

Their top need, the user's evidence for it, plain statement of interest. Rehearsed once out loud.

## Persona notes

```
career-changer → the Reframing Guide is the centerpiece. Expect "why the change?"
  in every round and answer it identically and confidently each time.
entry-level    → coursework and projects are legitimate STAR sources. Expect
  "why this field?" and "where do you want to be in five years."
senior-ic      → expect probing on depth. Have one story where you were the last
  line of defense on something hard.
people-leader  → expect underperformance, conflict, and layoff scenarios. Have real ones.
executive      → expect scope questions and a strategic read on their market. Have an
  opinion about their industry, held lightly.
```

## Day before

- [ ] Re-read the doc once, don't memorize it
- [ ] Re-check the news for anything from the last week
- [ ] Test the video link, camera, mic, and background
- [ ] Confirm the time zone. This failure is common and entirely avoidable
- [ ] Print or open the resume version you actually sent them
- [ ] Rehearse "tell me about yourself" and the closing pitch out loud, once each

## After

Debrief while it's fresh — what went well, what fumbled, what surprised you, what you learned about the role, and the next step and date they gave. Thank-you within 24 hours via `prompts/08-follow-up.md`. Any new story the conversation surfaced goes into `star-stories.md`.
