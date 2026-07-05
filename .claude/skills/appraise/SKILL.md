---
name: appraise
description: Instant BUY/PASS verdict with a max offer, from live eBay sold comps and full fee math. Usage: /appraise <item> <price> <condition> (e.g. /appraise "LEGO 75192 sealed" 45 new). Use in-store on clearance finds and at book sales — answer in under a minute of reading.
---

# Skill: /appraise — BUY/PASS Decision Engine

## Purpose
The owner is standing in a store aisle or at a book-sale table with an item in hand. This skill gives a fast, unambiguous verdict: **BUY** (with a max price) or **PASS** (with the one-line reason). No essays — the owner may have 30 seconds.

## Usage
`/appraise <item> <price> <condition>`
- `<item>`: name/model/ISBN/UPC — as specific as possible
- `<price>`: the asking/shelf price
- `<condition>`: `new`, `sealed`, `open-box`, `used-complete`, `used-incomplete`

## Method
1. **Pull sold comps** — eBay sold listings, last 90 days, matching condition. Use the median of real sales, not the best one and not asking prices.
2. **Count velocity** — roughly how many sold per month at that price. <3/month = slow; say so.
3. **Fee math (always shown):**
   - eBay: sale price × ~13.25% + $0.30 per order
   - Shipping: estimate by category (media mail for books ≈ $4–5; poly-mailer consumables ≈ $4–6; boxed toys/games ≈ $6–12) unless charging buyer-paid shipping
   - Net = median sold − fees − shipping − cost
4. **Apply the buy rules:**
   - Expected sale ≥ **3× cost** (items under $10 cost) or ≥ **2.5×** (above $10)
   - Minimum net: **$8** books/media · **$15** retail arbitrage · **$50** electronics
   - Item cost ≤ **20% of working capital**
5. **Verdict.** If PASS at the asking price but viable lower, give the exact max offer that makes it a BUY.

## Condition checks before any BUY stands
- **Books:** no water damage, no missing pages, no heavy highlighting (light highlighting OK for textbooks — disclose it). Check edition matters (textbooks: edition is everything).
- **Board games / toys:** sealed preferred. Used games: complete parts or PASS (verify against a parts list).
- **Consumables:** unexpired, unopened, packaging intact.
- **Electronics (⚠️ RISK — always):**
  - New/sealed or trusted-source (store clearance, retailer open-box with receipt) preferred.
  - If used from an individual: IMEI/serial check, activation-lock check, and power-on test are **mandatory — no exceptions, or PASS.**
  - $50 minimum net and ≤20% of capital, regardless of how good the deal looks.

## Output format (short — this is read on a phone in an aisle)
```
VERDICT: BUY (max $X) — or — PASS (reason)
Comps: sold $X–$Y, median $Z, ~N sales/mo
Math: $Z sale − $F fees − $S ship − $C cost = $N net (M.M× multiple)
Condition flags: <anything to check before paying / disclose when listing>
⚠️ RISK: <electronics checklist items, if applicable>
```

## Tone
Decisive. Never "it depends" — if information is missing, state the one thing to check and give the verdict conditional on it ("BUY at ≤$20 IF complete parts count verified").
