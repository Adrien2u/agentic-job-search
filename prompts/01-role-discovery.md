# 01 — Role Discovery

Find openings worth scoring. The output is candidates, not decisions — scoring is `02`.

**Inputs:** `config.md`
**Output:** rows added to `tracker.csv` with status `Researched`

---

## Where to look, by persona

Channel choice matters more than search-string cleverness. `{{PERSONA}}` decides the mix.

```
IF PERSONA = entry-level THEN
  1. University career center and campus recruiting calendar — cycles, not continuous posting
  2. Alumni directory, filtered to your target roles
  3. Entry-level and internship-tagged boards
  4. Professional association student memberships — usually cheap or free, and the job board is the point
  5. Large-employer early-career programs — these have fixed application windows. Find the dates.
  Aggregators last. They are the most competitive channel and the least effective at this level.

IF PERSONA = early-career THEN
  1. Former colleagues who have moved on — the highest-yield channel and the most neglected
  2. Aggregators and major boards, saved-search alerts on
  3. Target-company career pages directly
  4. Professional association boards
  5. Recruiters who specialize in your function

IF PERSONA = career-changer THEN
  1. Roles ADJACENT to {{ORIGIN_INDUSTRY}} first — the bridge is shorter and the story lands
  2. Orgs that hire from your origin field on purpose. They exist; find them by looking at
     where people with your background ended up on LinkedIn
  3. Communities in the target field — the vocabulary you pick up there is half the work
  4. Roles that explicitly say "or equivalent experience"
  Outreach is not optional here. The resume screen is the step working against you;
  a referral skips it.

IF PERSONA = senior-ic THEN
  1. Specialist communities, forums, Slack and Discord groups in your discipline
  2. Conference speaker and attendee lists
  3. Open source, standards bodies, working groups
  4. Niche discipline-specific boards over aggregators
  5. Specialist recruiters — they know which "Senior" postings are actually Staff

IF PERSONA = people-leader THEN
  1. Direct company career pages at orgs you'd want to work for
  2. Your own former reports and peers — they refer managers they liked
  3. Function-specific leadership communities
  4. Recruiters at the manager and director level

IF PERSONA = executive THEN
  1. Executive search firms — build relationships BEFORE you need them
  2. Board and advisory networks
  3. Investor and portfolio-company introductions
  4. Direct outreach to the hiring principal — CEO, board chair, or the search committee
  5. Industry associations at the executive tier
  Job boards are the LAST channel, not the first. Most roles at this level are
  never posted, and the ones that are have usually been decided.
```

## Search strings

Build these from `config.md`, then hand them to the user to paste into whichever board they use:

```
"{{TARGET_ROLE}}" {{LOCATION}} {{WORK_MODE}}
"{{TARGET_ROLE}}" {{TARGET_INDUSTRY}}
{{TARGET_ROLE_SYNONYM}} {{LOCATION}}
```

**Title synonyms matter more than anything else here.** The same job is posted as Program Manager, Project Manager, Delivery Manager, Engagement Manager, and Initiative Lead at five different orgs. Generate 5–8 real synonyms for each entry in `{{TARGET_ROLES}}` and search all of them. Missing a synonym means missing an entire slice of the market silently.

**Site-restricted search** finds career pages that aggregators miss:

```
site:{{COMPANY_DOMAIN}} careers "{{TARGET_ROLE}}"
```

## Filters to apply

| Filter | Setting |
|---|---|
| Location | `{{LOCATIONS}}` + Remote if `{{WORK_MODE}}` includes it |
| Posted within | 14 days. Older postings are frequently filled or stale |
| Exclude | `{{EXCLUDED_INDUSTRIES}}` |
| Seniority | match `{{PERSONA}}`, but read the responsibilities — titles lie |

## What to capture per candidate

Enough to score it, nothing more:

- Company, exact title, URL, **the posting text saved locally**, date posted, comp if published, location and work mode, source channel

Save the posting text. They disappear, and you will want it the night before an interview.

## Volume

Find roughly 3× `{{WEEKLY_APPLICATIONS}}` candidates per session. Scoring will cut most of them, and that's the system working — a pipeline where everything scores above 80 means the search is too narrow or the scoring is inflated.

## Red flags — skip before scoring

- Reposted continuously for months. Something is wrong with the role, the comp, or the manager.
- No company name, or a "confidential client" with no recruiter you can identify.
- Asks for payment, personal financial details, or a "training fee." Always a scam.
- A wildly wide comp range on a specific role — usually a fishing posting, not a real req.
- Requirements that don't cohere (entry-level title, 8 years required, executive scope). Nobody owns this posting.

## Then

Add to `tracker.csv` with status `Researched`, then score them with `prompts/02-role-scoring.md`. Do not apply to anything unscored — that is how a pipeline fills with roles nobody actually wanted.
