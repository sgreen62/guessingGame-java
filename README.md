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
            String message = "Correct! You guessed it in " + attempts + " tries.\n";
            if (attempts <= 3) {
                message += "Great work! You are a mathematical wizard.";
            } else if (attempts <= 7) {
                message += "Not too bad! You’ve got some potential.";
            } else {
                message += "What took you so long?";
            }
            return message;
        } else {
            int difference = guess - targetNumber;
            if (difference > 10) {
                return "Way too high! Guess again.";
            } else if (difference > 0) {
                return "Too high! Guess again.";
            } else if (difference < -10) {
                return "Way too low! Guess again.";
            } else {
                return "Too low! Guess again.";
            }
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
