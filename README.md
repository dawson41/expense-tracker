# expense-tracker
expense_tracker/
│
├── main.py
└── expenses.csv
import csv
import os

def add_expense(date, description, amount):
    with open('expenses.csv', mode='a', newline='') as file:
        writer = csv.writer(file)
        writer.writerow([date, description, amount])

def view_expenses():
    if not os.path.exists('expenses.csv'):
        print("No expenses recorded yet.")
        return
    with open('expenses.csv', mode='r') as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)

def main():
    while True:
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Exit")
        choice = input("Enter your choice: ")

        if choice == '1':
            date = input("Enter date (YYYY-MM-DD): ")
            description = input("Enter description: ")
            amount = float(input("Enter amount: "))
            add_expense(date, description, amount)
            print("Expense added successfully.")
        elif choice == '2':
            view_expenses()
        elif choice == '3':
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
