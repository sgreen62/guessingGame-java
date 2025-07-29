import java.util.Random;

public class Game {
    private int number;
    private int guessNumber;
    private int counter;

    public void generateNumberToBeGuessed() {
        Random rand = new Random();
        number = rand.nextInt(100) + 1;
        counter = 0;
    }

    public void makeGuess(int guess) {
        guessNumber = guess;
        counter++;
    }

    public boolean isCorrectGuess() {
        return guessNumber == number;
    }

    public void displayWelcomeMessage() {
        System.out.println("Welcome to the Guessing Game!");
    }

    public void displayPleaseGuessMessage() {
        System.out.println("Please enter a number between 1 and 100:");
    }

    public void displayCorrectGuessMessage() {
        System.out.println("Congratulations! You guessed the correct number: " + number);
        if (counter <= 3) {
            System.out.println("Great work! You are a mathematical wizard.");
        } else if (counter <= 7) {
            System.out.println("Not too bad! You've got some potential.");
        } else {
            System.out.println("What took you so long?");
        }
    }

    public void displayGuessAgainMessage() {
        int difference = guessNumber - number;
        if (difference > 10) {
            System.out.println("Way too high! Guess again.");
        } else if (difference > 0) {
            System.out.println("Too high! Guess again.");
        } else if (difference < -10) {
            System.out.println("Way too low! Guess again.");
        } else {
            System.out.println("Too low! Guess again.");
        }
    }
}
