
# Java Class Exercise: Grade Analyzer

## Objective

Write a Java program that:

- Accepts grades for a group of students  
- Passes the array of grades to a method  
- That method calculates and prints:
  - Average grade  
  - Highest grade  
  - Number of failing grades (below 65)  

---

## Instructions

1. In `main`, ask the user for the number of students.
2. Create an array to store grades.
3. Use a loop to get each grade from the user.
4. Pass the array to a method called `analyzeGrades(int[] grades)`.
5. In that method:
   - Calculate average  
   - Find highest grade  
   - Count failing grades (`grade < 65`)  
   - Print the results
  
## Sample Run:

<img width="240" height="188" alt="image" src="https://github.com/user-attachments/assets/9eab49f2-bc5e-4f15-b80b-5aa81aad1727" />

```java
import java.util.Scanner;

public class GradeAnalyzer {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Ask how many students
        System.out.print("Enter number of students: ");
        int numStudents = scanner.nextInt();

        // Create array to store grades
        int[] grades = new int[numStudents];

        // Read grades from user
        for (int i = 0; i < numStudents; i++) {
            System.out.print("Enter grade for student " + (i + 1) + ": ");
            grades[i] = scanner.nextInt();
        }

        // Analyze grades
        analyzeGrades(grades);

        scanner.close();
    }

    // Method to analyze grades
    public static void analyzeGrades(int[] grades) {
        int sum = 0;
        int highest = grades[0];
        int failingCount = 0;

        for (int grade : grades) {
            sum += grade;
            if (grade > highest) {
                highest = grade;
            }
            if (grade < 60) {
                failingCount++;
            }
        }

        double average = (double) sum / grades.length;

        // Print results
        System.out.println("\nAverage grade: " + average);
        System.out.println("Highest grade: " + highest);
        System.out.println("Failing grades: " + failingCount);
    }
}
