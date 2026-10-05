## Week 5 StoreSalesAnalyzer Assignment 

```java
import java.util.Scanner;
public class StoreSalesAnalyzer {
    public static void main (String[] args) {
        double[][] sales = new double[4][7];

        Scanner input = new Scanner(System.in);

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {

                System.out.print("Enter sales for Store " + (row + 1) + ", Day " + (column + 1) + "; ");

                sales[row][column] = input.nextDouble();

                while (sales[row][column] < 0) {
                    System.out.print("Sales cannot be negative. Enter again: ");
                    sales[row][column] = input.nextDouble();
                }
            }
        }
        printSales(sales);

        double overallTotal = totalSales(sales);
        System.out.println("Overall sales: " + overallTotal);

        double average = averageSale(sales);
        System.out.println("Average sale per entry: " + average);

        for (int row = 0; row < sales.length; row++) {
            System.out.println("Store " + (row + 1) + " total: " + rowTotal(sales, row));
        }

        for (int column = 0; column < sales[0].length; column++) {
            System.out.println("Day " + (column + 1) + " total: " + columnTotal(sales, column));
        }

        int best = bestStore(sales);
        System.out.println("Best-performing store: Store " + (best + 1));

        double largestSale = findMaximum(sales);
        System.out.println("Largest individual sale: " + largestSale);

        int[] maxPosition = findMaximumPosition(sales);
        System.out.println("Largest sale position: Store " + (maxPosition[0] +1) + ", Day " + (maxPosition[1] + 1));

        double[][] irregularSales = {
                {120.0, 145.0, 160.0},
                {90.0, 105.0},
                {200.0, 210.0, 220.0, 230.0},
                {75.0}
        };

        System.out.println("Ragged array:");
        printSales (irregularSales);
        System.out.println("Ragged array total: " + totalSales(irregularSales));
    }
    public static void printSales(double[][] sales) {

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {
                System.out.print(sales[row][column] + "\t");
            }

            System.out.println();
        }
    }
    public static double totalSales(double[][] sales) {

        double total = 0;

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {
                total += sales[row][column];
            }
        }

        return total;
    }
    public static double rowTotal(double[][] sales, int row) {

        double total = 0;

        for (int column = 0; column < sales[row].length; column++) {
            total += sales[row][column];
        }
        return total;
    }
    public static double columnTotal(double[][] sales, int column) {

        double total = 0;

                for (int row = 0; row < sales.length; row++) {
                    total += sales[row][column];
                }
                return total;
    }

    public static int bestStore(double[][] sales) {

        int bestRow = 0;
        double bestTotal = rowTotal(sales, 0);

        for (int row = 1; row < sales.length; row++) {

            double currentTotal = rowTotal(sales, row);

            if (currentTotal > bestTotal) {
                bestTotal = currentTotal;
                bestRow = row;
            }
        }

        return bestRow;
    }

    public static double findMaximum(double[][] sales) {

        double maximum = sales[0][0];

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {

                if (sales[row][column] > maximum) {
                    maximum = sales[row][column];
                }
            }
        }

        return maximum;
    }

    public static int[] findMaximumPosition(double[][] sales) {

        int maxRow = 0;
        int maxColumn = 0;

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {

                if (sales[row][column] > sales[maxRow][maxColumn]) {
                    maxRow = row;
                    maxColumn = column;
                }
            }
        }

        return new int[]{maxRow, maxColumn};
    }

    public static double averageSale(double[][] sales) {

        double total = 0;
        int count = 0;

        for (int row = 0; row < sales.length; row++) {

            for (int column = 0; column < sales[row].length; column++) {
                total += sales[row][column];
                count++;
            }
        }

        return total / count;
    }
}
/* Part 10:
1. The assumption that the inner loop makes is that the number of columns is equivalent to the
number of rows because of the use of sale.length.
2.This could fail for a non-square matrix because it can cause a non-square matrix to skip
values or try to access columns that don't actually exist.
3. Correct loop:
for (int row = 0; row < sales.length; row++) {
    for (int column = 0; column < sales[row].length; column++0 {
        System.out.println(sales[row][column]);
    }
}
 */
/* 1. The first array index represents a row which represents one of the stores
in the application.
2. Nested loops are appropriate for two dimensional arrays because it allows
every element in the two dimensional array to be accessed.
3. The difference between a row total and a column total a row is giving the total for one store
and a column total is providing the total across all stores for a given day.
4. Rows in a two dimensional array can have different lengths because Java two- dimensional
arrays in each row are seperate arrays that have their own length.
5. A method should use sales[row].length because it gives the number of elements in the current row.
6. A method can return the row and column of a located value because it can 
store row and column indexes. 
 */
