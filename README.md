Here's a simple console-based Tic-Tac-Toe game in C++ that allows two players to play against each other by following the steps you provided:

```cpp
#include <iostream>
using namespace std;

// Function to draw the tic-tac-toe board
void drawBoard(char board[3][3]) {
    cout << "-------------" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "| " << board[i][0] << " | " << board[i][1] << " | " << board[i][2] << " |" << endl;
        cout << "-------------" << endl;
    }
}

// Function to check if there is a win
bool checkWin(char board[3][3], char player) {
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == player && board[i][1] == player && board[i][2] == player) {
            return true;  // Check rows
        }
        if (board[0][i] == player && board[1][i] == player && board[2][i] == player) {
            return true;  // Check columns
        }
    }
    if (board[0][0] == player && board[1][1] == player && board[2][2] == player) {
        return true;  // Check diagonal
    }
    if (board[0][2] == player && board[1][1] == player && board[2][0] == player) {
        return true;  // Check diagonal
    }
    return false;
}

// Function to check if the game is a draw
bool checkDraw(char board[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] == ' ') {
                return false;  // If any empty space found, game is not a draw
            }
        }
    }
    return true;  // No empty space found, game is a draw
}

int main() {
    char board[3][3] = { {' ', ' ', ' '}, {' ', ' ', ' '}, {' ', ' ', ' '} };
    char currentPlayer = 'X';

    while (true) {
        drawBoard(board);

        // Player input
        int row, col;
        cout << "Player " << currentPlayer << ", enter your move (row and column): ";
        cin >> row >> col;

        // Update board
        if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') {
            board[row][col] = currentPlayer;

            // Check for win
            if (checkWin(board, currentPlayer)) {
                drawBoard(board);
                cout << "Player " << currentPlayer << " wins!" << endl;
                break;
            }

            // Check for draw
            if (checkDraw(board)) {
                drawBoard(board);
                cout << "It's a draw!" << endl;
                break;
            }

            // Switch players
            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        } else {
            cout << "Invalid move! Try again." << endl;
        }
    }

    return 0;
}
```

When you run this C++ program, it creates a simple console-based Tic-Tac-Toe game that allows two players to take turns making moves. The board is displayed after each move, and the game checks for a win or a draw after each move. The game continues until a player wins or the game ends in a draw, after which the result is displayed.

You can test this program by compiling and running it in a C++ compiler. Players will input their moves by specifying a row and a column number, and the game will display the result at the end. If the players want to play another game, the program can be run again.
