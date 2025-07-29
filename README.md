package guessingGame;

public class Game {
    private int number;
    private int guessNumber;
    private int counter;
    private int lastGuess = -1; // store the previous guess

    public void generateNumberToBeGuessed() {
        number = (int)(Math.random() * 100) + 1;
        counter = 0;
        lastGuess = -1;
    }

    public void makeGuess(int guess) {
        guessNumber = guess;
        counter++;
    }

    public boolean isCorrectGuess() {
        return guessNumber == number;
    }

    public void displayWelcomeMessage() {
        System.out.println("Welcome to the guessing game!");
    }

    public void displayPleaseGuessMessage() {
        System.out.println("Try to guess the number (between 1 and 100):");
    }

    public void displayCorrectGuessMessage() {
        System.out.println("Nice! You got it. The number was " + number + ".");
        if (counter <= 3) {
            System.out.println("Great work! You are a mathematical wizard.");
        } else if (counter <= 7) {
            System.out.println("Not too bad! You’ve got some potential.");
        } else {
            System.out.println("What took you so long?");
        }
    }

    public void displayGuessAgainMessage() {
        if (guessNumber < number) {
            System.out.println("Too low.");
        } else {
            System.out.println("Too high.");
        }

        if (lastGuess != -1) {
            int prevDiff = Math.abs(lastGuess - number);
            int currentDiff = Math.abs(guessNumber - number);

            if (currentDiff < prevDiff) {
                System.out.println("Warmer.");
            } else if (currentDiff > prevDiff) {
                System.out.println("Colder.");
            } else {
                System.out.println("Same distance as before.");
            }
        }

        lastGuess = guessNumber; // update last guess
    }
}
