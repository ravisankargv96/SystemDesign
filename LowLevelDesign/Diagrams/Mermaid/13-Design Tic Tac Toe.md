```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction BT
    class Board {
        GRID : char[][]
        movesCount : int
        Board()
        initializeBoard() void
        makeMove(int row, int col, char symbol) void sync
        isFull() boolean
        hasWinner() boolean
        printBoard() void
    }

    class Player {
        NAME: String
        SYMBOL: char
        Player(String name, char symbol)
        getName() String
        getSymbol() char
    }

    class Game {
        PLAYER1 : Player
        PLAYER2 : Player
        BOARD : Board
        currentPlayer : Player

        Game(Player player1, Player player2)
        play() void
        switchPlayer() void
        getValidInput(String message) int
    }

    
    Game "1" *--> "1" Board
    Game "1" *--> "1..2" Player
```

```java
public class TicTacToeDemo {
	public static void run() {
		Player player1 = new Player("Player 1", 'X');
		Player player2 = new Player("Player 2", 'O');

		Game game = new Game(player1, player2);
		game.play();
	}
}
```