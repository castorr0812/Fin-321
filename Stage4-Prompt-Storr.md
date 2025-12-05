You are a financial modeling assistant.

# GOAL
Create an Excel file modeling forward, money market, and option hedges for my EUR receivable.

# CONTEXT FILES (GitHub)
Use the logic in:
- (https://github.com/castorr0812/Fin-321/blob/28c40ed33a1451b1edd9afdb2c5100a0b82b072b/stage2-Spec-Storr.md)
- (https://github.com/castorr0812/Fin-321/blob/28c40ed33a1451b1edd9afdb2c5100a0b82b072b/stage3-model-STORR-.xlsx)

# INPUT VARIABLES
Use these exact scenario values and create single-cell named ranges for each:

FC_AMT    = 12,500,000      # EUR receivable
S0_in     = 1.1632          # Spot rate (USD/EUR)
F0_in     = 1.0910          # Forward rate (USD/EUR)
R_USD     = 4.11%           # USD interest rate (per year)
R_FC      = 2.15%           # EUR interest rate (per year)
K_PUT     = 1.1632          # Put strike (USD/EUR)
K_CALL    = 1.1632          # Call strike (USD/EUR)
PREM_PUT  = 0.017           # Put premium (USD/EUR)
PREM_CALL = 0.022           # Call premium (USD/EUR)
T_DAYS    = 360             # Days to maturity
T_YRS     = T_DAYS / 360    # Time to maturity in years

Define Excel named ranges EXACTLY as:
FC_AMT, S0_in, F0_in, R_USD, R_FC, K_PUT, K_CALL, PREM_PUT, PREM_CALL, T_DAYS, T_YRS

All formulas must reference these named ranges (no hard-coded numbers).

# SPREADSHEET REQUIREMENTS
- Create a single main sheet called "Model".
- Build an input/assumption table at the top with:
  - Column A: Variable
  - Column B: Value
  - Column C: Description
- Color code:
  - Inputs (the values listed above) = yellow
  - Assumptions / derived (e.g., T_YRS, scenario spot levels) = blue
  - Calculation formulas / intermediate steps = green
  - Outputs / KPIs (final hedge proceeds, parity checks, net option results) = gray

Include at minimum:

1. Forward Hedge
   - Locked-in USD proceeds using: USD_forward = FC_AMT * F0_in

2. Money Market Hedge (3-step)
   - Step 1: Borrow EUR today:
     FC_borrow = FC_AMT / (1 + R_FC * T_YRS)
   - Step 2: Convert borrowed EUR to USD at spot:
     USD_today = FC_borrow * S0_in
   - Step 3: Invest USD until maturity:
     USD_MM = USD_today * (1 + R_USD * T_YRS)

3. Option Hedges (Put and Call)
   - Define three spot-at-maturity scenarios:
     S_T_low  = S0_in * 0.95
     S_T_mid  = S0_in
     S_T_high = S0_in * 1.05
   - For each S_T, compute:
     Unhedged_USD = S_T * FC_AMT
     Forward_USD  = USD_forward
     MM_USD       = USD_MM
   - Put hedge net payoff per scenario:
     Put_payoff_per_EUR = MAX(K_PUT - S_T, 0)
     Put_payoff_total   = Put_payoff_per_EUR * FC_AMT
     Put_premium_total  = PREM_PUT * FC_AMT
     Put_net_USD        = Put_payoff_total - Put_premium_total
   - Call hedge net payoff per scenario:
     Call_payoff_per_EUR = MAX(S_T - K_CALL, 0)
     Call_payoff_total   = Call_payoff_per_EUR * FC_AMT
     Call_premium_total  = PREM_CALL * FC_AMT
     Call_net_USD        = Call_payoff_total - Call_premium_total

4. Sensitivity Analysis Table (±5% Spot)
   - A small table with rows for S_T_low, S_T_mid, S_T_high
   - Columns: S_T, Unhedged_USD, Forward_USD, MM_USD, Put_net_USD, Call_net_USD
   - Scenario S_T values should be blue; results should be gray.

# MODEL LOGIC
Implement the pseudocode from my Stage 2 spec using:
- Named ranges listed above
- No hard-coded input values in formulas
- Clear separation between inputs, calculations, and outputs

# VERIFICATION
- Validate parity between forward and money market hedges:
  Parity_Diff = USD_MM - USD_forward
- Confirm that all named ranges exist and are used in formulas.
- Ensure the sensitivity table correctly references S_T_low, S_T_mid, and S_T_high.

# EXPORT
Return:
- A downloadable Excel (.xlsx) file with:
  - Inputs, assumptions, and named ranges
  - Forward hedge, money market hedge, option hedges
  - Sensitivity analysis and parity check
- A brief text summary of sheet structure and key formulas.
