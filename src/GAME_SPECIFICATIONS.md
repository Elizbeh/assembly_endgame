# Assembly Game - Specification Document
1. Overview

Project Name: Assembly Game
Description: An interactive word-guessing game where the player must guess a hidden programming-related word (e.g., “react”) by selecting letters on a virtual keyboard. The game tracks correct and incorrect guesses, provides visual feedback, and indicates win/loss conditions. Additional features include farewell messages for wrong guesses, visual confetti for wins, and accessible feedback for screen readers.

2. Functional Requirements
2.1 Game Logic

Hidden Word: Stored in currentWord.

Guessed Letters: Stored in guessedLetters array.

Correct Guess: Letter exists in the word; highlighted green on the keyboard.

Wrong Guess: Letter does not exist in the word; highlighted red on the keyboard.

Win Condition: All letters in the hidden word have been guessed.

Loss Condition: Number of wrong guesses ≥ total allowed (length of languages array).

2.2 User Interface
Keyboard

Displays letters A-Z.

Correctly guessed letters are highlighted in green.

Incorrectly guessed letters are highlighted in red.

Unused letters remain in default color.

Disabled once the game ends.

Word Display

Hidden letters appear as empty boxes initially.

Correctly guessed letters are revealed in uppercase.

On game loss, unguessed letters are revealed with red highlight (missed-letter).

Languages / Chips

Each chip represents an attempt or theme.

Chips corresponding to incorrect guesses display a “💀” overlay.

Game Status

Displays “You Win!” with a congratulatory message and confetti if the player wins.

Displays “Game Over!” with a losing message if the player loses.

Farewell messages appear when a wrong guess occurs during the game.

Status background colors:

Win: green (#10A95B)

Loss: red (#BA2A2A)

Farewell: purple (#7A5EA7)

New Game Button

Appears when the game ends.

Resets all state values (currentWord, guessedLetters) and clears highlights.

2.3 Accessibility

Keyboard buttons include aria-pressed, aria-disabled, and descriptive aria-label.

Game status section includes aria-live="polite" messages for screen readers.

Screen reader-only section announces the correctness of the last guess and remaining attempts.

3. State Management

React useState Hooks:

currentWord → string

guessedLetters → array of letters

Derived State:

wrongGuessCount → number of incorrect guesses

isGameWon → true if all letters guessed

isGameLost → true if wrong guesses exceed limit

isGameOver → true if won or lost

isLastGuessIncorrect → true if last guessed letter is wrong

4. UI Layout
Header
---------------------------------
| Assembly Game Logo & Title   |
---------------------------------
Language Chips (attempts)
---------------------------------
Word Display (letters)
---------------------------------
Keyboard Section (A-Z buttons)
---------------------------------
Game Status (Win/Loss/Farewell message)
---------------------------------
New Game Button (appears on game end)

5. Styling

Background: dark (#262626)

Text: light (#D9D9D9)

Correct letters: green (#10A95B)

Wrong letters: red (#EC5D49)

Missed letters (revealed on loss): red (#BA2A2A)

Chips: colored backgrounds as per languages array

Lost chip overlay: semi-transparent black with skull emoji

Farewell messages: purple background, dashed border

Confetti: displayed when player wins

6. Future Enhancements

Add timer to measure completion speed.

Support multiple difficulty levels (e.g., word length, allowed attempts).

Include hints after a number of incorrect guesses.

Add sound effects for correct and incorrect guesses.

Support different themes and multilingual words.

7. Technologies Used

React (17+)

JavaScript / JSX

CSS / Flexbox

clsx for conditional class management

react-confetti for celebratory effects (optional)

8. File Structure
/src
  /components
    Header.jsx
    AssemblyEndgame.jsx
  /assets
    logo.png
  /styles
    styles.css
/languages.js
/utils.js
index.jsx
package.json
README.md
SPECIFICATION.md

9. Notes

Fully client-side; no backend required.

Uses state-driven UI with React hooks.

Supports responsive design for desktop and mobile.

Accessibility considerations included (aria attributes, screen reader updates).

Visual feedback for wins, losses, and incorrect guesses is built-in.

clsx library manages dynamic class assignments for styling based on game state.