#tictactoe.java

package tictactoe;

import java.util.Scanner;

public class TicTacToe {
    private String[][] board = new String[3][3];
    private String currentPlayerMark = "X";

    public void displayWelcomeMessage() {
        System.out.println("Welcome to Tic Tac Toe!");
    }

    public void displayGrid() {
        System.out.println();
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                String cell = board[i][j];
                System.out.print(cell == null ? "_" : cell);
                if (j < 2) System.out.print(" | ");
            }
            System.out.println();
        }
        System.out.println();
    }

    public void startGame() {
        Scanner scanner = new Scanner(System.in);
        int moves = 0;
        boolean hasWinner = false;

        while (moves < 9 && !hasWinner) {
            displayGrid();
            takeTurn(scanner);
            hasWinner = checkForWinner();
            if (hasWinner) {
                displayGrid();
                System.out.println("Player " + currentPlayerMark + " wins!");
                return;
            }
            moves++;
            currentPlayerMark = currentPlayerMark.equals("X") ? "O" : "X";
        }

        if (!hasWinner) {
            displayGrid();
            System.out.println("It's a tie!");
        }
    }

    public void takeTurn(Scanner scanner) {
        int row, col;
        while (true) {
            System.out.print("Player " + currentPlayerMark + ", enter row (0-2): ");
            row = scanner.nextInt();
            System.out.print("Enter column (0-2): ");
            col = scanner.nextInt();

            if (row >= 0 && row < 3 && col >= 0 && col < 3) {
                if (board[row][col] == null) {
                    board[row][col] = currentPlayerMark;
                    break;
                } else {
                    System.out.println("That spot is already taken. Try again.");
                }
            } else {
                System.out.println("Invalid input. Please enter numbers between 0 and 2.");
            }
        }
    }

    public boolean checkForWinner() {
        for (int i = 0; i < 3; i++) {
            if (match(board[i][0], board[i][1], board[i][2])) return true;
            if (match(board[0][i], board[1][i], board[2][i])) return true;
        }
        return match(board[0][0], board[1][1], board[2][2]) ||
               match(board[0][2], board[1][1], board[2][0]);
    }

    private boolean match(String a, String b, String c) {
        return a != null && a.equals(b) && b.equals(c);
    }
}


#tictactoeapp.java

package tictactoe;

public class TicTacToeApp {
    public static void main(String[] args) {
        TicTacToe game = new TicTacToe();
        game.displayWelcomeMessage();
        game.startGame();
    }
}
