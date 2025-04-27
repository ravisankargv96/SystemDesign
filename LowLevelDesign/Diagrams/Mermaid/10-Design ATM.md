```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction BT
    class ATM {
        - BANKINGSERVICE : BankingService
        - CASHDISPENSER : CashDispenser
        - TRANSACTIONCOUNTER : AtomicLong$

        + ATM(BankingService bankingService, CashDispenser cashDispenser)
        + authenticateUser(Card card) void
        + checkBalance(String accountNumber) double
        + withdrawCash(String accountNumber, double amount) void
        + depositCash(String accountNumber, double amount) void
        - generateTransactionId() String
    }

    ATM o--> BankingService
    ATM *--> CashDispenser
    ATM --> Card

    class Account {
        - ACCOUNTNUMBER : String
        - balance : double

        + Account(String accountNumber, double balance)
        
        + getAccountNumber() String
        + getBalance() double
        + debit(double amount) void
        + credit(double amount) void
    }

    class BankingService {
        - ACCOUNTS : Map~String, Account~
        + createAccount(String accountNumber, double initialBalance) void
        + getAccount(String accountNumber) Account
        + processTransaction(Transaction transaction) void
    }

    BankingService *--> Account
    BankingService --> Transaction

    class Card {
        - CARDNUMBER : String
        - PIN : String
        + Card(String cardNumber, String pin)
        + getCardNumber() String
        + getPin() String
    }

    class CashDispenser {
        - cashAvailable : int
        + CashDispenser(int initialCash)
        + dispenseCash(int amount) sync
    }

    class Transaction {
        <<abstract>>
        # TRANSACTIONID : String
        # ACCOUNT : Account
        # AMOUNT : Double
        + Transaction(String transactionId, Account account, double amount)
        + execute() void*
    }

    class DepositTransaction {
        + DepositTransaction(String transactionId, Account account, double amount)
        + execute() void
    }

    class WithdrawalTransaction{
        + WithdrawalTransaction(String transactionId, Account account, double amount)
        + execute() void
    }

    DepositTransaction --|> Transaction
    WithdrawalTransaction --|> Transaction
```

```java
public class ATMDemo {
	public static void run() {
		BankingService bankingService = new BankingService();
		CashDispenser cashDispenser = new CashDispenser(10000);
		ATM atm = new ATM(bankingService, cashDispenser);

		// Create sample accounts
		bankingService.createAccount("1234567890", 1000.0);
		bankingService.createAccount("9876543210", 500.0);

		// Perform ATM operations
		Card card = new Card("1234567890", "1234");
		atm.authenticateUser(card);

		double balance = atm.checkBalance("1234567890");
		println("Account balance: "+ balance);


		atm.withdrawCash("1234567890", 500.0);
		atm.depositCash("9876543210", 200.0);

		balance = atm.checkBalance("1234567890");
		println("Updated account balance: " + balance);
	}
}
```
