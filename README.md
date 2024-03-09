# CODSOFT
Welcome to my Python Mini Projects repository! This collection of small but mighty projects is designed to showcase fundamental programming concepts through fun and interactive applications. 
# **PYTHON PROGRAMMING**

# **TASK: CALCULATOR**

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y == 0:
        return "Cannot divide by zero"
    return x / y

print("Select operation:")
print("1. Add")
print("2. Subtract")
print("3. Multiply")
print("4. Divide")

choice = input("Enter choice (1/2/3/4): ")

num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

if choice == '1':
    print("Result:", add(num1, num2))
elif choice == '2':
    print("Result:", subtract(num1, num2))
elif choice == '3':
    print("Result:", multiply(num1, num2))
elif choice == '4':
    print("Result:", divide(num1, num2))
else:
    print("Invalid input")


# **TASK: PASSWORD GENERATOR**

import random
import string

def generate_password(length, complexity):
    characters = {
        1: string.ascii_lowercase, 
        2: string.ascii_lowercase + string.ascii_uppercase, 
        3: string.ascii_lowercase + string.ascii_uppercase + string.digits, 
        4: string.ascii_lowercase + string.ascii_uppercase + string.digits + string.punctuation 
    }

    complexity = max(min(complexity, 4), 1)

    chosen_characters = characters[complexity]

    password = ''.join(random.choice(chosen_characters) for _ in range(length))
    
    return password

def main():
    print("Welcome to the Password Generator!")

    length = int(input("Enter the desired length of the password: "))

    complexity = int(input("Enter the desired complexity (1-4):\n1. Just lowercase letters\n2. Lowercase and uppercase letters\n3. Letters and numbers\n4. Letters, numbers, and symbols\nYour choice: "))

    password = generate_password(length, complexity)

    print(f"Your new password is: {password}")

if __name__ == "__main__":
    main()


# **TASK: Rock-Paper-Scissors Game**

import random

def get_user_choice():
    while True:
        user_choice = input("Choose rock, paper, or scissors: ").lower()
        if user_choice in ['rock', 'paper', 'scissors']:
            return user_choice
        else:
            print("Invalid choice. Please choose rock, paper, or scissors.")

def get_computer_choice():
    return random.choice(['rock', 'paper', 'scissors'])

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == 'rock' and computer_choice == 'scissors') or \
         (user_choice == 'paper' and computer_choice == 'rock') or \
         (user_choice == 'scissors' and computer_choice == 'paper'):
        return "You win!"
    else:
        return "Computer wins!"

def main():
    user_score = 0
    computer_score = 0

    while True:
        print("\nRock, Paper, Scissors Game")
        print("---------------------------")
        user_choice = get_user_choice()
        computer_choice = get_computer_choice()

        print(f"\nYou chose: {user_choice}")
        print(f"Computer chose: {computer_choice}")

        result = determine_winner(user_choice, computer_choice)
        print(result)

        if result == "You win!":
            user_score += 1
        elif result == "Computer wins!":
            computer_score += 1

        print(f"\nScore - You: {user_score}, Computer: {computer_score}")

        play_again = input("\nDo you want to play again? (yes/no): ").lower()
        if play_again != 'yes':
            print("Thanks for playing!")
            break

if __name__ == "__main__":
    main()
