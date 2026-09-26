# Servicas — Business Prototype

For investors, pilot partners, and advisors. What is built, how the business model is
wired into it, and what the next 90 days test.

Companion docs: [BUSINESS_OVERVIEW.md](./BUSINESS_OVERVIEW.md) (market, competition, the
ask) · [INVESTOR_BRIEF.md](./INVESTOR_BRIEF.md) (one page). Technical architecture is
available on request.

> **Stage.** Built, deployed, pre-launch. No production customers, GMV, or revenue.
> Figures here are either **configuration that exists in the product** (*built*) or
> **model assumptions** (*illustrative*). Nothing here is reported traction.

---

## 1. What Servicas is

A customer describes a problem in text, voice, or a photo. AI ranks verified local
providers. Booking, chat, invoicing, payment, reviews, and disputes all stay on platform.
Providers run their whole job operation in the same app. Operators open and govern a
market from an admin console instead of an engineering ticket.

Angi, Thumbtack, TaskRabbit, and Handy sell leads: $30–$120 each, closing about one in
ten, paid whether or not a job happens. Servicas charges on completed work and gives the
provider the operating system for free.

---

## 2. What is built

A deployed application, not a clickable mockup. One React codebase reaches web, iOS,
Android, and desktop, against seven Spring Boot services on Google Cloud Run, each with
its own database. A feature ships once and lands everywhere — which is how a small team
covers a five-workspace product.

| Layer | Status | Notes |
|---|---|---|
| Customer journey — search → AI match → book → chat → pay → review → dispute | **Built, end to end** | Runs against live services, not browser mocks |
| Provider journey — inbox → accept/quote → schedule → invoice → payouts → ratings | **Built** | Verified providers self-serve; external providers driven by staff |
| Admin console — bookings, customers, providers, catalog, markets, finance, roles, payment rails, pricing | **Built** | The operator surface competitors keep internal-only |
| Support desk — queue, SLA, disputes, refunds, evidence, escalation | **Built** | Includes AI case summaries and suggested replies |
| Regional workspace — demand, supply, readiness, launch planning | **Built, partly indicative** | Launch controls persist; some cards await production telemetry |
| Monetization — bundles, pay-per-action, section gating | **Built** | Admin-editable, no code release (§4) |
| Payments — Stripe, Square, PayPal, Apple Pay | **Built, sandbox** | Provider-agnostic adapters |
| Production traffic, GMV, revenue | Not started | Pre-launch by design |
| Legal entity per market, insurance, background checks | Not started | Contracted at pilot launch |

The engineering repo keeps a running list of the sections that are still dashboard-style
rather than full workflows; it is available to anyone doing diligence.

---

## 3. Business model

Three groups pay attention to Servicas for different reasons. **Customers** want a
verified provider at a transparent price and one place to book, pay, and complain.
**Providers** want to stop paying for leads that go nowhere, and they get a job OS,
native-language chat, and fast payout in exchange for a share of work that actually
completes. **Operators** — regional managers now, franchises and municipal programs
later — want to open a market in days, which is possible because catalog, tax,
compliance, pricing, roles, and payment rails are all configuration.

What it takes to run, beyond the platform itself:

| | |
|---|---|
| **Key activities** | Recruiting and vetting providers · buying demand per metro · configuring catalogs and markets · trust, safety, and disputes |
| **Key partners** | Payment providers · background-check and insurance vendors · trade associations · AI and geo providers · property-management software · regional managers |
| **Cost structure** | Provider and customer acquisition dominate. Engineering next. Cloud and AI inference are small and elastic. The support desk grows slower than bookings because AI drafts the summaries and replies. |

---

## 4. How it makes money

A take rate on completed bookings, charged to the provider at settlement. The price the
customer sees stays clean.

| Stream | State | Detail |
|---|---|---|
| Take rate on completed bookings | Rails built; rate applied at launch | 10–15% of booking value, blended by category |
| Subscription bundles, customer + provider | **Built, admin-configurable** | Price, currency, interval, trial, and which sections a tier unlocks |
| Pay-per-action | **Built** | A non-subscriber pays per search or per contact instead of subscribing |
| Featured placement | Designed | Capped per category to protect trust; off during pilot |
| FX margin on cross-border settlement | Rate table built; not applied | 0.5–1.0% |
| Insurance / warranty attach | Designed | Vendor contracted at pilot launch |

**Why this is unusual at seed stage.** Pricing is data, not code. An operator changes a
tier's price, trial, or contents from the admin console with no release, so the pilot
tests three price points in a quarter instead of three release cycles. And two
willingness-to-pay curves run on one mechanism: committed users subscribe, occasional
users pay per action, so casual demand a subscription-only model would lose still pays.

---

## 5. Unit economics (illustrative)

On a $180 average booking at a 12% take rate, contribution is **$14.20** — 66% of revenue.

| Line | Per booking |
|---|---|
| Average booking value | $180.00 |
| Gross revenue at 12% | $21.60 |
| Payment processing | −$5.40 |
| AI + notifications | −$0.20 |
| Support / dispute reserve (1% of GMV) | −$1.80 |
| **Contribution** | **$14.20** |

A customer books 2.4 times in year one — reminders, rebooks, recurring work — worth ~$98
of take-rate LTV over 24 months. Provider CAC starts near $80 and falls as referrals kick
in; customer CAC runs $35–$60 and falls as catalog SEO compounds. LTV:CAC is about 1.2×
early, with 3× the target once a metro is dense.

Bundles change the shape, not the size. A $19/month customer bundle at 8% attach adds
~$1.80 per active customer per month at almost no marginal cost. A provider Pro tier at
25% attach across 100 providers is ~$1.2k MRR — small money, but it is direct evidence
that providers value the operating system over lead flow.

---

## 6. Illustrative 24-month trajectory

Model output, not a forecast.

| | M3 | M6 | M12 | M18 | M24 |
|---|---|---|---|---|---|
| Metros live | 1 | 1 | 2 | 3 | 5 |
| Active providers | 60 | 150 | 420 | 900 | 1,800 |
| Monthly bookings | 120 | 700 | 3,200 | 8,500 | 18,000 |
| Monthly GMV | $22k | $126k | $576k | $1.53M | $3.24M |
| Take-rate revenue | $2.6k | $15k | $69k | $184k | $389k |
| Bundle + per-action | — | $2k | $12k | $38k | $92k |
| Monthly burn | $85k | $110k | $160k | $220k | $300k |

**One number decides whether this holds:** bookings per active provider per month. At
four it works. At two, the cost of supply doubles and the model breaks. That ratio is
what the pilot buys information about, and it is the number to press us on.

---

## 7. The 90-day pilot

One Sun-Belt metro, 100 verified providers across four categories. Seven experiments,
each with one metric and a decision rule committed before it starts.

| Hypothesis | Metric | Decision rule |
|---|---|---|
| Providers accept an outcome-based take rate over pay-per-lead | Share onboarded who take a job in 30 days | Scale ≥50%; rework the pitch <30% |
| AI matching produces a bookable first result | Booking rate, AI-matched vs. browse | Scale if AI converts ≥1.5× browse |
| The job stays on platform | Share of bookings invoiced + paid in app | Scale >70%; investigate leakage <50% |
| Customers repeat | 90-day repeat booking rate | Scale ≥25% |
| Willingness to pay exists beyond the take rate | Bundle attach %, per-action acceptance % | Keep whichever clears 5%; drop the other |
| Support cost per booking falls as volume grows | Support minutes per booking, M1 vs M6 | Scale if it falls ≥30% |
| A market launches by configuration | Days from market chosen to first live booking | Target <14 days, no engineering ticket |

Weeks 1–2 market and entity · 3–6 supply, targeting 60 job-ready providers · 5–10 demand,
holding CAC inside the $35–$60 band · 7–12 the pricing A/B · 9–13 trust vendors live, with
disputes under 3% and resolution under 48h · 12–13 readout and the call on metro #2.

Deliberately out of scope: a second metro, white-label, an open API, Europe. The failure
mode at this stage is breadth, not depth.

**The signal worth the most** is unmet demand by service × ZIP — the provider recruiting
list and the market-readiness input in one. Waitlist joins are captured today; logging
searches that returned no bookable provider is the first instrumentation task at launch,
a two-week build.

---

## 8. The demo (12 minutes)

One real booking followed across all five workspaces, in the order that tells the business
story rather than the feature list. Demo accounts are provided on request.

| Min | Workspace | What you see | The point |
|---|---|---|---|
| 0–2 | Customer | Describe a problem in plain language; AI ranks nearby verified providers | Demand capture without forms |
| 2–4 | Customer | Book a slot; job goes requested → scheduled | Nothing is sold until a job exists |
| 4–6 | Provider | The same job in the inbox: accept, quote, invoice | The economics inversion |
| 6–7.5 | Customer | Pay the invoice; receipt; review | Money stays on platform — the take rate lands here |
| 7.5–9 | Support | A dispute on that booking: evidence, refund decision | The trust layer |
| 9–11 | Admin | Market rules, catalog rollout, a subscription price changed live | A new market and a new price are configuration |
| 11–12 | Regional | Readiness scoring for an unlaunched market | How metros 2–20 get chosen |

---

## 9. Risks

| Risk | Mitigation |
|---|---|
| Two-sided cold start | One metro; supply recruited before paid demand switches on |
| Providers churn back to lead-gen | The job OS — invoices, payouts, chat, ratings, documents — is the switching cost. Experiment #1 measures it. |
| Trust or safety incident | Verification badges, document review, insurance attach, and the dispute + evidence workflow are built |
| Payment provider concentration | Provider-agnostic adapters; volume moves between rails without a code change |
| AI cost or vendor risk | Prompts stored server-side and admin-tuned; models swap without a release |
| Licensing and tax per market | Per-market compliance rules in the geo engine; legal review per state at launch |
| Key-person concentration | Docs, CI/CD, and tests in place; first hires are senior backend + mobile |
| Pre-revenue | Acknowledged — the raise funds go-to-market for a product already built |

---

## 10. The ask

A seed round to take one metro to real transaction volume: provider recruiting, customer
acquisition, two senior engineering hires, trust-and-safety vendors — reported against the
seven experiments in §7. Breakdown:
[BUSINESS_OVERVIEW.md §11](./BUSINESS_OVERVIEW.md#11-the-ask-illustrative--2m-seed).

Useful beyond capital: pilot partners with concentrated demand or supply in one metro
(property managers, short-let operators, trade associations), introductions to
background-check and insurance vendors, and a first metro-launcher hire.

**Most marketplaces raise to build the product. This one is built; the raise puts it into
a market.**

---

### Three questions we get asked

**Prototype or product?** A product, pre-launch. Five workspaces, seven services, three
platforms, CI-green, deployed. What is missing is customers, not code.

**Why will providers switch?** They stop paying for leads that do not convert, and they
get a free operating system for work they already do. Experiment #1 measures exactly that,
with a kill rule.

**Riskiest assumption?** Bookings per active provider per month (§6).

---

_Pilot version · last updated 2026-09-26._
