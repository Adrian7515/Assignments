## W5 GridValidator Assignment

```java
public class GridValidator {
    public static void main(String[] args) {

        int[][] grid = {
                {5, 3, 4, 6, 7, 8, 9, 1, 2},
                {6, 7, 2, 1, 9, 5, 3, 4, 8},
                {1, 9, 8, 3, 4, 2, 5, 6, 7},
                {8, 5, 9, 7, 6, 1, 4, 2, 3},
                {4, 2, 6, 8, 5, 3, 7, 9, 1},
                {7, 1, 3, 9, 2, 4, 8, 5, 6},
                {9, 6, 1, 5, 3, 7, 2, 8, 4},
                {2, 8, 7, 4, 1, 9, 6, 3, 5},
                {3, 4, 5, 2, 8, 6, 1, 7, 9}
        };

        System.out.println("Values in range: " + valuesInRange(grid));

        System.out.println("Row 0 valid: " + isRowValid(grid, 0));

        System.out.println("All rows valid: " + areRowsValid(grid));

        System.out.println("Column 0 valid " + isColumnValid(grid, 0));

        System.out.println("All columns valid: " + areColumnsValid(grid));

        System.out.println("Region valid: " + isRegionValid(grid, 0, 0));

        System.out.println("All regions valid: " + areRegionsValid(grid));

        System.out.println("Entire grid valid: " + isValidGrid(grid));
    }

    public static boolean valuesInRange(int[][] grid) {

        for (int row = 0; row < grid.length; row++) {

            for (int column = 0; column < grid[row].length; column++) {

                if (grid[row][column] < 1 || grid[row][column] > 9) {
                    return false;
                }
            }
        }

        return true;
    }

    public static boolean isRowValid(int[][] grid, int row) {

        boolean[] seen = new boolean[10];

        for (int column = 0; column < grid[row].length; column++) {

            int value = grid[row][column];

            if (seen[value]) {
                return false;
            }

            seen[value] = true;
        }

        return true;
    }

    public static boolean areRowsValid(int [][] grid) {

        for (int row = 0; row < grid.length; row++) {

            if (!isRowValid(grid, row)) {
                return false;
            }
        }

        return true;
    }

    public static boolean isColumnValid(int[][] grid, int column) {

        boolean[] seen = new boolean[10];

        for (int row = 0; row < grid.length; row++) {

            int value = grid[row][column];

            if (seen[value]) {
                return false;
            }

            seen[value] = true;
        }

        return true;
    }

    public static boolean areColumnsValid(int[][] grid) {

        for (int column = 0; column < grid[0].length; column++) {

            if (!isColumnValid(grid, column)) {
                return false;
            }
        }

        return true;
    }

    public static boolean isRegionValid(int[][] grid, int startRow, int startColumn) {
        boolean[] seen = new boolean[10];

        for (int row = startRow; row < startRow + 3; row++) {

            for (int column = startColumn; column < startColumn + 3; column++) {

                int value = grid[row][column];

                if (seen[value]) {
                    return false;
                }

                seen[value] = true;
            }
        }

        return true;
    }

    public static boolean areRegionsValid(int[][] grid) {

        for (int row = 0; row < 9; row += 3) {

            for (int column = 0; column < 9; column +=3) {

                if (!isRegionValid(grid, row, column)) {
                    return false;
                }
            }
        }

        return true;
    }

    public static boolean hasValidDimesions(int[][] grid) {

        if (grid.length != 9) {
            return false;
        }

        for (int row = 0; row < grid.length; row++) {

            if (grid[row].length != 9) {
                return false;
            }
        }

        return true;
    }

    public static boolean isValidGrid(int[][] grid) {

        if (!hasValidDimesions(grid)) {
            return false;
        }

        if (!valuesInRange(grid)) {
            return false;
        }

        if (!areRowsValid(grid)) {
            return false;
        }

        if (!areColumnsValid(grid)) {
            return false;
        }

        if (!areRegionsValid(grid)) {
            return false;
        }

        return true;
    }
}
