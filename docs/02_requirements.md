# Requirements Specification — ATM Simulator

## 1. Introduction

### 1.1 Purpose
This document defines the functional and non-functional requirements for the ATM Simulator system.
The purpose is to establish a clear baseline for testing and validation.

### 1.2 System Overview
The system under test is a CLI-based ATM Simulator that allows users to perform basic banking operations such as:

- User authentication
- Balance enquiry
- Deposit
- Withdrawal
- Fund transfer
- Transaction history

### 1.3 Source
These requirements are derived from the application:

👉 https://github.com/enayetrashid/atm-simulator

They have been formalized from a QA perspective for validation and testing.

---

## 2. Functional Requirements

### FR-001: User Authentication

**Description:**  
The system shall authenticate a user using a valid account number and PIN before granting access to the main menu.

**Acceptance Criteria:**
- Login succeeds when a valid account number and matching PIN are entered
- Login fails when the PIN is incorrect
- Login fails when the account number does not exist
- On failed login, the system displays a clear validation message and does not grant access

---

### FR-002: Balance Enquiry

**Description:**  
The system shall allow an authenticated user to view the current account balance.

**Acceptance Criteria:**
- The system displays the correct balance for the logged-in account
- The balance reflects all previous successful transactions
- The response is shown immediately after selection
- Balances are displayed with exactly two decimal places
- Very large balances display without overflow

---

### FR-003: Deposit Funds

**Description:**  
The system shall allow an authenticated user to deposit money into their account.

**Acceptance Criteria:**
- The system accepts only positive numeric values greater than 0 as a valid deposit amount
- The balance is increased correctly after deposit
- A successful deposit is logged with transaction type, amount, and timestamp
- If zero is entered, the system displays a validation error and prompts the user to re-enter an amount; balance remains unchanged
- If a negative amount is entered, the system displays a validation error and balance remains unchanged
- The system displays a clear validation message if a non-numeric value is entered
- Large valid deposit amounts are processed without corrupting balance data

---

### FR-004: Withdraw Funds

**Description:**  
The system shall allow an authenticated user to withdraw money from their account.

**Acceptance Criteria:**
- The system allows withdrawal only if sufficient balance exists
- The balance is reduced correctly after a successful withdrawal
- A successful withdrawal is logged with transaction type, amount, and timestamp
- If the requested amount exceeds the available balance, the system displays "Insufficient funds", does not modify the balance, and returns the user to the menu
- The system rejects negative values, zero, and non-numeric input
- If the withdrawal amount equals the current balance, the withdrawal succeeds and the remaining balance becomes 0.00

---

### FR-005: Fund Transfer

**Description:**  
The system shall allow an authenticated user to transfer funds to another valid account.

**Acceptance Criteria:**
- For a valid transfer, amount X moves from source account A to destination account B and both balances update correctly
- The destination account must exist
- The source and destination accounts must not be the same
- The source account must have sufficient balance
- The transfer is rejected with a validation error if the amount entered is zero, negative, or non-numeric
- Successful transfer activity is recorded in transaction history
- On any rejection, no balance changes occur

---

### FR-006: Transaction History

**Description:**  
The system shall record and display transaction history for the account.

**Acceptance Criteria:**
- Each successful deposit, withdrawal, and transfer creates the required transaction record(s)
- Each record includes transaction type, amount, account number, and timestamp
- Failed or rejected operations are not logged as successful transactions
- Transaction records are permanent and are not deleted or modified by any user-facing operation
- Transaction history displays all records for the account
- If no records exist, the system displays "No transactions found"

---

## 3. Non-Functional Requirements

### NFR-001: Performance
- System response time should be less than 2 seconds for all standard operations

### NFR-002: Reliability
- The system should not crash due to invalid input
- The system should maintain consistent balances and transaction data

### NFR-003: Usability
- Error messages should be clear and user-friendly
- The system should guide users when valid input is required

### NFR-004: Data Persistence
- Account data and transaction history should persist between sessions

---

## 4. Assumptions
- The system operates in a single-user CLI environment
- Authentication is handled using account number and PIN
- Only basic banking operations are considered

## 5. Constraints
- CLI-based interface only
- No external API integration
- Limited to local data storage
