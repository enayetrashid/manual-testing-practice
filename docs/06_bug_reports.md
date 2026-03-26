# Bug Reports — ATM Simulator

## Test Execution Note

This file contains defects verified and selected for repository evidence in the current manual testing cycle.

---

## BUG-001: Non-numeric amount input shows a generic validation message

**Module:** Deposit / Input Validation  
**Severity:** Medium  
**Priority:** High  
**Status:** Open  

### Requirement Reference
- FR-003 Deposit Funds
- FR-005 Input Validation

### Description
When the user enters a non-numeric value such as `abc` in an amount field, the application displays the message:

`Please enter a valid number.`

The message is too generic and does not clearly describe the expected input in the context of the current action.

### Steps to Reproduce
1. Launch the ATM application
2. Log in with a valid account such as `1001` / `1234`
3. Select `2` for Deposit
4. Enter `abc` at the amount prompt

### Expected Result
The system should display a clear, user-friendly, context-aware validation message such as:
- `Please enter a valid deposit amount`
- `Amount must be a number`

### Actual Result
The system displays:
`Please enter a valid number.`

### Impact
This reduces usability and does not fully meet the repository requirement for a clear validation error message.

### Evidence
- `TC-011_Non_numeric_input.png`

---

## BUG-002: Invalid amount input does not re-prompt the user for the same field

**Module:** Deposit / Input Handling  
**Severity:** Medium  
**Priority:** High  
**Status:** Open  

### Requirement Reference
- FR-005 Input Validation

### Description
After the user enters an invalid amount such as `abc`, the system returns to the main menu instead of prompting the user to re-enter the amount.

### Steps to Reproduce
1. Launch the ATM application
2. Log in with a valid account such as `1001` / `1234`
3. Select `2` for Deposit
4. Enter `abc` at the amount prompt

### Expected Result
The system should keep the user in the same transaction flow and ask again for a valid amount.

### Actual Result
The system prints the validation message and returns the user to the main menu.

### Impact
This breaks the expected input flow and makes the user repeat navigation steps unnecessarily.

### Evidence
- `TC-011_Non_numeric_input.png`

---

## BUG-003: Invalid destination account message is too generic during transfer

**Module:** Transfer  
**Severity:** Low  
**Priority:** Medium  
**Status:** Open  

### Requirement Reference
- FR-005 Fund Transfer
- FR-006 Input Validation

### Description
When the user enters a non-existent destination account during a transfer, the application displays:

`Error: Account does not exist.`

The message does not clearly state that the invalid account is the destination account.

### Steps to Reproduce
1. Launch the ATM application
2. Log in with a valid account such as `1001` / `1234`
3. Select `4` for Transfer
4. Enter an invalid target account such as `9999`
5. Enter a valid amount

### Expected Result
The system should display a destination-specific validation message such as:
`Destination account does not exist.`

### Actual Result
The system displays:
`Error: Account does not exist.`

### Impact
The message is ambiguous and can confuse the user about which account caused the error.

### Evidence
- `TC-020_wrong_account_transfer.png`

---

## Bug Selection Note

Additional scenarios were executed successfully during the same test cycle, including authentication, balance enquiry, withdrawal, successful transfer, and transaction history.
Only the defects above were included in this repository because they are:
- clear
- reproducible
- supported by screenshot evidence
- aligned with the documented requirements and test execution results
