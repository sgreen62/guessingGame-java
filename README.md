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
