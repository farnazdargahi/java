Exercise: Theater Ticket Discount

Write a program that asks the user for their age and calculates the ticket price based on the following rules:

Standard ticket price: $12
Under 12: $8 
65 or older: $6 

<img width="2733" height="459" alt="image" src="https://github.com/user-attachments/assets/9347e347-0382-4c62-a168-134e7641138f" />



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
