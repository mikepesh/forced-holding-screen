---
name: forced-holding-screen
description: Analyze an investment portfolio for FORCED exposure to specific stocks via index-fund inclusion — especially upcoming or recent IPOs like SpaceX, Anthropic, or OpenAI. Use when someone wants to know which of their ETFs/index funds already hold (or will soon be forced to hold) a given company, whether they're exposed to an IPO through their funds, how to avoid being forced into a stock while keeping similar market exposure, what "clean" alternative funds cover the same segment, or when they paste a list of fund tickers/holdings and ask about exposure or alternatives. Works entirely on de-identified holdings (ticker + description only — no dollar amounts).
---

# Forced-Holding Screen

Help someone find out where their index funds would **force** them to hold a specific stock — typically a big new IPO (SpaceX, and eventually Anthropic / OpenAI) — and what currently-clean alternatives cover the same market exposure without that name. When a private company IPOs it gets added to indexes, and every holder of those index funds is then forced to own it. This skill maps that risk.

**This is informational only — not investment, tax, or legal advice. Never issue buy/sell recommendations. Present alternatives as category examples and let the person decide. Include the disclaimer at the end of every report.**

## Step 1 — Get de-identified holdings (privacy by design)

Ask the person to export their positions (in Fidelity: **Accounts → Positions → Download**) and paste **only these columns**:

- **Symbol** (ticker)
- **Description** (fund/stock name)
- *(optional)* **% of Account** — a percentage, not a dollar figure; enables a look-through estimate
- *(optional)* **Account type** (e.g. "Roth IRA", "Individual") — enables tax tagging of swaps

Tell them explicitly: **do not paste dollar amounts, share quantities, or account numbers.** None of those are needed, and leaving them out means nothing sensitive about their net worth is shared. If they paste a full export anyway, use only the columns above and ignore the rest.

If they haven't named which company/companies to avoid, default to the current crop of pre-IPO / newly-public names (SpaceX, Anthropic, OpenAI) and confirm.

## Step 2 — Get current facts (do not rely on memory)

Fund holdings, IPO dates, and index rules change constantly, so **use web search** to verify before classifying:

- The IPO/listing status and ticker of each watched company.
- Whether each *fund the person holds* owns the name (or a private stake), and at roughly what weight — check the issuer's holdings page or recent reporting.
- Whether the name is in, or a fast-track candidate for, the index a fund tracks.

Prefer primary sources (issuer holdings pages, index methodology docs, SEC filings) and note the "as of" date. If you can't verify a fund, say so rather than guessing.

## Step 3 — Classify each holding

| Bucket | Meaning |
|---|---|
| **HOLDS NOW** | The fund already owns the name (or a private stake) — the person is exposed today. |
| **IMMINENT** | The fund tracks an index that will include the name very soon. In practice: **total-market** funds (no profitability screen) and the **Nasdaq-100** (fast-track path for big IPOs). |
| **BUFFERED** | Clean for now but could be added later. The **S&P 500** excludes brand-new IPOs on profitability + seasoning grounds, so S&P 500 funds are a near-term "clean" large-cap vehicle — but not permanently. |
| **SAFE** | Methodology structurally excludes the name: value, dividend, equal-weight, ex-US/international, and bond funds. |
| **INDIVIDUAL STOCK** | A single stock the person chose — no forced-index risk (they can sell whenever). Detect by description (a company name, not a fund) — flag it as a likely stock and let them confirm. |
| **UNKNOWN** | A fund you couldn't verify — say what to check rather than assuming. |

Key facts to apply (verify current specifics via search):
- **S&P 500 ≠ total market.** Someone whose core is an S&P 500 fund has *no* near-term exposure to a fresh IPO; someone in a total-market fund does. Don't conflate them.
- Still-private names (e.g. Anthropic/OpenAI before they list) have **no index path at all** — the only exposure is via funds holding private stakes directly.
- **Closed-end / interval funds** (e.g. a tech-IPO CEF) can trade at large premiums/discounts to NAV, so their "exposure" to a name isn't a clean mark — flag this if relevant.

## Step 4 — For each at-risk holding, explain and suggest

For every **HOLDS NOW** and **IMMINENT** holding, give a short block:

- **Why it's at risk** — the specific index/inclusion mechanism.
- **Suggested swap** — a currently-clean equivalent covering the same segment (e.g. a total-market fund → an S&P 500 fund; a Nasdaq-100 fund → an S&P 500 Growth fund). Present 1–3 example tickers as a *category*, not a recommendation.
- **What you keep** — the exposure the swap preserves.
- **Why the swap stays clean** — the methodology reason it excludes the name (e.g. S&P-based funds inherit the S&P's profitability gate).
- **What changes / trade-off** — e.g. moving off a total-market fund loses mid/small-cap coverage; suggest pairing an S&P MidCap 400 + SmallCap 600 fund to restore it.
- **Tax note** (if account type was given) — swapping in a tax-advantaged account (IRA/401k/HSA) is a free move; in a taxable/brokerage account it may realize capital gains. State it's the person's call whether a gain is worth realizing.

For **HOLDS NOW** funds that own the stake directly, note there's no clean equivalent — the fund *is* the exposure, so exiting is the only way to zero it.

Also note the one true name-level exclusion option: **direct indexing** (e.g. Fidelity FidFolios and similar) lets someone own an index's components while excluding specific tickers by rule — the only way to keep index-like exposure while permanently dropping a name. Everything else is "pick funds whose methodology won't include it."

## Step 5 — Output

A clean markdown report:
1. **Watched names** + current status (from your search).
2. **Summary** — counts per bucket, and if "% of Account" was provided, an estimated look-through to each watched company (sum of fund weight × the name's weight in that fund).
3. **At risk — review first** — the per-holding blocks from Step 4.
4. **Clean for now / Structurally safe / Individual stocks / Unknown** — short lists.
5. **Disclaimer.**

## Disclaimer (include verbatim at the end)

> Informational only — not investment, tax, or legal advice, and no guarantee of accuracy. Fund holdings and index rules change constantly; verify against primary sources before acting. "Clean equivalent" funds are category examples, not recommendations. You decide what, if anything, to do.

## Notes

- The watched companies aren't special-cased — this works for **any** name someone wants to avoid (or check exposure to). Just ask which.
- To re-check after an IPO, the person re-runs the skill with a fresh paste — the ad-hoc version of monitoring.
