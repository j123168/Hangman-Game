# Hangman-Game
import random

# List of predefined words
words = ["python", "apple", "tiger", "chair", "robot"]

# Randomly choose a word
secret_word = random.choice(words)

# Store guessed letters
guessed_letters = []

# Number of incorrect guesses allowed
incorrect_guesses = 6

print("🎮 Welcome to Hangman Game!")
print("Guess the word one letter at a time.")

# Game loop
while incorrect_guesses > 0:

    # Display the word with underscores
    display_word = ""

    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)

    # Check if player won
    if "_" not in display_word:
        print("🎉 Congratulations! You guessed the word:", secret_word)
        break

    # Take user input
    guess = input("Enter a letter: ").lower()

    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("⚠ Please enter only one alphabet letter.")
        continue

    # Check if already guessed
    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    # Add guess to list
    guessed_letters.append(guess)

    # Check guess
    if guess in secret_word:
        print("✅ Correct guess!")
    else:
        incorrect_guesses -= 1
        print("❌ Wrong guess!")
        print("Remaining chances:", incorrect_guesses)

# If player loses
if incorrect_guesses == 0:
    print("\n💀 Game Over!")
    print("The correct word was:", secret_word)
