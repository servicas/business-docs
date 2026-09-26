# Servicas — Business Overview

Market, competition, and the funding ask. Companion docs:
[BUSINESS_PROTOTYPE.md](./BUSINESS_PROTOTYPE.md) (what is built, business model canvas,
pilot experiments, demo script) · [INVESTOR_BRIEF.md](./INVESTOR_BRIEF.md) (one page).
Technical architecture is available on request.

> **Stage.** Built, deployed, pre-launch. No production customers, GMV, or revenue.
> Market figures come from public industry reports; everything about Servicas itself is
> either shipped product (marked *built*) or a model assumption (marked *illustrative*).

---

## 1. In one page

Servicas is an AI-augmented marketplace **and** operating system for home services —
HVAC, plumbing, electrical, cleaning, lawn, pool, childcare, emergency repair.

A customer describes a problem in text, voice, or a photo. AI ranks verified local
providers. Booking, chat, invoicing, payment, reviews, and disputes all stay on the
platform. Providers run their whole job operation in the same app, free. Operators launch
and govern a new market from an admin console instead of an engineering ticket.

**The model:** a take rate on completed work, plus subscription bundles and pay-per-action
billing that are already built and admin-editable.

---

## 2. The problem

Home services is a ~$1.5T global category (~$600B US by 2027) that is still mostly analog.
The incumbents — Angi, Thumbtack, TaskRabbit, Handy — sell **leads, not outcomes**.

| Side | What hurts |
|---|---|
| **Customers** | Verification is opaque: you cannot tell who will actually show up. Quotes for the same job spread 3–5×. Refunds and no-shows get settled in DMs. Non-English speakers fall back to WhatsApp groups. |
| **Providers** | They pay $30–$120 per lead at roughly a 10% close rate — cash out the door whether or not a job happens. Then they run the real business in spreadsheets, Zelle, and a camera roll. Single-language platforms exclude the immigrant-owned businesses that make up much of this labor pool. |
| **Operators** | Launching a market is a compliance and content project: licensing, insurance, holidays, tax, catalog. Existing platforms expose almost no tooling for it, so every new market is an engineering cycle. |

---

## 3. The solution

Five workspaces — Customer, Provider, Admin, Support, Regional manager — on seven
Spring Boot services, from one React codebase shipped to web, iOS/Android, and desktop.

| What sets it apart | Why it matters commercially |
|---|---|
| **End to end on platform** | Discovery → booking → chat → payment → review → dispute. Nothing hands off, so the transaction — and the take rate — lands here. |
| **AI-native, not bolted on** | Matching, translation, photo triage, voice intake, ticket summaries. Lowers intake friction and support cost per booking. |
| **Multi-market from day one** | Markets, holidays, pricing, tax, insurance rules, SLAs are configuration. A new market is days, not a release. |
| **Operator-grade admin** | The back office competitors keep internal-only is a product surface here — which is what makes white-label possible later. |
| **One codebase, three platforms** | Capacitor for mobile, Tauri for desktop. A small team covers a five-workspace product. |

Detail: [BUSINESS_PROTOTYPE.md §2](./BUSINESS_PROTOTYPE.md#2-what-is-built). Per-service
and per-workspace reference is available on request.

---

## 4. Why now

| Tailwind | Why it matters here |
|---|---|
| Multimodal AI got cheap | Translation, photo triage, and voice intake are finally viable at marketplace unit economics |
| A bilingual, mobile-first workforce is underserved | English-only platforms leave supply on the table in TX, FL, CA, NY, AZ, GA |
| Trust in lead-gen is eroding on both sides | Weak customer sentiment and rising provider churn make a switch pitchable |
| Home-services spend stayed sticky post-COVID | ~$430B US (2020) → $600B+ projected (2027) |
| Managed cloud collapsed infra cost | A seven-service stack runs at low-three-digit USD/month at pilot scale |

---

## 5. Market

| Layer | What it counts | Scale |
|---|---|---|
| **TAM** | Global home / local services GMV | ~$1.5T |
| **SAM** | English + Spanish North America home services GMV | ~$200B |
| **SOM** | Reachable in years 1–3 — 5 metros, 6 categories, ~5% local share | ~$300M GMV |

At a 12% blended take rate the SOM implies a ~$36M annual revenue **ceiling** for the
first three years. That is the size of the opening, not a plan: the 24-month model in
[BUSINESS_PROTOTYPE.md §6](./BUSINESS_PROTOTYPE.md#6-illustrative-24-month-trajectory)
reaches ~$39M annualized GMV by month 24, about 13% of that ceiling. In this category the
binding constraint is provider supply, not customer demand — which is why the pilot spends
most of its effort on recruiting.

---

## 6. Who it is for

| Side | Who | Why they pick Servicas |
|---|---|---|
| **Demand** | Homeowners 30–55 · bilingual households · property managers and short-let hosts · small businesses | A verified provider at a transparent price, chat in their own language, and one place for booking, payment, and recourse. For multi-property owners: recurring scheduling and one invoice across units. |
| **Supply** | Independent tradespeople (1–5 staff) · immigrant-owned businesses · multi-truck shops | No pay-per-lead, a free job inbox, fast payout, native-language customer chat, and document and insurance management. |
| **Operator** | Regional managers today · co-ops, franchisors, municipal aid programs later | Readiness scoring and recruiting signals to launch markets we don't run directly — and, eventually, a white-label of the admin stack. |

---

## 7. How it makes money

The primary stream is a take rate on completed bookings, charged to the provider at
settlement. The customer-facing price stays clean.

| Stream | State | Detail |
|---|---|---|
| **Take rate** *(primary)* | Charging rails built; rate applied at pilot launch | 10–15% of booking value. Higher on low-ticket repeat work like cleaning, lower on big-ticket HVAC installs to keep providers loyal. |
| **Subscription bundles**, customer + provider | **Built, admin-configurable** | Price, currency, interval, trial, and which portal sections a tier unlocks — all editable without a deploy |
| **Pay-per-action** | **Built** | A non-subscriber accepts a per-search or per-contact fee instead of subscribing |
| Featured placement | Designed; off during pilot | Sponsored slot per category × region, capped at 1 in 3 results to protect trust |
| FX margin | Rate table built; margin not applied | 0.5–1.0% on cross-border settlement. No markup on domestic card processing. |
| Insurance / warranty attach | Designed | ~5–10% of booking at ~20% margin; vendor contracted at pilot launch |
| Tips | Built | 100% to the provider. Retention, not revenue. |

**Intended pilot packaging** for the provider side — data in the bundle engine, not
hard-coded, so three price points can be tested in a quarter:

| Tier | Monthly | Includes |
|---|---|---|
| Free | $0 | Job inbox, basic profile, full job OS |
| Pro | $49 | Verified badge surface, photo gallery, scheduling automation |
| Business | $149 | Multi-staff, payroll exports, branded invoices, priority support |
| Fleet | Custom | API access, regional dispatch, route optimization |

Why that matters pre-revenue: packaging is data, so a pilot tests price points instead of
shipping releases, and two willingness-to-pay curves run on one mechanism — committed
users subscribe, casual users pay per action. Detail: [BUSINESS_PROTOTYPE.md §4](./BUSINESS_PROTOTYPE.md#4-how-it-makes-money).

### Unit economics (illustrative)

| Line | Per booking |
|---|---|
| Average booking value | $180.00 |
| Gross revenue at 12% take | $21.60 |
| Payment processing | −$5.40 |
| AI + notifications | −$0.20 |
| Support / dispute reserve (1% of GMV) | −$1.80 |
| **Contribution** | **$14.20** (66%) |

24-month LTV on take rate alone is ~$98 per customer at a 35% year-one repeat rate,
against ~$80 provider CAC and $35–$60 customer CAC: **1.2× LTV:CAC early, 3× the target
at metro density.** The one number that decides the model is bookings per active provider
per month — four works, two doubles the cost of supply.

---

## 8. Go-to-market

| Phase | Window | What happens |
|---|---|---|
| **1 — One metro** | Months 0–6 | One US Sun-Belt metro (Atlanta or Austin, both already seeded). 100 verified providers across 4 categories. First 1,000 paying customers. Seven experiments with pre-committed decision rules — [BUSINESS_PROTOTYPE.md §7](./BUSINESS_PROTOTYPE.md#7-the-90-day-pilot). |
| **2 — Adjacent** | Months 6–18 | Two more metros in the same state, riding identical tax and compliance. Paid tiers layered on the free tier. Regional-manager program opens. |
| **3 — Multi-state** | Months 18–36 | Texas-wide → Florida → California. One white-label pilot with a co-op or municipal program. Open API for property-management software. |

| Acquiring customers | Acquiring providers |
|---|---|
| Paid social by ZIP + homeowner intent | In-person door-knock — highest pilot conversion |
| Auto-generated SEO pages per service × region | Trade associations (NACE, PHCC, NARI), Pro-tier discount year one |
| Spanish-language radio and community partners | Direct recruiting of top-rated profiles on competitors |
| Provider referral — both sides get booking credit | $50 bounty per provider who completes a first paid job |
| Property manager and host integrations as B2B referrers | |

---

## 9. Competition

Two axes matter: **charging on outcomes instead of leads**, and **operator depth** — the
multi-market, multi-language admin layer. Every incumbent sits on the lead-gen,
English-only, thin-admin corner of that map.

| Competitor | Model | Their strength | Why Servicas wins |
|---|---|---|---|
| Thumbtack | Pay-per-quote | Brand, SEO | Provider economics are broken at a sub-10% close rate; we charge on the outcome |
| Angi / HomeAdvisor | Lead-gen + subscription | Massive ad spend | Weak customer sentiment; AI matching makes a better first impression |
| TaskRabbit | Hourly gig labor | Brand, IKEA partnership | Verified provider *businesses*, for trades that need licensing |
| Handy (ANGI) | Hourly cleaning | Bundled with Angi | Multi-category from day one, not boxed into cleaning |
| Booksy | Beauty / personal services | Strong vertical playbook | Different vertical, ~4× the TAM |
| Facebook groups, WhatsApp | Free and informal | Real trust relationships | We ship the trust layer — verification, on-platform payment, disputes — on top |

---

## 10. Moat

1. **Geo and compliance engine.** Market, tax, insurance, holiday, and SLA rules as
   configuration. Slow to model correctly, unglamorous to copy, and it is what makes a
   market launch in days.
2. **Provider-side operating system.** Once invoices, photos, payouts, and ratings live in
   Servicas, leaving is expensive. Lead-gen has no switching cost at all.
3. **Prompt and model abstraction.** Prompts live in the database, admin-tuned. Models swap
   without a deploy.
4. **One codebase across three platforms.** A structurally smaller engineering org than
   competitors running parallel native teams.
5. **Liquidity in bilingual markets.** Needs localized GTM and product, not a translate
   button — which is why English-only incumbents have not taken it.

---

## 11. Where the product actually stands

| Pillar | Status |
|---|---|
| Product | 7 backends + 5 workspaces on Cloud Run (non-prod), CI green. Booking lifecycle, payments (sandbox), monetization, AI, and the admin console all built. |
| Mobile / desktop | Capacitor + Tauri builds working from the single codebase |
| **Customers, GMV, revenue** | **Pre-launch.** Nothing in production. |
| **Provider supply** | **Pre-launch.** Onboarding wizard ready; live recruiting is next. |
| Compliance | Document review flow built; legal entity per market not started |
| Team | Founder + technical contributors; first hires open |

Per-layer breakdown: [BUSINESS_PROTOTYPE.md §2](./BUSINESS_PROTOTYPE.md#2-what-is-built).

The engineering repo keeps a running list of the sections that are still dashboard-style
rather than full workflows; it is available to anyone doing diligence.

---

## 12. Roadmap

Quarters are relative to the pilot start, not calendar commitments.

| Pilot Q1 | Q2 | Q3 | Q4 | Year 2+ |
|---|---|---|---|---|
| First metro live | Pro tier launch | Metros 2 and 3 | White-label pilot | Multi-state |
| 100 providers | Subscription revenue | Texas-wide | Property-management API | EU pilot |
| 1,000 customers | Featured slots | RM program | Insurance attach | Public catalog SEO |
| Insurance attach pilot | Provider referral loop | Voice-first intake | Payout v2 | Series A |

---

## 13. Risks

| Risk | Mitigation |
|---|---|
| Two-sided cold start | One metro. Supply recruited before paid demand switches on. |
| Providers churn back to lead-gen | The job OS is the switching cost — pilot experiment #1 measures it, with a kill rule |
| Trust or safety incident | Verification, document review, background-check partner, insurance attach, and the dispute workflow are built |
| Licensing and tax per market | Per-market compliance rules in the geo engine; legal review per state at launch |
| Key-person concentration | Docs, CI/CD, and tests in place; first hires are senior backend + mobile |
| Pre-revenue | Acknowledged. The raise funds go-to-market for a product that already exists. |

Payment-rail, AI-cost, and remaining risks, with pilot decision rules:
[BUSINESS_PROTOTYPE.md §9](./BUSINESS_PROTOTYPE.md#9-risks).

---

## 14. Use of funds (illustrative — $2M seed ask)

| Bucket | % | Notes |
|---|---|---|
| Provider acquisition, metro 1 | 25% | Door-knock, bounty, onboarding ops |
| Customer acquisition, metro 1 | 25% | Paid social, Spanish-language community, local SEO |
| Engineering, 2 hires | 25% | Senior backend + mobile lead |
| Trust & safety, compliance | 10% | Background-check vendor, insurance attach pilot |
| Infra + AI runway | 5% | 12-month buffer at projected scale |
| Working capital, G&A | 10% | Legal, accounting, per-market entity setup |

Burn target: ~$110k/month at month 6, ~$160k/month at month 12. Spend is reported against
the seven pilot experiments, not against a feature roadmap.

Useful beyond capital: pilot partners with concentrated demand or supply in one metro,
introductions to background-check and insurance vendors, and a first metro-launcher hire.

---

## 15. Closing

The platform is built — seven services, five workspaces, the AI layer, the payment
abstraction, the multi-market admin, all shipped and CI-green. What remains is go-to-market:
pick a metro, recruit 100 providers, win the first 1,000 customers, and let the
switching cost compound.

**Most marketplaces raise to build the product. This one is built; the raise puts it into
a market.**

_Live demo on request: one booking followed across all five workspaces, from AI match to
payment to dispute — [BUSINESS_PROTOTYPE.md §8](./BUSINESS_PROTOTYPE.md#8-the-demo-12-minutes)._

Founder: Olivier Santos · repo access for investors on request.

_Pilot version · last updated 2026-09-26._
