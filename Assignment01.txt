import java.util.Scanner;

/**
 * 
 *
 * Name       -THOmmadura De Silva
 * Student Id -24077101
 * Date      -11/09/2023

 */
public class StudentStatistics
{
    
    /**
     * The main method of the program.
     *
     * @param args The command-line arguments (not used in this program).
     */
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Input assignment name
        System.out.print("Enter the assignment name: ");
        String assignmentName = input.nextLine();

        // Input students' marks
        int[] marks = new int[30];
        for (int i = 0; i < 30; i++) {
            int mark;
            do {
                System.out.print("Enter student " + (i + 1) + "'s mark (0-30): ");
                mark = input.nextInt();
                if (mark < 0 || mark > 30) {
                    System.out.println("Invalid input. Mark must be between 0 and 30.");
                }
            } while (mark < 0 || mark > 30);
            marks[i] = mark;
        }

        // Print assignment name and marks
        System.out.println("Assignment: " + assignmentName);
        System.out.println("Student Marks:");
        for (int i = 0; i < 30; i++) {
            System.out.println("Student " + (i + 1) + ": " + marks[i]);
        }

        // Calculate and print highest and lowest marks
        findAndPrintHighestAndLowestMarks(marks);

        // Calculate and print mean and standard deviation
        calculateAndPrintMeanAndStdDev(marks);
    }

    
    /**
     * Finds and prints the highest and lowest marks in an array of marks.
     *
     * @param marks An array of student marks.
     */
    public static void findAndPrintHighestAndLowestMarks(int[] marks) {
        int maxMark = Integer.MIN_VALUE;
        int minMark = Integer.MAX_VALUE;
    
        for (int mark : marks) {
            if (mark > maxMark) {
                maxMark = mark;
            }
            if (mark < minMark) {
                minMark = mark;
            }
        }
    
        System.out.println("Highest Mark: " + maxMark);
        System.out.println("Lowest Mark: " + minMark);
    }

    
    /**
     * Calculates and prints the mean and standard deviation of an array of marks.
     *
     * @param marks An array of student marks.
     */
    public static void calculateAndPrintMeanAndStdDev(int[] marks) {
        int sum = 0;
        int sumOfSquares = 0;
    
        // Calculate the sum
        for (int mark : marks) {
            sum += mark;
        }
    
        // Calculate mean
        double mean = (double) sum / marks.length;
    
        // Calculate the sum of squared differences
        for (int mark : marks) {
            double squaredDifference = (mark - mean) * (mark - mean);
            sumOfSquares += squaredDifference;
        }
    
        // Calculate variance
        double variance = (double) sumOfSquares / marks.length;
    
        // Calculate standard deviation (square root of variance)
        double stdDev = Math.sqrt(variance);
    
        // Print mean and standard deviation
        System.out.println("Mean: " + mean);
        System.out.println("Standard Deviation: " + stdDev);
    }

}
