# Auto Insurance Portfolio Profitability Analysis

Excel analysis of claims vs. earned premium across 9,134 auto insurance policies, flagging policies over their coverage tier's target claims ratio and comparing profitability across customer segments.

## Data

[Vehicle Insurance Customer Data](https://www.kaggle.com/datasets/ranja7/vehicle-insurance-customer-data) on Kaggle: 9,134 policies, 24 fields (state, coverage, employment status, income, monthly premium, months since policy inception, total claim amount, vehicle, sales channel, etc.).

## Files

| Path | What it is |
| --- | --- |
| `excel/auto_insurance_claims_analysis.xlsx` | The analysis workbook |
| `data/AutoInsurance.csv` | Raw policy data |

## Workbook

**Data sheet**, one row per policy:
- **Earned premium** = monthly premium × months since policy inception
- **Claims ratio** = total claim amount ÷ earned premium, with `IFERROR` so the 83 policies with no earned premium (0 months in force) show "No premium" instead of a divide-by-zero error
- **Target ratio** by coverage tier (Basic 0.70, Extended 0.68, Premium 0.65), assigned with `XLOOKUP`
- **Flag**: `IF` logic marks each policy "Over target" or "Within target"

**Summary sheet**: `SUMIFS` / `COUNTIFS` table of earned premium, claims, claims ratio, and policy count for each employment status, plus counts of no-premium and over-target policies.

**Pivot Table sheet**: claims vs. earned premium by coverage tier.

## Findings

- **529 policies (5.8%)** are over their tier's target claims ratio.
- **Employment status is the clearest difference.** Unemployed customers have a 13.0% claims ratio vs. 8.0% for employed customers (63% higher), and make up 25.9% of earned premium ($10.7M of $41.1M).
- **Coverage tier makes little difference:** Basic 9.6%, Extended 9.7%, Premium 9.9%.
- Portfolio-wide claims ratio: 9.6% ($4.0M claims on $41.1M earned premium).
