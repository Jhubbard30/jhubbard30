---
name: product-scout
description: Sourcing engine for the reselling business. Produces a ranked buy-list from live online data — mispriced eBay listings, FB Marketplace shipped deals, online clearance, book arbitrage, bundle/lot plays — enforcing the 3×/2.5× buy rule. Usage: /product-scout <category> <budget> (e.g. /product-scout books 60). Run before every sourcing session.
---

# Skill: /product-scout — Ranked Buy-List Generator

## Purpose
The system does the finding; the owner executes the list. This skill researches live prices and deals online and delivers a ranked buy-list that already clears the buy rules. The owner never wanders stores hunting — **in-store pickups appear on the list ONLY as a specific item + specific store + max price.**

## Usage
`/product-scout <category> <budget>`
- `<category>`: one of `books`, `consumables`, `toys-games`, `electronics` (⚠️ RISK lane), or `all`
- `<budget>`: max total spend for this list, in dollars. Never exceed working capital minus the reserve (check `inventory.csv` and the gameplan's capital split).

## Where to look (online-first, in this order)
1. **Mispriced eBay listings** — search the category for listings with bad titles, few/poor photos, misspellings, or wrong categories that are priced under sold comps. These are buy-to-relist plays: the profit is in re-listing them optimized.
2. **Facebook Marketplace shipped deals** — underpriced items with shipping enabled (no meetup needed).
3. **Online clearance** — Walmart.com, Target.com, Woot, Ollie's online, and brand outlet pages. Cross-check every clearance price against eBay sold comps before it goes on the list.
4. **Book arbitrage** — price gaps between buyback/marketplace prices (BookScouter-style) and eBay/Amazon sold prices. Textbooks (science/medical/nursing) first; August–September and January are spike seasons.
5. **Bundle/lot opportunities** — cheap lots that can be split, or singles that can be bundled up later.
6. **In-store leads (only when specific)** — a known clearance run (e.g. Target toy clearance in January) may generate an entry, but it must name the item, the store, and the max price. "Go check Walmart clearance" is never a valid list entry.

## Buy rules (enforced — nothing goes on the list that fails these)
- Expected sale price ≥ **3× total cost** for items under $10 cost; ≥ **2.5×** above that. Cost includes shipping-to-you and taxes.
- Minimum expected net: **$8** per book/media flip, **$15** per retail-arbitrage flip, **$50** per electronics flip.
- Never recommend putting more than **20% of working capital** into a single item.
- Comps must be **sold** listings (last 90 days), not asking prices. Note sell-through: if fewer than ~3 sales/month at the target price, flag it as slow.
- Finding nothing that clears the rules is a valid outcome. Say so plainly — a short list beats a padded one.

## Electronics (⚠️ RISK lane)
Every electronics entry carries a **⚠️ RISK** label and:
- Prefer new/sealed or trusted-source (store clearance, retailer open-box, trade-in programs). No stranger-meetup used electronics on a scout list, ever.
- $50 minimum expected net; ≤20% of working capital.
- Note in the entry what must be verified on arrival (serial/IMEI, activation lock, power-on test) if not factory sealed.

## Output format
A ranked table, best deal first:

| # | Item | Source (link or store) | Buy price (max) | Expected sale | Expected net | Multiple | Sell-through | Notes |

Followed by:
- **Budget check:** total of recommended buys vs `<budget>`, and vs working capital minus reserve.
- **In-store pickups** (if any): item / store / max price / aisle-section hint.
- **Passes worth explaining:** 2–3 near-misses and why they failed the rules (trains the owner's eye).

## Tone
Numbers-first. Every recommendation must show the math (cost → expected sale → fees → net → multiple). No "might be worth a look" entries — everything on the list is a BUY at or below the stated max price.
