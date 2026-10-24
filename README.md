# serp api free: What the Free Tiers Actually Include, the Credit Math Most Reviews Skip, and When ScraperAPI's Trial Beats a Small Free Plan

Searching for a free SERP API usually means one of two things: you want enough free queries to test a pipeline, or you want to run a small project without paying. Here's the short version: no provider currently gives away unlimited Google results, but several give meaningful free allowances — and one of the largest test allowances comes from ScraperAPI, which hands new accounts 5,000 API credits over a 7-day trial (no credit card) plus 1,000 credits on a free account. The catch most comparisons don't explain: on ScraperAPI, a Google or Bing request costs 25 credits, not 1, so those numbers translate to about 200 trial searches and 40 free-account searches.

> **Quick take:** if you only need to test a handful of Google queries, a dedicated SERP API with a renewing free tier is the simpler choice. If you want one API key that covers Google, Bing, Amazon, LinkedIn and general web scraping with proxy rotation, CAPTCHA handling and JS rendering built in, ScraperAPI's 7-day trial is the biggest free test drive in this space — 👉 [Start the 7-day trial with 5,000 free credits](https://www.scraperapi.com/signup?fp_ref=coupons)

## What "free" actually means in the SERP API market

Every free tier falls into one of three buckets: a monthly-renewing quota, a one-time credit grant, or a timed trial. The difference matters more than the headline number, because a renewing 250 searches/month can sustain a hobby project forever, while a one-time 2,500-query grant is gone after a weekend of testing.

Here's the current landscape, based on provider pricing pages checked in October:

| Provider | Free allowance | Renews | Card required | Engines |
| --- | --- | --- | --- | --- |
| Bright Data | 5,000 requests | Monthly | No | Google, Bing, others |
| SerpApi | 250 searches (50/hour cap) | Monthly | No | Google, Bing, others |
| Searlo | 3,000 credits, valid 1 year | One-time | No | Google |
| Serper | 2,500 queries | One-time | No | Google |
| Oxylabs | $5 in credits (~5,000 Google results, no JS rendering) | One-time | Not stated | Google, Bing, others |
| ScraperAPI | 5,000 credits / 7-day trial + 1,000 credits free | Trial + one-time | No | Google, Bing, others |
| SearchApi | 100 requests | One-time | Not stated | Google, Bing, others |
| Scrapingdog | 100 credits (~20 Google Light searches) | One-time | No | Google + scraping APIs |

One option quietly disappeared: Google's own Custom Search JSON API stopped accepting new customers, and existing users must move to an alternative by January 1, 2027. It never returned full Google result pages anyway — it queried a Programmable Search Engine you configured yourself. So for new projects, the "official free option" is effectively gone.

For scale context: a rank tracker checking 100 keywords once a day burns roughly 3,000 searches a month. That's beyond every free tier on this list. Free allowances cover prototyping and evaluation; anything production-sized gets paid.

## ScraperAPI's free plan and trial: what you actually get

ScraperAPI gives new users two separate allowances, and they're often confused in reviews:

- **7-day trial: 5,000 API credits, no credit card required.** This is the trial you get at signup.
- **Free account: 1,000 API credits**, capped at 5 concurrent connections. Support can grant additional test credits on request.

The 1,000-credit free tier is a signup grant, not a monthly allowance — it doesn't refresh. So the realistic free sequence is: 5,000 credits for a week of intensive testing, then 1,000 credits on the free plan for slow, ongoing poking around.

Note the concurrency limit on the free account: 5 connections. If your test script fires 50 parallel requests, most will queue or fail. Throttle your script or you'll waste your testing window.

👉 [Create a free ScraperAPI account and claim the 1,000 credits](https://www.scraperapi.com/signup?fp_ref=coupons)

## The credit math: why 5,000 credits isn't 5,000 searches

This is the part most comparison posts skip, and it changes the whole answer. ScraperAPI charges per domain, not per request:

| Target | Credits per request |
| --- | --- |
| Standard web pages | 1 |
| Amazon, Walmart, eBay | 5 |
| **Google, Bing (all subdomains)** | **25** |
| LinkedIn | 30 |
| Bot-protected domains (Cloudflare, DataDome, PerimeterX, Akamai bypass) | 10 |
| `render=true` or `premium=true` | +10 each |
| `ultra_premium=true` | +30 (paid plans only) |
| `ultra_premium=true` + `render=true` | 75 (paid plans only) |

So the free allowances translate like this: the 7-day trial's 5,000 credits buy roughly **200 Google searches**, and the free account's 1,000 credits buy about **40**. Parameters that add no cost: `country_code`, `session_number`, `device_type`, `output_format`, `autoparse` — geotargeting is free, which is worth knowing before you assume you need a premium option.

Two practical tools keep this manageable. The dashboard's Domain Cost Estimator shows the exact credit cost of any URL before you scrape, there's an API endpoint (`/account/urlcost`) that does the same without a GUI, and you can set a `max_cost` per scrape so a single request can't blow through your budget. Every response also includes a `sa-credit-cost` header, so you can audit real spending after the fact.

Run the paid math the same way: Hobby's 100,000 monthly credits equal about 4,000 Google searches, or up to 100,000 plain pages. That's why "high pricing" complaints about ScraperAPI are only partly fair — plain HTML comes out to roughly $0.10–0.15 per 1,000 pages from Startup up, and the expensive reputation comes from rendered and protected pages, which cost 10–30× that.

## Full plan comparison: every ScraperAPI tier

All paid plans include the same feature set: JS rendering, premium residential and mobile IPs, advanced anti-bot bypass, parsing and structured data APIs, DataPipeline, full crawler access and pay-as-you-go eligibility. The tiers differ only in credits, concurrency, geotargeting scope and analytics history. Annual billing takes 10% off every tier.

| Plan | Monthly price | Annual (per month) | Credits/month | Concurrency | Link |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 (one-time) | 5 connections | [ Claim free credits](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 threads | [ Get Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 threads | [ Get Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 threads | [ Get Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 threads | [ Get Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 threads | [ Get Professional](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 threads | [ Get Advanced](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ threads | [ Contact sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Beyond the raw SERP fetching, the same credits now cover structured JSON endpoints for Google Search, News, Jobs, Shopping and Maps, plus Amazon, Walmart, eBay, Home Depot, Redfin and AI answer engines like ChatGPT, Perplexity and Gemini. In 2026 ScraperAPI also acquired Traject Data and folded its Rainforest and SerpWow SERP and e-commerce APIs into the same credit system — so if you outgrow simple search results, you don't switch providers, you switch endpoints.

## Which plan makes sense for SERP work specifically

Translate each tier into Google searches (25 credits each) and the decision gets simple:

- **Just evaluating?** Stay free. Trial + free account gives you about 240 Google searches total, plus thousands of standard-page scrapes to test the rest of the API.
- **Small ongoing SERP monitoring (up to ~4,000 Google searches/month):** Hobby at $49, or **$44.10/month billed annually**. Annual Hobby costs $529.20 for the year with 1.2M credits.
- **Rank tracking or AI-agent search pipelines at volume:** Startup gives 40,000 Google searches/month for $149; Business gives 120,000 for $299 and unlocks country-level targeting everywhere.
- **Anyone running mixed workloads** (some Google, mostly e-commerce or plain pages) gets far more out of the same credits, since non-Google targets cost 1–5 credits.

One thing worth checking before you commit to a plan size: credits don't roll over, and overage billing only exists from Scaling up. If your monthly volume swings wildly, a smaller plan plus pay-as-you-go (available from Scaling) beats a big flat plan you only half-use.

## Fine print that affects real usage

These details only show up in the docs and FAQ, but they change how the free tier behaves:

- **Failed requests are free.** ScraperAPI retries with different IPs until a request succeeds, and only successful responses (200 and 404 status codes) get billed. For SERP work this matters — Google blocks aggressively, and you won't pay for blocked attempts.
- **Your own cancellations aren't free.** If you kill a request before the 70-second window completes, that counts as billable. Set your client timeout to 70 seconds as the docs recommend.
- **Geotargeting has a paywall.** Hobby and Startup only target US and EU. Country-level targeting anywhere else starts at Business ($299). If your use case needs Japanese or Brazilian Google results on a budget, factor that in before choosing a tier.
- **Auto-upgrade is opt-in.** When credits run out, scraping pauses by default. On Hobby through Professional you can enable auto-upgrade to bump to the next plan automatically; from Scaling up you can use pay-as-you-go at a fixed per-credit rate instead.
- **Refunds are easy.** The docs state it plainly: a 7-day no-questions-asked refund policy, handled through support. Combined with the no-card trial, your real risk of trying this is zero.

👉 [Check current plan prices and start with the 7-day trial](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## When a free ScraperAPI isn't the right answer

Honesty about fit saves everyone time. ScraperAPI's free offer loses to alternatives in specific situations:

- **You need a renewing free tier for an ongoing micro-project.** ScraperAPI's 1,000 credits are one-time. SerpApi's 250 searches/month and Bright Data's 5,000 requests/month both renew, which suits a permanently tiny workload better.
- **Google is 100% of your workload and cost per search is everything.** Dedicated SERP APIs price Google results far below 25 credits' equivalent. SerpApi's entry plan works out to $25 per 1,000 searches; PrismCrawl sells a one-time $5 package covering 16,667 searches ($0.30 per 1,000). Hobby's effective rate of about $11 per 1,000 Google searches sits between those — competitive for an all-in-one API, not the floor for Google-only use.
- **You need to pick specific IPs, ASNs or cities.** ScraperAPI deliberately doesn't expose that level of proxy control; you choose country, session and IP tier. If you need it, raw proxies are the answer.

Where ScraperAPI clearly wins the free-value comparison: breadth. One trial key tests Google, Bing, Amazon, LinkedIn, Cloudflare-protected pages, JS-rendered pages, structured JSON endpoints, the crawler and DataPipeline — competitors' free tiers cover their SERP endpoint and little else.

## FAQ

**Does ScraperAPI have a free plan?** Yes. A 7-day trial with 5,000 API credits (no credit card), plus a free account tier with 1,000 one-time credits and up to 5 concurrent connections. Support can add test credits if you ask.

**How many free Google searches does that equal?** About 200 on the trial and 40 on the free account, since Google and Bing requests cost 25 credits each. Standard web pages cost 1 credit, so the same balance stretches much further on non-SERP targets.

**Do failed requests use credits?** No. Only successful responses (200 and 404) are billed, and ScraperAPI retries blocked requests automatically. Cancelled requests within the 70-second window are the exception — those get billed.

**Is there a refund if I pay and regret it?** Yes — a 7-day no-questions-asked refund through support, per the official billing documentation.

**Can I use it for rank tracking for free?** Not sustainably. A tracker checking 100 keywords daily needs roughly 3,000 searches a month, which is 75,000 credits — nearly a Hobby plan's monthly allowance, and far beyond any free tier on the market.

## Picking your option before you sign up

Match your situation to the move:

- Testing a scraper or agent against Google and other targets this week → take the trial, burn the 5,000 credits on real queries, keep the 1,000 free credits for follow-ups.
- Ongoing hobby-scale SERP monitoring with no budget → a renewing free tier from a dedicated SERP provider (SerpApi's 250/month, Bright Data's 5,000/month) fits better than ScraperAPI's one-time credits.
- Ready to pay for mixed scraping + SERP work → Hobby annual at $44.10/month is the entry point, and Business is the first tier with worldwide country targeting.

Two checks before you commit: run a few of your real target URLs through the Domain Cost Estimator so you know your actual credit multiplier, and if you go paid, remember the refund window is 7 days — that's enough time to validate your heaviest domains. 👉 [Start your 7-day trial with 5,000 credits — no card needed](https://www.scraperapi.com/signup?fp_ref=coupons)
