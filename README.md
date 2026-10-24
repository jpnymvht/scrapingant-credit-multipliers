# scrapingant pricing: credit multipliers explained, real page costs, and when ScraperAPI is worth the upgrade

ScrapingAnt pricing starts at $19/month for the Enthusiast plan, and there's a genuinely free tier: 10,000 API credits every month with no credit card required. That's the short answer. The longer answer matters more, because ScrapingAnt sells credits, and a default request burns 10 of them. That $19 plan buys you about 10,000 JavaScript-rendered pages per month, not 100,000.

This guide walks through every ScrapingAnt plan, the actual credit math behind the headline numbers, the fine print most pricing pages skip, and the point where a rival like ScraperAPI starts making more financial sense despite its higher sticker price.

> **Quick take:** if you're scraping plain, unprotected pages at low volume, ScrapingAnt's free tier may cover you indefinitely. If your targets include Amazon, Google, LinkedIn, or sites behind Cloudflare and DataDome, run the numbers on ScraperAPI instead — its Hobby plan at $49/month (or $44.10/month billed annually) includes 100,000 credits and 20 concurrent threads. 👉 [Check ScraperAPI's current plans and annual pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## ScrapingAnt plans and prices

ScrapingAnt currently sells five paid tiers plus a recurring free plan. Here's the full lineup as shown on its official site:

| Plan | Credits/mo | Price/mo | Support level |
| --- | --- | --- | --- |
| Free | 10,000 | $0 | Docs only |
| Enthusiast | 100,000 | $19 | Email |
| Startup | 500,000 | $49 | Priority email |
| Business | 3,000,000 | $249 | Priority email + debug sessions |
| Business Pro | 8,000,000 | $599 | Priority debug sessions |
| Custom | 10M+ | $699+ | Dedicated manager + enterprise onboarding |

A few differences between tiers don't show up in the credit counts. Custom proxy pools, custom anti-bot avoidance setups, and a dedicated account manager only unlock at Business and above — Enthusiast and Startup customers get standard pools like everyone else. Startup and up also get custom code snippets for integration help, while Enthusiast is pointed at the documentation.

The free tier deserves a note: it renews monthly, so it's a standing allowance rather than a one-time trial. If your project needs fewer than 10,000 credits a month, you may never pay ScrapingAnt anything.

## What a ScrapingAnt credit actually costs

Credits are not requests. This is the single most important thing to understand about ScrapingAnt pricing, and it's the part most comparison articles gloss over.

Every option you enable multiplies the cost of one request. ScrapingAnt's own documentation states that most requests cost between 1 and 25 credits depending on proxy type and JavaScript rendering, and that the default request — Chrome rendering with standard proxies — costs 10 credits. On the $19 Enthusiast plan, that works out like this:

| Request type | Credits per request | Cost per 1,000 pages (Enthusiast) |
| --- | --- | --- |
| Simple fetch + datacenter proxy | 1 | $0.19 |
| Headless, JS disabled | 2 | $0.38 |
| JS rendering + standard proxies (the default) | 10 | $1.90 |
| Simple fetch + residential proxy | 25 | $4.75 |
| JS rendering + residential proxy | 125 | $23.75 |

The last row is the budget killer. At 125 credits per request, the Enthusiast plan's entire monthly balance covers roughly 800 residential-plus-rendering pages. If your targets need residential IPs, the "cheap" plan gets expensive fast.

The AI extractor stacks another charge on top: 1 credit per 30 characters of output (markdown plus extracted text), added to the base scrape cost. The same math applies if you use ScrapingAnt's MCP server with Claude Code, Cursor, or Windsurf — agent calls draw from the same credit pool as direct API requests.

> Before committing to a plan size, estimate your real per-request cost: take your mix of simple fetches, rendered pages, and residential requests, apply the multipliers above, and only then compare plans.

## ScrapingAnt fine print that affects your bill

Three rules sit outside the pricing table but directly change what you'll pay.

**Unused credits don't roll over.** If you use half your monthly allowance, the rest disappears at renewal. ScrapingAnt does soften this in one way: if you run out mid-month, you can restart your plan instantly and the credits refresh immediately — you don't wait for the next billing cycle. That's useful for bursty workloads, but it means paying twice in one month if you misjudge your volume.

**There's no concurrency cap on any plan.** Every request gets its own Chrome instance and proxy automatically. This matters if you're running parallel jobs: ScraperAPI, by contrast, caps concurrent threads per plan (20 on Hobby, up to 500 on Advanced) and returns a 429 error when you exceed the limit — the request is turned away rather than queued, with no extra charge for going over.

**Failed requests cost 0 credits, according to ScrapingAnt.** That's the company's own claim ("pay only for successful scrapes"). Independent benchmark notes from Scrapeway have flagged that blocked requests sometimes still get charged, so treat the zero-cost-failure promise as a policy to verify against your own billing dashboard rather than a guarantee.

## What independent testing says about the price-to-performance ratio

ScrapingAnt is cheap, and independent benchmarks say there's a reason. In Scrapeway's March 14–20 benchmark window, ScrapingAnt averaged a 31.4% success rate across protected targets — well below the 58.2% industry average in the same dataset — with a 17.6-second average response time against an 8.7-second industry average. It scored 0% on Zillow, Booking.com, and several other major sites in that window.

A separate comparison by webscraping.cc, last verified in 2026, ranked ScrapingAnt worst for success in its testing at around 35%, slowest in the run at nearly 22 seconds average response, and noted that the steep credit multiplier means headline credit counts overstate real capacity. ScraperAPI scored around 62–64% success in independent benchmarks, with a known weakness on Cloudflare and DataDome targets where it can return 500 errors.

Two different test runs, same direction: low price, low success on hard targets. Neither figure comes from either vendor, so treat them as directional rather than gospel — but if your project lives or dies on success rates against protected sites, the per-page math changes completely. A $0.19-per-1,000-page plan that fails two-thirds of the time costs more per successful page than a pricier plan that works.

## When ScraperAPI is the better deal

ScrapingAnt wins on entry price, free tier size, and unlimited concurrency. ScraperAPI wins on success rates, credit cost predictability for standard pages, and plan flexibility. Here's ScraperAPI's full current lineup from its official pricing page — every plan includes JS rendering, premium proxies, CAPTCHA and anti-bot handling, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee:

| Plan | Monthly credits | Concurrent threads | Monthly price | Annual (per month) | Get started |
| --- | --- | --- | --- | --- | --- |
| Free | 1,000 | 5 | $0 | — | [ Sign up for 1,000 free credits](https://dashboard.scraperapi.com/signup?fp_ref=coupons) |
| Hobby | 100,000 | 20 | $49 | $44.10 | [ Start the Hobby trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Startup | 1,000,000 | 50 | $149 | $134.10 | [ Start the Startup trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Business | 3,000,000 | 100 | $299 | $269.10 | [ Start the Business trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Scaling | 5,000,000 | 200 | $475 | $427.50 | [ Start the Scaling trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Professional | 10,500,000 | 300 | $975 | $877.50 | [ Start the Professional trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Advanced | 21,500,000 | 500 | $1,975 | $1,777.50 | [ Start the Advanced trial](https://www.scraperapi.com/signup?fp_ref=coupons) |
| Enterprise | 22M+ | 500+ | Custom | Custom | [ Talk to ScraperAPI sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Annual billing saves 10% across the board. On Hobby, that's $529.20 for the year instead of $588 — a real $58.80 difference, not a rounding error.

The credit economics differ from ScrapingAnt's in one useful way: ScraperAPI prices by target site, not by feature toggle. A standard page costs 1 credit. Amazon costs 5, Google and Bing cost 25, LinkedIn costs 30, and sites behind Cloudflare, Datadome, or PerimeterX add 10 credits when the bypass succeeds. A dashboard tool called the Domain Cost Estimator tells you the exact cost for any URL before you commit, and a `max_cost` parameter caps what any single request can spend. You can plan a month's budget down to the credit, which is harder to do when every enabled option multiplies your burn rate.

Running out of credits works differently too. By default, scraping pauses until renewal. On Hobby through Professional, you can opt into auto-upgrade, which bumps you to the next plan automatically when credits run out. On Scaling and above, pay-as-you-go keeps you scraping at a fixed per-credit rate up to a monthly spending cap you set. Annual plans can renew early for a fresh batch of credits.

If you want to test before committing, the free plan includes 1,000 credits with 5 concurrent connections, and there's a 7-day trial with 5,000 credits — neither requires a credit card. 👉 [Start the 7-day trial with 5,000 credits](https://www.scraperapi.com/signup?fp_ref=coupons)

One more angle on the comparison: ScrapingAnt's free tier (10,000 credits monthly) is about ten times larger than ScraperAPI's free plan (1,000 credits), and ScrapingAnt charges nothing for failed requests while ScraperAPI expects a 1–3% failure rate it doesn't bill. If you're a student or hobbyist testing a scraping idea, ScrapingAnt's free tier is the more generous sandbox. The trade-off shows up when you scale: at $19 for 100,000 credits versus ScraperAPI's $49 for the same credit count, ScrapingAnt looks five times cheaper until you remember its default request consumes ten credits and its benchmarked success rate sits near the bottom of independent testing.

## FAQ

**Is ScrapingAnt's free plan really free?**
Yes. It includes 10,000 API credits every month, renews automatically, and requires no credit card. You only enter payment details if you upgrade.

**How many pages do 100,000 ScrapingAnt credits actually get me?**
It depends entirely on your request settings. Simple fetches with datacenter proxies: 100,000 pages. The default setup with JavaScript rendering: about 10,000 pages. JavaScript rendering plus residential proxies: about 800.

**Do unused ScrapingAnt credits roll over to next month?**
No. Unused credits expire at each billing cycle. If you run out early, you can restart the plan immediately for an instant credit refresh.

**Does ScrapingAnt limit concurrency?**
No. There's no concurrency cap on any plan, free or paid. Compare that to ScraperAPI, where thread limits scale from 20 (Hobby) to 500 (Advanced) and over-limit requests get a 429 response with no charge.

**Which is cheaper per page, ScrapingAnt or ScraperAPI?**
For simple, unprotected pages, ScrapingAnt — $0.19 per 1,000 simple fetches on Enthusiast versus $0.49 per 1,000 standard pages on ScraperAPI Hobby. For JS-rendered pages the gap narrows ($1.90 vs. 5–10 credits per page), and for hard targets the picture can invert once failure rates enter the math.

## Picking between them

Map your situation to one of these:

- **Hobby project or early prototype, normal websites, under 10,000 credits a month** → stay on ScrapingAnt's free tier. It costs nothing and requires no card.
- **Bulk scraping of easy, undefended sites at volume** → ScrapingAnt's simple-fetch pricing ($0.19 per 1,000) is hard to beat, and unlimited concurrency helps. If you hit its success-rate ceiling, ScraperAPI's Hobby tier at $44.10/month annual is the next rung.
- **Amazon, Google, LinkedIn, or bot-protected targets** → ScraperAPI's per-site credit pricing and higher benchmarked success rate (62–64% vs. ~31–35%) make it the more defensible spend, even at 2.5x the entry price. Its Cloudflare/DataDome weakness is worth testing against your specific targets first.
- **AI agent workflows needing markdown extraction from ordinary pages** → ScrapingAnt built MCP support and AI extraction for exactly this, and its credit costs are manageable on normal pages that don't fight back.

Before you buy either one, do two things: run your actual target URLs through the vendor's cost estimator (ScrapingAnt publishes a credit cost breakdown; ScraperAPI has the Domain Cost Estimator in its dashboard), and check an independent benchmark for your specific target sites — success rates vary wildly by domain, and the plan that looks cheap on paper is the one that fails quietly on yours.

If the math points to ScraperAPI, 👉 [compare all ScraperAPI plans and pick your tier](https://www.scraperapi.com/pricing/?fp_ref=coupons) — the 7-day trial with 5,000 credits is enough to benchmark your real targets before you spend a dollar.
