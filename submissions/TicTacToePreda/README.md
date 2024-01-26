
# TicTacToe Example Contract Documentation

This contract is a smart contract that implements a simple game of Tic-Tac-Toe. It allows players to challenge each other, make moves, and determine the winner of the game. The contract uses the Preda language and incorporates various features such as global and address scopes, relay transactions, and data structures.

## Contract Structure

The `TicTacToe` contract consists of several structs, global variables, and functions that facilitate the game process.

### Structs
-   `GameData`: Represents the data for a game, including the addresses of player one and player two, the winner of the game, and the current turn.

### Global Variables
-   `addressList` (map<address, uint32>): Stores the mapping of player addresses to game indices.
-   `games` (array<GameData>): Stores the list of active games.
- 
### Address Scope Variables
-   `score` (int64): Represents the score of the player in the current game.
-   `isInGame` (bool): Indicates if the player is currently in a game.
-   `invites` (array<address>): Stores the list of pending invitations in the current game.
-   `board` (array<bool>): Represents the Tic-Tac-Toe game board in the current game.

## Functions explanation

### `challenge(opponent: address)`
the `challenge` function allows a player to send a game invitation to another player (`opponent`) only if the sender is not currently in a game and the opponent is also not in a game. In that case, the sender's address is added to the `invites` array, indicating that an invitation has been sent.

#### `acceptInvitation(opponent: address) -> bool`
the `acceptInvitation` function checks if the player is already in a game. If not, it searches for a specific invitation in the `invites` array.
 If a matching invitation is found and the opponent is available (not in another game), the following actions are performed:
    
  -   The game data is initialized, including the players' addresses, game status, and board state.
  -   The `isInGame` flag is set to `true` for both the player accepting the invitation and the opponent.
  -   The `board` array is reset to represent an empty game board for both players.
  -   The `invites` array is cleared to remove any pending invitations.
  
Finally, the function returns `true` to indicate that the invitation was accepted successfully and the game has started.

#### `makeMove(move: uint32) -> uint8`
This function allows a player to make a move on a game board. It performs several checks to ensure the move is valid, such as verifying if the player is in a game, if it's their turn, and if the selected position on the board is available. If the move is valid, it marks the position as occupied, checks for win conditions, updates the game state accordingly, and returns a value to indicate the outcome of the move. If the move results in a win, it returns `2`. If the move results in a draw, it returns `3`. Otherwise, it returns `1` for a successful move and `0` for not valid move.

