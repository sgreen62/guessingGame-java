package guessingGame;

public class Game {
    private int targetNumber;
    private int attempts;

    public Game() {
        targetNumber = (int)(Math.random() * 100) + 1;
        attempts = 0;
    }

    public String makeGuess(int guess) {
        attempts++;
        if (guess == targetNumber) {
            return "Correct! You guessed it in " + attempts + " tries.";
        } else if (guess < targetNumber) {
            return "Too low. Try again.";
        } else {
            return "Too high. Try again.";
        }
    }
}


#GuessNumbersApp
package guessingGame;

import java.util.Scanner;

public class GuessNumberApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Game game = new Game();
        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("Guess a number between 1 and 100.");

        boolean guessedCorrectly = false;
        while (!guessedCorrectly) {
            System.out.print("Enter your guess: ");
            int guess = scanner.nextInt();
            String result = game.makeGuess(guess);
            System.out.println(result);
            if (result.startsWith("Correct!")) {
                guessedCorrectly = true;
            }
        }

        scanner.close();
    }
}
