## W5 Assignment 2 ArrayAlgorithmToolkit

```java
import java.util.Random;
import java.util.Arrays;
import java.util.Scanner;
public class ArrayAlgorithmToolkit {

    static  int linearComparisons;
    static  int binaryComparisons;

    public static void main(String[] args) {

        int size = 20;
        if (args.length > 0) {
            try {
                int requestedSize = Integer.parseInt(args[0]);

                if (requestedSize > 0) {
                    size = requestedSize;
                } else {
                    System.out.println("Array size must be positive. Using default size 20.");
                }
            } catch (NumberFormatException e) {
                System.out.println("Invalid array size. Using default size 20.");
            }
        }
        int[] data = generateData(size, 1, 100);

        System.out.println("Array using printArray:");
        printArray(data);

        System.out.println("\nArray using Arrays.toString:");
        System.out.println(Arrays.toString(data));

        int[] reversedData = reverse(data);

        System.out.println("\nReversed array:");
        System.out.println(Arrays.toString(reversedData));

        System.out.println("\nOriginal array after reverse:");
        System.out.println(Arrays.toString(data));

        int[] sortedData = Arrays.copyOf(data, data.length);
        selectionSort(sortedData);

        System.out.println("\nSorted array using selection sort:");
        System.out.println(Arrays.toString(sortedData));

        System.out.println("\nOriginal array after selection sort:");
        System.out.println(Arrays.toString(data));

        int key = data[5];

        int foundIndex = linearSearch(data, key);

        System.out.println("\nLinear search:");
        System.out.println("Searching for: " + key);
        System.out.println("Found at index: " + foundIndex);
        System.out.println("Comparisons: " + linearComparisons);

        int binaryIndex = binarySearch(sortedData, key);

        System.out.println("\nBinary search:");
        System.out.println("Searching for; " + key);
        System.out.println("Found at index: " + binaryIndex);
        System.out.println("Comparisons: " + binaryComparisons);

        int[] javaCopy = Arrays.copyOf(data, data.length);
        Arrays.sort(javaCopy);

        int javaIndex = Arrays.binarySearch(javaCopy, key);

        System.out.println("nJava utilities:");
        System.out.println("Java sorted array: " + Arrays.toString(javaCopy));
        System.out.println("Java binary search index: " + javaIndex);

        int[] shuffledData = Arrays.copyOf(data, data.length);

        System.out.println("\nArray before shuffle:");
        System.out.println(Arrays.toString(shuffledData));

        shuffle(shuffledData);

        System.out.println("Array after shuffle:");
        System.out.println(Arrays.toString(shuffledData));

        System.out.println("\nBefore swapFirstTwo:");
        System.out.println(Arrays.toString(data));

        swapFirstTwo(data);

        System.out.println("After swapFirstTwo");
        System.out.println(Arrays.toString(data));

        System.out.println("\nVariable-length arguments:");
        System.out.println("Average of 4, 8, 12:" + average(4, 8, 12));
        System.out.println("Average of 10, 20, 30, 40, 50:" + average(10, 20, 30, 40, 50));

        System.out.println("\nDuplicate Analysis:");
        reportDuplicates(data);

        renMenu(data);
    }
    public static int[] generateData(int size, int min, int max) {

        int[] values = new int[size];
        Random random = new Random();

        for (int i = 0; i < values.length; i++) {
            values[i] = random.nextInt(max - min + 1) + min;
        }
        return values;
    }
    public static void printArray(int [] values) {
        for (int i = 0; i < values.length; i++) {
            System.out.println("Index " + i + ": " + values[i]);
        }
    }
    public static int[] reverse(int[] values) {

        int [] reversed = new int[values.length];

        for (int i = 0; i < values.length; i++) {
            reversed[i] = values[values.length - 1 - i];
        }
        return reversed;
    }
    public static void selectionSort(int[] values) {

        for (int i = 0; i < values.length - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < values.length; j++){
                if (values[j] < values[minIndex]) {
                    minIndex = j;
                }
            }
            int temp = values[i];
            values[i] = values[minIndex];
            values[minIndex] = temp;
        }
    }
    public static int linearSearch(int[] values, int key) {

        linearComparisons = 0;

        for (int i = 0; i < values.length; i++) {

            linearComparisons++;

            if(values[i] ==key) {
                return  i;
            }
        }

        return -1;
    }

    public static int binarySearch(int[] values, int key) {

        int low = 0;
        int high = values.length - 1;

        binaryComparisons = 0;

        while (low <= high) {

            int mid = (low + high) / 2;

            binaryComparisons++;

            if (values[mid] == key) {
                return mid;
            }

            if (values[mid] < key) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return -1;
    }

    public static void shuffle(int[] values) {
        Random random = new Random();

        for (int i = values.length - 1; i > 0; i--) {
            int j = random.nextInt(i + 1);

            int temp = values[i];
            values[i] = values[j];
            values[j] = temp;
        }
    }
    public static void swapFirstTwo(int[] values) {
        int temp = values[0];
        values[0] = values[1];
        values[1] = temp;
    }
    public static double average(int... values) {
        int total = 0;

        for (int value : values) {
            total += value;
        }
        return (double) total / values.length;
    }
    public static void renMenu(int[] data) {
        Scanner input = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\nAlgorithm Menu");
            System.out.println("1. Display data");
            System.out.println("2. Reverse data");
            System.out.println("3. Sort using selection sort");
            System.out.println("4. Search using linear search");
            System.out.println("5. Search using binary search");
            System.out.println("6. Shuffle data");
            System.out.println("7. Regenerate data");
            System.out.println("0. Exit");
            System.out.print("Enter your choice: ");

            choice = input.nextInt();

            switch (choice) {
                case 1:
                    System.out.println(Arrays.toString(data));
                    break;

                case 2:
                    data = reverse(data);
                    System.out.println("Reversed data:");
                    System.out.println(Arrays.toString(data));
                    break;

                case 3:
                    selectionSort(data);
                    System.out.println("Sorted data:");
                    System.out.println(Arrays.toString(data));
                    break;

                case 4:
                    System.out.print("Enter value to search for: ");
                    int linearKey = input.nextInt();
                    int linearResult = linearSearch(data, linearKey);
                    System.out.println("Found at index: " + linearResult);
                    break;

                case 5:
                    System.out.print("Enter value to search for: ");
                    int binaryKey = input.nextInt();

                    int[] sortedCopy = Arrays.copyOf(data, data.length);

                    int binaryResult = binarySearch(sortedCopy, binaryKey);
                    System.out.println("Found at index: " + binaryResult);
                    break;

                case 6:
                    shuffle(data);
                    System.out.println("Shuffled data:");
                    System.out.println(Arrays.toString(data));
                    break;

                case 7:
                    int[] newData = generateData(data.length, 1, 100);
                    System.arraycopy(newData, 0, data, 0, data.length);
                    System.out.println("New data generated:");
                    System.out.println(Arrays.toString(data));
                    break;

                case 0:
                    System.out.println("Exiting menu.");
                    break;

                default:
                    System.out.println("Invalid choice.");

            }
        } while (choice != 0);
    }
        public static int countOccurrences (int[] values, int key) {
            int count = 0;

                    for (int value : values) {
                        if (value == key) {
                            count++;
                        }
                    }
                    return count;
        }
        public static void reportDuplicates(int[] values) {
        System.out.println("\nDuplicate values:");

        for (int i = 0; i < values.length; i++) {
            boolean alreadyChecked = false;

            for (int j = 0; j < i; j++) {
                if (values[i] == values[j]) {
                    alreadyChecked = true;
                    break;
                }
            }
            if(!alreadyChecked) {
                int count = countOccurrences(values, values[i]);

                if (count > 1) {
                    System.out.println(values[i] + " occurs " + count + " times");
                }
            }
        }
    }
}
/* 1. Binary search can eliminate half of the remainning elements because the array is sorted.
Comparing the key to the middle value and decides whether the key is in the lower or upper half.
2. The precondition that must be satisfied before the binary search is that the
array has to be sorted.
3. Selection sort finds the smallest value in the unsorted array and organizes it
into the correct spot.
4. Reverse returns a new array while selectionSort can modify the supplied array because
reverse returns a new array so the supplied array can remain the same, and selectionSort modifies
the original array directly because arrays are reference types.
5. A copy of the reference to the array is passed to the method.
6. Arrays.binarySearch and Arrays.sort are related because the array has to be sorted by
Array.sort before the binary search can take place to search for a specific value.
7. Variable length arguments are useful when a method needs to accept
different number of arguments each time it is called.
 */
