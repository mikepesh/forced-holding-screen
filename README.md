# Forced-Holding Screen

[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

**A Claude skill that finds out where your index funds would *force* you to hold a specific stock — and what currently-clean alternatives cover the same market exposure without it.**

When a big private company IPOs (SpaceX, and eventually Anthropic / OpenAI), it doesn't just become buyable — it gets added to indexes, and then every holder of those index funds is *forced* to own it whether they want to or not. This skill maps that risk across your portfolio, explains the at-risk holdings, and suggests swaps that keep your exposure but skip the name.

It runs on **de-identified input by design**: you paste only ticker + description (and optionally a percentage), so no dollar amounts, share counts, or account numbers are ever shared.

> [!WARNING]
> **Not investment, tax, or legal advice. No warranty.** This is informational tooling.
> Suggested "clean equivalent" funds are examples of a category, not recommendations.
> Fund holdings and index rules change constantly — verify against primary sources before acting.

## What it does

- Buckets every holding by **forced-holding risk**: *holds now* (funds with a stake today), *imminent* (total-market and Nasdaq-100 funds pick up new listings fast), *buffered* (the S&P 500's profitability screen keeps brand-new IPOs out near-term), *structurally safe* (value, international, bonds), and *individual stocks* (no forced risk).
- For at-risk holdings, explains **why**, suggests a **currently-clean equivalent**, what you keep vs. trade off, and — if you note the account type — whether swapping is tax-free (IRA/401k) or a taxable event.
- Uses **web search at run time** to check current IPO status and fund holdings, so it isn't relying on stale baked-in data.
- Generalizes to **any** company you want to avoid — not just the three above.

See [`examples/sample-report.md`](examples/sample-report.md) for what the output looks like, and [`examples/sample-input.txt`](examples/sample-input.txt) for the paste format.

## Install

This is a Claude **skill** — a single `SKILL.md`. Drop the folder into your skills directory:

- **Claude Code / Cowork:** place `forced-holding-screen/` in your skills folder (e.g. `~/.claude/skills/` or your project's `skills/` — see Anthropic's skills docs for your setup).
- Then just ask Claude something like *"check my portfolio for forced exposure to the SpaceX IPO"* and it triggers.

No dependencies, no install scripts, nothing to run.

## Use

1. Export your positions (in Fidelity: **Accounts → Positions → Download**).
2. Paste **only** Symbol + Description (optionally "% of Account" and account type). **Leave out dollar amounts, quantities, and account numbers.**
3. Claude verifies current facts, classifies each holding, and returns a report with suggested clean swaps.
4. To "monitor," re-run it after an IPO — the ad-hoc version of a tripwire.

## Why a skill (and not a script)

Because the input is de-identified, there's nothing sensitive to protect, so it doesn't need to run locally. And because index membership and fund holdings change constantly, live web search beats any data file that would go stale. The result is one portable text file instead of an app to install and maintain.

## Built with AI

This skill was designed and specified by **Mike "Pesh" Poeschl** and built using [Claude](https://claude.ai) (Anthropic) as the primary authoring tool. The requirements, logic, privacy-by-design constraints, and classification framework came from the author; Claude translated those specifications into the `SKILL.md` prompt and supporting files.

It is not hand-coded in the traditional sense — it is a human-directed, AI-assisted artifact. That distinction feels worth naming: the judgment calls and design decisions are human; the drafting is AI. If you use or adapt this, you're welcome to do the same.

## Contributing

Issues and PRs welcome — especially clarifications to the classification logic or the
clean-equivalent guidance in `SKILL.md`. Keep it informational (no buy/sell advice) and
keep the de-identified-input principle intact.

## License

MIT — see [LICENSE](LICENSE).
