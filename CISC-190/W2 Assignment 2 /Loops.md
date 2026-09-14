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

        System.out.print("Enter a scor efrom 0 to 100 (-1 to finish): ");
        double score = input.nextDouble();

        while (score != -1) {
            if (score >=0 && score <=100) {

            } else {
                System.out.println("Invalid score. Value ignored.");
            }
            System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
            score = input.nextDouble();
        }
    }
}
