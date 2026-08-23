# 09 — Offer & Negotiation

Evaluate the whole package, then frame a counter.

**Inputs:** the offer details, `config.md`, `workspace/research/{{COMPANY}}.md`
**Output:** a comparison, a recommendation, and a script

---

## Boundaries

This is a negotiation *framework*, not legal, tax, or financial advice. Employment agreements, non-competes, equity terms, and tax treatment vary by jurisdiction and by contract. For anything binding, the user talks to a qualified professional. Say so once, plainly, and then be useful.

---

## Step 1 — Buy time

Never accept on the call. Never counter on the call either.

> "Thank you — I'm genuinely pleased. Could you send the details in writing? I'd like to review the full package properly and come back to you by {{DATE}}."

Two to five business days is standard and expected. An employer who won't allow 48 hours to read an offer has told the user something useful about how they operate.

## Step 2 — Get it in writing

Base · bonus (target and how it's actually determined) · equity (type, count, strike, vesting, cliff, current valuation) · sign-on and any clawback · start date · title · reporting line · work mode and any onsite requirement · PTO and whether it's accrued · retirement match and vesting · health premium cost to the employee · relocation · severance · non-compete or non-solicit · review and promotion cycle.

An offer discussed only verbally is not an offer.

## Step 3 — Total comp

| Component | This offer | Current / other offer | Notes |
|---|---:|---:|---|
| Base | | | |
| Target bonus | | | actual payout history, if known |
| Equity (annualized) | | | see below |
| Sign-on (year 1 only) | | | clawback terms? |
| Retirement match | | | % of base, vesting schedule |
| Health premium (annual, employee cost) | | | a real number, often thousands |
| PTO value | | | days × daily rate |
| Other | | | learning budget, stipends |
| **Total, year 1** | | | |
| **Total, steady state** | | | year 1 minus sign-on |

Compare on steady state. A sign-on makes year one look better than the job is.

**Equity:** RSUs at a public company have a knowable value. Private-company equity has a *number*, not a value — model it at zero and treat anything above that as upside. Options at a high strike price frequently end up worth nothing. Do not let an equity figure carry the offer.

## Step 4 — The non-comp side

Money is the easiest thing to compare and rarely the thing people leave over.

| Factor | Read | Weight |
|---|---|---|
| Manager | the single biggest predictor of whether this goes well | high |
| Scope and autonomy | is this the work they want to do | high |
| Growth | is there a next step, and does it exist today | high |
| Org health | from research — runway, layoffs, leadership churn | high |
| Culture read | what the interviews actually showed | medium |
| Commute / flexibility | the daily cost of the job | medium |
| Team | who they'd work beside | medium |

If the score against `reference/scoring-rubric.md` was under 65 and the offer is strong, that gap is worth naming out loud before deciding.

## Step 5 — Should you counter?

Almost always yes, on something. Most employers expect one round and have room. A polite, specific counter very rarely costs an offer — offers being pulled over a reasonable counter is rare enough to be notable when it happens.

Counter on the thing that matters most, and ask for one or two things, not six:

- **Base** — most valuable, compounds into every future raise and offer
- **Sign-on** — easiest yes, since it doesn't touch the band
- **Equity** — meaningful only where equity is actually liquid
- **Start date** — free to give, genuinely valuable
- **Title** — matters more than it should for the *next* search
- **Remote or flexibility days** — often costs the employer nothing
- **Review at 6 months** — good fallback when the band is genuinely capped

Weak positions to counter from: no competing offer, no market data, no specific number. Bring at least one of the three.

## Step 6 — The script

> Hi {{NAME}} — thank you again for the offer. I'm excited about {{SPECIFIC_THING}} and I want to make this work.
>
> Based on {{MARKET_DATA / COMPETING_OFFER / THE_SCOPE_WE_DISCUSSED}}, I was targeting {{NUMBER}} for base. Is there room to get closer to that?
>
> {{OPTIONAL_SECOND_ASK}}
>
> Everything else looks good, and I'm ready to move forward once we settle this.

What makes it work: enthusiasm first, one specific number, a stated reason, and a clear signal that this closes the deal. What breaks it: an ultimatum, a vague "can you do better," or three separate asks.

**Never bluff a competing offer.** It gets called, occasionally verified, and it ends the process.

## Step 7 — Handling the response

| They say | Do |
|---|---|
| Yes | confirm in writing, then accept in writing |
| Partial | usually take it. One round is normal; a second reads as bad faith |
| No, band is capped | ask for sign-on, start date, or a 6-month review instead |
| "Best and final" | it's a real signal. Decide on the offer in front of you |
| Pressure to answer immediately | a data point about the org. Hold the original date politely |

## Step 8 — Decide

Compare against: the other offers, the current situation, and *doing nothing*. Staying is a real option with real value, and it's the one people forget to price.

Declining well:

> Thank you for the offer and for the process — I've decided to accept another role. I was genuinely impressed by {{SPECIFIC}}, and I hope our paths cross again.

No detailed justification, no apology. Decline in writing, promptly.

## Step 9 — Accepting

- Accept in writing, referencing the written terms
- **Do not resign until the signed offer is in hand** and any background check has cleared
- Withdraw from every other active process explicitly (`prompts/08-follow-up.md`)
- Update the tracker: `Accepted`, and close every open row
- Thank everyone in `outreach-log.md` who helped, and tell them how it turned out

That last line is the one people skip, and it's the whole difference between a search that ended and a network that persists.

---

## Persona notes

```
IF PERSONA = executive THEN
  Negotiate severance and change-of-control terms explicitly — these matter more than
  base at this level. Equity structure, vesting acceleration, and board reporting are
  in scope. Get a lawyer to read the agreement. This is standard, not adversarial.

IF PERSONA = entry-level THEN
  Countering is still normal and still expected. A modest, polite ask on base or a
  sign-on is fine. Program roles with fixed, published bands genuinely have no room —
  ask, accept the answer, move on.

IF EMPLOYMENT_STATUS = unemployed THEN
  The position is weaker and the pressure is real. Still counter — once, politely.
  Set a walk-away number in advance, before the emotion of an actual offer is in the room.
```
