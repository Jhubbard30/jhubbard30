---
name: make-listing
description: Generates a copy-paste-ready, keyword-optimized eBay listing (title, item specifics, description, pricing, shipping) plus a Facebook Marketplace version, following the Listing Optimization Playbook. Auto-detects electronics and prepends the ⚠️ RISK checklist. Usage: /make-listing <item details, cost, condition>.
---

# Skill: /make-listing — Listing Generator

## Purpose
Every item gets listed within 24h of arrival, and every listing follows the Listing Optimization Playbook from RESELLINGGAMEPLAN_v2.md. This skill outputs both platform versions ready to paste — no drafting from scratch, no forgotten fields.

## Usage
`/make-listing <item details>` — include what it is, condition, what's included, cost paid, and any flaws. If key details are missing (edition, model number, completeness), ask for them before generating — a listing with guessed specifics gets returns.

## Step 0 — Electronics detection (runs first, automatically)
If the item is electronics (anything with a plug, battery, chip, or serial number), prepend this **⚠️ RISK block** to the output. It is an internal pre-listing checklist for the owner — **never shown to buyers:**

```
⚠️ RISK — ELECTRONICS PRE-LISTING CHECKLIST (internal, do not paste)
[ ] Serial number / IMEI photographed
[ ] Activation lock / account lock checked and CLEAR
[ ] Powered on and function-tested (list what was tested)
[ ] If sale price > $100: signature confirmation ON
[ ] Condition-disclosure language included below (do not remove)
```
The listing body for electronics also gets tightened condition-disclosure language: exactly what was tested, what works, what wasn't tested, and cosmetic condition by surface.

## eBay listing output

1. **Title (≤80 chars):** most important keywords FIRST — brand, model, size/count, color, key attribute, condition. Build from real buyer search phrasing (eBay autocomplete style). No filler ("L@@K", "WOW"), no keyword stuffing.
2. **Item specifics — EVERY field, not just required ones.** Output as a `field: value` list covering brand, model, MPN, UPC/ISBN, type, size, color, features, era/year, edition — whatever the category offers. Unfilled specifics make the listing invisible to sidebar filters.
3. **Condition + condition description:** honest, specific. Used items: name every flaw (matches the photograph-every-flaw rule).
4. **Description:** short, scannable, mobile-first (60%+ of buyers are on phones): what it is, what's included, condition detail, shipping/handling promise. No walls of text, no unrelated boilerplate.
5. **Pricing:** priced to **sold comps, not asking prices**, charm-priced ($24.99 not $25). Include: list price, Best Offer ON with auto-accept and auto-decline thresholds (auto-accept ≈ 90% of list, auto-decline ≈ 70% — adjust to margin).
6. **Shipping:** free shipping baked into price when margin allows; otherwise calculated. State the service (media mail for books, ground/Priority otherwise). Handling time: 1 business day. Returns: 30 days.
7. **Photo checklist (12 slots):** list the exact shots to take — clean first photo on neutral background (it's the search thumbnail), then angles, labels/serials, flaws, contents, packaging.
8. **Promoted Listings:** recommend 2% only if the listing is new with no sales history or high-margin; otherwise skip.

## Facebook Marketplace version
- Shorter title (FB truncates), local-buyer phrasing.
- Price slightly above eBay-net-equivalent (0% fees leaves room to negotiate).
- Body: condition, pickup area, "cash or tap-to-pay only, public meetup" line.
- Note whether shipping is enabled.

## After generating
Remind the owner to add the item to `inventory.csv` (date bought, source, item, category, cost, listed price, platform) if not already logged.

## Tone
Output is the deliverable — copy-paste blocks, clearly separated by platform, minimal commentary around them.
