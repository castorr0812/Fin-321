# Managing FX Exposure for € 12.5 Million Receivable – Technical Specification

**Created by:** Connor A. Storr  
**Updated by:** Connor A. Storr  
**Date Created:** October 24, 2025  
**Date Updated:** November 7, 2025  
**Version:** 1.1  
**LLM Used:** GPT-5  

**Role:** Treasury Analyst  
**Audience:** Chief Financial Officer (CFO)  

---

## Purpose
Provide a professional, quantitative specification outlining the analytical structure for evaluating hedging alternatives for the company’s € 12.5 million receivable.

---

## 1. Problem Statement

Our U.S.-based firm expects to receive **€ 12.5 million in one year** from a European client.  
At the current **spot rate (1.1632 USD/EUR)**, this equals **$ 14.54 million**.  
However, the **one-year forward rate (1.0910 USD/EUR)** implies potential receipts of only **$ 13.64 million**, representing a **$ 900 k potential loss** if the euro depreciates.

**Exposure Type:** Foreign-currency receivable (long EUR / short USD)  
**Time Horizon:** 1 year  
**Objective:** Protect USD proceeds from euro weakness while assessing flexibility trade-offs.  
**Decision Context:** The Treasury team will recommend the optimal hedge—forward, money-market, or option—to stabilize cash flows and align with the CFO’s risk tolerance.

---

## 2. Inputs (Known Variables)

| Variable | Description | Unit | Example / Value | Source |
|-----------|--------------|------|-----------------|---------|
| `FC_AMT` | Foreign-currency receivable | EUR | 12,500,000 | Sales contract |
| `S₀` | Current EUR/USD spot rate | USD/EUR | 1.1632 | Bloomberg FX feed |
| `F₀` | 1-year EUR/USD forward rate | USD/EUR | 1.0910 | Dealer quote |
| `r_USD` | USD 1-year interest rate | % p.a. | 4.11 % | Fed H.15 |
| `r_EUR` | EUR 1-year interest rate | % p.a. | 2.15 % | ECB data |
| `t` | Time to maturity | Years | 1.0 | Contract term |
| `K_put` | EUR put strike | USD/EUR | 1.1632 | At-the-money |
| `Premium_put` | EUR put premium | USD/EUR | 0.017 | Dealer pricing |
| `t_txn` | Transaction cost | % of notional | 0.10 % | Assumed |
| `Scenarios` | Spot rate range | % change | –10 %, 0 %, +10 % | Sensitivity plan |

> **Note:** Inputs are stored in a central data block to enable direct linkage with Stage 3 Excel formulas.

---

## 3. Assumptions & Constraints

- Interest rates quoted on a simple annual (360-day) basis.  
- Forward rate reflects a 1-year maturity.  
- Settlement = exactly 12 months from valuation date.  
- No credit, liquidity, or counterparty risk assumed.  
- Transaction cost = 0.10 % per FX leg.  
- Exchange rates quoted USD per EUR.  
- Option premium paid upfront in USD.  
- Taxes and hedge accounting excluded.  
- Outputs expressed in USD for reporting clarity.

---

## 4. Calculation Flow

### A. Forward Hedge
1. Sell € 12.5 M forward at 1.0910 USD/EUR.  
2. Compute:  
    `USD_forward = FC_AMT × F₀ × (1 – t_txn)`  
3. Outcome = locked-in USD proceeds ≈ $ 13,637,500.

---

### B. Money-Market Hedge
1. Borrow PV of € 12.5 M at 2.15 %:   
    `PV_EUR = FC_AMT / (1 + r_EUR)` ≈ € 12.24 M.  
2. Convert to USD at spot (1.1632):   
    `USD_today = PV_EUR × S₀ = $ 14.23 M`.  
3. Invest USD at 4.11 % for 1 year:   
    `USD_future = USD_today × (1 + r_USD)` ≈ $ 13.72 M.  
4. Use receivable to repay euro loan; retain USD investment maturity value.

---

### C. Option Hedge (EUR Put)
1. Buy € 12.5 M put at strike 1.1632 for premium 0.017 USD/EUR.  
    Total premium = `0.017 × 12.5 M = $ 212,500`.  
2. At maturity:  
    - If Sₜ < 1.1632 → exercise → receive € × 1.1632.  
    - If Sₜ > 1.1632 → let expire → receive € × Sₜ.  
3. Net USD:   
    `USD_option = (FC_AMT × Effective Rate) – Premium_cost`.  
4. Plot payoff diagram vs. Sₜ to show downside protection and upside retention.

---

### D. Comparison & Evaluation
- Compare USD_forward, USD_mm, and USD_option vs unhedged case.  
- Measure risk reduction and opportunity cost.  
- Summarize trade-offs: certainty (forward/MM) vs flexibility (option).

---

## 5. Outputs

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_unhedged` | Projected USD at expected spot | Numeric | Baseline |
| `USD_forward` | USD from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD from money-market hedge | Numeric | Parity check |
| `USD_option` | Net USD after option premium | Table / chart | Optionality analysis |
| `Chart_1` | USD Receipts vs Spot Rate (Sₜ) | Line chart | Visual comparison |
| `Chart_2` | Sensitivity Impact by Hedge Type | Bar / tornado chart | FX exposure view |
| `Chart_3` | Option Payoff Diagram | Line chart | Protection floor visual |
| `Summary` | Executive interpretation | Text | CFO decision support |

---

## 6. Sensitivity Plan

- **Variable:** Future spot rate (Sₜ)  
- **Range:** 1.00 → 1.25 USD/EUR in 0.01 increments.  
- Recalculate USD receipts under each hedge.  
- Generate line chart of USD outcomes.  
- Compute expected value, σ, and 95 % VaR.  

---

## 7. Limitations & Next Steps

**Limitations**
- Static interest and volatility assumptions.  
- Transaction cost simplified.  
- No credit or tax effects included.  
- Option premium assumed constant.  

