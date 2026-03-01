# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
Bug 1 — Hints Are Backwards
Sometimes the game told me to guess higher when my number was already too high, and told me to guess lower when my number was too low.

Bug 2 — New Game Doesn’t Work
When I press “New Game,” the game does not reset, and I cannot start over properly.

Bug 3 — Out-of-Range Numbers Are Allowed
The game allows numbers below 1 or above 100. When I enter them, it gives incorrect hints instead of rejecting the input.
---

## 2. How did you use AI as a teammate?

AI tools used:
I used ChatGPT to help analyze bugs, understand errors, and improve my code.

Correct AI suggestion: AI suggested that my history and attempts were mismatched because attempts started at 1 and history was not always updated. I verified this by checking the debug info and fixing the counter. After the fix, attempts and history matched.

Misleading AI suggestion: At first, AI suggested that the score problem was only caused by one line of code, but later I realized the scoring system itself was unbalanced. I verified this by calculating scores manually and testing multiple games.

---

## 3. Debugging and testing your fixes

How I knew bugs were fixed: I used the debug panel and checked if attempts, history, score, and secret number stayed consistent after each guess.
One test I ran: I used pytest to test check_guess with values like:

check_guess(50, 50) → “Win”
check_guess(60, 50) → “Too High”
check_guess(150, 50) → “Invalid”

This showed that my logic worked correctly.

How AI helped with tests:
ChatGPT helped me design test cases for edge cases like out-of-range numbers and explained why my original tests were not working.

---

## 4. What did you learn about Streamlit and state?

Why the secret kept changing: The secret number changed because Streamlit reruns the app every time the user interacts, and the secret was being recreated instead of saved.

Explaining reruns and session state: Streamlit reruns the whole program whenever something changes. Session state is like memory that saves values so they don’t reset every time.

What fixed it: I stored the secret number in st.session_state so it only gets created once per game.

---

## 5. Looking ahead: your developer habits

One habit I will reuse: I will always test my code using small examples and debug output before assuming it works.

One thing I’d do differently with AI: Make sure it understands what I am trying to ask it.

How this project changed my view of AI code: This project taught me that AI-generated code is helpful, but it often contains bugs. I need to understand and test the code instead of trusting it blindly.
