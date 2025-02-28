# Artisan Loan Smart Contract - Advanced Features

## Overview
The Artisan Lend Smart Contract is designed to provide a comprehensive lending platform for artisans and small business owners. The contract handles loan creation, repayments, collateral deposits, and credit score management, with built-in logic for interest rates, penalties, and early repayments.

## Features
- **Credit Score System:** Borrowers are assigned a credit score ranging from 0 to 100, affecting their loan interest rate.
- **Collateral Requirement:** Borrowers must deposit collateral equal to 150% of the loan amount.
- **Flexible Loan Terms:** Loan terms can range from 1 to 365 days, with a minimum daily repayment requirement.
- **Interest Rates:** Interest rates depend on the borrower's credit score, with a base rate of 5% and a minimum of 1%.
- **Penalties and Fees:** Late payments incur a 10% daily penalty, and early repayments are subject to a 2% fee.
- **Loan Repossession:** If payments are missed for over 30 days or exceed five missed payments, the contract owner can repossess the loan.

## Constants
- **Loan Amounts:** Minimum 1 STX, Maximum 10,000 STX.
- **Interest Rate:** Base 5%, minimum 1%.
- **Penalty Rate:** 10% daily.
- **Collateral Ratio:** 150% of the loan amount.
- **Grace Period:** 3 blocks.
- **Maximum Loan Term:** 365 days.

## Data Structures
- **Loans:** Stores loan details, including amount, start date, term length, repayment details, and borrower credit score.
- **Balances:** Stores the balance of each borrower.
- **Collateral Deposits:** Stores the collateral amount deposited by each borrower.
- **Credit Scores:** Stores the credit score of each borrower.

## Functions
### Read-Only Functions
- **get-loan(borrower):** Retrieves loan details for a borrower.
- **get-balance(account):** Retrieves the balance of an account.
- **get-credit-score(borrower):** Retrieves the credit score of a borrower (default 50 if none exists).
- **get-collateral(borrower):** Retrieves the collateral deposited by a borrower.

### Private Helper Functions
- **min-uint(a, b):** Returns the minimum of two unsigned integers.
- **max-uint(a, b):** Returns the maximum of two unsigned integers.
- **calculate-interest-rate(credit-score):** Calculates the interest rate based on the borrower's credit score.
- **calculate-required-collateral(amount):** Calculates the collateral required for a given loan amount.
- **update-credit-score(borrower, is-good-payment):** Updates the borrower's credit score based on repayment behavior.

### Public Functions
- **initialize-credit-score():** Initializes the credit score for a new borrower (default 50).
- **deposit-collateral(amount):** Allows borrowers to deposit collateral.
- **create-loan(amount, term-length):** Creates a new loan if the borrower meets collateral and repayment requirements.
- **make-repayment(amount):** Allows borrowers to make repayments, applying penalties and updating credit scores as needed.
- **repossess-loan(borrower):** Allows the contract owner to repossess a loan if the borrower has excessive missed payments.

## Usage
### Borrower Workflow
1. **Initialize Credit Score:** Call `initialize-credit-score()` to set the default credit score.
2. **Deposit Collateral:** Call `deposit-collateral(amount)` to deposit the required collateral.
3. **Create Loan:** Call `create-loan(amount, term-length)` to request a loan.
4. **Make Repayments:** Call `make-repayment(amount)` to repay the loan, avoiding penalties and maintaining a good credit score.

### Contract Owner Workflow
1. **Monitor Loans:** Use `get-loan(borrower)` to monitor borrower performance.
2. **Repossession:** Call `repossess-loan(borrower)` to seize collateral if payments are excessively missed.

## Error Codes
- **u100:** Owner-only operation.
- **u101:** Loan not found.
- **u102:** Loan already active.
- **u103:** Insufficient balance.
- **u104:** Invalid loan amount.
- **u105:** Invalid repayment amount.
- **u106:** Late penalty applied.
- **u107:** Insufficient collateral.
- **u108:** Invalid loan term.
- **u109:** Early repayment fee applied.
- **u110:** Loan not due for repossession.

## Security Considerations
- **Access Control:** Only the contract owner can repossess loans.
- **Collateral Management:** Collateral is securely locked until the loan is fully repaid.
- **Credit Score Updates:** Repayment behavior directly affects credit scores, incentivizing timely payments.

## Conclusion
This Artisan Lend Smart Contract provides a robust, transparent, and fair lending system tailored for artisans and small business owners. Its advanced features ensure responsible lending, timely repayments, and credit-building opportunities, fostering financial growth within the community.

