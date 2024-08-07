# CBT-CIP
Java ATM Machine
import java.util.Scanner;

class ATM {
    private int correctPin = 1234;  // Hardcoded PIN for simplicity
    private double balance = 1000.0; // Initial balance

    public void checkPin() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your PIN: ");
        int enteredPin = scanner.nextInt();

        if (enteredPin == correctPin) {
            System.out.println("PIN accepted.");
            menu();
        } else {
            System.out.println("Incorrect PIN. Try again.");
            checkPin();
        }
       scanner.close();
    }

    private void menu() {
        System.out.println("enter your choice");
        System.out.println("1.check A/C balance");
        System.out.println("2.withdraw money");
        System.out.println("3.deposit money");
        System.out.println("4.EXIT");

        Scanner scanner=new Scanner(System.in);
        int opt=scanner.nextInt();
        if(opt==1)
        {
            checkBalance();
        }
        else if(opt==2)
        {
            withdrawMoney();
        }
        else if(opt==3)
        {
            depositMoney();
        }
        else if(opt==4)
        {
            System.out.println("Thankyou for choosing ATM");
            
        }
        else{
            System.out.println("Enter a valid choice");
        }
        scanner.close();
        
    }

    private void checkBalance() {
        System.out.println("Your current balance is: " + balance);
        menu();
    }

    private void withdrawMoney() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter amount to withdraw: ");
        int amount = scanner.nextInt();

        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Successfully withdrew " + amount);
            System.out.println("Your new balance is: " + balance);
            menu();
        } else {
            System.out.println("Invalid amount or insufficient balance.");
            menu();
        }
       scanner.close();
    }

    private void depositMoney() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter amount to deposit: ");
        int amount = scanner.nextInt();

        if (amount > 0) {
            balance += amount;
            System.out.println("Successfully deposited " + amount);
            System.out.println("Your new balance is: " + balance);
        } else {
            System.out.println("Invalid deposit amount");
            menu();
        }
        scanner.close();
    }
    
}
 class ATMMachine {
    public static void main(String[] args) {
        ATM atm = new ATM();
        atm.checkPin();
    }
}
      
     
