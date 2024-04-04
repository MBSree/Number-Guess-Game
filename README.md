
# Number Guessing Game

A simple console-based Number Guessing Game implemented in Python. Try to guess the correct number between 1 and 100 within a limited number of attempts.

## Rules

- The game randomly selects a number between 1 and 100.
- The player has a limited number of attempts to guess the correct number.
- After each guess, the game provides feedback on whether the guess was too high or too low.
- The game ends when the player correctly guesses the number or runs out of attempts.

## Features

- Adjustable difficulty levels: 'easy' (10 turns) and 'hard' (5 turns).
- Feedback on the remaining number of attempts.
- Clear interface with the game logo.

## How to Play

1. Run the Python script in a console or terminal.
2. Choose the difficulty level: 'easy' or 'hard'.
3. Guess the correct number within the specified number of attempts.

## Code Structure

- `check_answer(guess, answer, turns)`: Function to check the user's guess against the correct answer.
- `set_difficulty()`: Function to set the difficulty level (number of turns).
- `game()`: Main function to initiate and control the game.

## Usage

1. Run the Python script.
2. Follow the prompts to choose the difficulty level and make guesses.
3. Try to guess the correct number within the given attempts.

## Example

```python
from random import randint
from art import logo

from random import randint
from art import logo

EASY_LEVEL_TURNS = 10
HARD_LEVEL_TURNS = 5
turns = 0


#Function to check user's guess against actual answer.
def check_answer(guess, answer, turns):
  """checks answer against guess. Returns the number of turns remaining."""
  if guess > answer:
    print("Too high.")
    return turns - 1
  elif guess < answer:
    print("Too low.")
    return turns - 1
  else:
    print(f"You got it! The answer was {answer}.")


#Make function to set difficulty.
def set_difficulty():
  levels = input("Choose a difficulty. Type 'easy' or 'hard': ")
  level = levels.lower()
  if level == "easy":
    global turns
    return EASY_LEVEL_TURNS
  else:
    return HARD_LEVEL_TURNS


def game():
  print(logo)
  #Choosing a random number between 1 and 100.
  print("Welcome to the Number Guessing Game!")
  print("I'm thinking of a number between 1 and 100.")
  answer = randint(1, 100)
  print(f"Pass, The correct answer is {answer}")

  turns = set_difficulty()

  guess = 0
  while guess != answer:
    print(f"you have {turns} attempts remaining to guess the number.")

    #Let the user guess a number.
    guess = int(input("Make a guess: "))

    turns = check_answer(guess, answer, turns)
    if turns == 0:
      print("You've run out of guesses, you lose.")
      return
    elif guess != answer:
      print("Guess again.")

game()
