

# Java I/O Examples (Console, Memory, File)

## 1. Input

### a) From Console
```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
System.out.print("Enter name: ");
String name = sc.nextLine();
sc.close();
```
- `Scanner(System.in)` → Reads from keyboard.

### b) From Memory (String)
```java
import java.util.Scanner;

String data = "Alice 25";
Scanner sc = new Scanner(data);
String name = sc.next();
int age = sc.nextInt();
sc.close();
```
- `Scanner(String)` → Parses a string in memory.

### c) From File (using FileInputStream)
```java
import java.io.FileInputStream;
import java.util.Scanner;

FileInputStream fis = new FileInputStream("data.txt");
Scanner sc = new Scanner(fis);
while (sc.hasNextLine()) {
    System.out.println(sc.nextLine());
}
sc.close();
```
- `FileInputStream` → Reads bytes from a file.  
- `Scanner` wraps it for easy text reading.

---

## 2. Output

### a) To Screen
```java
System.out.println("Hello, World!");
```
- `System.out` → Standard output stream.

### b) To String (in memory)
```java
import java.io.StringWriter;
import java.io.PrintWriter;

StringWriter sw = new StringWriter();
PrintWriter pw = new PrintWriter(sw);
pw.println("Hello, String!");
pw.flush();
String result = sw.toString();
System.out.println(result);
```
- `StringWriter` → Holds output in memory.

### c) To File (using FileOutputStream)
```java
import java.io.FileOutputStream;
import java.io.PrintWriter;

FileOutputStream fos = new FileOutputStream("output.txt");
PrintWriter pw = new PrintWriter(fos);
pw.println("Hello, File!");
pw.close();
```
- `FileOutputStream` → Sends bytes to a file.  
- `PrintWriter` wraps it for easy text writing.

---

## Summary Table

| **Source/Destination** | **Class/Method**                           | **Purpose** |
|------------------------|--------------------------------------------|-------------|
| Console Input          | `Scanner(System.in)`                       | Read from keyboard |
| Memory Input           | `Scanner(String)`                          | Parse string |
| File Input             | `Scanner(new FileInputStream("file"))`     | Read from file |
| Screen Output          | `System.out.println()`                     | Print to console |
| Memory Output          | `PrintWriter → StringWriter`               | Store text in memory |
| File Output            | `PrintWriter(new FileOutputStream("file"))`| Save text to file |
