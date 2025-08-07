# Exercise: Password Strength Checker

## Objective

Write a Java program that asks the user to enter a password and evaluates whether the password is **strong** or **weak** based on specific rules.



## Password Rules (Strong Password Must Have)

- At least **8 characters**
- At least **one uppercase letter** (A–Z)
- At least **one lowercase letter** (a–z)
- At least **one digit** (0–9)

If any of these conditions are not met, the password is considered **weak**.



##  Sample Runs

<img width="352" height="77" alt="1" src="https://github.com/user-attachments/assets/1cf28257-4abd-40d2-9b4c-72c508805cb4" />
<img width="340" height="87" alt="1" src="https://github.com/user-attachments/assets/eef8a503-44d1-4387-b503-dbeb51bd353e" />

<br>

```java

import java.util.Scanner;

public class PasswordChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Ask for password
        System.out.print("Enter a password: ");
        String password = scanner.nextLine();

        boolean hasUpper = false;
        boolean hasLower = false;
        boolean hasDigit = false;

        // Check each character
        for (int i = 0; i < password.length(); i++) {
            char ch = password.charAt(i);

            if (Character.isUpperCase(ch)) {
                hasUpper = true;
            } else if (Character.isLowerCase(ch)) {
                hasLower = true;
            } else if (Character.isDigit(ch)) {
                hasDigit = true;
            }
        }

        // Final check
        if (password.length() >= 8 && hasUpper && hasLower && hasDigit) {
            System.out.println("Password is strong!");
        } else {
            System.out.println("Password is weak.");
        }

        scanner.close();
    }
}
