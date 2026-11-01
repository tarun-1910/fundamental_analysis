---
name: fundamental-analysis
description: Perform structured fundamental analysis of a listed company or stock - business quality, financial statements, ratios, valuation, management/governance, and risks - ending in a clear verdict with the reasoning behind it. Use this skill whenever the user asks whether a stock or company is worth investing in, wants a company evaluated or compared with peers, asks about intrinsic value, P/E, ROE, ROCE, debt, cash flow, moat, or "is X overvalued/undervalued", or pastes annual reports, quarterly results, or screener data for review. Trigger even if the user never says "fundamental analysis" - any request to research, assess, or sanity-check a company as an investment qualifies.
---

# Fundamental Analysis

Evaluate a company the way a careful long-term investor would: understand the business first, check that the numbers confirm the story, then ask whether the price is fair. The goal is a reasoned judgment the user can verify, not a list of ratios.

## Principles

- **Business before numbers.** Ratios describe the past; the business model and competitive position determine the future. A cheap stock in a dying business is a trap.
- **Trends over snapshots.** One good year means little. Look at 5-10 years where possible, and note whether a metric is improving, stable, or deteriorating.
- **Compare against the right yardstick.** Judge ratios against the company's own history and its closest peers. A P/E of 25 is cheap for one sector and expensive for another.
- **Cash is the check on profit.** Accounting profit can be shaped; operating cash flow is much harder to fake. Persistent gaps between the two deserve explanation.
- **Show uncertainty honestly.** State what you could not verify and which assumptions drive the conclusion.

## Step 0: Gather data

1. Identify the company, exchange, and the user's context (time horizon, risk appetite, whether they already hold it). If missing and it materially changes the answer, ask once; otherwise state your assumption and proceed.
2. **Always search for current data** (price, latest quarterly results, recent news, shareholding pattern). Financial facts go stale quickly, so do not rely on memory for numbers.
3. **Go to the company's own published documents first.** Find and actually read the latest annual report (ideally the last 2-3), the most recent quarterly results, the latest investor presentation, and recent earnings call transcripts, using the company's investor-relations page and the exchange (BSE/NSE for India, SEC EDGAR for the US). Read `references/company-documents.md` for which sections matter and what to extract; the auditor's report and notes to accounts are where most problems surface. Use screeners such as Screener.in or Tickertape for quick comparison and finding leads, but verify key figures against the filings, since screeners can lag or mis-tag data.
4. If the user supplied files or pasted data, use those as the primary source and note any gaps.
5. Record the date of each data point you rely on. If you cannot find a figure or cannot access a document, say so rather than estimating silently.

## Step 1: Understand the business

Answer in plain language:
- What does it sell, to whom, and how does it earn money? Revenue split by segment and geography.
- What is the **moat**? Name the specific source: brand, switching costs, network effects, scale/cost advantage, regulation or licences, patents. "Strong brand" with no evidence does not count; look for pricing power or stable margins as proof.
- Industry: growth outlook, cyclicality, competitive intensity, regulatory exposure, disruption risk.
- Concentration risks: dependence on a few customers, suppliers, products, or a single region.

## Step 2: Analyse financial performance

Pull multi-year data from the income statement, balance sheet, and cash flow statement. See `references/ratios.md` for formulas, rules of thumb, and sector adjustments. Cover:

**Growth** - Revenue, EBITDA, and net profit CAGR over 3, 5, and 10 years. Is growth organic or acquisition-driven?

**Profitability** - Gross, operating, and net margins and their trend; ROE, ROCE, ROA. High returns sustained over many years are the clearest quantitative sign of a moat.

**Balance sheet strength** - Debt-to-equity, net debt/EBITDA, interest coverage, current ratio. Check maturity profile and whether borrowing funds growth or covers losses.

**Cash flow quality** - Operating cash flow vs net profit, free cash flow (OCF minus capex), and working-capital trends (receivable days, inventory days, payable days). Rising receivables with flat cash flow is a classic warning sign.

**Capital allocation** - How is cash used: reinvestment at high returns, dividends, buybacks, acquisitions? Check dilution from share issuance.

## Step 3: Assess management and governance

- Track record: did past guidance and promises match results?
- Ownership: promoter/insider holding trend, **pledged shares** (a red flag when high or rising), institutional holding changes.
- Red flags: frequent auditor changes or qualified audit opinions, large related-party transactions, unexplained contingent liabilities, regulatory or legal actions, aggressive revenue recognition, frequent fundraising despite reported profits, key-management exits.
- Compensation and alignment: are executives paid in ways that reward long-term value or short-term targets?

## Step 4: Value the stock

Use more than one lens and say how they agree or disagree:

1. **Relative valuation** - P/E, P/B, EV/EBITDA, EV/Sales, PEG, dividend yield versus the company's 5-10 year range and versus peers. Use sector-appropriate multiples (see `references/ratios.md`).
2. **Intrinsic value** - A simple discounted cash flow or earnings-power estimate with explicit assumptions (growth rate, margin, discount rate, terminal growth). Present a **range** with base, bull, and bear cases, and show how sensitive the result is to the assumptions. Do not present a single precise target as fact.
3. **Margin of safety** - How far is the current price from your conservative estimate of value?

A great business can be a poor investment at the wrong price, and a mediocre business can be a fair one at a very low price. Say which situation this is.

## Step 5: Identify risks and what would change the view

List the top 3-5 risks specific to this company (not generic ones), covering regulatory, competitive, financial, execution, and macro exposure (currency, commodities, interest rates). For each, note what evidence would signal it is materializing. Also state what would make the thesis stronger.

## Step 6: Deliver the verdict

Use this structure for a full analysis:

```
# [Company] ([Ticker]) - Fundamental Analysis
Data as of: [date] | Price: [x] | Market cap: [x]

## Summary verdict
[2-4 sentences: quality of business, financial health, valuation, and an overall stance
 such as "high-quality business, fairly valued - suitable to accumulate on dips" or
 "avoid: weak cash flow and rising debt".]

## Scorecard
| Area | Rating (Strong / Adequate / Weak) | Key evidence |
|---|---|---|
| Business & moat | | |
| Growth | | |
| Profitability | | |
| Balance sheet | | |
| Cash flow quality | | |
| Management & governance | | |
| Valuation | | |

## Business and moat
## Financial analysis (include a compact multi-year table of key metrics)
## Management and governance
## Valuation (methods, assumptions, bear/base/bull range)
## Key risks and what to monitor
## Sources and data gaps (list the filings you read, with period, and any you could not access)
```

For quick questions ("is X overvalued?"), skip the full template. Give the verdict first, the three or four facts that drive it, and offer the full analysis.

When comparing several companies, put the key metrics side by side in one table and then explain which is stronger and why, rather than analysing each in isolation.

## Guardrails

- This is research support, not personalized financial advice. Include a short note saying so and that the user should weigh their own goals, risk tolerance, and portfolio diversification, and may wish to consult a registered financial adviser (such as a SEBI-registered adviser in India). Keep it to one or two sentences.
- Do not predict short-term price movements; fundamental analysis speaks to value over a multi-year horizon.
- Avoid false precision. Round figures sensibly and label estimates as estimates.
- Flag when the evidence is thin (new listing, limited history, opaque disclosures) and lower your confidence accordingly.
- If the company is a bank, insurer, NBFC, REIT, or early-stage loss-making business, use the sector-specific metrics in `references/ratios.md` instead of the standard industrial template.
