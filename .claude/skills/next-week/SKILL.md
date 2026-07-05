---
name: next-week
description: Weekly action planner and scaling engine for the reselling business. Turns the latest /weekly-review results into next week's plan — goals for the owner, tasks for Claude, one process improvement — and drives the scaling ladder to raise average net-per-sale. Run every Sunday after /weekly-review, or standalone.
---

# Skill: /next-week — Weekly Action Planner & Scaling Engine

## Purpose
Turns the latest `/weekly-review` results into a concrete plan for the coming week: goals for the OWNER, tasks for CLAUDE, and one process improvement. Also drives the **scaling ladder** — deliberately raising average net-per-sale over time so growth comes from bigger flips, not just more hours. Keeps the business compounding instead of drifting.

## Trigger
Run every Sunday, immediately after `/weekly-review`. Can also run standalone (it will call /weekly-review logic on `inventory.csv` first if no fresh review exists).

## Inputs
- `inventory.csv` (single source of truth)
- Last week's `/next-week` plan (to score follow-through)
- Current phase gate from RESELLINGGAMEPLAN_v2.md (Phase 1/2/3 targets)

## Output format

### 1. Scoreboard (5 lines max)
- Net profit this week vs last week
- Sell-through rate + avg days-to-sale by category
- Working capital + Profit First pots (pay-yourself, tax)
- Last week's plan: done / partial / missed (with one-line reasons)
- Distance to current phase gate

### 2. YOUR goals for next week (3–5, each specific + measurable)
Examples of the required style:
- "2 sourcing runs: Tues clearance (budget $40), Sat book sale (budget $25)"
- "List 12 items by Wednesday; relist 3 stale items with 15% markdown"
- "Ship all sales within 24h (streak: X weeks)"
Rules: goals must fit 10–20 hrs/week; never exceed available capital minus reserve; prioritize the category with the best days-to-sale last month.

### 3. CLAUDE's tasks for next week (3–5)
Examples:
- "Run /product-scout across all lanes; deliver Tuesday's buy-list with max prices + any in-store pickups (item/store/price)"
- "Draft /make-listing for everything arriving this week, same day"
- "Listing diagnostics: flag low-impression listings (weak titles → rewrite) and viewed-but-unsold listings (price/photo fix)"
- "Weekly listing-research task: check one topic (Cassini updates, category trends, top-competitor title patterns) and update the Listing Optimization Playbook if warranted"

### 4. One improvement (exactly one)
A single system/process upgrade, E-Myth style. Examples: "photograph in batches of 10 with a fixed station", "create a saved eBay search for retired LEGO under $20", "add a days-listed column to inventory.csv". Never more than one — improvements compound weekly.

### 5. Scaling ladder (every week)
Report current **average net per sale** and current tier, then recommend the next move up:
- **Tier 1 — $10–15 avg net:** books, consumables, small toys. Goal: feedback + capital.
- **Tier 2 — $25 avg net:** retired LEGO, sealed board games, textbook season plays, bundles/lots (selling 5 books as one lot = one shipment, higher ticket).
- **Tier 3 — $50 avg net:** sealed collectibles, higher-end clearance (small appliances, tools), ⚠️ RISK electronics from trusted sources only (new/open-box/trade-in — never untested stranger buys; $50 net minimum; ≤20% of capital per item).
- **Tier 4 — $100+ avg net:** manifested liquidation lots (<$150 test lots, local pickup, manifest verified), premium ⚠️ RISK electronics, rare books/first editions.
**Promotion rule:** recommend moving a portion of buying budget up one tier only when the current tier shows ≥50% sell-through and capital ≥ 3× the typical buy cost of the next tier. Never abandon lower tiers entirely — they keep feedback and cash flow alive.
**Every electronics recommendation at any tier carries the ⚠️ RISK label and its checklist.**

### 6. Flags (only if triggered)
- Category with sell-through <30% for 2 weeks → recommend pausing buys there
- Capital concentration >20% in one item → warn
- Phase gate reached → announce and switch targets
- 2 consecutive months ≥ $4k net → the quit-the-warehouse rule is satisfied

## Tone
Direct, numbers-first, no filler. If a week was bad, say why and what changes — never just encouragement.
