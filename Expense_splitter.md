# EXPENSE-SPLITTER-USING-PYTHON
def split_expenses():
    num_people = int(input("Enter the number of people: "))

    # Get the names of the people
    people = []
    for i in range(num_people):
        name = input(f"Enter the name of person {i+1}: ")
        people.append(name)

    # Initialize a dictionary to store expenses
    expenses = {name: 0.0 for name in people}

    while True:
        # Get expense details
        expense_description = input("Enter expense description (or 'done' to finish): ")
        if expense_description.lower() == 'done':
            break
        
        amount = float(input("Enter the amount: "))
        payer = input("Who paid? Enter the name: ")
                # Update the expenses dictionary
        if payer in expenses:
            expenses[payer] += amount
        else:
            print(f"{payer} is not in the list of people.")

        # Split the expense among everyone
        split_amount = amount / num_people
        for person in people:
            if person != payer:
                expenses[person] -= split_amount
            else:
                expenses[person] += (amount - split_amount)

    split_expenses()
