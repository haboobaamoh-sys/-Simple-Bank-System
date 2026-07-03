# Simple Bank System

A simple Java console application that allows customers to open and manage bank accounts. The system supports basic banking operations like deposits, withdrawals, transfers, checking balances, and printing account statements while strictly enforcing real-time financial rules.

---

## Features

* **Customer Management:** Create a new customer profile by name.
* **Account Flexibility:** Customers can own multiple accounts under different types (Savings / Current).
* **Core Operations:** Perform dynamic Deposits, Withdrawals, and Transfers using text-based account numbers.
* **Live Inquiries:** Check account balances and print a formatted transaction statement with timestamps.

---

## Account Types & Rules

### Savings Account:
* Must maintain a strict minimum balance of **500 EGP** at all times.
* Any withdrawal or transfer that pushes the balance below 500 EGP will be immediately rejected with an error.

### Current Account:
* Includes an overdraft allowance, meaning the balance can go negative.
* The balance cannot drop below the overdraft limit of **-1000 EGP**. Any transaction exceeding this limit will fail.

---

## Validations & Error Handling

The system will print an error message and cancel the operation if:
* The deposit, withdrawal, or transfer amount is zero or negative.
* A withdrawal or transfer violates the specific account type balance rules.
* A transfer fails because the source account does not have enough funds.
* An account number typed into the console does not exist in the system.

---

## File Structure

The project is split into 5 clear files to keep the code organized and easy to read:
1. `Transaction.java`: Stores details for individual actions (Type, Amount, Timestamp, and Balance after the action).
2. `BankAccount.java`: Contains core financial math, balance updates, and account-specific rule validations.
3. `Customer.java`: Holds the customer's name and links them to their owned bank accounts using a map.
4. `BankSystem.java`: The primary controller that stores all global accounts and routes traffic between them using text IDs.
5. `Main.java`: The entry point running the interactive `Scanner` menu loop inside the terminal.

---

## How to Run & Test

Run the `Main.java` file and follow the console prompts. 

### Example Test Case:
```text
Account: [ACC-001 | Savings | Balance: 2000 EGP]

Deposit 500 EGP → Balance: 2500 EGP
Withdraw 2100 EGP → Error: Cannot go below minimum balance (500 EGP)
Withdraw 1500 EGP → Balance: 1000 EGP
Transfer 600 EGP to ACC-002 → Balance: 400 EGP insufficient funds

--- Statement for ACC-001 ---
[2026-07-03 10:00] Deposit +500.0 EGP | Balance: 2500.0 EGP
[2026-07-03 10:05] Withdrawal -1500.0 EGP | Balance: 1000.0 EGP
