# Test Scenarios — ATM Simulator

## TS-001 Authentication
Verify that login succeeds with valid credentials and fails with invalid credentials.

## TS-002 Balance Enquiry
Verify that the system displays the correct balance for the logged-in account and reflects recent successful transactions.

## TS-003 Deposit
Verify that a valid positive deposit updates the balance correctly and is recorded in transaction history.

## TS-004 Deposit Validation
Verify that deposit rejects negative, zero, non-numeric, and other invalid values without changing balance data.

## TS-005 Withdrawal
Verify that a valid withdrawal with sufficient balance is processed correctly and recorded in transaction history.

## TS-006 Withdrawal Validation
Verify that withdrawal rejects amounts exceeding balance, zero, negative, and invalid input values.

## TS-007 Transfer
Verify that a valid transfer updates both source and destination accounts correctly.

## TS-008 Transfer Validation
Verify that transfer rejects non-existent destination accounts, same-account transfer, insufficient balance, and invalid amounts.

## TS-009 Transaction History
Verify that successful transactions are recorded and visible in history, and that empty history is handled safely.

## TS-010 Input Handling and Stability
Verify that invalid input produces clear validation messages and does not crash the application.
