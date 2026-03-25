# Test Plan — ATM Simulator

## 1. Objective
The objective of this test plan is to verify that the ATM Simulator meets defined functional and non-functional requirements and handles both expected and unexpected user behavior reliably.

## 2. Scope

### In Scope
- Balance enquiry
- Deposit
- Withdrawal
- Fund transfer
- Input validation
- Transaction logging
- Data persistence checks
- Negative and boundary testing

### Out of Scope
- Performance benchmarking beyond basic response check
- Security testing
- Multi-user concurrency testing
- GUI and accessibility testing

## 3. Test Strategy
Testing will be performed manually using requirement-based test design.

### Test Types
- Functional testing
- Negative testing
- Boundary value testing
- Error handling validation
- Smoke / sanity checks
- Regression re-check after bug fixes

## 4. Test Environment
- Application Type: CLI-based Python application
- Runtime: Python 3.14.3
- OS: Windows 11
- Storage: SQLite

## 5. Entry Criteria
- Latest application build is available
- Test data/accounts are prepared
- Requirements and expected behavior are documented
- Application launches successfully

## 6. Exit Criteria
- All critical and high-priority test cases are executed
- No open critical defects remain
- Test summary is reviewed
- Requirement coverage is completed

## 7. Deliverables
- Requirements specification
- Test scenarios
- Test cases
- Bug reports
- Traceability matrix
- Evidence screenshots / logs
