# 08 — Follow-Up

Thank-yous, nudges, and closing things out. The stage most searches drop entirely.

**Inputs:** `tracker.csv`, `reference/cadence.md`, `config.md`
**Output:** a draft message + updated tracker row

---

## What's due

Start by listing every row where `next_action_date` has passed. Timing comes from `reference/cadence.md`, keyed to `{{URGENCY}}`.

Quick reference, business days, `active`:

| Trigger | Action | When |
|---|---|---|
| Applied | find a human at the org | +2 |
| Applied, silence | first nudge | +8 |
| Applied, silence | second and final nudge | +18 |
| Applied, silence | mark Ghosted | +28 |
| Any interview | thank-you note | within 24h, always |
| Their stated deadline passed | nudge | +2 |
| Interviewed, no date given | nudge | +7 |
| Outreach, silence | follow-up | +5 |
| Outreach, two attempts | stop | — |

If they gave a date, their date wins over this table. Follow up a week after it, not before.

---

## Tone, for all of it

- One short paragraph. Three sentences.
- **Add something.** An article, a thought about their problem, a finished credential. Never "just checking in."
- No guilt, no urgency theater, no "I haven't heard back from you."
- Reply in the existing thread.
- Silence is capacity, not insult. Recruiters carry 30 to 60 open roles.

---

## Templates

### Thank-you — within 24 hours, every interviewer, every round

> Subject: Thank you — {{ROLE}}
>
> Hi {{NAME}} — thanks for the time today. {{SPECIFIC_THING_THEY_SAID}} was the part I keep thinking about, particularly {{DETAIL}}.
>
> {{ONE_SENTENCE: reinforce the strongest point you made, or repair the weakest one}}
>
> Looking forward to {{NEXT_STEP_THEY_NAMED}}.
>
> {{FULL_NAME}}

Non-negotiable, and it's genuinely a differentiator because most candidates skip it. Individually written per interviewer — a panel comparing four identical notes is worse than none.

The middle line does real work: if an answer landed badly, this is the one chance to fix it. *"On the budget question — I gave you the annual figure, but the number that's actually relevant is the $2.1M I managed directly."*

### First nudge after applying

> Subject: Re: Application — {{ROLE}}
>
> Hi {{NAME}} — following up on my application for {{ROLE}}, submitted {{DATE}}.
>
> {{ONE_NEW_THING}}
>
> Still very interested. Happy to send anything useful.
>
> {{FULL_NAME}}

### Nudge after their deadline passed

> Hi {{NAME}} — you'd mentioned deciding by {{DATE}}, so I wanted to check in.
>
> No rush if timelines have shifted — that's normal. Just let me know where things stand when you get a chance.

_Referencing their own stated date makes this a reasonable question rather than a chase._

### Second and final nudge / close-out

> Hi {{NAME}} — last note from me on this one.
>
> I'm still interested in {{ROLE}}, but I'll assume the timing didn't line up. If that changes, I'd be glad to talk.
>
> Either way, thanks for your time.

_This sentence has restarted more processes than any third nudge ever has. It's graceful, it's final, and it leaves the door open without asking anyone to hold it._

### After a rejection

> Hi {{NAME}} — thanks for letting me know, and for the process.
>
> If you're open to it, I'd value a line on what would have made me a stronger fit — genuinely useful for me either way.
>
> And if something closer to my background opens up, I'd welcome hearing about it.

_Send this. Roughly a third reply with something useful, and re-approaching a candidate who handled a rejection well is common. A graceless rejection reply closes a door permanently for no gain._

### Withdrawing

> Hi {{NAME}} — I want to withdraw from consideration for {{ROLE}}. I've accepted another offer.
>
> Thanks for the time and consideration — the conversations were genuinely useful.

_Withdraw explicitly. Ghosting an employer costs the user in a way that isn't visible until it does._

### Staying in touch with a near-miss

> Hi {{NAME}} — it's been a few months. {{SOMETHING_ABOUT_THEIR_ORG}}.
>
> Still interested if anything opens up on your team. Hope things are going well.

_Every 3–4 months, and only where the process ended well. Second-choice candidates get called back when the first choice doesn't work out, which happens far more often than anyone advertises._

---

## Persona notes

```
IF PERSONA = executive THEN
  Everything is ~50% slower. While a search firm is engaged, follow up with the
  search partner, not the hiring company — going around them damages the relationship
  that's representing you.

IF PERSONA = entry-level THEN
  Cycle-based programs have fixed dates. Their timeline always wins. Slow is not rejection.

IF EMPLOYMENT_STATUS = employed AND confidential THEN
  Never from a work address or device.
```

## Closing things out

Mark `Ghosted` at the interval and mean it. A closed row is capacity returned, not a failure. Record the elimination reason.

Two nudges. Not three. A third does not produce a response; it produces a reputation.

## Then

Update `tracker.csv`: `last_action_date`, `next_action`, `next_action_date`, and `status` if it changed. Every open row has a next action and a date. If you can't name one, the row should be closed.
