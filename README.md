#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

#define MAX_ACCOUNTS 100
#define FILENAME "accounts.dat"

struct Account {
    char name[50];
    int age;
    char address[100];
    long accountNumber;
    int pin;
    double balance;
    char phone[15];
};

struct Account accounts[MAX_ACCOUNTS];
int numAccounts = 0;

// Function prototypes
void createAccount();
void viewAccount();
void depositMoney();
void withdrawMoney();
void checkBalance();
void updateAccount();
void deleteAccount();
void listAllAccounts();
void changePIN();
void saveAccounts();
void loadAccounts();
int findAccount(long accountNumber);
int findAccountByName(char* name);

int main() {
    int choice;
    loadAccounts();
    
    while(1) {
        printf("\nBanking Management System\n");
        printf("1. Create Account\n");
        printf("2. View Account Details\n");
        printf("3. Deposit Money\n");
        printf("4. Withdraw Money\n");
        printf("5. Check Balance\n");
        printf("6. Update Account Info\n");
        printf("7. Delete Account\n");
        printf("8. List All Accounts\n");
        printf("9. Change PIN\n");
        printf("0. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1: createAccount(); break;
            case 2: viewAccount(); break;
            case 3: depositMoney(); break;
            case 4: withdrawMoney(); break;
            case 5: checkBalance(); break;
            case 6: updateAccount(); break;
            case 7: deleteAccount(); break;
            case 8: listAllAccounts(); break;
            case 9: changePIN(); break;
            case 0: 
                saveAccounts();
                printf("Thank you for using our banking system!\n");
                exit(0);
            default: printf("Invalid choice!\n");
        }
    }
    return 0;
}

void createAccount() {
    if(numAccounts >= MAX_ACCOUNTS) {
        printf("Maximum number of accounts reached!\n");
        return;
    }
    
    struct Account newAccount;
    int choice;

    printf("Enter name (or 0 to go back): ");
    scanf(" %[^\n]s", newAccount.name);
    if(strcmp(newAccount.name, "0") == 0) return;
    printf("1. Continue\n0. Go back\nEnter choice: ");
    scanf("%d", &choice);
    if(choice == 0) return;

    printf("Enter age (or 0 to go back): ");
    scanf("%d", &choice);
    if(choice == 0) return;
    newAccount.age = choice;
    printf("1. Continue\n0. Go back\nEnter choice: ");
    scanf("%d", &choice);
    if(choice == 0) return;

