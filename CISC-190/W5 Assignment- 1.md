## Week 5 Assignment 1 - Assessment Analyzer

```java

import java.util.Scanner;
public class AssessmentAnalyzer {
    public static void main(String[] args) {
        Scanner input = new Scanner (System.in);
        double[] scores = new double[10];
        for (int i = 0; i < scores.length; i++) {

            System.out.print("Enter score " + (i + 1) + ": ");
            double score = input.nextDouble();
            while (score <0 || score > 100) {
                System.out.print("Invalid score. Enter a score from 0 to 100: ");
                score = input.nextDouble();
            }
            scores[i] = score;
        }
        System.out.println("\nScores:");
        printScores(scores);
        double average = calculateAverage(scores);
        System.out.println("Average: " + average);
        double minimum = findMinimum(scores);
        double maximum = findMaximum(scores);

        System.out.println("Minimum: " + minimum);
        System.out.println("Maximum: " + maximum);

        int aboveAverage = countAboveAverage(scores, average);

        System.out.println("Above average: " + aboveAverage);

        System.out.print("Enter a score to locate: ");
        double target = input.nextDouble();

        int index = linearSearch(scores, target);

        if (index == -1) {
            System.out.println("Score not found.");
        } else {
            System.out.println("Score found at index " + index);

            double[] copiedScores = copyArray(scores);

            System.out.println("\nBefore changing the copy:");
            System.out.println("Original first score: " + scores[0]);
            System.out.println("Copy first score: " + copiedScores[0]);
            copiedScores[0] = 0;
            System.out.println("\nAfter changing the copy:");
            System.out.println("Original first score: " +scores[0]);
            System.out.println("Copy first scores: " + copiedScores[0]);

            System.out.println("\nBefore shift:");
            printScores(scores);
            shiftLeft(scores);
            System.out.println("\nAfter sift:");
            printScores(scores);

            System.out.println("\nFinal Report");
            System.out.println("Number of scores: " + scores.length);
            System.out.println("Average: " + average);
            System.out.println("Minimum: " + minimum);
            System.out.println("Maximum: " + maximum);
            System.out.println("Above average: " + aboveAverage);
        }
    }
    public static void printScores(double[] scores) {
        for (int i = 0; i < scores.length; i++) {
            System.out.println("Index " + i + ": " + scores[i]);
        }
    }
    public static double calculateAverage (double[] scores) {
        double total = 0;

        for (double score : scores) {
            total += score;
        }
        return  total / scores.length;
    }
    public static double findMinimum(double[] scores) {
        double minimum = scores[0];

        for (double score: scores) {
            if (score < minimum) {
                minimum = score;
            }
        }
        return  minimum;
    }
    public static double findMaximum(double[] scores) {
        double maximum = scores[0];

        for (double score : scores) {
            if (score > maximum) {
                maximum = score;
            }
        }
        return maximum;
    }
    public static int countAboveAverage(double [] scores, double average) {
        int count = 0;

        for (double score : scores) {
            if (score > average) {
                count++;
            }
        }
        return count;
    }
    public static int linearSearch(double[] scores, double target) {
        for (int i = 0; i < scores.length; i++) {
            if (scores[i] == target) {
                return i;
            }
        }
        return -1;
    }
    public static double [] copyArray(double[] source) {
        double[] copy = new double[source.length];
        for (int i = 0; i < source.length; i++) {
            copy[i] = source[i];
        }
        return copy;
    }
    public static void shiftLeft(double[] scores) {
        double first = scores[0];
        for (int i = 0; i < scores.length - 1; i++) {
            scores[i] = scores[i + 1];
        }
        scores[scores.length - 1] = first;
    }
}

/* 1. The last valid index is length -1 because Java arrays begin indexing at 0, so 0
is counted as the first index and subtracting length-1.
2. The enhanced for loop is preferable to an indexed loop when the programmer needs to process
each element but does not needs its index or modify the elements by position.
3. Simple array assignment does not create an independent copy because it copies
the reference to the array instead of copying each element into a new array, so
both variables are able to refer to the same array.
4. When the target is absent a linear search returns the sentinel value I set which is -1
to indicate that no matching element was found.
5. A method can modify elements of an array passed to it because a copy of the arrays
reference is passed to the method which locates the same array object as the original variable,
which lets the method affect the original array.
 */
