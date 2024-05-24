# Bank-Management-System

This repository contains a simple Bank Management System implemented in Java. The system allows for the creation and management of bank accounts, customers, and a bank entity. It supports basic operations such as deposit, withdrawal, and interest calculation for different types of accounts.

## Features

- **Bank Accounts**
  - Current Bank Account
  - Savings Bank Account
- **Customer Operations**
  - Deposit money into an account
  - Withdraw money from an account
- **Bank Operations**
  - Display details of all customers and their accounts

## Class Structure

### BankAccount (Abstract Class)

Represents a generic bank account with the following properties:
- Interest Rate
- Account Balance
- Account Number
- Account Type (Savings or Current)

Provides methods for:
- Deposit
- Withdraw
- Print Account Details
- Abstract method for paying interest

### CurrentBankAccount (Extends BankAccount)

Represents a current bank account with a specific interest rate.

### SavingsBankAccount (Extends BankAccount)

Represents a savings bank account with a specific interest rate.

### Customer

Represents a customer with the following properties:
- Customer Name
- Customer ID
- List of Bank Accounts

Provides methods for:
- Deposit money into an account
- Withdraw money from an account
- Print Customer Details

### Bank (Final Class)

Represents a bank with the following properties:
- Bank Name
- IFSC Code
- List of Customers

Provides methods for:
- Print Bank Details

## Usage

To run the Bank Management System, compile and execute the `Main` class.

```java
public class Main {
    public static void main(String[] args) {
        List<BankAccount> accounts1 = new ArrayList<>();
        accounts1.add(new SavingsBankAccount(8000));
        accounts1.add(new SavingsBankAccount(8000));
        accounts1.add(new CurrentBankAccount(6000));

        List<BankAccount> accounts2 = new ArrayList<>();
        accounts2.add(new CurrentBankAccount(5000));
        accounts2.add(new CurrentBankAccount(1000));

        Customer saurav = new Customer("Saurav Kumar", "ID-001", accounts1);
        Customer anandSagar = new Customer("Anand Sagar", "ID-002", accounts2);

        Bank SBI = new Bank("SBI HUBLI B1", "SBI000012", List.of(saurav, anandSagar));

        saurav.deposit(102, 1000); // This account does not exist
        saurav.deposit(772682, 2000); // This account exists and 2000 will be deposited in this account

        saurav.withdraw(772682, 13879348); // Withdrawing more than the balance
        saurav.withdraw(772682, 1500); // Withdrawing within the balance

        SBI.printDetails();
    }
}
