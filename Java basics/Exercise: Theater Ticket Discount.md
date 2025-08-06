# Exercise: Theater Ticket Discount

This is a simple Java program that calculates the price of a theater ticket based on the user's age.

## Problem Description

Write a program that:

- Prompts the user to enter their age.
- Calculates the ticket price based on the following rules:

### Pricing Rules:
- Standard ticket price: **$12**
- Children under 12: **$8**
- Seniors 65 or older: **$6**

## Sample Input and Output

<img width="200" height="170" alt="image" src="https://github.com/user-attachments/assets/fd3c1e64-bbd6-4484-8023-d4c92eca5959" />
<br>

```Java
import java.util.Scanner;

public class TheaterTicket {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your age: ");
        int age = scanner.nextInt();

        int price;

        if (age < 12) {
            price = 8;
        } else if (age >= 65) {
            price = 6;
        } else {
            price = 12;
        }

        System.out.println("Ticket price: $" + price);

        scanner.close();
    }
}
```
