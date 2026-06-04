# Spec: SOP Jeopardy

**File:** `games/jeopardy/index.html`
**Status:** Complete (v1)

## Purpose

A Jeopardy-style game for reinforcing Safety Organized Practice (SOP) concepts after a training session. Intended for virtual facilitation with screen sharing — the facilitator controls the browser while participants call out answers.

## Game Board

- 5 categories × 4 point values ($100, $200, $300, $400) = 20 questions
- Category headers displayed above each column
- Tiles show the dollar value; disabled (faded) once answered
- Tile and used state persist in localStorage — survives page refresh

## Question Overlay

- Full-screen overlay appears when a tile is clicked
- Shows category name and point value as a label
- Displays question text (supports multi-line via `white-space: pre-line`)
- "Reveal Answer" button shows the answer
- After reveal: "Award Points" and "Close — No Award" buttons appear
- Closing (with or without award) marks the tile as used

## Award Points Flow

- Triggered by "Award Points" button after answer is revealed
- Inline form in the overlay (no page navigation):
  - Name field with autocomplete from existing scorer names
  - Points field pre-filled with the tile value (editable)
  - Enter key submits from either field
- Adding a score updates the scoreboard and closes the overlay
- "Cancel" returns to the post-reveal state

## Scoreboard

- Visible panel on the right side of the board during play
- Shows only players who have answered (no zero entries)
- Sorted by total score descending, with rank numbers
- Scores persist in localStorage
- "New Game" button resets scores and board (with confirmation)
- Supports up to ~30 players

## Question Editor

- "Edit Questions" button in the page header opens a full-screen edit overlay
- Sticky header with Save / Reset to Defaults / Cancel buttons (visible while scrolling)
- Edit form shows all 5 categories with:
  - Editable category name
  - Editable question and answer text for each of the 4 point values
- Saves to localStorage on "Save Changes"
- "Reset to Defaults" restores original questions (with confirmation)
- No coding required — all editing done through the UI

## Navigation

- "← All Games" link in page header returns to platform home (`index.html`)

## Acceptance Criteria

- [ ] Game board renders all 5 categories with correct tiles
- [ ] Clicking a tile opens the question overlay
- [ ] "Reveal Answer" reveals the answer
- [ ] "Award Points" flow allows entering a name and point value
- [ ] Awarding points updates the scoreboard and closes the overlay
- [ ] "Close — No Award" marks tile used without awarding
- [ ] Scoreboard shows only players who have answered, sorted by score
- [ ] Scores and used tiles persist across page refreshes
- [ ] "New Game" clears scores and board after confirmation
- [ ] "Edit Questions" opens editor; changes save and persist
- [ ] "Reset to Defaults" restores original questions after confirmation
- [ ] Page opens and works as a local file with no server
