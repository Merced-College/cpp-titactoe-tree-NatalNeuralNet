[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=19078533)
# cpp_tictactoe_tree

What is the purpose of the minimax function?
The minimax function serves as the heart of the AI’s decision-making: it systematically explores possible move sequences from the current board state, alternately assuming the computer (maximizer) and the human (minimizer) both play optimally. By recursively simulating each legal move and assigning terminal scores (+1 for a computer win, –1 for a human win, 0 for a draw), minimax propagates these values back up the call stack. On maximizing turns it selects the highest score and on minimizing turns the lowest, so that when findBestMove() queries minimax, it receives the optimal guaranteed outcome for the computer.

How does the GameState class represent the tree?
The GameState class is how we represent each spot in the decision tree. Internally it just holds a nine‐cell array of X’s, O’s, or blanks. Whenever we need to explore a next move, we call makeMove() to get a brand‐new GameState with one extra mark on the board. In this way, each GameState object acts like a node in the game tree, and its “children” are the new states you get by playing in each empty cell.

When does the recursion stop in the minimax algorithm?
Recursion in minimax stops as soon as we reach a “leaf” of this tree. That happens when we hit our depth limit (we’ve looked ahead as far as we’re allowed), when checkWinner() finds an X or O three‐in‐a‐row, or when the board is full with no more moves. At that point we return +1, –1, or 0 instead of diving deeper.