# Test Scenarios — ATM Simulator

## Test Execution Status

This document records the execution status of the main manual test scenarios for the ATM Simulator based on the current evidence set.

| Scenario ID | Scenario | Execution Status | Result | Evidence Summary |
|---|---|---|---|---|
| TS-001 | Authentication | Executed | Pass | Login success, invalid PIN rejection, and non-existing account rejection captured in screenshots. |
| TS-002 | Balance Enquiry | Executed | Pass | Balance display and balance updates after transactions are captured in screenshots. |
| TS-003 | Deposit | Executed | Fail | Most deposit validations passed, but non-numeric input handling did not fully meet the requirement. |
| TS-004 | Withdrawal | Executed | Pass | Successful withdrawal, over-limit rejection, negative rejection, zero rejection, and exact-balance withdrawal are evidenced. |
| TS-005 | Transfer | Executed | Fail | Valid transfer and insufficient funds rejection were evidenced, but invalid destination account messaging was too generic. |
| TS-006 | Transaction History | Executed | Pass | Transaction history screenshots were provided. |
| TS-007 | Input Handling and Stability | Executed | Fail | Non-numeric amount entry showed a generic message and returned the user to the menu instead of re-prompting. |

---

## TS-001 Authentication
**Objective:** Verify that login succeeds with valid credentials and blocks invalid credentials.

**Execution Status:** Executed  
**Result:** Pass  

**Evidence:**
- `TC-001_Succesful_login.png`
- `TC-002_Login_with_invalid_pin.png`
- `TC-003-Login_with_non_existing_account_number.png`

**Execution Notes:**
- Valid login succeeded using demo credentials.
- Invalid PIN and non-existing account number were rejected as expected.

---

## TS-002 Balance Enquiry
**Objective:** Verify that the system shows the correct current account balance.

**Execution Status:** Executed  
**Result:** Pass  

**Evidence:**
- `TC-004_Check_balance_display.png`
- `TC-005_Balance_reflects_deposit.png`
- `TC-006_Balance_reflects_withdrawal.png`
- `TC-007_Balance_reflects_transfer.png`

**Execution Notes:**
- Balance display was captured successfully.
- Screenshots indicate balance reflects successful deposit, withdrawal, and transfer activity.

---

## TS-003 Deposit
**Objective:** Verify that deposit accepts valid positive values and rejects invalid input.

**Execution Status:** Executed  
**Result:** Fail  

**Evidence:**
- `TC-008_Successful_deposit.png`
- `TC-009_Negative_amount.png`
- `TC-010_Zero_amount.png`
- `TC-011_Non_numeric_input.png`
- `TC-012_deposit_large_amount.png`
- `TC-013_deposit_decimal_edge_case.png`

**Execution Notes:**
- Positive deposit, negative amount handling, zero amount handling, large amount handling, and decimal edge-case testing were executed.
- Non-numeric input handling revealed a usability defect.
- This scenario resulted in confirmed defects BUG-001 and BUG-002.

**Related Bugs:** BUG-001, BUG-002

---

## TS-004 Withdrawal
**Objective:** Verify that withdrawal works with sufficient balance and blocks invalid amounts.

**Execution Status:** Executed  
**Result:** Pass  

**Evidence:**
- `TC-014-Successful_withdrawal.png`
- `TC-015_Withdraw_exceeding_amount.png`
- `TC-016_Reject_Negative_amount.png`
- `TC-017_withdraw_reject_zero_amount.png`
- `TC-018_withdraw_exact_balance.png`

**Execution Notes:**
- Successful withdrawal was verified.
- Rejection for insufficient funds, negative amount, and zero amount were captured.
- Exact-balance withdrawal was also tested.

---

## TS-005 Transfer
**Objective:** Verify that fund transfer works for valid destination accounts and rejects invalid targets.

**Execution Status:** Executed  
**Result:** Fail  

**Evidence:**
- `TC-019_Succesful_transfer.png`
- `TC-020_wrong_account_transfer.png`
- `TC-022_Transfer_rejects_insufficient_funds.png`

**Execution Notes:**
- Valid transfer and insufficient funds rejection were executed.
- Invalid destination account handling produced a generic message instead of a clear destination-specific message.
- This scenario resulted in confirmed defect BUG-003.

**Related Bugs:** BUG-003

---

## TS-006 Transaction History
**Objective:** Verify that transaction history displays correctly and handles empty history safely.

**Execution Status:** Executed  
**Result:** Pass  

**Evidence:**
- `TC-024-025-026_Transaction_history.png`

**Execution Notes:**
- Transaction history evidence was provided for the current test cycle.
- No confirmed defect was selected for this scenario.

---

## TS-007 Input Handling and Stability
**Objective:** Verify that invalid input is handled clearly, safely, and without interrupting the user flow.

**Execution Status:** Executed  
**Result:** Fail  

**Evidence:**
- `TC-011_Non_numeric_input.png`
- `TC-020_wrong_account_transfer.png`

**Execution Notes:**
- Numeric validation messaging was generic instead of context-aware.
- The system did not re-prompt for the same amount field after invalid input.
- Destination-account validation in transfer was functional but ambiguous in wording.

**Related Bugs:** BUG-001, BUG-002, BUG-003

---

## Summary

### Executed and Passed
- TS-001 Authentication
- TS-002 Balance Enquiry
- TS-004 Withdrawal
- TS-006 Transaction History

### Executed and Failed
- TS-003 Deposit
- TS-005 Transfer
- TS-007 Input Handling and Stability

### Overall Note
The current cycle now demonstrates both:
- broad manual test execution coverage
- real defect documentation supported by evidence screenshots
