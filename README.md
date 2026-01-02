This project is a basic ATM PIN system built using Python to practice the fundamentals of Object-Oriented Programming (OOPS).

The program starts by asking the user to enter an ATM PIN and, after successful verification, displays a menu with different options. Users can check their balance, deposit money, withdraw money, and change their PIN through a menu-driven interface.

This is a beginner-level project created to understand how classes, objects, and basic encapsulation work in real-world style applications. The project helped me gain hands-on experience with writing structured code and applying OOPS concepts in a simple and practical way.

class ATM:


    def __init__(self, pin, balance=0):
        self.pin = pin
        self.balance = balance  
        
    def verify_pin(self):
        entered_pin = int(input("Enter your ATM PIN: "))
        if entered_pin == self.pin:
            print("\n PIN verified successfully")
            return True
        else:
            print("\n Incorrect PIN")
            return False

    def check_balance(self):
        print(f" Current Balance: ₹{self.balance}")

    def deposit(self):
        amount = int(input("Enter amount to deposit: "))
        self.balance += amount
        print(f" {amount} deposited successfully")
        print(f" Current Balance: ₹{self.balance}")

    def withdraw(self):
        amount = int(input("Enter amount to withdraw: "))
        if amount <= self.balance:
            self.balance -= amount
            print(f" {amount} withdrawn successfully")
            print(f" Current Balance: ₹{self.balance}")
        else:
            print("Insufficient balance")
            print(f" Current Balance: ₹{self.balance}")
            print(f" Withdraw less than or equal to the amount in your account or you will be charged 50/- for every wrong transcation")
    def change_pin(self):
        old_pin = int(input("Enter current PIN: "))
        if old_pin == self.pin:
            new_pin = int(input("Enter new PIN: "))
            confirm_pin = int(input("Confirm new PIN: "))
            if new_pin == confirm_pin:
                self.pin = new_pin
                print(" PIN changed successfully")
            else:
                print(" PIN confirmation failed")
        else:
            print(" Incorrect current PIN")

    def menu(self):
        while True:
            print("\n------ ATM MENU ------")
            print("1. Check Balance")
            print("2. Deposit")
            print("3. Withdraw")
            print("4. Change PIN")
            print("5. Exit")

            choice = input("Choose an option: ")

            if choice == "1":
                self.check_balance()
            elif choice == "2":
                self.deposit()
            elif choice == "3":
                self.withdraw()
            elif choice == "4":
                self.change_pin()
            elif choice == "5":
                print("\n Thank you for using the ATM")
                break
            else:
                print(" Invalid option")

    def start(self):
        if self.verify_pin():
            self.menu()



atm = ATM(pin=1234, balance=5000)
atm.start()
