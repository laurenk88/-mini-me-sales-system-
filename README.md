# Mini Me Sports — Sales Intelligence & Prospecting System

A system to help Mini Me Sports (MMS) spend less time on repetitive research, CRM upkeep,
and follow-up — and more time on the human conversations that actually win partnerships.

MMS runs on-site multi-sport enrichment programs for kids ages 2.5–5 at early childhood
schools around the Minneapolis/St. Paul metro (within ~60 minutes). The sale is getting a
school's **director or owner** to say yes to a partnership; most revenue then comes from
parents enrolling their kids monthly.

## What this system is being built to do (long-term)

1. Understand why schools buy, reject, or ignore MMS — from real evidence.
2. Sharpen the offer/positioning around the highest-value problem MMS solves.
3. Research prospects automatically instead of by hand.
4. Surface the strongest, evidence-based reason each specific school should care.
5. Tell Lauren who to contact, what to know first, and the best angle for a call/visit.
6. Make CRM updates and touchpoint tracking far less manual.
7. Make sure no prospect slips because a follow-up was forgotten.
8. Feed what we learn back into marketing and content.

We are building this in **small, high-value steps** — each one useful on its own and a
foundation for the next. We are deliberately **not** automating the relationship or the
selling itself.

## Where we are

| Build | What it does | Status |
|-------|--------------|--------|
| **1. Lead Enrichment** | Auto-researches in-range schools and fills the CRM with the facts that predict a *yes*, so the "who to call next" list finally has real signal. | **Live — 75 schools enriched** |
| **1b. Daily 10** | Ten schools to work each weekday (email or visit), drawn from the enriched pool, self-refreshing as leads are worked. | **Live** |
| 2. Follow-up safety net | Makes sure every active prospect has a next action + date, and nothing goes quiet by accident. | Planned |
| 3. Won/lost evidence & positioning | Mines Gmail/Docs/proposals to learn why schools really buy, and sharpens the offer. | Planned |
| 4. Marketing feedback loop | Turns sales/prospect learnings into marketing and content direction. | Planned |

## The evidence behind Build 1

From MMS's own sales experience, two things predict which schools say yes:

- **Independent, owner-operated schools** say yes far more often than corporate/national
  chains or franchises (which need HQ approval and rarely grant it).
- **Schools with little or no existing enrichment** have the biggest opening.

Neither of those facts lived in the CRM, and both are tedious to look up by hand across
1,100+ schools — which is exactly why earlier attempts to prioritize the list stalled.
Build 1 fills that gap automatically.

See [`docs/enrichment-playbook.md`](docs/enrichment-playbook.md) for how it works and how to
run it on the rest of the list.

## The CRM

Live CRM is Airtable — base **"MMS Sales Pipeline"**, table **Schools** (~1,140 schools).
The system reads and writes there directly. Build 1 added six clearly-labeled research
fields; it never overwrites anything already in the CRM.
