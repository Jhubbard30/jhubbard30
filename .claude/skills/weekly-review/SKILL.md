---
name: weekly-review
description: Sunday business review for the reselling operation. Reads inventory.csv and reports P&L, sell-through and days-to-sale by category, aging inventory with markdown suggestions, Profit First splits, listing diagnostics, and progress against the current phase gate. Run every Sunday, before /next-week.
---

# Skill: /weekly-review — Weekly P&L and Diagnostics

## Purpose
The only forecast that matters is real sold data. This skill reads `inventory.csv` and tells the owner exactly how the business did, what's stuck, and where the numbers stand against the current phase gate. Its output is the direct input to `/next-week`.

## Trigger
Every Sunday. Always runs before `/next-week`.

## Input
`inventory.csv` — columns: date_bought, source, item, category, cost, listed_price, platform, sold_date, sold_price, fees, shipping, net_profit. If rows are missing data needed for the math (e.g. sold rows without fees), flag them for cleanup rather than guessing.

## Report sections

### 1. P&L (this week + running)
- Sales count, gross revenue, fees, shipping, COGS, **net profit** — this week and month-to-date.
- Net vs last week, with the one-line reason for the change (more sales? bigger tickets? a slow category?).

### 2. Sell-through & velocity by category
For each category (books/media, consumables, toys-games, electronics ⚠️ RISK):
- Sell-through % (sold ÷ listed, trailing 30 days)
- Average days-to-sale
- Average net per sale
Rank categories by days-to-sale — **sell-through beats margin**: a 40% margin that sells in 5 days beats a 70% margin that sits 90 days. Say explicitly which category next week's buying budget should favor.

### 3. Aging inventory
- List every unsold item ≥ **21 days** listed: item, days listed, cost, current price.
- For each: a markdown suggestion (start ~15%), a bundle/lot suggestion (5 slow $5 items → one $25 lot), or "hold" with a stated reason (e.g. textbook waiting for August spike).

### 4. Listing diagnostics (the improvement loop)
Using whatever impression/view data the owner reports (ask if not provided):
- **Low impressions** → weak title/keywords → rewrite (queue for `/make-listing` redo)
- **Views but no sales** → price/photos/trust problem → adjust price or reshoot
- **Sold fast (<3 days)** → priced too low → raise price on the next one of that item

### 5. Profit First splits
From this week's net sales: **10% → pay-yourself pot, 15% → tax pot**, remainder → reinvestment. Report all three pot balances (running totals) and current working capital. Confirm the reserve is intact ($30 in Phase 1, growing to $250 by Phase 3).

### 6. Phase gate progress
State the current phase and distance to its gate:
- **Phase 1 → 2:** capital doubled ($200 → $400) AND 10+ eBay feedback
- **Phase 2 → 3:** ~$1,000 working capital AND a full month ≥ $500 net
- **Phase 3 exit (quit rule):** 2 consecutive months ≥ $4,000 net profit
Announce loudly when a gate is crossed.

### 7. Warnings (only if triggered)
- Any single item > 20% of working capital
- Reserve touched
- Category sell-through < 30% for 2 straight weeks
- eBay account limits nearly full (item or dollar cap) — plan the overflow to FB

## Handoff
End with one line: "Ready for /next-week" — that skill turns this review into the coming week's plan.

## Tone
Numbers-first, honest. A bad week gets a diagnosis, not a pep talk. Every number that changed materially gets a one-line why.
