# final_project_simple.py
# This program allows the user to use a calculator or play a quiz game.

def display_menu():
    print("\nMain Menu:")
    print("1. Calculator")
    print("2. Quiz Game")
    print("3. Exit")

def get_valid_number(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a number.")

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Cannot divide by zero"
    return a / b

def calculator():
    print("\nCalculator")
    print("Select Operation:")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")

    operation = input("Enter operation (1/2/3/4): ")

    if operation in ['1', '2', '3', '4']:
        num1 = get_valid_number("Enter first number: ")
        num2 = get_valid_number("Enter second number: ")

        if operation == '1':
            result = add(num1, num2)
        elif operation == '2':
            result = subtract(num1, num2)
        elif operation == '3':
            result = multiply(num1, num2)
        elif operation == '4':
            result = divide(num1, num2)

        print("Result:", result)
    else:
        print("Invalid operation selected.")

def quiz_game():
    print("\nQuiz Game")
    questions = [
        {
            "question": "What is the capital of France?",
            "options": ["A. Paris", "B. London", "C. Berlin"],
            "answer": "A"
        },
        {
            "question": "Which language is used to write this program?",
            "options": ["A. Java", "B. Python", "C. C++"],
            "answer": "B"
        },
        {
            "question": "What is 2 + 2?",
            "options": ["A. 3", "B. 4", "C. 5"],
            "answer": "B"
        }
    ]

    score = 0

    for q in questions:
        print("\n" + q["question"])
        for opt in q["options"]:
            print(opt)
        answer = input("Your answer (A/B/C): ").upper()
        if answer == q["answer"]:
            print("Correct!")
            score += 1
        else:
            print("Incorrect. The correct answer was", q["answer"])

    print("\nYour total score is:", score, "out of", len(questions))

def main():
    while True:
        display_menu()
        choice = input("Enter your choice (1/2/3): ")

        if choice == '1':
            calculator()
        elif choice == '2':
            quiz_game()
        elif choice == '3':
            print("Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice. Please select from the menu.")

# Entry point
if __name__ == "__main__":
    main()
