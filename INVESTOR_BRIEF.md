# Servicas — Investor Brief

One page. Deeper: [BUSINESS_PROTOTYPE.md](./BUSINESS_PROTOTYPE.md) (model, pilot plan,
demo) · [BUSINESS_OVERVIEW.md](./BUSINESS_OVERVIEW.md) (market, competition, ask).

> **Stage:** built, deployed, pre-launch. No production customers, GMV, or revenue.
> Figures are model assumptions unless marked *built*.

**What it is.** An AI-augmented marketplace *and* operating system for home services —
HVAC, plumbing, electrical, cleaning, lawn, pool, childcare, emergency repair. Customers
describe a problem in text, voice, or a photo; AI matches verified local providers;
booking, chat, invoicing, payment, reviews, and disputes all stay on platform.

**The problem.** Incumbents (Angi, Thumbtack, TaskRabbit, Handy) sell *leads, not
outcomes*: providers pay $30–$120 per lead at roughly a 10% close rate, then run the
actual business in spreadsheets and camera rolls. Customers face 3–5× price spreads,
opaque verification, and disputes settled in DMs. Non-English-speaking providers — a
large share of the labor pool — are barely served.

**The wedge.** Charge on completed work, not on leads. Give the provider the operating
system for free and take a share of the transaction it produces.

### Built today

| | |
|---|---|
| Five workspaces | Customer · Provider · Admin · Support · Regional manager |
| Seven services | identity · customer · marketplace · payment · notification · support · ai-assistant (Spring Boot on Cloud Run, Postgres each) |
| Three platforms, one codebase | Web, iOS/Android, desktop |
| AI, native | Matching, translation, photo/video triage, voice intake, ticket summaries |
| Operator console | Markets, tax, compliance, catalog rollout, roles, payment rails, AI prompts — configuration, not code |
| Monetization engine | Subscription bundles **and** pay-per-action billing, section-level entitlements, editable without a deploy |
| Payments | Stripe · Square · PayPal · Apple Pay, provider-agnostic (sandbox) |

### Revenue model

1. **Take rate** — 10–15% of booking value, charged to the provider at settlement *(primary)*
2. **Subscription bundles** — customer and provider tiers *(built, configurable)*
3. **Pay-per-action** — per-search / per-contact fee for non-subscribers *(built)*
4. Featured placement · FX margin · insurance attach *(designed)*

### Economics and market

$180 average booking × 12% take = $21.60 revenue; less processing, AI, and a support
reserve = **$14.20 contribution per booking** (66%). TAM ~$1.5T global local services
GMV · SAM ~$200B English + Spanish North America · SOM ~$300M GMV in years 1–3
(5 metros, 6 categories).

### Why now

Multimodal AI is finally cheap enough for per-message translation and photo triage · a
mobile-first bilingual workforce is underserved by English-only platforms · trust in
lead-gen marketplaces is eroding on both sides · managed cloud collapsed the cost of
running a seven-service stack at pilot scale.

### Next 90 days

One Sun-Belt metro. 100 verified providers across four categories. Paid social by ZIP
plus local SEO and community channels. Three price points tested on the bundle engine.
Seven experiments with pre-committed decision rules: provider acceptance of the take
rate, AI-match conversion, on-platform payment completion, repeat rate, willingness to
pay, support cost per booking, days-to-launch a market.

### The ask

A seed round to take one metro to liquidity: provider recruiting, customer acquisition,
two senior engineering hires, trust-and-safety vendors. Breakdown in
[BUSINESS_OVERVIEW.md §15](./BUSINESS_OVERVIEW.md#15-use-of-funds-illustrative--2m-seed-ask).
Also valuable: pilot partners with concentrated demand or supply in one metro,
introductions to background-check and insurance vendors, a first metro-launcher hire.

**Most marketplaces raise to build the product. This one is built — the raise puts it
into a market.**

_Live demo on request: one booking followed across all five workspaces, from AI match to
payment to dispute. Script in [BUSINESS_PROTOTYPE.md §8](./BUSINESS_PROTOTYPE.md#8-the-demo-12-minutes)._

_Last updated 2026-09-23._
