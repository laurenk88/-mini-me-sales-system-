# Build 1 — Lead Enrichment Playbook

**Goal:** Turn the ~1,140-school raw list into a prioritized "who to call next" list by
automatically filling in the two facts that predict a *yes* — plus the basics you need to
actually make the call — so the CRM machinery you already have (Priority Score, views) finally
has real signal to work with.

This doc is the reusable method. Anyone (or any future Claude session) can follow it to enrich
the next batch of schools.

---

## What predicts a yes (the whole basis for this)

From MMS's own sales experience, two factors separate schools that say yes from schools that
don't:

1. **Independent / owner-operated** beats corporate/national chains and franchises. Chains need
   HQ approval and rarely grant it.
2. **Little or no existing enrichment** = the biggest opening. Schools already saturated with
   sports/dance/music are a harder, "differentiate don't fill a void" sell.

Everything below is built to capture those two things at scale, plus a third practical filter:

3. **Within ~60 minutes of Minneapolis/St. Paul.** Farther than that, MMS doesn't serve.

---

## The six research fields (in the Schools table)

These were added by Build 1. They are **additive** — the enrichment never overwrites anything
already in the CRM.

| Field | Type | What it holds |
|-------|------|---------------|
| **Ownership Type** | Single select | Independent / Local Chain (2-5 sites) / Regional/National Chain / Franchise / Faith-Affiliated / Nonprofit/Community / Unknown |
| **Enrichment Gap** | Single select | None Found (best) / Light / Heavy / Unknown |
| **Research Fit** | Single select | A - Call First / B - Good Fit / C - Lower Fit / Route - Chain/Out of Area |
| **Call Angle (Research)** | Long text | The evidence-based reason THIS school should care + key facts + ⚠ verify notes |
| **Research Confidence** | Single select | High / Medium / Low |
| **Researched On** | Date | When it was last researched (data goes stale, so this flags refreshes) |

Where a school's **Primary Contact Name / Email / Phone** was **empty**, enrichment fills it in
from research. If a value was already present, it is **left untouched** — even when research
suspects it's wrong, in which case the warning goes in the Call Angle instead (see the All
Saints example, where the email on file belongs to a different school).

---

## Scoring rubric (how Research Fit is decided)

- **A - Call First** — Independent / Faith / Nonprofit single-site **and** Enrichment Gap None
  or Light **and** in range. These are the profile that says yes most.
- **B - Good Fit** — Independent-style but Heavy existing enrichment, **or** a small local chain
  (2–5 sites) with a gap. Still in range.
- **C - Lower Fit** — Larger local chain, heavy overlapping enrichment, or a flagged risk (e.g.
  regulatory/fraud issues) — still worth knowing about, but not the first calls.
- **Route - Chain/Out of Area** — Regional/national chain or franchise (needs corporate
  approval → belongs in the Corporate Outreach table), **or** drive time clearly over ~60 min.

---

## How a batch gets enriched

1. **Select candidates** from the Schools table: `Stage = New Lead`, in-range city, and *not*
   an obvious national chain (those go to Corporate Outreach). Skip anything already worked.
2. **Research each school** with web search — the school's own website, Facebook, Google
   listing, **MN DHS licensing lookup**, and review sites. Find ownership, existing enrichment,
   director/owner + contact, rough size, and drive time.
3. **Score** each with the rubric above and write a plain-English **Call Angle**.
4. **Write back** to the six fields (and fill empty contact fields). Stamp **Researched On**.
5. **Flag, never fake.** If something can't be verified, lower the confidence and write
   "verify on call." A confident "couldn't confirm" is more useful than a made-up detail —
   daycare ownership and staff change constantly.

The exact research instructions used for each school are in
[`prompts/school-research-prompt.md`](../prompts/school-research-prompt.md). To enrich the next
batch, hand that prompt a new list of schools.

---

## Freshness

Daycares change directors, owners, and phone numbers often. Treat any enrichment older than a
few months as stale — re-run it (the **Researched On** date is there to spot these). Confidence
should always be read together with the date.

---

## Deliberately out of scope for Build 1

- The follow-up safety net (Build 2).
- The won/lost evidence & positioning study across Gmail/Docs/proposals (Build 3).
- Any change to the existing pipeline, formulas, or views.
- Automating the call, the pitch, or the relationship. That stays human.
