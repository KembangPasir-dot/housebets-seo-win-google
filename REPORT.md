# Win Google for Housebets — SEO Audit, Keyword Map & 90-Day Plan

**Contest:** Housebets Contest Labs — "Win Google for Housebets" (Growth) · Prizes $15,000 · 215 entered (14 Nov 2026)
**Date:** 12 November 2026 (research) · **Package updated:** 14 November 2026 (starter-kit formats added: keywords.csv, pages.csv, brand-serp.csv, report.pdf)
**Author:** Ali Ulin — LinkedIn: https://www.linkedin.com/in/ali-ulin/
**Scope:** Audit (20) · Keywords and satellites (15) · Win back our brand searches (20) · Pages (15) · First 90 days (15) · AI search (15) — 100 points, in the starter kit's order. AI-search dataset: `ai-answers.csv` (same package).

## How this report was built — and what it cannot claim

This is an **external audit**. I had no access to Search Console, Google Analytics, or any Housebets internal data, and no account was created. All findings come from public evidence gathered on 12 November 2026: text fetches of housebets.com pages (robots.txt, sitemaps, homepage, casino, sports, promotions, blog, legal pages, help centre), web searches for brand and money keywords, and the official Contest Labs pages. Direct `curl` to housebets.com is blocked (Cloudflare); the site was read through a text-fetch crawler, which returns rendered text but not meta tags, canonicals, hreflang, structured data, HTTP status codes, or Core Web Vitals — anything of that kind is marked **unverified** in this report, not invented.

Rankings quoted here are **a single-day snapshot from a text-search tool** (5–8 results returned per query), not a screenshot of a live google.com SERP, and geo/personalisation are unknown. Where the tool returned only the top ~4–6 results, "not in the top 10" is **not** established — only "not in the returned results". No search volumes, keyword-difficulty scores, CPCs, or traffic numbers appear anywhere in this report: no keyword tool was available, and inventing them would be fabrication. Target calls (own / compete / ignore) rest on observed SERP composition only.

No AI-engine answer in this report is quoted unless it was actually read from a tool result. Where an engine could not be reached (see §6), that is stated plainly with the method to re-test it. Nothing in this report is copied from any other entrant's submission.

## Executive summary

Housebets has a real product and a genuinely strong legal/transparency layer — but Google barely sees it, and the brand conversation is owned by other people.

1. **Google may not be able to crawl the flagship product.** `/sports` returns only "Sportsbook is not available in your region" to this crawler, and Googlebot crawls mainly from the US — a prohibited jurisdiction in Housebets' own Terms. If Googlebot gets the same block, the sportsbook returns zero indexable content. The homepage is also nearly empty to a text crawler (hero promo only), and `/house-games` renders almost nothing. `/casino` renders richly; the inconsistency itself is a finding.
2. **housebets.com ranks nowhere for its own brand.** In 10 brand queries tested on 12 Nov 2026, the official site appeared in **none** of the returned results. Review/affiliate sites own "Housebets", "Housebets review", "Housebets bonus", "is Housebets legit"; lookalike domains own "Housebets login" (8/8 results) and push fake APK downloads for "Housebets app".
3. **Affiliates define the offer — and invent it.** At least six different promo codes and three different welcome bonuses circulate in top results, while hands-on reviewers say no deposit match exists on any house page. The real offers (Duel Mode 50% rakeback, Wave 2 on-chain bonus) have no ranking official page to state them.
4. **A live mirror splits the brand.** housebets.win serves the same branding with contradictory numbers (bankroll $450K vs $2.91M on .com; contests $18,000/1 entry vs $43,000/497; sportsbook contest $4,000 vs $15,000; no "Win Google" contest at all) and its legal pages already rank. Whether it is official, staging, or third-party is unverified — but it must be consolidated before anything else is built off-domain.
5. **The winnable keywords are not the head terms.** "Best crypto casino" and "bitcoin casino" are owned by affiliate listicles (Stake #1 almost everywhere). Housebets' ownable ground is its differentiators: the on-chain wallet-history bonus (no incumbent), 50% rakeback via Duel Mode (a priced number with a published formula), a provably-fair verification guide built on its 11 Originals at ~99% RTP, and the USDT/no-KYC long tail.
6. **AI search is the thinnest surface of all — and the most fixable.** No live AI answer about Housebets could be obtained from public routes on 12 Nov 2026 (see §6 and `ai-answers.csv`). Housebets appears in none of the "best crypto casino" lists the engines draw from. The fix is canonical, citable facts: one page per fact cluster, in tables, plus corroboration on the review domains the engines already cite.
7. **Satellite sites: don't build them.** Google's doorway-abuse policy describes exactly "multiple websites with slight variations… to maximize reach for any specific query". Housebets already has the failure mode in miniature with .win. Fix the duplicate first; build on the main domain and the existing help subdomain instead.

The 90-day plan (§5) sequences this: stop the bleeding first (crawl access, mirror, trust pages), then build the ownable pages, then measure and iterate.

---

## 1. Audit (20 pts)

### 1.1 How Google's crawlers see Housebets

**The sportsbook may be invisible to Google.** Fetching `https://www.housebets.com/sports` on 12 Nov 2026 returned only: "Sportsbook is not available in your region. Access to the sportsbook is restricted where you are located." Googlebot crawls mainly from the US, and the United States is a Prohibited Jurisdiction in Housebets' own Terms (§5). If Googlebot is treated like any other US visitor, the sportsbook — a flagship product, and the subject of a live $15,000 design contest — returns **no indexable content at all**. Whether Googlebot specifically is allow-listed is **unverified** from outside; it needs a server-log / Search Console check by the Housebets team. This is the single biggest "how Google sees us" fact in this audit, and the first thing to verify in the 90-day plan.

**Rendering is inconsistent.** The homepage returned only 32 lines to the text crawler (hero promo: "$5M Wave 2 is live", sign-in options, the on-chain bankroll figure) — no footer, no licence line, no descriptive copy. `/house-games` returned almost nothing (a leaderboard fragment). By contrast `/casino` rendered richly (game lists, providers, links) and `/contests` rendered fully. The site is Next.js, which can server-side render, so the thin homepage may partly be a text-extraction limit — but it is a warning, not an excuse: **do not assume the homepage's content is indexed; verify in Search Console.** And even fully rendered, the homepage is promo-led with almost no indexable descriptive copy — a thin-content homepage for a brand that wants to "win Google".

**The technical base is competent.** `robots.txt` (1,047 lines, fetched) is thorough: account/admin/partner paths disallowed across ~19 locale prefixes, ending with `Sitemap: https://www.housebets.com/sitemap.xml`. The sitemap index lists 11 sub-sitemaps (static, 5 game-catalog files, providers, blog, promotions, legal, about). No AI-crawler rules (GPTBot / CCBot / Google-Extended) were observed. ~19 locales exist (ar, da, de, es, fi, fr, hi, hu, **id**, it, ja, ko, pl, pt, ru, th, tr, vi, zh + English default), with locale-prefixed URLs for every core and legal page. Two cautions: (a) 16 legal pages × 19 locales ≈ 300 near-duplicate URLs — if translations are thin or hreflang is missing/broken, Google may pick the wrong locale or treat them as duplicates (hreflang implementation itself is **unverified**); (b) several locale prefixes correspond to **prohibited jurisdictions** (de, fr, it, es, pt, da, pl, hu…) — localised pages for countries where the service is banned are a confusing signal for users and for Google. The static sitemap lists no `/contests` URLs — Contest Labs pages may rely on internal links alone (**unverified** whether they appear in another sub-sitemap).

**The blog is stale.** It exists with weekly cadence through Aug–Sep 2026, but nothing newer than 3 Sep 2026 in the fetch — ~10 weeks stale at audit date. Posts are sports picks/event previews with repeated boilerplate descriptions (thin/duplicate-snippet risk).

### 1.2 Trust signals Google wants from a gambling site

The legal/fairness layer is genuinely strong for a Curaçao casino — unusually thorough. The weak spots are specific and fixable.

| Signal | Status | Evidence |
|---|---|---|
| Licence number displayed | Present | Curaçao Gaming Authority licence **OGL/2024/431/0231**, in Terms §1 and the Regulatory Scope page. Every independent reviewer found cites the same number. (One older source cites a stale Antillephone licence 8048/JAZ 2022-024 — do not use that as current.) |
| Licence verifiable on regulator register | Reported, not independently verified here | Two reviewers claim to have checked the CGA register (Nov 2026). Not checked in this audit. |
| Operator / company | Present | Bridge Technologies B.V., Chamber of Commerce 160264(0), Dr. M.J. Hugenholtzweg 25, Willemstad, Curaçao (Terms §1). Payments via Bridge Technologies (Cyprus) Ltd (HE 440867). |
| Responsible gambling tools | Present (documented) | Deposit/loss/wager limits, session limits + reality checks, cooling-off, self-exclusion 24h–permanent, per-product (casino/sportsbook/both), irreversible during the period. But one reviewer (updated 12 Nov 2026) claims the live account offers only deposit limit + cool-off + self-exclusion in practice — a policy-vs-practice gap to check, not to assert. |
| Responsible-gambling support organisations | Unclear | The page has a "Support organisations" heading but the body did not render in the fetch. GamCare / Gambling Therapy / BeGambleAware links not confirmed. |
| Complaints / ADR | Present, strong | Support email, formal Complaint Form, timelines (acknowledge 7 days / 2 days for RG; resolve 4 weeks), independent ADR **Resolvo Curaçao** (free), then CGA escalation. Above average for a Curaçao site. |
| Fairness / provably fair | Present, excellent | Full RNG + provably-fair documentation with **runnable Node.js code** for the shared draw function and every game, worked examples with real seeds. The most-cited trust asset in reviews. But no RNG lab names or certificates were linked on the pages fetched (iTech Labs / GLI / eCOGRA not named) — unverified. |
| Help centre / FAQ | Present | help.housebets.com, ~129 articles in 12 categories. Lives on a subdomain, so its SEO value accrues to the subdomain unless linked well. |
| About / founder | Present, thin | About page names founder Porchy; no team, no owners/directors behind Bridge Technologies B.V., no company history beyond the founder story. Reviewers flag the same gap. |
| 2FA / account security | Conflicting, unverified | Terms §3 says "Enable multi-factor authentication". One reviewer claims **no 2FA at all** (WagerDB, security 3.0); another tells readers to switch on 2FA in settings. Cannot resolve without an account. |
| KYC position | Mixed messaging | Marketing copy says "no KYC"; Terms and payment policy say KYC is mandatory at verification/withdrawal thresholds (reviewers cite ~€2,000 lifetime / XCG 4,000; manual audit on every cashout). The contradiction is itself a trust problem — reviewers and complainants both flag it. |
| On-chain transparency | Present | Homepage shows live "House bankroll · on-chain $2,911,788" with coin breakdown and an Arkham link ("View wallet"). |
| Licence scope honesty | Present (double-edged) | The Regulatory Scope page openly states the $HBTS token, airdrops, on-chain rewards, affiliate programme and DeFi sit **outside** the CGA licence. Rare honesty — but it means the homepage's lead offer is unregulated. |

**Net assessment:** licence, operator identity, ADR, responsible-gambling and provably-fair pages are real and unusually thorough. The gaps are: (a) Curaçao-only licence, shared across ~13 domains per one reviewer; (b) "no KYC" marketing vs KYC-at-withdrawal reality; (c) no public evidence on RG support organisations, named RNG labs, 2FA, or the people behind the operator; (d) the token/rewards the homepage leads with are explicitly outside the licence.

### 1.3 Restricted countries — and the Indonesia question

The authoritative list is Terms §5: **~45 jurisdictions**, including the US, UK, Australia, Brazil, Germany, France, Netherlands, Spain, Portugal, Poland, Italy, and anywhere online gambling is prohibited. **Indonesia is NOT on the prohibited list.** Reviewers disagree with each other on the list (counts of 10, 23, 41, ~45; one stale review even welcomes US players — plainly wrong vs. the current Terms). The Terms are the only authoritative source; the disagreement itself is a brand-search problem (see §3).

Indonesia deserves a straight answer because the brief asks how Google's crawlers see the site "in some countries": gambling is illegal in Indonesia, and Komdigi blocks gambling domains at scale through the TrustPositif system distributed to ISPs. **Whether housebets.com specifically is on the TrustPositif list was not verified** — it was not tested from an Indonesian network and was not found named on a published blocklist. Do not claim it is blocked. What can be said: (a) Indonesia is not a prohibited jurisdiction in the Terms, yet the site operates an Indonesian locale (`/id/` exists) while gambling is illegal there — a compliance/positioning tension; (b) **if** the domain is TrustPositif-listed, Indonesian users cannot reach it without workarounds, so Indonesian search demand cannot convert and any `.id`-targeted SEO is wasted; (c) Googlebot does not crawl from Indonesia, so an Indonesian ISP block would not affect Google's crawl — the geo-block that matters for Google is the **US/prohibited-jurisdiction gate on /sports** (§1.1), not Indonesia.

### 1.4 The housebets.win mirror — a live duplicate

housebets.win serves the same title, hero and branding as housebets.com, but different data (verified by direct text fetch on 12 Nov 2026):

| | housebets.com | housebets.win |
|---|---|---|
| Open prizes (contests) | $43,000 | $18,000 |
| Total entries | 497 | 1 |
| "Win Google for Housebets" | $15,000, 191 entries | **Not listed at all** |
| "Sportsbook is coming" | $15,000, 155 entries, ends 14 Nov | $4,000, 1 entry, ends 16 Nov |
| Homepage bankroll | $2,911,788 | $450,000 |

Its legal/blog pages are already indexed and ranking (its Terms page ranked for a licence query in this audit's searches). Whether .win is an official alternate domain, a staging/preview deployment, or a third-party copy is **unverified** — no statement on either domain explains it, and the same `_next` asset paths suggest the same codebase, which is inference, not proof. Either way it is a live duplicate-content and brand-confusion risk: two domains, same content, conflicting numbers, and Google is already indexing the stale one. If it is official, it needs canonicals / noindex / consolidation; if it is not, it needs a takedown/brand-protection action. This is the most concrete duplicate-content finding in the audit — and it is the reason the satellite verdict below is "don't".

### 1.5 Satellite sites — verdict: DON'T BUILD THEM

**Recommendation: do not build satellite sites.**

Google's spam policies define "doorway abuse" as sites or pages created to rank for specific, similar search queries, and list as an example *"having multiple websites with slight variations to the URL and home page to maximize their reach for any specific query"*. A network of Housebets satellite sites built to rank and funnel to housebets.com matches that example almost word for word. Consequences: sites violating the spam policies "may rank lower in results or not appear in results at all", and doorway pages surface as a "Thin content with little or no added value" manual action in Search Console — remediation takes days to weeks, and algorithmic demotion comes with no notice. For a gambling site, which Google already treats as a high-scrutiny category, the risk is asymmetric: the upside is a few extra rankings; the downside is the **main domain** being demoted or actioned.

Housebets already has the problem in miniature: .win is a live second domain with identical branding and conflicting numbers, already indexed. Adding more domains multiplies exactly this failure mode. The lookalike domains already ranking (housebets.co, housebets.uk.com, housebetscasinoindia.com…) are mostly affiliate/review sites, and Housebets' own Affiliate Terms forbid affiliates from bidding on branded keywords and impersonating the brand — a satellite network blessed by Housebets would sit in direct tension with its own affiliate rules.

**The only safe forms — and they are not "satellite sites":** (1) a single clearly-branded, genuinely useful standalone property with original content that answers queries itself and does not funnel — e.g. an independent, editorially separate responsible-gambling / provably-fair education resource that links to Housebets only where relevant and discloses the relationship; (2) legitimate localised subdirectories on housebets.com itself (`/id/`, `/pt/`…) with real translations, proper hreflang and canonicals — which already exist in the sitemap and should be fixed, not duplicated off-domain; (3) the existing help.housebets.com subdomain, a legitimate support property. None of these is a satellite network, and none should be built as a ranking funnel.

### 1.6 Prioritised audit fixes

| # | Fix | Why it matters | Effort |
|---|---|---|---|
| A1 | Confirm from server logs / Search Console whether Googlebot gets the `/sports` geo-block; allow-list Googlebot (or a crawlable sports-content path) if it does | The flagship product may return zero indexable content to Google | Low (check) / Medium (fix) |
| A2 | Consolidate housebets.win: canonicalise, noindex, redirect to .com — or formally claim and differentiate it | Live duplicate with conflicting numbers, already indexed | Medium |
| A3 | Give the homepage real indexable copy (what Housebets is, licence, games, sportsbook, rakeback — in crawlable text, not JS-only hero) | Brand term has almost nothing to rank | Low–Medium |
| A4 | Fix `/house-games` rendering so the page has crawlable content (game list, RTPs, fairness method) | Near-empty to a text crawler | Medium |
| A5 | Publish the restricted-countries list as a public page (not buried in Terms §5) | Ends the contradictory third-party lists that dominate brand search | Low |
| A6 | Publish RG support organisations, RNG lab names/certificates, and the real 2FA status | Closes the exact gaps reviewers flag | Low |
| A7 | Reconcile "no KYC" marketing with the real KYC-at-cashout rule in one public place | The contradiction fuels complaints and "legit?" doubt | Low |
| A8 | Refresh the blog (stale since 3 Sep 2026) and fix boilerplate descriptions | Stale + thin snippets | Low |
| A9 | Fix locale/hreflang: verify hreflang + canonicals per locale; reconsider locales for prohibited jurisdictions | ~300 near-duplicate legal URLs | Medium |
| A10 | Add `/contests` URLs to a sitemap and link them from the main nav | Contest pages rely on internal links alone | Low |

---

## 2. Keywords and satellites (15 pts)

### 2.1 What the money SERPs actually look like

Thirteen money keywords were tested on 12 Nov 2026 ("crypto casino", "best crypto casino", "bitcoin casino", "best bitcoin casino 2026", "online casino crypto", "crypto sportsbook", "bitcoin sportsbook", "best crypto sportsbook", "USDT casino", "provably fair casino", "crypto casino no deposit bonus", "instant withdrawal casino", "best crypto casino no KYC"). **Housebets appeared in none of the returned results for any of them.**

The pattern is consistent: **the head terms are owned by affiliate comparison listicles, not operators.** The winning format is almost everywhere a ranked listicle ("Best X 2026 — N sites ranked/tested") with a comparison table (coins, bonus, payout speed, KYC, licence) plus short per-brand reviews and an FAQ. Guides win only for explainer-intent queries ("what is a crypto casino", "provably fair casino", "no deposit bonus" mechanics). Operator homepages essentially never rank for head terms. **Stake is the single most dominant operator brand** (#1 on most lists, 32 in-house provably fair Originals), followed by Shuffle, BC.Game, Cloudbet, BitStarz, Wild.io, Roobet, Gamdom, Rainbet and Jack.com. AskGamblers appeared in none of the returned results (not proof of absence beyond ~position 6).

### 2.2 Keyword map — 9 clusters

"Target" is a judgement from SERP composition only (no volume/difficulty data was available). **Own** = Housebets has a unique, verifiable claim and the SERP is winnable with a dedicated page. **Compete** = winnable long-tail or via affiliate inclusion, not head-term ranking. **Ignore** = no fit, or the SERP is captured by a different market.

| # | Cluster | Primary keyword | Intent | Current top rankers | Target |
|---|---|---|---|---|---|
| 1 | On-chain bonus (the moat) | "on-chain casino bonus" | Commercial | No incumbent — no SERP leader observed | **OWN** |
| 2 | Rakeback | "crypto casino 50% rakeback" / "best rakeback crypto casino" | Commercial | Rainbet, Gamdom, Stake, Shuffle, Thrill, Duelbits (via listicles) | **OWN the long-tail; COMPETE on head** |
| 3 | Provably fair / Originals | "provably fair casino" / "crypto casino originals" | Informational + commercial | Guides (virlan.co, racefi.io, vip-grinders.com) + listicles; Stake, Gamdom, BetFury, Rollbit | **COMPETE** |
| 4 | Best crypto casino (head) | "best crypto casino" / "best bitcoin casino 2026" | Commercial | Affiliate listicles (bitcoin.com, fairgambling.com, bestbitcoincasino.com); Stake, Shuffle, BC.Game, BitStarz | **COMPETE via inclusion, not ranking** |
| 5 | Bitcoin / USDT | "bitcoin casino" / "USDT casino" | Commercial | Affiliate listicles; BC.Game, BitStarz, Wild.io, Cloudbet; USDT niche: Bets.io, Sportsbet.io, CryptoGames | **COMPETE (USDT long-tail only)** |
| 6 | Crypto sportsbook | "best crypto sportsbook" / "bitcoin sportsbook" | Commercial | Affiliate listicles; Cloudbet, Stake, BC.Game, Sportsbet.io, Rainbet, Roobet | **COMPETE (long-tail)** |
| 7 | No-KYC / instant withdrawal | "best crypto casino no KYC" / "instant withdrawal crypto casino" | Commercial / transactional | No-KYC: Wild.io, BitStarz, Ybets, mBit, Flush. Bare "instant withdrawal casino" is a UKGC-fiat SERP — wrong market | **COMPETE (no-KYC); OWN the crypto-qualified instant variant — after verification** |
| 8 | Bonuses / no-deposit | "crypto casino no deposit bonus" | Commercial | Thin guides + bitcoin.com listicle; genuine offers rare (BetFury, Bitz only) | **IGNORE as a ranking target; use as a guide angle** |
| 9 | Brand | "Housebets", "Housebets review", "Housebets bonus" | Navigational / commercial | Third-party reviews (casino.clinic, cryptocasinoreviews.io, realcasinosbonus.com, wagerdb.com, cryptotips.com) | **OWN** |

### 2.3 The differentiators — what is actually verifiable

| Differentiator | Verified status (12 Nov 2026, via search + site fetch) | Keyword it could own |
|---|---|---|
| **On-chain bonus** | Verified, distinctive. Wave 2 live since 3 Oct 2026: up to **$25,000** per player, $1 deposit to unlock, **1× wagering** (on a 4% house-edge basis); Wave 1 paid for past deposits at other casinos via a read-only wallet scan (up to 5 wallets). Homepage presents the pool as "$5M Wave 2". Campaign-allocation figures conflict across sources ($5M vs $25M) — verify live terms. "On-chain" here means *history-based bonus*, not on-chain wagering — say so plainly. | "on-chain casino bonus", "casino bonus based on wallet history", "Housebets on-chain bonus" |
| **House Games / Originals** | Verified. 20 House Games: **11 Housebets Originals** (Dice, Blackjack, Mines, Limbo, Roulette, Keno, Coinflip, Plinko, Hi-Lo, Baccarat, Hubie's Road, plus newer titles) + 9 Tequity titles; most at **~99% RTP**; provably fair via server seed + client seed + nonce. | "provably fair house games", "crypto casino originals", "casino with 99% RTP games" |
| **50% rakeback (Duel Mode)** | Verified. Duel Mode toggle: **50% of the house edge back as cash** (formula: wager × house edge × 50%); trade-off: XP at half speed, other rewards paused, part of rakeback held until next level. Standard mode: instant rakeback + 24h cashback + weekly/monthly bonuses; ~50% of house edge returned overall (half as rewards, half as House Keys for future $HBTS). | "crypto casino 50% rakeback", "best rakeback crypto casino", "rakeback vs lossback casino" |
| **Instant withdrawals** | Mixed. Casino Clinic timed a **$5,500 USDT withdrawal in 1 minute (29 Oct 2026), no documents**. But reviewers also report every cashout passes a manual audit, a 24h policy window, and KYC triggers after winning sessions. Claim "fast crypto payouts" with evidence — not unqualified "instant". | "instant withdrawal crypto casino", "fastest payout crypto casino" |
| **Hubie (AI host)** | Verified as an **AI host** (LLM-based, offers/gifts/personal reloads by email and chat; operator discloses it can misunderstand). **Not verified as a "streamer"** — do not use that label. Weak as a keyword target; use as supporting colour. | "crypto casino AI host" |
| **XP race / leaderboards** | Verified. XP Race: first to **80,000,000 XP wins a Jacob & Co. watch (~$324,000)**; weekly leaderboard $10,000 (sources conflict: $10k vs $50k weekly; monthly $30k vs $50k vs $100k — verify live). Niche demand; good for brand/community content, not a traffic pillar. | "crypto casino XP race", "casino leaderboard race" |
| **No-KYC at the door** | Mixed. WagerDB: "No KYC, ID never required"; other reviewers: no ID at sign-up, but manual audit per cashout and KYC trigger ~€2,000 lifetime. Honest framing ("no ID at sign-up; verification can be triggered") matches what the top pages already say about every operator. | "no KYC crypto casino", "crypto casino no verification withdrawal" |
| **VIP status match** | Verified via reviews (VIP status transfer from other platforms; 9–10 tiers, Rookie → Castle). Genuinely distinctive; small, high-intent audience. | "crypto casino VIP status match" |

### 2.4 Content plan — the five openings, ranked

1. **On-chain bonus (Cluster 1 — OWN).** Nobody else offers a wallet-history bonus; the SERP has no incumbent. A clear, honest Wave 2 page (how the wallet scan works, $25k cap, $1 unlock, 1× wagering, eligibility, worked example) is the single most ownable asset in this research.
2. **50% rakeback / Duel Mode (Cluster 2 — OWN long-tail).** A concrete, priced number with a published formula. Publish the maths and the trade-offs, with a comparison table vs Stake/Shuffle/Rainbet rakeback. Rivals' rakeback is usually vague or tier-gated.
3. **Provably-fair verification guide (Cluster 3 — COMPETE).** The one head-adjacent SERP where guides beat listicles. A step-by-step verification guide using Housebets' own games as the worked example (server seed / client seed / nonce, with a verifiable bet), plus a House Games hub page listing the 11 Originals with RTPs. Lead with 99% RTP and verifiability, not count (Stake has 32 Originals vs Housebets' 11).
4. **USDT casino, network/fees angle (Cluster 5 — COMPETE).** Small SERP (4 results), methodology-led, directly aligned with the on-chain story. Needs verified network/minimum/payout facts first (TRC-20/ERC-20/BEP-20, minimums, fees, measured payout times).
5. **Get listed in the no-KYC and "best crypto casino" listicles (Clusters 4 + 7 — COMPETE via inclusion).** Housebets matches the no-KYC theme but appears in none of those pages, and has only ~2 tracked community reviews (WagerDB 62.5/100). Inclusion + a credible review footprint is worth more than another on-site listicle the head SERPs will ignore. Do not try to outrank the affiliates with a housebets.com listicle.

### 2.5 Satellites — verdict: don't build

**Recommendation: do not build satellite sites.** Google's spam policies describe doorway abuse as "having multiple websites with slight variations to the URL and home page to maximize their reach for any specific query" — a Housebets satellite network built to rank and funnel to housebets.com matches that example almost word for word. The full reasoning, including the live housebets.win duplicate that already shows the failure mode, is in §1.5. The only safe forms are not satellite sites at all: a single clearly-branded, genuinely useful standalone property with original content; legitimate localised subdirectories on housebets.com itself with real translations and proper hreflang; and the existing help.housebets.com subdomain.

---

## 3. Win back our brand searches (20 pts)

### 3.1 The headline finding

**housebets.com did not appear in the returned results for ANY of the 10 brand queries tested** — "Housebets", "Housebets casino", "Housebets review", "Housebets sportsbook", "Housebets login", "Housebets bonus", "Housebets promo code", "Housebets withdrawal", "is Housebets legit", "Housebets app". Not #1, not anywhere in the returned 5–8 results. The brand SERP is owned by third-party review/affiliate sites plus a swarm of lookalike domains. The only query where housebets.com surfaced was the contest-named search ("Win Google for Housebets"), where housebets.com/contests ranked #1. This is the contest's core brief, stated as a measurement: the brand's own domain is invisible for its own name.

### 3.2 What owns each brand query

| Query | #1 in returned results | Who owns it | The gap |
|---|---|---|---|
| Housebets | cryptocasinoreviews.io (review, 20 House Games, 50% rakeback) | Review sites + lookalikes | No official homepage/brand hub ranks |
| Housebets casino | cryptocasinoreviews.io | Review sites | Same |
| Housebets review | wagerdb.com (62.5/100) | Review sites only (100% third-party) | No official page anchors the narrative; review scores spread 6.8/10, 62.5/100, 2.62/5 |
| Housebets sportsbook | cryptotips.com (review, sportsbook section) | Affiliates | No official sportsbook page ranks — while a $15,000 contest is being run to design that sportsbook |
| Housebets login | housebets.me.uk (lookalike login guide) | **Lookalikes, 8/8 results** | Worst query for brand safety: "mirror" logins pushed, phishing-shaped |
| Housebets bonus | cryptotips.com (100% to $1,000, code MAX) | Affiliates + lookalikes | Invented offers (see §3.3) |
| Housebets promo code | cryptotips.com (code MAX) | Affiliates + lookalikes | Six different codes circulate; two sources say no code exists at all |
| Housebets withdrawal | realcasinosbonus.com | Reviews | Sentiment split (instant vs delays/KYC); no official withdrawals/help page ranks |
| is Housebets legit | cryptotips.com (licence FAQ) | Reviews only | No official trust/licence page ranks for the most trust-sensitive query |
| Housebets app | cryptotips.com (no native app, PWA) | Reviews + lookalikes | Three lookalikes tell users to sideload an APK / get it from the App Store |

### 3.3 Affiliates define the bonus — and invent it

"Housebets bonus" and "Housebets promo code" surface at least **six different promo codes** (MAX, HOUSE100, socgid, HB150, SPINS20, CASINOMAX) and **three different welcome bonuses** (100% to $1,000 / 100% to $500 + 100 spins / 100% to £200 + 50 spins). Against that, two hands-on reviewers (Casino Clinic, CryptoCasinoReviews — both claiming to have checked the live site in Oct–Nov 2026) say **no deposit match exists on any house page**; the real offers are Duel Mode rakeback and the Wave 2 on-chain bonus (up to $25,000, 1× wagering). The official site has no ranking bonus/promotions page to settle this, so affiliates' invented bonuses define the query — and users deposit against false expectations, which is exactly the dispute pattern in the complaints (§3.5).

### 3.4 Lookalikes own the transactional queries — a user-safety problem

"Housebets login" returned 8/8 lookalike domains (housebets.me.uk, house-bets.bet, housebets.uk.com, housebetsapp.com, housebets-bonus.com, housebets-uk.com, housbets.org, getinspired.media), several instructing users to log in via "the official site or a working mirror link". "Housebets app" has three lookalikes telling users to download an APK / sideload from unknown sources or get it from the App Store — while credible reviewers agree **no native app exists** (browser/PWA only). That is a concrete fake-APK risk that a ranking official "no app — mobile web/PWA only" page and a login/help page would neutralise. The lookalike swarm also publishes its own "responsible gambling" pages and country lists that **contradict Housebets' own Terms** (e.g. housebets.co says Germany/Poland/Finland accepted; the Terms say Germany/Poland prohibited).

### 3.5 Trust is decided by third parties

"Is Housebets legit" is answered only by reviews. The consensus is "legit, Curaçao-licensed" (OGL/2024/431/0231, verified on the register per two reviewers) — but the caveats travel with it: a shared licence across ~13 domains, thin payout history, KYC triggered after a winning session, a Portuguese player case (~9,228 USDC retained after account closure, cited by two reviewers), polarised Trustpilot (3.0–3.2/5 in most snapshots; one source claims 4.4 — snapshots conflict), no-2FA criticism (WagerDB security 3.0), and a 31 Oct 2026 Trustpilot complaint about a VIP bonus not paid as promised in writing. Positives exist (Casino Clinic's $5,500 USDT withdrawal in 1 minute, Casino Guru Safety Index 7.7/10, AskGamblers sportsbook score 7.2) but no official trust/licence/FAQ page ranks to present them. Two review sites (Gamblineers, BonusManiac) even carry a **false "permanently closed Oct 7, 2026" claim** — the site is live, serving Nov 2026 content; the label most plausibly refers to an ended affiliate partnership, mislabelled as a closure. It is a live brand-search liability.

Beyond Google: the official X account @housebets exists (founder @p0rchy is the public face), but no X result appeared in any brand-query result set. No official Housebets YouTube channel was found; YouTube search for the brand is dominated by a **name collision — "Housebets" is also an Australian CS2 esports team** — and the top casino video is a third-party airdrop video pushing a tinyurl referral link.

### 3.6 The win-back plan

| # | Action | Target query(s) | Why it wins |
|---|---|---|---|
| B1 | Official brand hub on housebets.com: what Housebets is, licence, games, sportsbook, rakeback — crawlable copy that can rank for the naked brand term | "Housebets", "Housebets casino" | The single biggest gap: nothing official ranks |
| B2 | Official Promotions / bonus-truth page: the real offers (Duel Mode, Wave 2), explicitly "no deposit match, no promo code" where true | "Housebets bonus", "Housebets promo code" | Displaces six invented codes and three invented bonuses |
| B3 | Official login/help + "no app" pages: how to log in, official domain only, mobile web/PWA, "we have no APK, never sideload" | "Housebets login", "Housebets app" | Neutralises the phishing / fake-APK lookalikes |
| B4 | Official licence/trust page: licence number + register link, operator, ADR route (Resolvo), payout evidence, dispute process | "is Housebets legit" | Gives the trust query an official voice with verifiable facts |
| B5 | Public restricted-countries page (see A5) + a withdrawals page (measured payout times, KYC triggers stated plainly) | "Housebets withdrawal", country queries | Ends contradictory third-party lists; answers the payout question with evidence |
| B6 | Review-footprint work: encourage genuine player reviews on Trustpilot/AskGamblers/WagerDB; respond to complaints publicly (the team already replies on Trustpilot — keep doing it, faster) | "Housebets review" | More tracked reviews raises listicle inclusion and dilutes the negative tail |
| B7 | Brand protection: challenge the "permanently closed" pages for correction; monitor lookalike domains; enforce Affiliate Terms against branded-keyword bidding and impersonation | All brand queries | Removes false and impersonating results at the source |
| B8 | Own the name on video/social: an official YouTube channel (launch video, House Games demos, Hubie) and consistent X presence, so the CS2 team and affiliate videos stop defining the brand on video surfaces | "Housebets" (video), YouTube | YouTube is cited in 55% of Google AI Overviews (Rankera) — video presence is also an AI-search asset (§6) |

---

## 4. Pages (15 pts)

The page plan below is the build list. Each page states its job, target query, and content spec. Pages marked **NEW** do not exist (or do not rank) today; **FIX** means an existing page needs work.

### 4.1 New pages to build (priority order)

| # | Page (suggested URL) | Target query / cluster | Content spec |
|---|---|---|---|
| P1 | `/what-is-housebets` (NEW) | "Housebets", "what is Housebets" (brand + AI) | One canonical brand-definition page: operator, licence number + register link, launch year, crypto-only, game count, sportsbook, rakeback, House Games. Short labelled facts in a table — the format AI answers lift. |
| P2 | `/promotions/on-chain-bonus` (NEW) | "on-chain casino bonus" (Cluster 1 — OWN) | How the wallet scan works (read-only, up to 5 wallets), Wave 2 terms ($25k cap, $1 unlock, 1× wagering), eligibility, worked example. State plainly that "on-chain" means history-based, not on-chain wagering. |
| P3 | `/promotions/duel-mode-rakeback` (NEW) | "crypto casino 50% rakeback" (Cluster 2 — OWN) | The formula (wager × house edge × 50%), worked $ maths, the honest trade-offs (half-speed XP, held share, paused rewards), comparison table vs Stake/Shuffle/Rainbet rakeback. |
| P4 | `/house-games` (FIX — rebuild as hub) | "provably fair casino", "crypto casino originals" (Cluster 3) | All 11 Originals listed with RTP (mostly ~99%), rules, and the provably-fair method per game; link to `/provably-fair`. Must render crawlable content (today it renders almost nothing to a text crawler). |
| P5 | `/guides/provably-fair-verification` (NEW) | "provably fair casino" (Cluster 3) | Step-by-step verification guide with a worked, verifiable bet (server seed / client seed / nonce). The one head-adjacent SERP where guides beat listicles. |
| P6 | `/is-housebets-legit` (NEW) | "is Housebets legit" (brand trust) | Licence + register link, operator, ADR (Resolvo) + CGA route, payout evidence (measured times), the KYC rule stated plainly, dispute process. No marketing fluff — verifiable facts only. |
| P7 | `/promotions` (FIX) | "Housebets bonus", "Housebets promo code" | Currently 5 promo cards, no T&Cs or detail copy. Add: the true offer set, an explicit "no deposit match / no promo code" statement where true, and per-offer terms. |
| P8 | `/help/login` + `/mobile` (NEW, on main domain or help subdomain with strong internal links) | "Housebets login", "Housebets app" | Official login steps, official domain only, "we have no APK — never sideload", mobile web/PWA instructions. Directly counters the lookalike swarm. |
| P9 | `/restricted-countries` (NEW) | Country + brand queries | The Terms §5 list as a public page (see A5). Ends contradictory third-party lists. |
| P10 | `/payments/withdrawals` (NEW) | "Housebets withdrawal" | Measured payout times (publish timed withdrawals, n>1), minimums/fees per coin, KYC triggers stated plainly, manual-audit disclosure. |
| P11 | `/usdt-casino` (NEW) | "USDT casino" (Cluster 5) | Networks supported (TRC-20/ERC-20/BEP-20 — verify), minimums, fees, measured payout times. Small, methodology-led SERP. |
| P12 | `/guides/no-deposit-bonus-myth` (NEW) | "crypto casino no deposit bonus" (Cluster 8, guide angle) | Honest myth-busting: genuine no-deposit offers are rare; what free value actually looks like (rakeback, races, on-chain bonus). Earns links without promising what doesn't exist. |

### 4.2 Existing pages to fix

| Page | Fix |
|---|---|
| `/` (homepage) | Add real indexable copy (A3): what Housebets is, licence, games, sportsbook, rakeback — in crawlable text. Keep the promo hero; stop being a hero-only page to crawlers. |
| `/sports` | Resolve the geo-block for Googlebot (A1) — or accept it is not an SEO product and stop spending search effort on sports content. Do not leave it as a dead end for crawlers. |
| `/blog` | Resume weekly publishing (stale since 3 Sep 2026); fix boilerplate descriptions; use it for the guides in §4.1 (P5, P12) and for "House Games" launch notes. |
| `/casino` | Strongest page; add descriptive copy per game/provider (today mostly names as links — thin-content risk at scale). Add per-game RTP where verified. |
| `/contests` | Add to a sitemap (A10); the SEO contest itself is a ranking asset — the page already ranks #1 for the contest-named query. |
| `/legal/*` (16 pages × 19 locales) | Verify hreflang + canonicals per locale (A9); add the RG support-organisation names, RNG lab names and 2FA status where they belong (A6). |
| `help.housebets.com` | Link it prominently from the main domain (nav + footer) so its ~129 articles pass value to the main domain; mirror the highest-demand help articles as on-domain pages (login, withdrawals, KYC). |

---

## 5. First 90 days (15 pts)

### Days 1–30 — stop the bleeding

| Week | Work | Done when |
|---|---|---|
| 1 | **Crawl access check.** Server logs / Search Console: does Googlebot get the `/sports` geo-block? Allow-list Googlebot or ship a crawlable sports-content path. Parallel: verify homepage rendering in Search Console (fetch-as-Google). | Written answer: blocked or not; fix shipped or decision recorded |
| 1 | **Mirror decision.** Establish whether housebets.win is official/staging/third-party; then canonicalise / noindex / redirect it to .com (or formally claim and differentiate it). | .win no longer serves conflicting live numbers |
| 1–2 | **Trust pages.** Publish RG support-organisation names, RNG lab names/certificates, real 2FA status; reconcile "no KYC" vs KYC-at-cashout in one public place; publish the restricted-countries page (P9). | The exact gaps reviewers flag are closed on-site |
| 2–3 | **Brand pages, part 1.** Ship P1 (what-is), P6 (legit/trust), P7 (promotions truth page), P8 (login + no-app). | Four ranking pages live for the worst brand queries |
| 3–4 | **Review footprint.** Respond to open Trustpilot/AskGamblers complaints (already done for some — faster, publicly); invite genuine player reviews; challenge the two "permanently closed" pages for correction. | Complaint response time down; correction requests filed |
| 4 | **AI-search baseline.** Re-run the 6 questions on all four engines (post-quota-reset) and log verbatim answers in `ai-answers.csv`. | A dated, honest AI baseline exists |

### Days 31–60 — build the ownable pages

| Week | Work | Done when |
|---|---|---|
| 5–6 | **Ownable content.** Ship P2 (on-chain bonus), P3 (Duel Mode rakeback), P5 (provably-fair guide), P4 (House Games hub rebuild), P11 (USDT page). | Five pages live for Clusters 1, 2, 3, 5 |
| 6–7 | **Affiliate inclusion.** Outreach to the listicle owners that dominate Clusters 4 and 7 (bitcoin.com, fairgambling.com, bestbitcoincasino.com, thecasinowizard.com, metbonus.com): factual correction pack + review access, aimed at inclusion in "best crypto casino" and no-KYC lists. | Housebets listed (or a dated "asked, declined" log) |
| 7–8 | **Blog relaunch + video.** Resume weekly blog (guides first: P5, P12); launch the official YouTube channel (House Games demos, "what is Housebets", Hubie). | Blog current; channel live with ≥4 videos |
| 8 | **Locales.** Verify hreflang + canonicals per locale; fix or remove locales for prohibited jurisdictions; refresh `/id/` properly or drop it. | Hreflang verified; no locale for a banned country ships thin machine translation |

### Days 61–90 — measure, iterate, compound

| Week | Work | Done when |
|---|---|---|
| 9–10 | **Measure what moved.** Search Console: indexed pages, impressions/clicks for brand + Cluster 1/2/3 queries, `/sports` crawl stats. Re-run the 6 AI questions; log deltas in `ai-answers.csv`. | First measurement report with before/after |
| 10–11 | **Iterate the winners.** Expand whichever of P2/P3/P5 moved first (second guide, comparison tables, translated versions for the locales that convert). Fix whichever brand page still doesn't rank. | One expansion per winning page |
| 11–12 | **Second inclusion push + review drive.** Second outreach round with the new pages as proof; second review drive. | Inclusion count and review count updated |
| 12 | **90-day report.** What ranked, what didn't, what the next 90 days should be. Honest numbers only — no invented traffic. | Report delivered to the Housebets team |

**What "win" looks like at day 90 (honest version):** Googlebot can crawl the sportsbook; .win is consolidated; housebets.com ranks for its own brand term and for "Housebets review / bonus / legit" with official pages; the on-chain-bonus and 50%-rakeback pages exist and are the citable source for those queries; the AI re-test shows Housebets mentioned (correctly) where it was absent. Rankings take time and no traffic numbers are promised here — the 90-day deliverable is the pages, the fixes, and the measurement, not a rank guarantee.

---

## 6. AI search (15 pts)

### 5.1 What was tested — and what was actually obtained

Six questions (4 English, 2 Indonesian) were defined for four engines — ChatGPT, Perplexity, Gemini, Google AI Overviews — one row per engine×question in `ai-answers.csv` (24 rows, date 2026-11-12). The questions:

1. EN — "What is the best crypto casino?"
2. EN — "What is Housebets?"
3. EN — "Is Housebets legit and safe?"
4. EN — "What are Housebets house games?"
5. ID — "Apa itu Housebets?"
6. ID — "Kasino kripto terbaik apa?"

**Honest result: no live AI answer about Housebets was obtained from any engine on 12 Nov 2026.** That is itself a finding, and it is recorded in the CSV rather than papered over. **Update 13 Nov 2026:** Gemini has since answered all 6 questions verbatim (see the Gemini row below and `ai-answers.csv`, date 2026-11-13) — the only engine to give live answers so far.

| Engine | Obtained? | What happened |
|---|---|---|
| Perplexity | No | perplexity.ai search pages are JavaScript-rendered; the text fetcher returned no readable text. Needs a live browser or the Perplexity API. |
| Google AI Overviews | No Overview observed | Across 5 searches ("best crypto casino", "what is Housebets", "is Housebets legit", etc.) no AI Overview block appeared in the returned results — ordinary organic results only. No Overview text or citation list could be quoted. |
| ChatGPT | No | No public route exists. Only third-party reports of what ChatGPT said (see §6.2). Not invented. |
| Gemini | **Yes — obtained 13 Nov 2026** | All 6 questions answered verbatim on 13 Nov 2026 (quota reset ~16:00 WITA; the model was overloaded, HTTP 503, at 16:06 and 16:17, then answered at 19:50 WITA). Housebets is described in 4 of the 6 answers (mostly correctly — generic Curaçao licence, no licence number, launch year or game count) and is absent from both 'best crypto casino' lists (Stake, BC.Game, BitStarz, Cloudbet named instead). Gemini cited no sources. Full answers in `ai-answers.csv` (date 2026-11-13). |

**Re-test method (for the judges or the Housebets team — 15 minutes):** ask each question verbatim in a fresh chat on ChatGPT / Perplexity / Gemini, and check the live Google SERP for an Overview; record the full answer text plus every source cited, and the date. Do not paraphrase. Repeat each question in a second fresh chat to check stability.

### 5.2 Background: what the engines do in this niche (third-party evidence, not live answers)

- **Google withholds AI Overviews for casino queries.** Rankera (Oct 2026, 34,000 searches, 243,714 citations): only **20% of online-casino searches** got an AI Overview, and only **1% of core casino questions** — casino is the one industry where Google holds Overviews back. By contrast, **94% of crypto searches** got one. When an Overview does appear, 72% of #1-ranked pages were cited vs 6% of pages ranked #16–20; 92% of Overviews cite at least one page outside the top 20; YouTube appears in 55% of Overviews. Most-cited sources in online casino are reference/government sources, not casino review sites.
- **Engines disagree with each other.** 5WPR's Crypto AI Visibility Index 2.0 (21 Oct 2026, 288 AI answers across ChatGPT, Claude, Gemini, Perplexity + 70 Google AI Overviews): engines rank the same brands differently (ChatGPT ranked Binance first while Google AI Overviews ranked Coinbase first). No single engine's answer is "the" answer.
- **Citations are rare.** DGM News (11 Nov 2026) ran "best crypto casino" and 9 other phrasings through AI assistants: the answer depends heavily on phrasing, location is the sharpest filter, and only ~23% of brand mentions carry a citation.
- **What ChatGPT reportedly says (third-party, stale):** CasinoWow (Nov 2024) asked ChatGPT "What is the best crypto casino now?" and reported ChatGPT named **BitStarz**, also recommending BC.Game, Roobet, Gamdom and Stake — and warned ChatGPT's casino information "is not always relevant or correct". That is a 2024 report, not a live answer, and it is not presented as one.
- **The pool the engines draw from:** Housebets appears in **none** of the "best crypto casino" top lists surfaced on 12 Nov 2026. The domains that dominate those lists — and therefore the citation pool — are fairgambling.com, moviemaker.com, actionnetwork.com, casinobonuswise.com, casinobee.com, casino.guide, bitcoin.com and bestbitcoincasino.com. The dedicated Housebets review domains (cryptocasinoreviews.io, realcasinosbonus.com, casino.clinic, fairgambling.com, wagerdb.com, cryptotips.com, house-bets.net, eu-housebets.com) are the citation pool for Housebets-specific questions.

### 5.3 Baseline facts — what a correct AI answer should say (and where sources contradict each other)

These facts come from organic search results read on 12 Nov 2026, not from any AI engine. They are the yardstick for judging future AI answers:

- **Operator / licence:** Bridge Technologies B.V. (Willemstad, Curaçao); CGA licence **OGL/2024/431/0231**. Registered address: Dr. M.J. Hugenholtzweg 25, Willemstad, Curaçao.
- **What it is:** crypto-only casino + sportsbook, launched 2024; ~3,500–4,100 games (sources disagree: 3,819 / ~3,900 / 4,111); sportsbook on the same balance.
- **House Games:** 20 titles — **11 Housebets Originals** + 9 Tequity titles; most at **~99% RTP** (Blackjack 99.43% optimal, European roulette 97.30%); provably fair via server seed + client seed + nonce; method at housebets.com/provably-fair.
- **Rewards:** no standard welcome bonus; 10% instant rakeback + 10% daily rakeback, Duel Mode to 50%; House Keys feed a future **$HBTS token — not live**, and explicitly outside the licence.
- **KYC:** contradictory across sources — "no KYC, ID never required" vs KYC trigger at ~€2,000 lifetime vs KYC after winning sessions / at cashout. The truth is conditional; any flat claim either way is wrong.
- **2FA:** multiple independent reviews say there is **no 2FA**; one affiliate-style site claims it exists. Unresolved without an account.
- **Trustpilot:** 3.2/5 in most snapshots vs 4.4 claimed by one source — snapshot-dependent.
- **Game count:** any single precise number (3,500–4,111) is source-dependent, not canonical. "9 in-house games" was true at launch and is now stale (20 titles).

### 5.4 What AI answers will get wrong — and how Housebets becomes the source they cite

**Expected errors** (from the contradictions above): a single game count presented as fact; "9 House Games"; flat "no KYC" or flat "KYC required"; 2FA claimed to exist; $HBTS described as a live, trading token; the .win mirror cited instead of .com; "founded 2023" (one affiliate site) vs 2024 (consensus).

**The fix — canonical, citable facts:**
1. **One page per fact cluster, in tables** (P1, P4, P6 in §4.1): "What is Housebets" (operator, licence, launch year, crypto-only, game count); a House Games index listing all Originals with RTP and the fairness method; a licence/safety page resolving the KYC contradictions in one place. Tables and short labelled facts are what AI answers lift.
2. **Third-party corroboration matters as much as housebets.com.** The engines cite review domains heavily in this niche. Getting Housebets accurately described on the already-cited review domains (cryptocasinoreviews.io, realcasinosbonus.com, casino.clinic, fairgambling.com) is likely as valuable as on-site pages.
3. **Video.** YouTube is cited in 55% of Google AI Overviews (Rankera). An official channel with House Games demos and a "what is Housebets" explainer is an AI-search asset, not just a brand asset.
4. **Re-test loop.** Re-run the 6 questions monthly on all four engines; log what changes in `ai-answers.csv` (it is designed to accumulate rows by date). A wrong answer that persists is a content brief: the fix column of each row names the page that should answer it.

---

## 7. About you

- **Name:** Ali Ulin
- **LinkedIn:** https://www.linkedin.com/in/ali-ulin/ (headline "Daepyonim at Tbk", Kecamatan Pelaihari, South Kalimantan, Indonesia)
- **CV:** none — LinkedIn provided, which satisfies the contest's "CV or LinkedIn link" requirement.
- **Track record (stated honestly):** I am a builder, not an SEO-agency veteran, and I claim no SEO client history. What I have built and submitted, both on 12 November 2026: the **Housebets sportsbook prototype** — a 5-page clickable prototype (Sports home, Live, Football, Match page, Bet slip + My bets), submitted to Housebets Contest Labs the same day (live at https://kembangpasir-dot.github.io/housebets-sportsbook/); and **PayPilot** — an AI chat agent that turns plain-language requests into PayPal invoices, submitted to the PayPal AI Hackathon on Devpost (live at https://devpost.com/software/paypilot-hj2iep). The SEO work in this submission is the evidence for the monthly-contract conversation: it was researched from public sources in one day, it names what could not be verified, and it is built to be executed, not just admired.

---

## Appendix — methods, limits & sources

**Methods.** Text fetches of housebets.com pages (homepage, contests, casino, sports, promotions, blog, house-games, legal pages, provably-fair, about, help centre) and housebets.win; robots.txt and sitemap index + sub-sitemaps; web searches for 10 brand queries and 13 money keywords (single-day snapshot, 12 Nov 2026); attempted AI-engine access (Perplexity text fetch, Google search for AI Overview blocks, Gemini API test call). Research notes are kept in the package's `hidden_files/` (site audit, brand search, keyword map, AI search, Gemini quota note).

**What could not be verified (do not treat as findings).** Googlebot's specific treatment of the `/sports` geo-block; indexed-page count (`site:` returned no results — a tool artefact); meta descriptions, canonicals, hreflang, structured data, HTTP status codes, Core Web Vitals, rankings beyond the returned results per query, traffic, search volumes, keyword difficulty; CGA register status (reviewers claim verified Nov 2026 — not checked here); whether housebets.com is on Indonesia's TrustPositif blocklist; whether housebets.win is official/staging/third-party; footer contents; live-account facts (RG tools in settings, 2FA, KYC thresholds, payout speed); contents of the game-catalog and promotions sub-sitemaps; any live AI answer from ChatGPT, Perplexity or Google AI Overviews (see §6.1); Gemini answers were obtained on 13 Nov 2026 (see §6.1).

**Key sources (all accessed 12 Nov 2026).** housebets.com (homepage, /contests, /contests/seo-growth, /casino, /sports, /promotions, /blog, /house-games, /legal/*, /provably-fair, /about-us/why-housebets, /robots.txt, /sitemap.xml + sub-sitemaps); help.housebets.com; housebets.win (homepage, /contests); cryptocasinoreviews.io/housebets/; casino.clinic/casinos/housebets/; realcasinosbonus.com/casinos/housebets/; cryptotips.com/housebets/; wagerdb.com/casinos/housebets; house-bets.net; eu-housebets.com; housebetcasino.com; fairgambling.com (best crypto casino 2026; Housebets Originals launch news); bitcoin.com/gambling/casino/; bestbitcoincasino.com; dappcrypto.org (Wave 2 on-chain bonus guide); rankera.ai/blog/how-google-ai-overviews-choose-sources/; dgmnews.com/we-asked-ai-best-online-casino/; 5wpr.com/research/crypto-ai-visibility-index-2026/.

*End of report — Win Google for Housebets, 12 November 2026.*
