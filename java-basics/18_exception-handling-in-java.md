# Session 18: Exception Handling in Java

## Table of Contents
1. [Introduction to Exception Handling](#introduction-to-exception-handling)
2. [Errors vs Exceptions](#errors-vs-exceptions)
3. [Types of Exceptions](#types-of-exceptions)
4. [Common Exception Examples](#common-exception-examples)
5. [Handling Exceptions with try-catch](#handling-exceptions-with-try-catch)
6. [Multiple catch Blocks](#multiple-catch-blocks)
7. [finally Block](#finally-block)
8. [Checked vs Unchecked Exceptions](#checked-vs-unchecked-exceptions)
9. [throws Keyword](#throws-keyword)
10. [Practice Assignments](#practice-assignments)

---

## Introduction to Exception Handling

### What is an Exception?
An **Exception** is an event that causes program termination during runtime. It occurs due to **user mistakes** (invalid input) rather than programming errors.

### Key Points About Exceptions
- **Runtime Event**: Occurs during program execution
- **User Mistake**: Caused by invalid user input
- **Program Termination**: Stops program execution immediately
- **Remaining Code Skipped**: Statements after exception are not executed

### Exception Handling Goal
**Exception Handling** allows us to:
1. **Handle the exception** gracefully
2. **Continue program execution** after handling
3. **Avoid program termination** due to invalid input

---

## Errors vs Exceptions

### Comparison Table

| Aspect | Errors | Exceptions |
|--------|--------|------------|
| **Cause** | Developer mistakes | User mistakes |
| **When Occurs** | Compile time / Logic issues | Runtime |
| **Types** | Syntax errors, Logical errors | Runtime exceptions |
| **Prevention** | Fix code | Handle with try-catch |

### Types of Errors

#### 1. Syntax Errors
```java
// ❌ Syntax Errors - Programming mistakes
public class SyntaxErrorExample {
    public static void main(String[] args) {
        System.out.println("Hello World")  // Missing semicolon
        int x = 10  // Missing semicolon
        if (x > 5 {  // Missing closing parenthesis
            System.out.println("Greater");
        }
    }
}
```

#### 2. Logical Errors
```java
// ❌ Logical Error - Program runs but wrong output
public class LogicalErrorExample {
    public static void main(String[] args) {
        int a = 2, b = 5;
        int sum = a - b;  // Should be a + b, but using subtraction
        System.out.println("Sum: " + sum);  // Output: -3 (Expected: 7)
    }
}
```

### Exception Example
```java
// ✅ Exception - User provides invalid input
import java.util.Scanner;

public class ExceptionExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Program started");
        
        System.out.print("Enter a number: ");
        int number = sc.nextInt();
        
        int result = 100 / number;  // Exception if user enters 0
        System.out.println("Result: " + result);
        
        System.out.println("Program completed");
    }
}
```

**What happens when user enters 0:**
```
Program started
Enter a number: 0
Exception in thread "main" java.lang.ArithmeticException: / by zero
```

**Problems:**
1. Program terminates immediately
2. "Program completed" is never printed
3. User gets technical error message

---

## Types of Exceptions

### Exception Categories

| Type | Description | Identification | Examples |
|------|-------------|----------------|----------|
| **Checked Exceptions** | Identified by Java compiler | Compiler shows error | IOException, InterruptedException |
| **Unchecked Exceptions** | Not identified by compiler | Developer must identify | ArithmeticException, NullPointerException |

---

## Common Exception Examples

### 1. ArithmeticException
**Cause**: Division by zero

```java
public class ArithmeticExceptionExample {
    public static void main(String[] args) {
        System.out.println("Program started");
        
        int result = 100 / 0;  // Throws ArithmeticException
        System.out.println("Result: " + result);
        
        System.out.println("Program completed");  // Never executed
    }
}
```

### 2. ArrayIndexOutOfBoundsException
**Cause**: Accessing invalid array index

```java
import java.util.Scanner;

public class ArrayIndexExceptionExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] arr = new int[5];  // Valid indices: 0 to 4
        
        System.out.print("Enter position (0-4): ");
        int position = sc.nextInt();
        
        System.out.print("Enter value: ");
        int value = sc.nextInt();
        
        arr[position] = value;  // Exception if position > 4 or < 0
        System.out.println("Value at position " + position + ": " + arr[position]);
        
        System.out.println("Program completed");
    }
}
```

**What happens when user enters position 5:**
```
Enter position (0-4): 5
Enter value: 100
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 5
```

### 3. NumberFormatException
**Cause**: Converting invalid string to number

```java
public class NumberFormatExceptionExample {
    public static void main(String[] args) {
        System.out.println("Program started");
        
        String s = "welcome";  // Invalid numeric string
        int number = Integer.parseInt(s);  // Throws NumberFormatException
        System.out.println("Number: " + number);
        
        System.out.println("Program completed");  // Never executed
    }
}
```

### 4. NullPointerException
**Cause**: Operating on null variables

```java
public class NullPointerExceptionExample {
    public static void main(String[] args) {
        System.out.println("Program started");
        
        String s = null;  // null value
        int length = s.length();  // Throws NullPointerException
        System.out.println("Length: " + length);
        
        System.out.println("Program completed");  // Never executed
    }
}
```

---

## Handling Exceptions with try-catch

### Basic try-catch Syntax
```java
try {
    // Code that might throw exception
} catch (ExceptionType e) {
    // Handle the exception
}
```

### Example: Handling ArithmeticException

```java
import java.util.Scanner;

public class HandleArithmeticException {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Program started");
        
        System.out.print("Enter a number: ");
        int number = sc.nextInt();
        
        try {
            int result = 100 / number;  // Might throw ArithmeticException
            System.out.println("Result: " + result);
        } catch (ArithmeticException e) {
            System.out.println("Invalid input! Cannot divide by zero.");
        }
        
        System.out.println("Program completed");  // Always executes
    }
}
```

**Output when user enters 0:**
```
Program started
Enter a number: 0
Invalid input! Cannot divide by zero.
Program completed
```

**Output when user enters 5:**
```
Program started
Enter a number: 5
Result: 20
Program completed
```

### Key Benefits of Exception Handling
1. **Program continues** after handling exception
2. **User-friendly messages** instead of technical errors
3. **Remaining code executes** normally

### Exception Object Methods

```java
try {
    int result = 100 / 0;
} catch (ArithmeticException e) {
    System.out.println("Exception message: " + e.getMessage());
    System.out.println("Exception type: " + e.getClass().getSimpleName());
    e.printStackTrace();  // Prints detailed stack trace
}
```

---

## Multiple catch Blocks

### When to Use Multiple catch Blocks
When you don't know exactly which exception might be thrown, you can handle multiple exception types.

### Example: Multiple catch Blocks

```java
public class MultipleCatchExample {
    public static void main(String[] args) {
        try {
            String s = null;
            int length = s.length();  // Could throw NullPointerException
            // OR
            // int result = 100 / 0;  // Could throw ArithmeticException
            // OR
            // int num = Integer.parseInt("abc");  // Could throw NumberFormatException
        } catch (ArithmeticException e) {
            System.out.println("Arithmetic Exception: " + e.getMessage());
        } catch (NullPointerException e) {
            System.out.println("Null Pointer Exception: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("Number Format Exception: " + e.getMessage());
        }
        
        System.out.println("Program completed");
    }
}
```

### Universal Exception Handler
Instead of multiple catch blocks, use the parent `Exception` class:

```java
public class UniversalExceptionHandler {
    public static void main(String[] args) {
        try {
            String s = null;
            int length = s.length();  // Any exception can occur here
        } catch (Exception e) {
            System.out.println("Exception occurred: " + e.getMessage());
            System.out.println("Exception type: " + e.getClass().getSimpleName());
        }
        
        System.out.println("Program completed");
    }
}
```

### Why Use Exception Class?
- **Exception** is the parent class of all exception classes
- **One catch block** handles all types of exceptions
- **Reduces code complexity** compared to multiple catch blocks
- **Handles unknown exceptions** that you might not anticipate

---

## finally Block

### What is finally Block?
The **finally block** always executes, regardless of whether an exception occurs or not.

### finally Block Syntax
```java
try {
    // Code that might throw exception
} catch (ExceptionType e) {
    // Handle exception
} finally {
    // Always executes
}
```

### When finally Block Executes

| Scenario | try Block | catch Block | finally Block |
|----------|-----------|-------------|---------------|
| **No Exception** | ✅ Executes | ❌ Skipped | ✅ Always Executes |
| **Exception Handled** | ✅ Executes | ✅ Executes | ✅ Always Executes |
| **Exception Not Handled** | ✅ Executes | ❌ Skipped | ✅ Always Executes |

### Example: finally Block

```java
public class FinallyBlockExample {
    public static void main(String[] args) {
        try {
            String s = "welcome";  // Change to null to test exception
            int length = s.length();
            System.out.println("Length: " + length);
        } catch (NullPointerException e) {
            System.out.println("Null Pointer Exception handled");
        } finally {
            System.out.println("Finally block always executes");
        }
        
        System.out.println("Program completed");
    }
}
```

**Output (No Exception):**
```
Length: 7
Finally block always executes
Program completed
```

**Output (With Exception - change s to null):**
```
Null Pointer Exception handled
Finally block always executes
Program completed
```

### Real-World Use of finally Block

**Common Use Case: File/Database Operations**
```java
import java.io.FileInputStream;
import java.io.IOException;

public class FinallyRealWorldExample {
    public static void main(String[] args) {
        FileInputStream file = null;
        
        try {
            // Open file connection
            file = new FileInputStream("data.txt");
            System.out.println("File opened successfully");
            // Read file operations here
        } catch (IOException e) {
            System.out.println("File not found or cannot be opened");
        } finally {
            // Always close the file connection
            try {
                if (file != null) {
                    file.close();
                    System.out.println("File connection closed");
                }
            } catch (IOException e) {
                System.out.println("Error closing file");
            }
        }
    }
}
```

### Key Points About finally Block
- **Optional**: You can use try-catch without finally
- **Always executes**: Regardless of exception occurrence
- **Resource cleanup**: Used for closing files, database connections
- **Position**: Must come after all catch blocks

---

## Checked vs Unchecked Exceptions

### Detailed Comparison

| Aspect | Checked Exceptions | Unchecked Exceptions |
|--------|-------------------|---------------------|
| **Compiler Detection** | ✅ Java compiler identifies | ❌ Developer must identify |
| **Handling Requirement** | Must be handled or declared | Optional to handle |
| **Handling Methods** | try-catch OR throws keyword | Only try-catch |
| **Examples** | IOException, InterruptedException | ArithmeticException, NullPointerException |
| **Cause** | External factors (files, network) | Programming logic issues |

### Unchecked Exceptions (Runtime Exceptions)
- **Not detected** by Java compiler
- **Developer responsibility** to identify and handle
- **Examples**: ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException

### Checked Exceptions
- **Detected by Java compiler** at compile time
- **Must be handled** or program won't compile
- **Examples**: IOException, InterruptedException, FileNotFoundException

---

## throws Keyword

### What is throws Keyword?
The **throws** keyword is used to declare that a method might throw certain exceptions. It's an alternative to try-catch for handling checked exceptions.

### Comparison: try-catch vs throws

| Aspect | try-catch | throws |
|--------|-----------|--------|
| **Level** | Statement level | Method level |
| **Usage** | Handle exception immediately | Declare exception, handle later |
| **Code Location** | Around specific statements | In method signature |
| **Exception Handling** | Handles exception in same method | Passes exception to caller |

### Example: Checked Exception with Thread.sleep()

**Problem: Compiler Error**
```java
public class CheckedExceptionExample {
    public static void main(String[] args) {
        System.out.println("Program started");
        System.out.println("Program in progress");
        
        Thread.sleep(5000);  // ❌ Compiler error: Unhandled InterruptedException
        
        System.out.println("Program resumed");
        System.out.println("Program completed");
    }
}
```

### Solution 1: Using try-catch

```java
public class HandleWithTryCatch {
    public static void main(String[] args) {
        System.out.println("Program started");
        System.out.println("Program in progress");
        
        try {
            Thread.sleep(5000);  // Wait for 5 seconds
        } catch (InterruptedException e) {
            System.out.println("Thread was interrupted");
        }
        
        System.out.println("Program resumed");
        System.out.println("Program completed");
    }
}
```

### Solution 2: Using throws Keyword

```java
public class HandleWithThrows {
    public static void main(String[] args) throws InterruptedException {
        System.out.println("Program started");
        System.out.println("Program in progress");
        
        Thread.sleep(5000);  // ✅ No compiler error
        
        System.out.println("Program resumed");
        System.out.println("Program completed");
    }
}
```

### Multiple Exceptions with throws

```java
import java.io.FileInputStream;
import java.io.IOException;

public class MultipleThrowsExample {
    public static void main(String[] args) throws InterruptedException, IOException {
        // Multiple checked exceptions declared
        Thread.sleep(2000);  // InterruptedException
        
        FileInputStream file = new FileInputStream("data.txt");  // IOException
        
        System.out.println("Operations completed");
    }
}
```

### When to Use throws vs try-catch

| Use throws When | Use try-catch When |
|----------------|-------------------|
| Method cannot handle exception meaningfully | You can provide meaningful error handling |
| Exception should be handled by caller | Exception should be handled immediately |
| Multiple methods need same exception handling | Specific handling needed for each case |
| Cleaner code without nested try-catch | User-friendly error messages needed |

---

## Real-World Exception Handling Example

### Login System with Exception Handling

```java
import java.util.Scanner;

public class LoginSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        try {
            System.out.println("=== Login System ===");
            
            System.out.print("Enter username: ");
            String username = sc.nextLine();
            
            System.out.print("Enter password: ");
            String password = sc.nextLine();
            
            // Validate input
            if (username == null || username.trim().isEmpty()) {
                throw new IllegalArgumentException("Username cannot be empty");
            }
            
            if (password == null || password.trim().isEmpty()) {
                throw new IllegalArgumentException("Password cannot be empty");
            }
            
            // Simulate authentication
            if (username.equals("admin") && password.equals("password123")) {
                System.out.println("Login successful! Welcome " + username);
                System.out.println("Redirecting to dashboard...");
            } else {
                System.out.println("Invalid credentials. Please try again.");
            }
            
        } catch (IllegalArgumentException e) {
            System.out.println("Input Error: " + e.getMessage());
        } catch (Exception e) {
            System.out.println("System Error: " + e.getMessage());
        } finally {
            System.out.println("Login attempt completed");
            sc.close();
        }
    }
}
```

### Benefits Demonstrated:
1. **Application doesn't crash** on invalid input
2. **User-friendly error messages** instead of technical exceptions
3. **Proper resource cleanup** in finally block
4. **Graceful handling** of different error scenarios

---

## Exception Handling Best Practices

### 1. Identify Exception-Prone Areas
```java
// Areas where exceptions commonly occur:
Scanner input = new Scanner(System.in);  // User input
int[] array = new int[5];               // Array operations
String text = getText();                // Null operations
int result = divide(a, b);              // Arithmetic operations
FileInputStream file = new FileInputStream("file.txt");  // File operations
```

### 2. Use Specific Exception Types
```java
// ✅ Good - Specific exception handling
try {
    int result = Integer.parseInt(userInput);
} catch (NumberFormatException e) {
    System.out.println("Please enter a valid number");
}

// ❌ Avoid - Too generic (unless necessary)
try {
    int result = Integer.parseInt(userInput);
} catch (Exception e) {
    System.out.println("Something went wrong");
}
```

### 3. Provide Meaningful Error Messages
```java
// ✅ Good - User-friendly message
catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero. Please enter a non-zero number.");
}

// ❌ Avoid - Technical message
catch (ArithmeticException e) {
    System.out.println(e.getMessage());  // "/ by zero"
}
```

### 4. Use finally for Cleanup
```java
Scanner sc = null;
try {
    sc = new Scanner(System.in);
    // Use scanner
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
} finally {
    if (sc != null) {
        sc.close();  // Always cleanup resources
    }
}
```

---

## Practice Assignments

### Assignment 1: Calculator with Exception Handling
Create a calculator program that:
- Takes two numbers and an operation from user
- Handles division by zero (ArithmeticException)
- Handles invalid number input (NumberFormatException)
- Handles invalid operation input
- Uses try-catch-finally blocks

### Assignment 2: Array Operations with Exception Handling
Create a program that:
- Creates an array of size 5
- Allows user to add/retrieve elements by index
- Handles ArrayIndexOutOfBoundsException
- Handles NumberFormatException for invalid input
- Provides user-friendly error messages

### Assignment 3: File Operations with Exception Handling
Create a program that:
- Attempts to read from a file
- Handles FileNotFoundException (checked exception)
- Uses both try-catch and throws approaches
- Demonstrates finally block for resource cleanup

### Assignment 4: Student Grade System
Create a grade management system that:
- Accepts student names and grades
- Handles null input (NullPointerException)
- Handles invalid grade ranges (custom validation)
- Uses multiple catch blocks
- Provides summary even if some inputs fail

### Assignment 5: Login System Enhancement
Enhance the login system example to:
- Handle multiple login attempts
- Implement account lockout after failed attempts
- Handle different types of input errors
- Use custom exception classes
- Demonstrate all exception handling concepts

---

## Interview Questions

1. **What is the difference between Error and Exception in Java?**
2. **What are checked and unchecked exceptions? Give examples.**
3. **What is the difference between throw and throws keywords?**
4. **Can we have multiple catch blocks for a single try block?**
5. **What is the purpose of finally block? When does it execute?**
6. **What happens if an exception occurs in finally block?**
7. **Can we have try without catch block?**
8. **What is the difference between Exception and RuntimeException?**
9. **How do you create custom exceptions in Java?**
10. **What are the best practices for exception handling?**

---

## Key Takeaways

### Exception Handling Fundamentals
- **Exceptions** are runtime events caused by invalid user input
- **Exception handling** prevents program termination and allows graceful error recovery
- **try-catch blocks** are used to handle exceptions at statement level
- **throws keyword** is used to declare exceptions at method level

### Exception Types
- **Unchecked exceptions**: Developer must identify and handle (ArithmeticException, NullPointerException)
- **Checked exceptions**: Java compiler identifies and forces handling (IOException, InterruptedException)

### Best Practices
- Handle exceptions close to where they occur
- Provide meaningful error messages to users
- Use finally block for resource cleanup
- Use specific exception types when possible
- Don't ignore exceptions - always handle appropriately

---

**Next Session Preview**: We'll explore **Collections Framework** - ArrayList, HashMap, HashSet and their practical applications in data management, along with iterators and advanced collection operations.

## Custom Exceptions

### Creating Custom Exception Classes
Sometimes built-in exceptions don't fit your specific business requirements. You can create your own custom exceptions.

### Custom Exception Example

```java
// Custom Exception Class
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);  // Call parent Exception constructor
    }
}

// Using Custom Exception
public class CustomExceptionExample {
    public static void validateAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age must be 18 or above for voting");
        }
        if (age > 120) {
            throw new InvalidAgeException("Age cannot be more than 120 years");
        }
        System.out.println("Valid age: " + age);
    }
    
    public static void main(String[] args) {
        try {
            validateAge(15);  // Will throw InvalidAgeException
        } catch (InvalidAgeException e) {
            System.out.println("Custom Exception: " + e.getMessage());
        }
        
        try {
            validateAge(25);  // Valid age
        } catch (InvalidAgeException e) {
            System.out.println("Custom Exception: " + e.getMessage());
        }
    }
}
```

**Output:**
```
Custom Exception: Age must be 18 or above for voting
Valid age: 25
```

### Banking System with Custom Exceptions

```java
// Custom Exceptions for Banking
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

class InvalidAccountException extends Exception {
    public InvalidAccountException(String message) {
        super(message);
    }
}

// Bank Account Class
class BankAccount {
    private String accountNumber;
    private double balance;
    
    public BankAccount(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }
    
    public void withdraw(double amount) throws InsufficientFundsException, InvalidAccountException {
        if (accountNumber == null || accountNumber.trim().isEmpty()) {
            throw new InvalidAccountException("Account number cannot be empty");
        }
        
        if (amount > balance) {
            throw new InsufficientFundsException("Insufficient funds. Available balance: " + balance);
        }
        
        balance -= amount;
        System.out.println("Withdrawal successful. Remaining balance: " + balance);
    }
    
    public double getBalance() {
        return balance;
    }
}

// Main Class
public class BankingSystemExample {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("ACC123", 1000.0);
        
        try {
            account.withdraw(500);   // Valid withdrawal
            account.withdraw(600);   // Will throw InsufficientFundsException
        } catch (InsufficientFundsException e) {
            System.out.println("Banking Error: " + e.getMessage());
        } catch (InvalidAccountException e) {
            System.out.println("Account Error: " + e.getMessage());
        }
    }
}
```

---

## throw vs throws Keywords

### Detailed Comparison

| Aspect | throw | throws |
|--------|-------|--------|
| **Purpose** | Actually throw an exception | Declare that method might throw exception |
| **Location** | Inside method body | In method signature |
| **Usage** | `throw new ExceptionType("message")` | `methodName() throws ExceptionType` |
| **Quantity** | One exception at a time | Multiple exceptions can be declared |
| **Execution** | Immediately throws exception | Just declares possibility |

### throw Keyword Example

```java
public class ThrowKeywordExample {
    public static void checkAge(int age) {
        if (age < 18) {
            throw new IllegalArgumentException("Age must be 18 or above");
        }
        System.out.println("Age is valid: " + age);
    }
    
    public static void main(String[] args) {
        try {
            checkAge(15);  // Will throw exception
        } catch (IllegalArgumentException e) {
            System.out.println("Exception caught: " + e.getMessage());
        }
        
        checkAge(25);  // Valid age
    }
}
```

### throws Keyword Example

```java
import java.io.FileInputStream;
import java.io.IOException;

public class ThrowsKeywordExample {
    // Method declares it might throw IOException
    public static void readFile(String filename) throws IOException {
        FileInputStream file = new FileInputStream(filename);
        System.out.println("File opened successfully");
        file.close();
    }
    
    public static void main(String[] args) {
        try {
            readFile("nonexistent.txt");  // Will throw IOException
        } catch (IOException e) {
            System.out.println("File operation failed: " + e.getMessage());
        }
    }
}
```

---

## Exception Propagation

### How Exceptions Propagate Through Method Calls

```java
public class ExceptionPropagationExample {
    public static void method1() {
        int result = 10 / 0;  // ArithmeticException occurs here
        System.out.println("This won't print");
    }
    
    public static void method2() {
        System.out.println("Method2 started");
        method1();  // Exception propagates from method1
        System.out.println("Method2 completed");  // Won't execute
    }
    
    public static void method3() {
        System.out.println("Method3 started");
        method2();  // Exception propagates from method2
        System.out.println("Method3 completed");  // Won't execute
    }
    
    public static void main(String[] args) {
        System.out.println("Main started");
        
        try {
            method3();  // Exception propagates through method3 → method2 → method1
        } catch (ArithmeticException e) {
            System.out.println("Exception caught in main: " + e.getMessage());
        }
        
        System.out.println("Main completed");
    }
}
```

**Output:**
```
Main started
Method3 started
Method2 started
Exception caught in main: / by zero
Main completed
```

### Exception Propagation with Method Handling

```java
public class ExceptionHandlingInMethods {
    public static void method1() {
        try {
            int result = 10 / 0;  // Exception occurs
        } catch (ArithmeticException e) {
            System.out.println("Exception handled in method1: " + e.getMessage());
        }
        System.out.println("Method1 completed normally");
    }
    
    public static void method2() {
        System.out.println("Method2 started");
        method1();  // No exception propagates because it's handled in method1
        System.out.println("Method2 completed");
    }
    
    public static void main(String[] args) {
        System.out.println("Main started");
        method2();
        System.out.println("Main completed");
    }
}
```

**Output:**
```
Main started
Method2 started
Exception handled in method1: / by zero
Method1 completed normally
Method2 completed
Main completed
```

---

## Nested try-catch Blocks

### When to Use Nested try-catch
When you need different levels of exception handling within the same method.

```java
import java.util.Scanner;

public class NestedTryCatchExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        try {
            System.out.print("Enter array size: ");
            int size = sc.nextInt();
            int[] arr = new int[size];
            
            try {
                System.out.print("Enter index to access: ");
                int index = sc.nextInt();
                
                System.out.print("Enter value to store: ");
                int value = sc.nextInt();
                
                arr[index] = value;
                System.out.println("Value stored successfully at index " + index);
                
                try {
                    System.out.print("Enter divisor: ");
                    int divisor = sc.nextInt();
                    int result = arr[index] / divisor;
                    System.out.println("Division result: " + result);
                } catch (ArithmeticException e) {
                    System.out.println("Cannot divide by zero");
                }
                
            } catch (ArrayIndexOutOfBoundsException e) {
                System.out.println("Invalid array index: " + e.getMessage());
            }
            
        } catch (Exception e) {
            System.out.println("General error: " + e.getMessage());
        } finally {
            sc.close();
            System.out.println("Scanner closed");
        }
    }
}
```

---

## Exception Handling in Real-World Scenarios

### Web Application Login System

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

// Custom Exceptions
class UserNotFoundException extends Exception {
    public UserNotFoundException(String message) {
        super(message);
    }
}

class InvalidPasswordException extends Exception {
    public InvalidPasswordException(String message) {
        super(message);
    }
}

class AccountLockedException extends Exception {
    public AccountLockedException(String message) {
        super(message);
    }
}

// User Management System
class UserManager {
    private Map<String, String> users;
    private Map<String, Integer> failedAttempts;
    private static final int MAX_ATTEMPTS = 3;
    
    public UserManager() {
        users = new HashMap<>();
        failedAttempts = new HashMap<>();
        
        // Sample users
        users.put("admin", "admin123");
        users.put("user1", "password123");
        users.put("john", "john456");
    }
    
    public boolean login(String username, String password) 
            throws UserNotFoundException, InvalidPasswordException, AccountLockedException {
        
        // Check if account is locked
        if (failedAttempts.getOrDefault(username, 0) >= MAX_ATTEMPTS) {
            throw new AccountLockedException("Account locked due to multiple failed attempts");
        }
        
        // Check if user exists
        if (!users.containsKey(username)) {
            throw new UserNotFoundException("User '" + username + "' not found");
        }
        
        // Check password
        if (!users.get(username).equals(password)) {
            int attempts = failedAttempts.getOrDefault(username, 0) + 1;
            failedAttempts.put(username, attempts);
            
            if (attempts >= MAX_ATTEMPTS) {
                throw new AccountLockedException("Account locked after " + MAX_ATTEMPTS + " failed attempts");
            }
            
            throw new InvalidPasswordException("Invalid password. Attempts remaining: " + (MAX_ATTEMPTS - attempts));
        }
        
        // Reset failed attempts on successful login
        failedAttempts.put(username, 0);
        return true;
    }
}

// Main Application
public class WebLoginSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        UserManager userManager = new UserManager();
        
        System.out.println("=== Web Application Login System ===");
        
        while (true) {
            try {
                System.out.print("\nEnter username (or 'exit' to quit): ");
                String username = sc.nextLine().trim();
                
                if (username.equalsIgnoreCase("exit")) {
                    System.out.println("Goodbye!");
                    break;
                }
                
                if (username.isEmpty()) {
                    throw new IllegalArgumentException("Username cannot be empty");
                }
                
                System.out.print("Enter password: ");
                String password = sc.nextLine().trim();
                
                if (password.isEmpty()) {
                    throw new IllegalArgumentException("Password cannot be empty");
                }
                
                boolean loginSuccess = userManager.login(username, password);
                
                if (loginSuccess) {
                    System.out.println("✅ Login successful! Welcome, " + username);
                    System.out.println("Redirecting to dashboard...");
                    break;  // Exit after successful login
                }
                
            } catch (UserNotFoundException e) {
                System.out.println("❌ " + e.getMessage());
            } catch (InvalidPasswordException e) {
                System.out.println("❌ " + e.getMessage());
            } catch (AccountLockedException e) {
                System.out.println("🔒 " + e.getMessage());
                System.out.println("Please contact administrator to unlock your account.");
            } catch (IllegalArgumentException e) {
                System.out.println("⚠️ Input Error: " + e.getMessage());
            } catch (Exception e) {
                System.out.println("💥 System Error: " + e.getMessage());
            }
        }
        
        sc.close();
    }
}
```

### E-commerce Order Processing System

```java
// Custom Exceptions for E-commerce
class ProductNotFoundException extends Exception {
    public ProductNotFoundException(String message) {
        super(message);
    }
}

class InsufficientStockException extends Exception {
    public InsufficientStockException(String message) {
        super(message);
    }
}

class PaymentFailedException extends Exception {
    public PaymentFailedException(String message) {
        super(message);
    }
}

// Product Class
class Product {
    private String id;
    private String name;
    private double price;
    private int stock;
    
    public Product(String id, String name, double price, int stock) {
        this.id = id;
        this.name = name;
        this.price = price;
        this.stock = stock;
    }
    
    // Getters and setters
    public String getId() { return id; }
    public String getName() { return name; }
    public double getPrice() { return price; }
    public int getStock() { return stock; }
    public void setStock(int stock) { this.stock = stock; }
}

// Order Processing System
class OrderProcessor {
    private Map<String, Product> products;
    
    public OrderProcessor() {
        products = new HashMap<>();
        
        // Sample products
        products.put("P001", new Product("P001", "Laptop", 999.99, 5));
        products.put("P002", new Product("P002", "Mouse", 29.99, 10));
        products.put("P003", new Product("P003", "Keyboard", 79.99, 0));
    }
    
    public void processOrder(String productId, int quantity, String paymentMethod) 
            throws ProductNotFoundException, InsufficientStockException, PaymentFailedException {
        
        System.out.println("Processing order for product: " + productId);
        
        // Step 1: Check if product exists
        if (!products.containsKey(productId)) {
            throw new ProductNotFoundException("Product with ID '" + productId + "' not found");
        }
        
        Product product = products.get(productId);
        
        // Step 2: Check stock availability
        if (product.getStock() < quantity) {
            throw new InsufficientStockException(
                "Insufficient stock for " + product.getName() + 
                ". Available: " + product.getStock() + ", Requested: " + quantity
            );
        }
        
        // Step 3: Calculate total amount
        double totalAmount = product.getPrice() * quantity;
        System.out.println("Order total: $" + totalAmount);
        
        // Step 4: Process payment
        if (!processPayment(totalAmount, paymentMethod)) {
            throw new PaymentFailedException("Payment failed for amount $" + totalAmount);
        }
        
        // Step 5: Update stock
        product.setStock(product.getStock() - quantity);
        
        System.out.println("✅ Order processed successfully!");
        System.out.println("Product: " + product.getName());
        System.out.println("Quantity: " + quantity);
        System.out.println("Total: $" + totalAmount);
        System.out.println("Remaining stock: " + product.getStock());
    }
    
    private boolean processPayment(double amount, String paymentMethod) {
        // Simulate payment processing
        System.out.println("Processing payment of $" + amount + " via " + paymentMethod);
        
        // Simulate random payment failure (20% chance)
        return Math.random() > 0.2;
    }
    
    public void displayProducts() {
        System.out.println("\n=== Available Products ===");
        for (Product product : products.values()) {
            System.out.println(product.getId() + " - " + product.getName() + 
                             " - $" + product.getPrice() + " (Stock: " + product.getStock() + ")");
        }
    }
}

// Main E-commerce Application
public class EcommerceSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        OrderProcessor orderProcessor = new OrderProcessor();
        
        System.out.println("=== E-commerce Order Processing System ===");
        
        while (true) {
            try {
                orderProcessor.displayProducts();
                
                System.out.print("\nEnter product ID (or 'exit' to quit): ");
                String productId = sc.nextLine().trim().toUpperCase();
                
                if (productId.equalsIgnoreCase("exit")) {
                    System.out.println("Thank you for using our system!");
                    break;
                }
                
                System.out.print("Enter quantity: ");
                int quantity = Integer.parseInt(sc.nextLine().trim());
                
                if (quantity <= 0) {
                    throw new IllegalArgumentException("Quantity must be greater than 0");
                }
                
                System.out.print("Enter payment method (Credit/Debit/PayPal): ");
                String paymentMethod = sc.nextLine().trim();
                
                if (paymentMethod.isEmpty()) {
                    throw new IllegalArgumentException("Payment method cannot be empty");
                }
                
                orderProcessor.processOrder(productId, quantity, paymentMethod);
                
            } catch (ProductNotFoundException e) {
                System.out.println("❌ Product Error: " + e.getMessage());
            } catch (InsufficientStockException e) {
                System.out.println("📦 Stock Error: " + e.getMessage());
            } catch (PaymentFailedException e) {
                System.out.println("💳 Payment Error: " + e.getMessage());
            } catch (NumberFormatException e) {
                System.out.println("⚠️ Please enter a valid number for quantity");
            } catch (IllegalArgumentException e) {
                System.out.println("⚠️ Input Error: " + e.getMessage());
            } catch (Exception e) {
                System.out.println("💥 System Error: " + e.getMessage());
                e.printStackTrace();
            }
            
            System.out.println("\n" + "=".repeat(50));
        }
        
        sc.close();
    }
}
```

---

## Exception Handling Performance Considerations

### Best Practices for Performance

#### 1. Don't Use Exceptions for Control Flow
```java
// ❌ Bad - Using exceptions for control flow
public class BadExceptionUsage {
    public static boolean isValidNumber(String input) {
        try {
            Integer.parseInt(input);
            return true;
        } catch (NumberFormatException e) {
            return false;
        }
    }
}

// ✅ Good - Proper validation without exceptions
public class GoodValidation {
    public static boolean isValidNumber(String input) {
        if (input == null || input.trim().isEmpty()) {
            return false;
        }
        
        try {
            Integer.parseInt(input);
            return true;
        } catch (NumberFormatException e) {
            return false;
        }
    }
}
```

#### 2. Cache Exception Objects When Possible
```java
public class ExceptionCaching {
    // Cache commonly used exceptions
    private static final IllegalArgumentException INVALID_AGE = 
        new IllegalArgumentException("Age must be between 0 and 120");
    
    public static void validateAge(int age) throws IllegalArgumentException {
        if (age < 0 || age > 120) {
            throw INVALID_AGE;  // Reuse cached exception
        }
    }
}
```

#### 3. Use Specific Exception Types
```java
// ✅ Good - Specific exception handling
public class SpecificExceptionHandling {
    public static void processFile(String filename) {
        try {
            // File operations
        } catch (FileNotFoundException e) {
            System.out.println("File not found: " + filename);
        } catch (IOException e) {
            System.out.println("IO error while processing file");
        } catch (SecurityException e) {
            System.out.println("Access denied to file: " + filename);
        }
    }
}
```

---

## Complete Exception Hierarchy

### Java Exception Class Hierarchy

```
java.lang.Object
    └── java.lang.Throwable
        ├── java.lang.Error (Unchecked)
        │   ├── OutOfMemoryError
        │   ├── StackOverflowError
        │   └── VirtualMachineError
        └── java.lang.Exception
            ├── Checked Exceptions
            │   ├── IOException
            │   │   ├── FileNotFoundException
            │   │   └── EOFException
            │   ├── InterruptedException
            │   ├── ClassNotFoundException
            │   └── SQLException
            └── RuntimeException (Unchecked)
                ├── ArithmeticException
                ├── NullPointerException
                ├── ArrayIndexOutOfBoundsException
                ├── NumberFormatException
                ├── IllegalArgumentException
                └── ClassCastException
```

### Exception Categories Summary

| Category | Checked by Compiler | Must Handle | Examples |
|----------|-------------------|-------------|----------|
| **Error** | No | No (shouldn't handle) | OutOfMemoryError, StackOverflowError |
| **Checked Exception** | Yes | Yes (try-catch or throws) | IOException, InterruptedException |
| **Unchecked Exception** | No | Optional | ArithmeticException, NullPointerException |

---

## Advanced Exception Handling Patterns

### 1. Exception Translation Pattern
```java
// Convert low-level exceptions to high-level business exceptions
public class DataService {
    public User getUserById(int id) throws UserServiceException {
        try {
            // Database operation that might throw SQLException
            return database.findUser(id);
        } catch (SQLException e) {
            // Translate SQLException to business exception
            throw new UserServiceException("Failed to retrieve user with ID: " + id, e);
        }
    }
}
```

### 2. Exception Chaining Pattern
```java
public class ExceptionChainingExample {
    public static void processData() throws DataProcessingException {
        try {
            // Some operation that throws IOException
            readFile("data.txt");
        } catch (IOException e) {
            // Chain the original exception
            throw new DataProcessingException("Data processing failed", e);
        }
    }
    
    public static void main(String[] args) {
        try {
            processData();
        } catch (DataProcessingException e) {
            System.out.println("Main exception: " + e.getMessage());
            System.out.println("Root cause: " + e.getCause().getMessage());
            e.printStackTrace();
        }
    }
}
```

### 3. Resource Management with try-with-resources
```java
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Scanner;

public class TryWithResourcesExample {
    // ✅ Automatic resource management
    public static void readFileWithTryWithResources(String filename) {
        try (FileInputStream file = new FileInputStream(filename);
             Scanner scanner = new Scanner(file)) {
            
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
            // Resources automatically closed here
            
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
        // No need for finally block to close resources
    }
    
    // ❌ Manual resource management (old way)
    public static void readFileManually(String filename) {
        FileInputStream file = null;
        Scanner scanner = null;
        
        try {
            file = new FileInputStream(filename);
            scanner = new Scanner(file);
            
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
            
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        } finally {
            // Manual cleanup required
            if (scanner != null) {
                scanner.close();
            }
            if (file != null) {
                try {
                    file.close();
                } catch (IOException e) {
                    System.out.println("Error closing file: " + e.getMessage());
                }
            }
        }
    }
}
```

---

## Exception Handling Testing

### Unit Testing Exception Scenarios

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class ExceptionHandlingTest {
    
    @Test(expected = IllegalArgumentException.class)
    public void testInvalidAgeThrowsException() {
        UserValidator.validateAge(-5);  // Should throw IllegalArgumentException
    }
    
    @Test
    public void testValidAgeDoesNotThrowException() {
        try {
            UserValidator.validateAge(25);  // Should not throw exception
            // Test passes if no exception is thrown
        } catch (Exception e) {
            fail("Valid age should not throw exception: " + e.getMessage());
        }
    }
    
    @Test
    public void testExceptionMessage() {
        try {
            UserValidator.validateAge(-5);
            fail("Expected IllegalArgumentException");
        } catch (IllegalArgumentException e) {
            assertEquals("Age must be between 0 and 120", e.getMessage());
        }
    }
}
```

---

## Summary and Key Points

### Exception Handling Mastery Checklist

#### ✅ Fundamental Concepts
- [x] Understand difference between Errors and Exceptions
- [x] Know Checked vs Unchecked exceptions
- [x] Master try-catch-finally blocks
- [x] Understand exception propagation
- [x] Know when to use throw vs throws

#### ✅ Advanced Concepts
- [x] Create and use custom exceptions
- [x] Implement exception chaining
- [x] Use try-with-resources for automatic resource management
- [x] Apply exception handling best practices
- [x] Handle exceptions in real-world scenarios

#### ✅ Best Practices Applied
- [x] Use specific exception types when possible
- [x] Provide meaningful error messages
- [x] Don't ignore exceptions
- [x] Use finally for resource cleanup
- [x] Don't use exceptions for control flow
- [x] Handle exceptions close to where they occur

#### ✅ Real-World Applications
- [x] Web application login systems
- [x] E-commerce order processing
- [x] File and database operations
- [x] User input validation
- [x] Banking and financial systems

### Exception Handling Decision Tree

```
Exception Occurs
    ├── Can you handle it meaningfully?
    │   ├── Yes → Use try-catch
    │   └── No → Use throws (let caller handle)
    ├── Is it a checked exception?
    │   ├── Yes → Must handle or declare with throws
    │   └── No → Optional to handle
    ├── Do you need cleanup?
    │   ├── Yes → Use finally block or try-with-resources
    │   └── No → Simple try-catch is sufficient
    └── Is it a business logic error?
        ├── Yes → Create custom exception
        └── No → Use built-in exception types
```

---

**🎯 Congratulations!** You've completed the comprehensive Exception Handling tutorial. You now understand how to:
- Handle runtime errors gracefully
- Create robust applications that don't crash on invalid input
- Implement professional error handling patterns
- Build user-friendly applications with proper exception management

**Next Session Preview**: We'll explore **Collections Framework** - ArrayList, HashMap, HashSet, and their practical applications in data management, along with iterators and advanced collection operations for building scalable Java applications.