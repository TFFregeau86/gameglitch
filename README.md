# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] The purpose of this game is to create an interactive number-guessing game where the player tries to guess a secret number within a limited number of attempts. The game gives feedback after each guess, showing whether the guess is too high, too low, or correct. It also keeps track of the player’s score and displays a high score to encourage improvement. The project focuses on learning debugging, testing, and managing state in a Streamlit application.
- [ ] During development and testing, several bugs were discovered:

Incorrect Hint Messages
The game sometimes gave the wrong hint, telling players to guess higher when they should guess lower, and vice versa.

New Game Reset Issues
Pressing the “New Game” button did not always reset the game properly. The secret number, score, and attempts were sometimes carried over into the new round.

Unstable Secret Number
The secret number changed unexpectedly because Streamlit reruns the script whenever the user interacts with the app.

Invalid Input Handling
The game allowed invalid inputs such as negative numbers, decimals, or extremely large values without properly rejecting them.

Score Calculation Problems
Players could finish the game with a negative or unfairly low score, even after winning.

History and Attempt Mismatch
The number of attempts and the guess history did not always match, confusing the debug panel.

Library and Import Errors
Errors related to PyArrow and missing modules caused the app to crash when displaying certain data.

Testing and Import Issues
Pytest initially failed due to circular imports and incorrect test setup.

- [ ] To solve these problems, several improvements were made:

Corrected Hint Logic
The check_guess function was fixed so that it always gives accurate “Too High” and “Too Low” messages based on the secret number.

Proper Game Reset
When “New Game” is pressed, all session variables (secret, attempts, score, history, and status) are reset, ensuring a fresh start.

Session State for Secret Number
The secret number is stored in st.session_state, so it is generated only once per game and does not change during reruns.

Improved Input Validation
The parse_guess function was updated to reject empty inputs, non-numbers, decimals, and values outside the allowed range.

Balanced Scoring System
The scoring logic was adjusted to reward faster wins and apply consistent penalties for incorrect or invalid guesses.

Synchronized Attempts and History
Attempts are now only counted for valid guesses, and all guesses are properly stored in history.

Safer Debug Display
Debug output was changed to use st.text() instead of st.write() to avoid dependency issues with pyarrow.

Fixed Testing Structure
Test files were cleaned up so they import functions correctly from logic_utils.py without circular dependencies.

Added High Score Feature
A high score system was implemented using a text file to store and display the best score, improving gameplay motivation.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
