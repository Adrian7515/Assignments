## Weeks 2 Assignment 2 Loops 

```java
import java.util.Scanner;
public class ScoreAnalyzer {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int count = 0;
        double total = 0;
        double highest = 0;
        double lowest = 0;
        int passing = 0;
        int below60 = 0;

        System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
        double score = input.nextDouble();

        while (score != -1) {
            if (score >=0 && score <=100) {
                count++;
                total += score;

                if (count == 1) {
                    highest = score;
                    lowest = score;
                } else {
                    if (score > highest) {
                        highest = score;
                    }
                    if (score < lowest) {
                        lowest = score;
                    }
                }
                if (score >= 60) {
                    passing++;
                } else {
                    below60++;
                }

            } else {
                System.out.println("Invalid score. Value ignored.");
            }
            System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
            score = input.nextDouble();
        }
        if (count > 0) {
            double average = total/ count;

            System.out.println("----- Score Summary -----");
            System.out.println("Valid scores: " + count);
            System.out.printf("Average: %.2f%n", average);
            System.out.printf("Highest: %.2f%n", highest);
            System.out.printf("Lowest: %.2f%n", lowest);
            System.out.println("Passing scores: " + passing);
            System.out.println("Below 60: " + below60);
        } else {
            System.out.println("No valid scores were entered.");
        }
    }
}

import java.util.Scanner;
public class ScoreAnalyzerDoWhile {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        double score;
        do {
            System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
            score = input.nextDouble();
        } while (score != -1);
    }
}

