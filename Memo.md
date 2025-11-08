# Executive Memo – FX Receivable Exposure (Scenario 3)

**Created by:** Connor A. Storr  
**Updated by:** Connor A. Storr  
**Date Created:** October 24, 2025  
**Date Updated:** November 7, 2025  
**Version:** 1.0  
**LLM Used:** GPT-5  

---

**To:** Chief Financial Officer  
**From:** Connor A. Storr, Treasury Analyst  
**Subject:** Managing FX Exposure for €12.5 Million Receivable  

---

## Executive Summary  
Our firm expects to receive **€12.5 million in one year** from a European client. With the **current spot rate at 1.1632 USD/EUR** and the **1-year forward rate at 1.0910 USD/EUR**, the euro is trading at a forward discount. This implies potential dollar receipts could fall from **$14.54 million to $13.64 million**, a projected loss of approximately **$900,000** due solely to exchange-rate movement.  

To mitigate this exposure, three hedging strategies—**forward contract, money-market hedge, and currency option**—were evaluated using an Excel-based quantitative model. Each strategy stabilizes future cash flows with different trade-offs in cost and flexibility.  
**Recommendation:** Execute a **1-year forward contract** to lock in USD proceeds and eliminate FX uncertainty.

---

## Background & Objectives  
The company faces **foreign-exchange transaction exposure** due to its euro-denominated receivable. As a U.S.-based firm reporting in USD, any depreciation of the euro directly reduces the realized dollar value of incoming cash flows. Given current interest rate differentials and euro-area inflation risks, the EUR/USD forward curve signals likely euro weakness.  

**Objectives:**  
1. Quantify FX risk on the €12.5 million receivable under multiple spot-rate scenarios.  
2. Compare cost, risk reduction, and flexibility across three hedge alternatives.  
3. Recommend the financially optimal and operationally practical hedge for execution.

---

## Methods  
An Excel-based FX hedging model was developed to project USD outcomes across spot rates from **1.00 to 1.25 USD/EUR**.  
The model incorporated the following current market data:  

- Spot rate: 1.1632 USD/EUR  
- 1-year forward rate: 1.0910 USD/EUR  
- USD interest rate: 4.11%  
- EUR interest rate: 2.15%  
- EUR Put Option Strike: 1.1632 USD/EUR  
- Option Premium: $0.017 per EUR  

### Hedge Strategies Evaluated  
**1. Forward Contract**  
- Sell €12.5M forward at 1.0910 USD/EUR → **Lock in $13,637,500**.  
- *Eliminates all exchange-rate risk but forfeits upside if the euro strengthens.*

**2. Money-Market Hedge**  
- Borrow PV(€12.5M) discounted at 2.15%, convert to USD at spot (1.1632), and invest USD at 4.11% for one year.  
- *Yields ≈ $13.72M at maturity; nearly identical to the forward hedge but uses balance sheet credit.*  

**3. Option Hedge (EUR Put)**  
- Buy a EUR put at 1.1632 for $0.017/€, total premium $212,500.  
- *Guarantees a minimum USD value if the euro weakens while retaining upside potential if it strengthens.*

---

## Limitations & Next Steps  
**Assumptions:**  
- Constant interest rates and option premiums throughout the hedge horizon.  
- Transaction costs, liquidity risk, and counterparty credit exposures excluded.  
- Based on market conditions as of **October 24, 2025**.  

**Next Steps:**  
1. Finalize Excel model with integrated payoff and sensitivity charts.  
2. Present findings to CFO and treasury committee for hedge selection.  
3. Execute the approved hedge strategy (forward or option) with authorized counterparties.  
4. Document hedge accounting treatment per **ASC 815** standards.

---

## References  
- Bloomberg Market Data (2025). *EUR/USD Spot and Forward Rates.*  
- European Central Bank (2025). *Euro Area Yield Curve Data.*  
- U.S. Federal Reserve (2025). *Selected Interest Rates (H.15).*  
- Hull, J. C. (2022). *Options, Futures, and Other Derivatives* (11th ed.). Pearson.
