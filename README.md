package guessingGame;

import java.util.Scanner;

public class GuessNumberApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Game game = new Game();

        game.displayWelcomeMessage();

        String playAgain = "y";

        while (playAgain.equalsIgnoreCase("y")) {
            game.generateNumberToBeGuessed();
            game.displayPleaseGuessMessage();

            boolean correct = false;

            while (!correct) {
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();

                game.makeGuess(guess);

                if (game.isCorrectGuess()) {
                    game.displayCorrectGuessMessage();
                    correct = true;
                } else {
                    game.displayGuessAgainMessage();
                }
            }

            System.out.print("Do you want to play again? (y/n): ");
            playAgain = scanner.next();
        }

        System.out.println("Thanks for playing!");
        scanner.close();
    }
}
