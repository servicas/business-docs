# Servicas — Business Overview

Market, competition, and the funding ask. Companion docs:
[BUSINESS_PROTOTYPE.md](./BUSINESS_PROTOTYPE.md) (what is built, the pilot, the demo) ·
[INVESTOR_BRIEF.md](./INVESTOR_BRIEF.md) (one page). Technical architecture is available
on request.

> **Stage.** Built, deployed, pre-launch. No production customers, GMV, or revenue.
> Market figures come from public industry reports. Everything about Servicas is either
> shipped product (*built*) or a model assumption (*illustrative*).

---

## 1. What Servicas is

Someone's air conditioning dies. They open Servicas and describe the problem — typed,
spoken, or photographed. AI ranks verified local providers who can actually come. They
book, chat, pay, and review without leaving the app. If the job goes wrong, the dispute
is settled there too.

The provider side is the real product. A tradesperson gets a job inbox, quotes, invoices,
payouts, ratings, documents, and customer chat that translates itself — free. It replaces
the spreadsheet, the camera roll, and the WhatsApp thread they run the business on today.

Servicas takes a share of completed work and charges nothing for leads.

---

## 2. Why that is a business

Home services is a ~$1.5T global category, ~$600B in the US by 2027, and still mostly
analog. Angi, Thumbtack, TaskRabbit, and Handy all sell the same thing: **leads, not
outcomes**.

**Providers** pay $30–$120 for a lead and win about one in ten. The money leaves whether
or not a job happens. Then they run the real work off-platform. And because these
platforms are English-only, they quietly exclude the immigrant-owned businesses that make
up much of this labor pool.

**Customers** can't tell who will actually show up. Quotes for one job spread 3–5×.
Refunds and no-shows get argued out in DMs.

**Operators** — anyone trying to open a new city — face a licensing, insurance, tax, and
catalog project with almost no tooling for it. Every new market becomes an engineering
cycle.

Charge on the outcome instead of the lead, and the provider's incentive flips: they want
every job to close, and so do we.

---

## 3. What is built

Five workspaces — customer, provider, admin, support, regional manager — on seven Spring
Boot services, from one React codebase that ships to web, iOS, Android, and desktop. A
feature ships once and lands everywhere, which is how a small team covers this much
product.

Four things here are unusual for a company at this stage. The whole journey is on
platform, from search to dispute, so the transaction never hands off. AI is in the spine,
not bolted on — matching, translation, photo triage, voice intake, ticket summaries.
Markets, tax, insurance rules, and pricing are configuration, so opening a city is setup
rather than a release. And the admin console competitors keep internal is a real product
surface, which is what makes white-label possible later.

| | Status |
|---|---|
| Product | 7 backends + 5 workspaces on Cloud Run (non-prod), CI green. Booking lifecycle, payments (sandbox), monetization, AI, and the admin console all built. |
| Mobile / desktop | Capacitor + Tauri builds working from the single codebase |
| **Customers, GMV, revenue** | **Pre-launch.** Nothing in production. |
| **Provider supply** | **Pre-launch.** Onboarding wizard ready; live recruiting is next. |
| Compliance | Document review built; legal entity per market not started |
| Team | Founder + technical contributors; first hires open |

Per-layer detail: [BUSINESS_PROTOTYPE.md §2](./BUSINESS_PROTOTYPE.md#2-what-is-built).
The engineering repo lists the sections that are still dashboard-style rather than full
workflows; it is available to anyone doing diligence.

---

## 4. How it makes money

A take rate on completed bookings, charged to the provider at settlement. The price the
customer sees stays clean.

| Stream | State | Detail |
|---|---|---|
| **Take rate** *(primary)* | Rails built; rate applied at launch | 10–15% of booking value. Higher on small repeat jobs like cleaning, lower on big HVAC installs to keep providers loyal. |
| **Subscription bundles** | **Built, admin-configurable** | Customer and provider tiers. Price, interval, trial, and what each tier unlocks are editable without a deploy. |
| **Pay-per-action** | **Built** | A non-subscriber pays per search or per contact instead of subscribing |
| Featured placement | Designed; off during pilot | Capped at 1 in 3 results to protect trust |
| FX margin | Rate table built; not applied | 0.5–1.0% on cross-border settlement. No markup on domestic cards. |
| Insurance / warranty | Designed | ~5–10% of booking at ~20% margin; vendor contracted at launch |

Intended pilot packaging on the provider side — data in the bundle engine, not hard-coded,
so a quarter can test three price points instead of shipping three releases: **Free** ($0,
job inbox and the full job OS), **Pro** ($49, verified badge, gallery, scheduling),
**Business** ($149, multi-staff, payroll exports, branded invoices), **Fleet** (custom,
API and dispatch). Two willingness-to-pay curves run on one mechanism: committed users
subscribe, casual users pay per action.

**Per booking**, on a $180 average at a 12% take:

| Line | |
|---|---|
| Gross revenue | $21.60 |
| Payment processing | −$5.40 |
| AI + notifications | −$0.20 |
| Support / dispute reserve | −$1.80 |
| **Contribution** | **$14.20** (66%) |

A customer is worth ~$98 over 24 months on take rate alone, at a 35% first-year repeat
rate. Provider CAC runs ~$80 and customer CAC $35–$60, so LTV:CAC starts near 1.2× and
needs metro density to reach 3×. The number that decides the whole model is bookings per
active provider per month: four works, two doubles the cost of supply.

---

## 5. The market

| Layer | What it counts | Scale |
|---|---|---|
| **TAM** | Global home / local services GMV | ~$1.5T |
| **SAM** | English + Spanish North America | ~$200B |
| **SOM** | 5 metros, 6 categories, ~5% local share, years 1–3 | ~$300M GMV |

At a 12% take that SOM is a ~$36M annual revenue ceiling — the size of the opening, not a
plan. The 24-month model reaches about 13% of it
([BUSINESS_PROTOTYPE.md §6](./BUSINESS_PROTOTYPE.md#6-illustrative-24-month-trajectory)).
The buyers are homeowners 30–55, bilingual households, property managers and short-let
hosts, and small businesses. The sellers are independent tradespeople, immigrant-owned
businesses, and multi-truck shops. In this category the constraint is always supply, not
demand, which is why the pilot spends most of its effort recruiting providers.

---

## 6. Why now

Multimodal AI only recently got cheap enough that translating every message and reading
every photo survives marketplace economics. Managed cloud did the same for infrastructure:
seven services run for low-three-digit dollars a month at pilot scale. Meanwhile trust in
lead-gen platforms is eroding from both sides, and the bilingual, mobile-first half of
this workforce is still being served by English-only products. The opening is real but it
is not permanent.

---

## 7. Competition

| Competitor | Model | Their strength | Why Servicas wins |
|---|---|---|---|
| Thumbtack | Pay-per-quote | Brand, SEO | Provider economics break at a sub-10% close rate; we charge on the outcome |
| Angi / HomeAdvisor | Lead-gen + subscription | Massive ad spend | Weak customer sentiment; AI matching makes a better first impression |
| TaskRabbit | Hourly gig labor | Brand, IKEA partnership | Verified provider *businesses*, for trades that need licensing |
| Handy (ANGI) | Hourly cleaning | Bundled with Angi | Multi-category from day one, not boxed into cleaning |
| Booksy | Beauty / personal | Strong vertical playbook | Different vertical, ~4× the TAM |
| Facebook, WhatsApp groups | Free and informal | Real trust | We ship the trust layer — verification, on-platform payment, disputes — on top |

---

## 8. What is hard to copy

The geo and compliance engine is slow to model correctly and unglamorous to build, and it
is the reason a market launch is days of setup. The job OS is the switching cost: once
invoices, photos, payouts, and ratings live here, leaving is expensive, where lead-gen has
no switching cost at all. Prompts live in the database and are admin-tuned, so models swap
without a deploy. One codebase across three platforms means a structurally smaller
engineering org than competitors running parallel native teams. And bilingual liquidity
needs localized product and recruiting, not a translate button — which is why English-only
incumbents have not taken it.

---

## 9. The plan

**Months 0–6.** One Sun-Belt metro — Atlanta or Austin, both already seeded. 100 verified
providers across four categories, then the first 1,000 paying customers. Seven experiments
run with decision rules committed in advance
([BUSINESS_PROTOTYPE.md §7](./BUSINESS_PROTOTYPE.md#7-the-90-day-pilot)). Providers come
from door-knocking, which converts best at this stage, plus trade associations, direct
recruiting off competitor listings, and a $50 bounty per provider who finishes a first
paid job. Customers come from paid social by ZIP, auto-generated SEO pages per service and
region, Spanish-language radio and community partners, and referrals that credit both
sides.

**Months 6–18.** Two more metros in the same state, riding identical tax and compliance.
Paid tiers layer on top of free. The regional-manager program opens so markets can launch
without us running them.

**Months 18–36.** Texas-wide, then Florida and California. One white-label pilot with a
co-op or municipal program. An open API for property-management software.

---

## 10. Risks

| Risk | Mitigation |
|---|---|
| Two-sided cold start | One metro. Supply recruited before paid demand switches on. |
| Providers churn back to lead-gen | The job OS is the switching cost — pilot experiment #1 measures it, with a kill rule |
| Trust or safety incident | Verification, document review, background-check partner, insurance attach, and the dispute workflow are built |
| Licensing and tax per market | Per-market rules in the geo engine; legal review per state at launch |
| Key-person concentration | Docs, CI/CD, and tests in place; first hires are senior backend + mobile |
| Pre-revenue | Acknowledged. The raise funds go-to-market for a product that already exists. |

Payment-rail, AI-cost, and remaining risks with their decision rules:
[BUSINESS_PROTOTYPE.md §9](./BUSINESS_PROTOTYPE.md#9-risks).

---

## 11. The ask (illustrative — $2M seed)

| Bucket | % | Notes |
|---|---|---|
| Provider acquisition, metro 1 | 25% | Door-knock, bounty, onboarding ops |
| Customer acquisition, metro 1 | 25% | Paid social, Spanish-language community, local SEO |
| Engineering, 2 hires | 25% | Senior backend + mobile lead |
| Trust & safety, compliance | 10% | Background-check vendor, insurance attach pilot |
| Infra + AI runway | 5% | 12-month buffer at projected scale |
| Working capital, G&A | 10% | Legal, accounting, per-market entity setup |

Burn target is ~$110k/month at month 6 and ~$160k/month at month 12, reported against the
seven pilot experiments rather than a feature roadmap.

Useful beyond money: pilot partners with concentrated demand or supply in one metro,
introductions to background-check and insurance vendors, and a first metro-launcher hire.

---

## 12. Closing

The platform is built — seven services, five workspaces, the AI layer, the payment
abstraction, the multi-market admin, shipped and CI-green. What is left is go-to-market:
pick a metro, recruit 100 providers, win the first 1,000 customers, and let the switching
cost compound.

**Most marketplaces raise to build the product. This one is built; the raise puts it into
a market.**

_Live demo on request: one booking followed across all five workspaces, from AI match to
payment to dispute — [BUSINESS_PROTOTYPE.md §8](./BUSINESS_PROTOTYPE.md#8-the-demo-12-minutes)._

Founder: Olivier Santos · repo access for investors on request.

_Pilot version · last updated 2026-09-26._
