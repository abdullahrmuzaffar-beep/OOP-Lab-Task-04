# OOP-Lab-Task-04
class Account
{
    int accountNumber;
    String holderName;
    double balance;

    Account(int accountNumber, String holderName, double balance) 
    {
        this.accountNumber = accountNumber;
        this.holderName = holderName;
        this.balance = balance;
    }

    void displayInfo() 
    {
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Holder Name: " + holderName);
        System.out.println("Balance: " + balance);
    }
}

class SavingsAccount extends Account 
{
    double interestRate; 

    SavingsAccount(int accountNumber, String holderName, double balance, double interestRate)
    {
        super(accountNumber, holderName, balance);
        this.interestRate = interestRate;
    }

    void displayInfo() 
    {
        System.out.println("--- Savings Account ---");
        super.displayInfo();
        System.out.println("Interest Rate: " + interestRate + "%");
        System.out.println("Yearly Interest: " + (balance * interestRate / 100));
    }
}

class CurrentAccount extends Account
{
    double overdraftLimit;

    CurrentAccount(int accountNumber, String holderName, double balance, double overdraftLimit) 
    {
        super(accountNumber, holderName, balance);
        this.overdraftLimit = overdraftLimit;
    }
    void displayInfo() 
    {
        System.out.println("--- Current Account ---");
        super.displayInfo();
        System.out.println("Overdraft Limit: " + overdraftLimit);
        System.out.println("Available Funds: " + (balance + overdraftLimit));
    }
}

public class main
{
    public static void main(String[] args)
    {
        Account a = new Account(1001, "Usman", 20000);
        SavingsAccount s = new SavingsAccount(1002, "Ali", 100000, 5);
        CurrentAccount c = new CurrentAccount(1003, "Sara", 50000, 25000);

        a.displayInfo();
        System.out.println();
        s.displayInfo();
        System.out.println();
        c.displayInfo();

        System.out.println("\n ==== Using parent reference ===");
        Account[] accounts = { s, c };
        for (Account acc : accounts)
        {
            acc.displayInfo();
            System.out.println();
        }
    }
}
