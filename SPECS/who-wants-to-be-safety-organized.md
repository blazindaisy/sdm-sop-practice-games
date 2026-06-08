# Spec: Who Wants to be Safety Organized?

**File:** `games/millionaire/index.html`
**Status:** In Progress

## Purpose

A Who Wants to be a Millionaire-style game for reinforcing Safety Organized Practice and SDM concepts. Designed for single-player facilitated sessions — one participant answers questions while a facilitator controls the browser.

## Prize Ladder

15 questions with the following values (checkpoints marked with ★):

| # | Value | Checkpoint |
|---|-------|-----------|
| 1 | $100 | |
| 2 | $250 | |
| 3 | $500 | |
| 4 | $1,000 | ★ |
| 5 | $2,500 | |
| 6 | $5,000 | |
| 7 | $10,000 | |
| 8 | $25,000 | ★ |
| 9 | $50,000 | |
| 10 | $75,000 | |
| 11 | $100,000 | |
| 12 | $250,000 | ★ |
| 13 | $500,000 | |
| 14 | $750,000 | |
| 15 | $1,000,000 | |

If a participant answers incorrectly between checkpoints, they walk away with the last checkpoint reached. Participants can also voluntarily walk away at any time (with confirmation) and keep the last correctly answered question's value.

## Gameplay Flow

1. Start screen — "New Game" button (or "Resume Game" if a session is in progress)
2. Questions displayed one at a time with 4 answer options (A/B/C/D)
3. Participant selects an answer → "Final Answer?" confirmation modal appears
4. Participant confirms → answer is locked in
5. **Correct:** brief correct-answer reveal, then auto-advance to next question (or win screen at Q15)
6. **Incorrect:** reveal the correct answer, then show walk-away screen with checkpoint amount

## Lifelines

Three lifelines, each usable once per game:

- **50/50:** Eliminates two wrong answers, leaving one wrong and the correct answer
- **Phone a Friend:** Pauses the game and shows a modal instructing the facilitator to have the participant consult someone in the room
- **Ask the Audience:** Displays a bar chart of audience vote percentages. Percentages are arbitrary but the correct answer always receives at least 1% more than the next highest option

## Walk Away

- A "Walk Away" button is always visible during gameplay
- Clicking it shows a confirmation modal: "Are you sure you want to walk away with $X?"
- Confirming ends the game and shows the walk-away result screen

## Game Screen Layout

- **Left sidebar:** Vertical prize ladder showing all 15 values; current question highlighted, checkpoints marked, already-answered values shown as passed
- **Center:** Question text + 2×2 answer button grid
- **Top of center:** Three lifeline buttons (disabled/greyed after use)

## Visual Style

- Dark dramatic aesthetic distinct from SOP Jeopardy
- Deep dark navy/slate background (`#0D1117`), not the same teal as Jeopardy
- Antique gold (`#C9A84C`) accents instead of bright amber
- Answer buttons: dark slate, gold border when selected, green on correct, red on wrong
- "Final Answer?" pulse effect on selected answer before reveal

## Facilitator Setup — Question Editor

- "Edit Questions" button in header opens a full-screen edit overlay (same pattern as SOP Jeopardy)
- Sticky header with Save / Reset to Defaults / Cancel buttons
- Edit form shows all 15 questions with: question text, four answer options (A–D), and which option is correct
- Saves to `localStorage` on "Save Changes"
- "Reset to Defaults" restores original questions (with confirmation)

## State Persistence

- Game state saved to `localStorage` (`millionaire_state`) on every answer and lifeline use
- State includes: current question index, lifelines used, 50/50 eliminated options, phase
- On page load: if a game is in progress, offer "Resume Game" alongside "New Game"
- `localStorage` key for questions: `millionaire_questions`

## Navigation

- "← All Games" link in header returns to `index.html`

## Acceptance Criteria

- [ ] Start screen shows New Game (and Resume if applicable)
- [ ] Questions display one at a time with 4 labeled options
- [ ] Selecting an answer triggers "Final Answer?" modal
- [ ] Confirming correct answer advances to next question; game auto-advances
- [ ] Confirming wrong answer reveals correct answer, then shows walk-away screen with checkpoint amount
- [ ] 50/50 eliminates exactly two wrong answers
- [ ] Phone a Friend shows facilitator instruction modal
- [ ] Ask the Audience shows percentage bars; correct answer always leads
- [ ] Walk Away button triggers confirmation; confirmed walk-away ends game
- [ ] Prize ladder updates as player progresses; checkpoints clearly marked
- [ ] Game state persists through page refresh
- [ ] New Game clears state (with confirmation if game is in progress)
- [ ] Edit Questions overlay works; changes persist to localStorage
- [ ] Reset to Defaults restores original question bank with confirmation
- [ ] Page works as a local file with no server
