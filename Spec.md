**Created by:** Connor Storr  
**Updated by:** Connor Storr  
**Date Created:** November 7, 2025  
**Date Updated:** November 7, 2025  
**Version:** 1.0  
**LLM Used:** GPT-5  

**Role:** Financial Analyst / Treasury Analyst  
**Audience:** CFO or Director of Treasury  

**Purpose:** Provide a professional, quantitative specification outlining the analytical structure for evaluating FX hedging alternatives for the firm’s € 4.5 million receivable.

---

## 1. Problem Statement  

Our company expects to receive **€ 4,500,000 in 12 months** from a European customer, exposing us to potential FX risk from fluctuations in the EUR/USD rate.  
This specification outlines the analytical framework for quantifying, comparing, and evaluating alternative hedging strategies to mitigate that risk.

**Exposure Type:** Receivable (long EUR / short USD)  
**Time Horizon:** 1 year  
**Objective:** Protect the USD value of the receivable while preserving upside if the euro strengthens.  
**Decision Context:** Corporate Treasury will select between forward, money-market, and option hedges to stabilize USD cash flows and reduce exchange-rate risk.

At today’s **spot rate (1.1619 USD/EUR)** the receivable equals about **$ 5.23 million**;  
at the **forward rate (1.0875 USD/EUR)** it would fall to **$ 4.89 million**, a potential loss of ≈ **$ 340 k** if unhedged.

---

## 2. Inputs (Known Variables)

| Variable | Description | Unit | Example / Value | Source |
|-----------|--------------|------|-----------------|---------|
| `FC_AMT` | Foreign-currency receivable | EUR | 4,500,000 | Sales contract |
| `S₀` | Current EUR/USD spot rate | USD/EUR | 1.1619 | Market data |
| `F₀` | 1-year EUR/USD forward rate | USD/EUR | 1.0875 | Dealer quote |
| `r_USD` | USD 1-year interest rate | % | 4.25 | Fed funds rate |
| `r_EUR` | EUR 1-year interest rate | % | 3.10 | ECB deposit rate |
| `t` | Time to maturity | Years | 1.0 | Contract |
| `K_put` | EUR put strike | USD/EUR | 1.15 | Analyst choice |
| `K_call` | EUR call strike | USD/EUR | 1.20 | Analyst choice |
| `Premium_put` | Put premium | USD/EUR | 0.036 | Market quote |
| `Premium_call` | Call premium | USD/EUR | 0.048 | Market quote |
| `t_txn` | Transaction cost | % of notional | 0.10 % | Assumed |
| `Scenarios` | Spot-rate range | % change | –10 %, 0 %, +10 % | Sensitivity plan |

> *Use these variable names as Excel named ranges and AI prompt parameters for later stages.*

---

## 3. Assumptions & Constraints  

- Interest rates quoted on a simple annual (360-day) basis.  
- Forward rate represents a 1-year maturity.  
- Settlement occurs exactly one year from valuation date.  
- No counterparty or credit risk assumed.  
- Transaction cost = 0.10 % per FX leg ( symmetrical ).  
- Exchange rates expressed as USD per EUR.  
- Option premiums paid upfront in USD.  
- Taxes, accounting, and liquidity effects excluded.  
- All outputs expressed in USD.  

> *Assumptions ensure reproducibility by another treasury analyst.*

---

## 4. Calculation Flow  

1. **Forward Hedge** – lock in rate `F₀`, calculate `USD_forward = FC_AMT × F₀ × (1 – t_txn)`  
2. **Money-Market Hedge** – borrow € = `FC_AMT / (1 + r_EUR × t)`; convert to USD at `S₀`; invest at `r_USD`.  
3. **Option Hedge** – pay premium = `Premium_put × FC_AMT`; at maturity receive `MAX(S_T, K_put) × FC_AMT – Premium_cost`.  
4. Compare USD results for unhedged, forward, MM, and option cases.  
5. Summarize trade-offs: certainty (forward/MM) vs flexibility (option).

---

## 5. Outputs  

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_unhedged` | USD value at expected spot | Numeric | Baseline |
| `USD_forward` | USD receipts from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD receipts from money-market hedge | Numeric | Parity check |
| `USD_option` | Net USD after option premium | Table / Chart | Optionality analysis |
| `Chart_1` | USD Receipts vs Spot Rate (Sₜ) | Line chart | Visual comparison |
| `Chart_2` | Sensitivity Impact by Hedge Type | Bar / Tornado chart | FX exposure view |
| `Summary` | Executive takeaway | Text | Decision support |

---

## 6. Sensitivity Plan  

- **Variable tested:** Spot rate at maturity (Sₜ)  
- **Range:** 0.90 × S₀ → 1.10 × S₀ ( 0.01 steps )  
- Recalculate USD proceeds for each hedge and plot line chart of results.  
- Compute expected value, σ, min/max, and 95 % VaR.  
- Visualize via data table + charts in Excel.  

---

## 7. Limitations & Next Steps  

**Limitations**  
- Static rates and volatility assumptions.  
- Flat transaction cost approximation.  
- Quoted option premiums (no model valuation).  
- No tax or accounting effects.  
- Credit risk not modeled.  


