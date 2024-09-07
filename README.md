# Task # 2
import random
import tkinter as tk
from tkinter import messagebox

def check_guess():
    try:
        guess = int(entry.get())
        global attempts
        attempts = attempts + 1
        difference = abs(guess - number_to_guess)

        # Check the proximity of the guess
        if guess < number_to_guess:
            if difference <= 10:
                result_label.config(text="Low! You are close.")
            else:
                result_label.config(text="Too low! Try again.")
        elif guess > number_to_guess:
            if difference <= 10:
                result_label.config(text="High! You are close.")
            else:
                result_label.config(text="Too high! Try again.")
        else:
            messagebox.showinfo("Congratulations!", f"You guessed the correct number in {attempts} attempts!")
            reset_game()
    except ValueError:
        messagebox.showwarning("Invalid input", "Please enter a valid number.")

def reset_game():
    global number_to_guess, attempts
    number_to_guess = random.randint(1, 100)
    attempts = 0
    result_label.config(text="")



number_to_guess = random.randint(1, 100)
attempts = 0


root = tk.Tk()
root.title("Number Guessing Game")
root.geometry("500x300")


instruction_label = tk.Label(root, text="Guess a number between 1 and 100:")
instruction_label.pack(pady=10)

entry = tk.Entry(root)
entry.pack(pady=5)

check_button = tk.Button(root, text="Check Guess", command=check_guess)
check_button.pack(pady=10)

result_label = tk.Label(root, text="")
result_label.pack(pady=5)

reset_button = tk.Button(root, text="Reset Game", command=reset_game)
reset_button.pack(pady=10)


root.mainloop()
