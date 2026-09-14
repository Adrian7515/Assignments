## W2 Assignment 1/2 Decision Statements 
```java 
import java.util.Scanner;
public class CourseRegistrationAdvisor {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.print("Placement score (0-100): ");
        int score = input.nextInt();

        System.out.print("Prerequisite completed? (true/false): ");
        boolean prerequisiteCompleted = input.nextBoolean();

        System.out.println("Program type: ");
        System.out.println("1 - Computer Science");
        System.out.println("2 - Data Science");
        System.out.println("3 - Information Systems");
        System.out.println("4 - Other");
        System.out.println("Enter Program type: ");
        int programType = input.nextInt();

        System.out.print("Completed college units: ");
        int completedUnits = input.nextInt();

        if (score < 0 || score > 100) {
            System.out.print("Invalid placement score. ");
        } else {

            String level;
            if (score >= 90) {
                level = "Advanced";
            } else if (score >= 75) {
                level = "Ready";
            } else if (score >= 60) {
                level = "Developing";
            } else {
                level = "Needs Preparation";
            }

            boolean eligible = score >= 75 && prerequisiteCompleted;

            String registrationStatus;
            if (eligible) {
                registrationStatus = "Eligible";
                System.out.println("Registration status: Eligible");
            } else {
                registrationStatus = "Advisor review required";
                System.out.println("Registration status: Advisor review required");
            }
            if (!eligible) {
                if (!prerequisiteCompleted) {
                    System.out.println("Complete the prerequisite course first.");
                } else if (score < 75) {
                    System.out.println("Additional preparation is recommended.");
                }
            }

            String programPathway;
            switch (programType) {
                case 1:
                    programPathway = "Computer Science pathway";
                    break;
                case 2:
                    programPathway = "Data Science pathway";
                    break;
                case 3:
                    programPathway = "Information Systems pathway";
                    break;
                case 4:
                    programPathway = "General elective pathway";
                    break;
                default:
                    programPathway = "Invalid program type";
            }
            String studentStatus =
                    (completedUnits < 12) ? "New Student" : "Continuing Student";

            boolean earlyPriority =
                    (completedUnits >= 30 && eligible)
                    || (completedUnits >= 60 && prerequisiteCompleted);

            System.out.println();
            System.out.println("----- Course Registration Advisor-----");
            System.out.println("Placement score: " + score);
            System.out.println("Preparation level: " + level);
            System.out.println("Prerequisite completed: " +prerequisiteCompleted);
            System.out.println("Registration status: " + registrationStatus);
            System.out.println("Program: " + programPathway);
            System.out.println("Student status: " + studentStatus);
            System.out.println("Early registration priority: " + earlyPriority);
        }
        input.close();
    }

}
/* Part 11: The following code contains a logic error because of the order of the code.
The program will display "D" because the first part of the if chain states that if the score
is grater than 60 that the screen will display "D", because this is the first line and
the score is indeed greater than 60 the if chain stops there and will not move on
to the other lines of the chain.
Part 12: This is a semicolon error because there is a semicolon directly behind the
closing parentheses after 12 when it should oun be an opening curly brace to allow the
print directive to be included in the decision if chain.
Part 13: When I used the given values for the boundary testing the program
behaved correctly, giving the expected outputs for each scenario dependant on
which value I input for placement score and units completed. I even tried inputing values
outside of the programs paremeters for placement score and it told me I had an
invalid placement score.
 */

  

