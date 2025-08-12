
# Java I/O Examples (Console, File)

## 1. Input Stream

### a) From Console
When you want your program to take input from the keyboard, you are reading from something called System.in.
Think of System.in as a pipe that connects your keyboard to your program. Whatever you type flows through this pipe into your program.

Java’s Scanner class is like a reader that can understand the characters flowing in from that pipe and convert them into usable data (words, numbers, etc.).

```java
import java.util.Scanner;

public class ConsoleInputExample {
    public static void main(String[] args) {
        // Create a Scanner object to read input from the console
        Scanner sc = new Scanner(System.in);

        // Ask the user to enter their name
        System.out.print("Enter your name: ");
        String name = sc.nextLine(); // Reads an entire line of text

        // Display the input back to the user
        System.out.println("Hello, " + name + "!");

        sc.close(); // Close the scanner to free system resources
    }
}

```
<img width="1589" height="227" alt="476844866-b7ca5125-f340-427e-a2a9-3213bc8df205" src="https://github.com/user-attachments/assets/f9f4f720-76e5-44d2-be0f-1abaab63db30" />




### b) From File (using FileInputStream)
When data is stored in a file (for example, data.txt), your program can read that data just like it reads from the console or a string in memory.
FileInputStream reads raw bytes from the file.
Scanner can wrap that stream to read the bytes as text (words, numbers, or lines).

```java
import java.io.FileInputStream;
import java.util.Scanner;

public class FileInputExample {
    public static void main(String[] args) throws Exception {
        // Create a FileInputStream to read from the file
        FileInputStream fis = new FileInputStream("data.txt");

        // Wrap the FileInputStream with a Scanner for easy text reading
        Scanner sc = new Scanner(fis);

        // Read each line from the file until there are no more lines
        while (sc.hasNextLine()) {
            System.out.println(sc.nextLine());
        }

        sc.close(); // Close the scanner (also closes the file)
    }
}

```
<img width="1589" height="185" alt="476849556-65000ad8-8eb9-43e4-ba62-0dfc23f4a019" src="https://github.com/user-attachments/assets/0a4686f3-d593-4f37-80f1-74b1d60b27a6" />


---

## 2. Output

### a) To Screen
When your program wants to show information to the user, it uses the standard output stream, known in Java as System.out.
System.out is like a pipe that sends data from your program to the console (screen).
println() writes text to that output stream and automatically moves to a new line afterward.
There are also other methods like print() (does not move to a new line) and printf() (formatted output).

```java
public class OutputExample {
    public static void main(String[] args) {
        // Print a message to the screen
        System.out.println("Hello, World!");
        
        // Print without moving to the next line
        System.out.print("Hello ");
        System.out.print("again!");

        // Print with formatting
        int age = 25;
        System.out.printf("\nI am %d years old.", age);
    }
}

```

<img width="1637" height="218" alt="476851090-f664dc2c-e50e-4a12-b325-554d3691e5be" src="https://github.com/user-attachments/assets/aae5a2f1-be8e-42f2-a570-0a740b8f7644" />


### b) To File (using FileOutputStream)
When your program needs to save data permanently, it can write output to a file instead of showing it on the screen.

In Java:

FileOutputStream writes bytes to a file.

Wrapping it with PrintWriter lets you write text easily, just like printing to the screen.

```java
iimport java.io.FileOutputStream;
import java.io.PrintWriter;

public class FileOutputExample {
    public static void main(String[] args) throws Exception {
        // Create a FileOutputStream to write to "output.txt"
        FileOutputStream fos = new FileOutputStream("output.txt");

        // Wrap it in a PrintWriter for easy text output
        PrintWriter pw = new PrintWriter(fos);

        // Write text to the file
        pw.println("Hello, File!");
        pw.printf("The sum of %d and %d is %d.", 5, 3, 5 + 3);

        // Flush and close the writer (also closes the file)
        pw.close();

        System.out.println("Data written to output.txt");
    }
}

```
<img width="507" height="59" alt="writing_to_file_pipeline" src="https://github.com/user-attachments/assets/2eba0035-7c3f-4d55-b7b1-bba129512665" />

---

## Summary Table

| **Source/Destination** | **Class/Method**                           | **Purpose** |
|------------------------|--------------------------------------------|-------------|
| Console Input          | `Scanner(System.in)`                       | Read from keyboard |
| File Input             | `Scanner(new FileInputStream("file"))`     | Read from file |
| Screen Output          | `System.out.println()`                     | Print to console |
| File Output            | `PrintWriter(new FileOutputStream("file"))`| Save text to file |
