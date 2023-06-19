# numbergussinggame
import java.util.Random;
import java.util.Scanner;

public class GuessTheNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int rangeStart = 1;
        int rangeEnd = 100;
        int maxAttempts = 5;
        int totalScore = 0;
        int rounds = 3;

        System.out.println("Welcome to Guess the Number!");
        System.out.println("I'm thinking of a number between " + rangeStart + " and " + rangeEnd + ".");
        System.out.println("You have " + maxAttempts + " attempts to guess the number.");

        for (int round = 1; round <= rounds; round++) {
            int secretNumber = random.nextInt(rangeEnd - rangeStart + 1) + rangeStart;
            int attempts = 0;
            int roundScore = maxAttempts;

            System.out.println("\n--- Round " + round + " ---");

            while (attempts < maxAttempts) {
                System.out.print("Enter your guess (Attempt " + (attempts + 1) + "): ");
                int guess = scanner.nextInt();
                scanner.nextLine(); // Consume the newline character

                attempts++;

                if (guess == secretNumber) {
                    System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
                    break;
                } else if (guess < secretNumber) {
                    System.out.println("Too low! Try a higher number.");
                } else {
                    System.out.println("Too high! Try a lower number.");
                }

                roundScore--;
            }

            totalScore += roundScore;

            System.out.println("\nThe number was: " + secretNumber);
            System.out.println("Score for this round: " + roundScore);
            System.out.println("Total score: " + totalScore);

            if (round < rounds) {
                System.out.print("\nPress enter to start the next round...");
                scanner.nextLine(); // Wait for enter key press
            }
        }

        System.out.println("\nGame Over!");
        System.out.println("Total score: " + totalScore);

        scanner.close();
    }
}
