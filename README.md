# Othello

This is my Othello game that I made with HTML, CSS and JavaScript. It uses React for the screen. You can play against the computer or play with another person on the same computer.

## How to start

1. Download or open this project.
2. Open `othello.html` in a web browser.
3. Pick one player or two players.
4. Type your name. If you play with two people, you can type both names.
5. If you play alone, choose Black or White.
6. Press **Start game**.

You do not need to install anything or run a server. You need internet because React, ReactDOM, HTM and the Fredoka font load from online links.

## How to play

- Black goes first.
- Click a glowing pink space to put down a piece.
- Your move must trap one or more of the other player's pieces between your pieces. The trapped pieces change to your color.
- If you have no move, your turn is skipped.
- The game ends when neither player can move. The player with more pieces wins.
- In one player mode, the computer takes its turn by itself. If you pick White, the computer goes first.
- **Make move** lets the computer pick a move for whoever has the current turn. You can use it in both game modes.
- Press the arrow button in the top-left corner to go back to the start screen.

## Game options

- **Table colors:** Choose one of the five color circles on the right. The choices are classic brown, lavender, pink, blue, and peach.
- **Level:** Click the Level button to pick Easy, Medium, or Hard. Easy looks 2 turns ahead, Medium looks 4 and Hard looks 6. The game starts on Easy. A harder level can take longer to move.
- **Dev mode:** Turn this on to see extra game information and tools.
- **Player names:** Click a name above the board to change it.

The toolbar is on the right like in my reference picture. It has five color circles, a ring around the color I picked, and rounded buttons for Level and Dev mode. The layout also gets smaller for phone screens.

## Other things in the game

- A kangaroo on the start screen that hops and waves.
- An 8 by 8 board with black and white pieces.
- Pink glowing dots that show where you can play.
- A flip animation when pieces change color.
- The score for both players above the board.
- A message for whose turn it is, when someone has to pass, and who wins or if it is a draw.
- Five themes: brown, lavender, pink, blue and peach. You can change the theme before or during a game.
- The back arrow takes you to the start screen so you can start a new game.
- A game over popup that matches the theme and shows the final score. If I beat the computer, it says **You win!** and drops confetti. In two player mode, it celebrates the winning player too.
- **Play again** starts a fresh board with the same names and settings. **View board** closes the popup so I can see the last board, and there is a **Restart game** button below it. Pressing Escape also closes the popup.

## How the computer plays

I used minimax to let the computer look at possible moves and the other player's replies. It picks the move with the best score from its search.

The score looks at good board spaces like corners, how many moves each side can make, and the piece count near the end. When the game is over, it scores the win, loss or draw. Alpha-beta pruning is on by default to skip parts of the search that will not change its choice.

## Dev mode tools

There is a little thinking box beside the board, between the game and the color toolbar. It matches the theme with a light transparent background and a small animated fox drawing. It shows the last move picked, positions checked, search time, depth and alpha-beta setting. These are the real search results. On small screens the box goes below the board so everything still fits.

Turn on Dev mode for the extra controls. You can also:

- Turn Debug on to see search paths, their scores and which branches got pruned inside the thinking box. The paths scroll inside their own little area, with up to 1,500 lines for each search.
- Turn alpha-beta pruning on or off. This helps the computer skip some moves it does not need to check.
- Change the search depth from 1 to 8. A higher number looks further ahead and can take longer.

If I pick a depth that is not 2, 4 or 6, the Level button says Custom. The extra search information shows after using Make move or after the computer takes a turn.

## Downloading my game trace

The game keeps a history from the start of each new game. After the game ends, click **Download game_trace.txt** in the game over popup. If I close the popup, the same download button is below the board too. The browser downloads the text file normally. It does not save directly into the project folder.

The first lines have the player names and the start date and time. The file includes the game settings, each move in order, flipped pieces, scores, forced passes, computer search stats and the final result. If I change a name or search setting during the game, it records the change too.

Debug stays off by default. To include search paths, heuristic values and pruned branches, turn on **Dev mode**, then **Debug** or **Detailed search**, before the searches I want to record. Each search can keep up to 1,500 debug lines. If any lines are left out, the trace says **SEARCH LOG TRUNCATED** and gives the number omitted. Earlier turns stay in the file when the computer searches again.

This is the history of the game I actually played, not a pre-filled example. Download it before restarting or refreshing because a new game starts a new trace.

## Things to know

The game stays in the current browser page. Refreshing the page starts it over. The computer searches in a background worker so the page and animation can keep moving. High depths still take longer, especially if alpha-beta is off. Older browsers can use the normal search if workers are unavailable.

## Files

- `othello.html` has the whole game, including its design, rules, computer player, and controls.
- `README.md` is this guide.
