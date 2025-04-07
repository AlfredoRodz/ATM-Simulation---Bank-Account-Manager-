# ATM-Simulation---Bank-Account-Manager-
#include <iostream>
#include <iomanip>
using namespace std;

// Function prototypes
void checkBalance(double balance);
void deposit(double &balance, double amount);
void withdraw(double &balance, double amount);
void exitSystem();

int main() {
    double balance = 0.0;
    int choice;
    double amount;

    while (true) {
        // ATM menu
        cout << "\nWelcome to the ATM\n";
        cout << "1. Check Balance\n";
        cout << "2. Deposit Money\n";
        cout << "3. Withdraw Money\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                checkBalance(balance);
                break;
            case 2:
                cout << "Enter deposit amount: ";
                cin >> amount;
                deposit(balance, amount);
                break;
            case 3:
                cout << "Enter withdrawal amount: ";
                cin >> amount;
                withdraw(balance, amount);
                break;
            case 4:
                exitSystem();
                return 0; // Exit the program
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    }

    return 0;
}

// Function definitions
void checkBalance(double balance) {
    cout << fixed << setprecision(2);
    cout << "Your current balance is: $" << balance << endl;
}

void deposit(double &balance, double amount) {
    if (amount > 0) {
        balance += amount;
        cout << "Deposited: $" << amount << "\n";
    } else {
        cout << "Deposit amount must be positive.\n";
    }
}

void withdraw(double &balance, double amount) {
    if (amount > 0 && amount <= balance) {
        balance -= amount;
        cout << "Withdrew: $" << amount << "\n";
    } else if (amount <= 0) {
        cout << "Withdrawal amount must be positive.\n";
    } else {
        cout << "Insufficient funds. Withdrawal failed.\n";
    }
}

void exitSystem() {
    cout << "Thank you for using the ATM. Goodbye!\n";
}
