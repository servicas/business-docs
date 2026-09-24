# Servicas — Business Prototype

For investors, pilot partners, and advisors. What is built, how the business model is
wired into it, and what the next 90 days test.

Companion docs: [BUSINESS_OVERVIEW.md](./BUSINESS_OVERVIEW.md) (market, competition,
funding ask) · [INVESTOR_BRIEF.md](./INVESTOR_BRIEF.md) (one page). Technical
architecture is available on request.

> **Stage.** Built, deployed, pre-launch. No production customers, GMV, or revenue.
> Figures here are either **configuration that exists in the product** (marked *built*)
> or **model assumptions** (marked *illustrative*). Nothing is reported traction.

---

## 1. What Servicas is

An AI-augmented marketplace *and* operating system for home services — HVAC, plumbing,
electrical, cleaning, lawn, pool, childcare, emergency repair. Customers describe a
problem in text, voice, or a photo; AI matches verified local providers; booking, chat,
invoicing, payment, reviews, and disputes all stay on platform. Providers run their
whole job operation in the same app. Operators launch and govern new markets from an
admin console instead of an engineering ticket.

**The wedge:** incumbents (Angi, Thumbtack, TaskRabbit, Handy) sell *leads*. Providers
pay $30–$120 per lead at roughly a 10% close rate. Servicas charges on completed work
and gives the provider the operating system for free.

---

## 2. What is built

A deployed application, not a clickable mockup: one React codebase shipped to web,
iOS/Android, and desktop, against seven Spring Boot services on Google Cloud Run, each
with its own database. A feature ships once and appears on all three platforms — which
is why a small team covers a five-workspace product.

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
| Legal entity per market, insurance attach, background checks | Not started | Contracted at pilot launch |

The engineering repo keeps a running list of the sections that are still
dashboard-style rather than full workflows; it is available to anyone doing diligence.

---

## 3. Business model

| Block | Servicas |
|---|---|
| **Customer segments** | Homeowners 30–55 · bilingual households · property managers and short-let hosts · small businesses. Supply side: independent tradespeople (1–5 staff), immigrant-owned businesses, multi-truck shops. Operators: franchise/co-op and municipal programs (white-label). |
| **Value proposition** | *Customers:* verified provider, transparent price, one place for booking → payment → dispute. *Providers:* no pay-per-lead, a full job OS, native-language chat, fast payout. *Operators:* launch a market in days — catalog, tax, compliance, pricing, roles, payment rails are all configuration. |
| **Channels** | Paid social by ZIP · local and category SEO · door-knock supply recruiting · trade associations · provider referral · B2B referrers (property managers, hosts) |
| **Relationships** | Self-serve app · in-app chat with translation · AI assistant as first-line support · human desk for escalation · regional-manager franchise motion |
| **Revenue** | Take rate (primary) · subscription bundles *(built)* · pay-per-action *(built)* · featured placement · FX margin · insurance attach |
| **Key resources** | Seven-service platform · five role workspaces · multi-market geo and compliance engine · admin-tuned AI prompt layer · provider liquidity |
| **Key activities** | Provider recruiting and vetting · demand acquisition per metro · catalog and market configuration · trust, safety and disputes |
| **Key partners** | Payment providers · background-check and insurance vendors · trade associations · AI and geo providers · property-management software · regional managers |
| **Costs** | Provider and customer acquisition (dominant) · engineering · cloud and AI inference (low, elastic) · trust and safety · support desk (scales sublinearly thanks to AI summarization) |

---

## 4. How it makes money

Primary stream is a take rate on completed bookings, charged to the provider at
settlement. The customer-facing price stays clean.

| Stream | State | Detail |
|---|---|---|
| Take rate on completed bookings | Rails built; rate applied at launch | 10–15% of booking value, blended by category |
| Subscription bundles, customer + provider | **Built, admin-configurable** | Price, currency, interval, trial, and which sections a tier unlocks |
| Pay-per-action | **Built** | A non-subscriber accepts a per-search / per-contact fee instead of subscribing |
| Featured placement | Designed | Capped per category to protect trust; off during pilot |
| FX margin on cross-border settlement | Rate table built; margin not applied | 0.5–1.0% |
| Insurance / warranty attach | Designed | Vendor contracted at pilot launch |

**Why this is unusual at seed stage.** Pricing and packaging are stored as data, not
compiled into the app. An operator changes a tier's price, trial, or contents from the
admin console with no release — so a pilot can test three price points in a quarter
instead of three release cycles. Two willingness-to-pay curves run on one mechanism:
committed users subscribe, occasional users pay per action, so casual demand a
subscription-only model would lose is still monetized. Both sides of the market use the
identical machinery.

---

## 5. Unit economics (illustrative)

On a $180 average booking at a 12% take rate, contribution is **$14.20 per booking** —
66% of revenue.

| Line | Per booking |
|---|---|
| Average booking value | $180.00 |
| Gross revenue at 12% | $21.60 |
| Payment processing | −$5.40 |
| AI + notifications | −$0.20 |
| Support / dispute reserve (1% of GMV) | −$1.80 |
| **Contribution** | **$14.20** |

| Driver | Pilot assumption |
|---|---|
| Bookings per customer, year 1 | 2.4 (maintenance reminders, rebook, recurring services) |
| 24-month customer LTV, take rate only | ~$98 |
| Provider CAC | ~$80, falling as the referral loop kicks in |
| Customer CAC | $35–$60, falling as catalog SEO compounds |
| LTV : CAC | 1.2× early, target 3× at metro density |

Bundles change the shape, not the size: a $19/month customer bundle at 8% attach adds
~$1.80 per active customer per month at near-zero marginal cost. A provider Pro tier at
25% attach on 100 providers is ~$1.2k MRR — small in absolute terms, but it is the
direct evidence that providers value the operating system over lead flow.

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

**The one sensitivity that decides the model:** bookings per active provider per month.
At four it works; at two, the supply cost doubles. That ratio is what the pilot buys
information about, and it is the number to press us on.

---

## 7. The 90-day pilot

One Sun-Belt metro, 100 verified providers across four categories. Seven experiments,
each with one metric and a decision rule committed in advance.

| Hypothesis | Metric | Decision rule |
|---|---|---|
| Providers accept an outcome-based take rate over pay-per-lead | Share onboarded who take a job in 30 days | Scale ≥50%; rework the pitch <30% |
| AI matching produces a bookable first result | Booking rate, AI-matched vs. browse | Scale if AI converts ≥1.5× browse |
| The job stays on platform | Share of bookings invoiced + paid in app | Scale >70%; investigate leakage <50% |
| Customers repeat | 90-day repeat booking rate | Scale ≥25% |
| Willingness to pay exists beyond the take rate | Bundle attach %, per-action acceptance % | Keep whichever clears 5%; drop the other |
| Support scales sublinearly | Support minutes per booking, M1 vs M6 | Scale if it falls ≥30% |
| A market launches by configuration | Days from market chosen to first live booking | Target <14 days, no engineering ticket |

Sequence: weeks 1–2 market and entity · 3–6 supply (target 60 job-ready providers) ·
5–10 demand (CAC inside the $35–$60 band) · 7–12 pricing A/B · 9–13 trust vendors live
(dispute rate <3%, resolution <48h) · 12–13 readout and the call on metro #2.

Deliberately out of scope: a second metro, white-label, an open API, Europe. The failure
mode at this stage is breadth, not depth.

**The signal that matters most** is unmet demand by service × ZIP — simultaneously the
provider recruiting list and the input to market-readiness scoring. Waitlist joins are
captured today; capturing searches that returned no bookable provider is the first
instrumentation task at launch (a two-week build, not a research problem).

---

## 8. The demo (12 minutes)

One real booking followed across all five workspaces, in the order that tells the
business story rather than the feature list. Demo accounts are provided on request.

| Min | Workspace | What you see | The point |
|---|---|---|---|
| 0–2 | Customer | Describe a problem in plain language; AI ranks nearby verified providers | Demand capture without forms |
| 2–4 | Customer | Book a slot; job goes requested → scheduled | Nothing is sold until a job exists |
| 4–6 | Provider | Same job in the inbox: accept, quote, invoice | The economics inversion |
| 6–7.5 | Customer | Pay the invoice; receipt; review | Money stays on platform — the take rate lands here |
| 7.5–9 | Support | Dispute on that booking: evidence, refund decision | The trust layer |
| 9–11 | Admin | Market rules, catalog rollout, change a subscription price live | New market and new price are configuration |
| 11–12 | Regional | Readiness scoring for an unlaunched market | How metros 2–20 get chosen |

---

## 9. Risks

| Risk | Mitigation |
|---|---|
| Two-sided cold start | One metro; supply recruited before paid demand switches on |
| Trust or safety incident | Verification badges, document review, insurance attach, dispute + evidence workflow already built |
| Providers churn back to lead-gen | The job OS (invoices, payouts, chat, ratings, documents) is the switching cost — experiment #1 measures it |
| Payment provider concentration | Provider-agnostic adapters; volume moves between rails without a code change |
| AI cost or vendor risk | Prompts stored server-side and admin-tuned; models swappable without a release |
| Licensing and tax per market | Per-market compliance rules in the geo engine; legal review per state at launch |
| Key-person concentration | Docs, CI/CD and tests in place; first hires are senior backend + mobile |
| Pre-revenue | Acknowledged — the raise funds go-to-market for a product already built |

---

## 10. The ask

A seed round to take one metro to liquidity: provider recruiting, customer acquisition,
two senior engineering hires, trust-and-safety vendors — reported against the seven
experiments in §7. Breakdown:
[BUSINESS_OVERVIEW.md §15](./BUSINESS_OVERVIEW.md#15-use-of-funds-illustrative--2m-seed-ask).

Useful beyond capital: pilot partners with concentrated demand or supply in one metro
(property managers, short-let operators, trade associations), introductions to
background-check and insurance vendors, and a first metro-launcher hire.

**Most marketplaces raise to build the product. This one is built; the raise puts it
into a market.**

---

### Three questions we get asked

**Prototype or product?** A product, pre-launch. Five workspaces, seven services, three
platforms, CI-green, deployed. What is missing is customers, not code.

**Why will providers switch?** They stop paying for leads that do not convert and get a
free operating system for work they already do. Experiment #1 measures exactly that,
with a kill rule.

**Riskiest assumption?** Bookings per active provider per month (§6).

---

_Pilot version · last updated 2026-09-23._
