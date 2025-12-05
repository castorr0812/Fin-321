## A. Exposure Summary

The firm expects to receive **€12,500,000 in 360 days**, creating a material foreign exchange (FX) exposure. Because the firm ultimately reports and spends cash in **USD**, fluctuations in the EUR/USD exchange rate directly impact:

- Reported revenue and margins  
- Cash flow available for operations and debt service  
- The firm’s ability to hit budget and forecast targets  

If the **EUR depreciates** against the USD, the USD value of the receivable falls, creating downside risk. If the **EUR appreciates**, the firm benefits, but this upside is uncertain and cannot be relied on for planning. Management therefore needs a hedge strategy that balances **downside protection**, **cost**, and **flexibility**.

---

## B. Summary of Hedge Outcomes (from Stage 4 Model)

Using the Stage 4 spreadsheet with the following inputs:

- **FC_AMT:** €12,500,000  
- **S0_in:** 1.1632 USD/EUR  
- **F0_in:** 1.0910 USD/EUR  
- **R_USD:** 4.11% per year  
- **R_FC:** 2.15% per year  
- **K_PUT = K_CALL = S0_in:** 1.1632 USD/EUR  
- **PREM_PUT = 0.017, PREM_CALL = 0.022**

The model shows:

- The **Forward Hedge** locks in a fixed USD amount based on the forward rate.  
- The **Money Market Hedge (MM)** delivers a very similar USD outcome, reflecting interest rate parity between EUR and USD.  
- **Put Options** create a floor on USD receipts while preserving upside, at the cost of premiums.  
- **Call Options** give upside participation but do not protect against EUR depreciation; they are more speculative in this context.

The key insight is that **forward and MM hedges provide nearly identical, stable USD proceeds**, while **options reshape the payoff profile**, trading off cost and optionality.

---

## C. Sensitivity Interpretation

The Stage 4 model includes a **±5% spot sensitivity** around the current spot rate:

- **EUR Depreciation Scenario (S_T = 0.95 × S0_in)**
  - **Unhedged:** USD proceeds fall meaningfully as EUR weakens.  
  - **Forward / MM:** USD proceeds remain unchanged; the firm is fully insulated from the weaker EUR.  
  - **Put hedge:** Performs well in this region, as option intrinsic value rises and offsets the weaker spot.  
  - **Call hedge:** Provides no protection; only the premium cost is realized.

- **EUR Appreciation Scenario (S_T = 1.05 × S0_in)**
  - **Unhedged:** USD proceeds rise the most, capturing full upside.  
  - **Forward / MM:** Do not benefit from appreciation; proceeds remain fixed.  
  - **Put hedge:** Still participates in upside (minus premium), since the firm can let the put expire out of the money.  
  - **Call hedge:** Becomes valuable as the spot ends above the strike, but this is not aligned with hedging a receivable (it is more of a speculative overlay).

**Summary:**  
- **Forward/MM** = maximum certainty, no upside.  
- **Put** = downside protection with retained upside, but at a premium cost.  
- **Call** = upside tool, not an effective hedge for a long EUR receivable by itself.  

---

## D. Strategic Recommendation

### Recommended Strategy: **Forward Hedge on the Full Notional**

I recommend that the firm **enter a forward contract** to sell the full **€12,500,000** at the agreed forward rate.

**Rationale:**

1. **Cash Flow Certainty**  
   The forward locks in a known USD amount, simplifying budgeting, forecasting, and performance measurement.

2. **Economic Equivalence to MM Hedge**  
   Given interest rate parity, the money market hedge produces nearly the same USD proceeds but with more operational complexity (borrowing, lending, and cash movements). The forward achieves the same economic result in a simpler, more scalable way.

3. **Risk Profile**  
   The firm’s objective is to eliminate downside FX risk on a large receivable, not to speculate on EUR movements. The forward delivers a clean, symmetric hedge that converts FX risk into a known USD outcome.

4. **Optionality as a Secondary Consideration**  
   If management wishes to retain some upside, a **small overlay of put options on a portion of the exposure** could be considered. However, the base recommendation remains a **full forward hedge** given cost, simplicity, and risk tolerance.

---

## E. Executive Justification

From a senior management perspective, the forward hedge aligns best with:

- **Cash Flow Stability**  
  Stable USD inflows support debt service, dividend policy, and capital expenditure planning.

- **Budget Certainty**  
  Locked-in FX rates allow finance and FP&A to set and defend budget assumptions without building in large FX buffers.

- **Liquidity**  
  Forwards typically require **no upfront premium**, unlike options. This preserves cash for operations and investment.

- **Simplicity & Governance**  
  Forwards are widely understood, easy to document, and straightforward to test for effectiveness. The Stage 4 model provides a transparent, reproducible calculation of hedge performance.

- **Optionality & Premium Costs**  
  While put options offer an attractive payoff shape, their premiums reduce net proceeds and may be hard to justify unless management has a clear upside view on EUR. Calls are even less appropriate as a primary hedge tool for this receivable.

Overall, the **forward hedge** offers the best balance of **stability, cost, and governance** for this exposure.
