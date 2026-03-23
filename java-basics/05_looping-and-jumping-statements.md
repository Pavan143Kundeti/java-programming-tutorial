# 05 - Looping and Jumping Statements in Java

## Table of Contents
1. [What are Looping Statements?](#what-are-looping-statements)
2. [Why Use Loops?](#why-use-loops)
3. [Three Essential Components of Loops](#three-essential-components-of-loops)
4. [While Loop](#while-loop)
5. [Do-While Loop](#do-while-loop)
6. [For Loop](#for-loop)
7. [Comparison: When to Use Which Loop](#comparison-when-to-use-which-loop)
8. [Jumping Statements](#jumping-statements)
9. [Practice Assignments](#practice-assignments)

---

## What are Looping Statements?

### Definition
**A loop is a set of statements that execute multiple times repetitively.**

### Purpose
- **Repeat statements** without writing them multiple times
- **Avoid code duplication**
- **Reduce code length**
- **Execute same logic** with different values

### Types of Loops in Java

| Loop Type | Description | Usage |
|-----------|-------------|-------|
| **while** | Condition checked first | When you don't know exact iterations |
| **do-while** | Statements execute first | When you need at least one execution |
| **for** | Most structured format | When you know exact iterations |
| **enhanced for** | For collections/arrays | Will be covered with arrays |

---

## Why Use Loops?

### Problem Without Loops
**To print numbers 1 to 10, you would need 10 separate statements:**

```java
System.out.println(1);
System.out.println(2);
System.out.println(3);
System.out.println(4);
System.out.println(5);
System.out.println(6);
System.out.println(7);
System.out.println(8);
System.out.println(9);
System.out.println(10);
```

### Solution With Loops
**Same result with just a few lines:**

```java
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

### Benefits of Using Loops
1. **Reduces code length** significantly
2. **Eliminates duplication** of similar statements
3. **Makes code maintainable** - change once, affects all iterations
4. **Handles dynamic requirements** - can change number of iterations

---

## Three Essential Components of Loops

**Every loop requires these three components:**

### 1. Initialization
- **Where to start** the loop
- **Starting point** of the iteration
- **Example:** `int i = 1` (start from 1)

### 2. Condition
- **How many times** to repeat
- **When to stop** the loop
- **Example:** `i <= 10` (repeat while i is less than or equal to 10)

### 3. Increment/Decrement
- **How much to change** in each iteration
- **Step size** for each round
- **Example:** `i++` (increase by 1 each time)

### Example Breakdown
```java
// Print numbers 1 to 10
int i = 1;        // 1. Initialization (start from 1)
while (i <= 10) { // 2. Condition (repeat while i <= 10)
    System.out.println(i);
    i++;          // 3. Increment (increase by 1)
}
```

### What Happens Without These Components?

#### Missing Initialization
```java
// Error: i is not defined
while (i <= 10) {  // ❌ Compilation error
    System.out.println(i);
    i++;
}
```

#### Missing Condition
```java
int i = 1;
while (true) {     // ❌ Infinite loop
    System.out.println(i);
    i++;
}
```

#### Missing Increment/Decrement
```java
int i = 1;
while (i <= 10) {
    System.out.println(i);  // ❌ Prints 1 forever (infinite loop)
    // Missing i++ - condition never becomes false
}
```

---

## While Loop

### Syntax
```java
// Initialization (before loop)
dataType variable = startValue;

while (condition) {
    // Statements to repeat
    // Increment/Decrement
}
```

### Execution Flow
1. **Check condition** first
2. **If true:** Execute statements, then increment/decrement
3. **If false:** Exit loop
4. **Repeat** steps 1-3 until condition becomes false

### Eclipse Example: Print 1 to 10
```java
package day5;

public class WhileLoopDemo {
    public static void main(String[] args) {
        // Example 1: Print numbers 1 to 10
        int i = 1;              // Initialization
        while (i <= 10) {      // Condition
            System.out.println(i);
            i++;                // Increment
        }
    }
}
```

### Example 2: Print Hello Message 10 Times
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;              // Start from 1
        while (i <= 10) {      // Repeat 10 times
            System.out.println("Hello");
            i++;                // Increment counter
        }
    }
}
```

### Example 3: Print Even Numbers (Approach 1)
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        // Print even numbers between 1 to 10
        int i = 2;              // Start from first even number
        while (i <= 10) {      // Up to 10
            System.out.println(i);
            i += 2;             // Increment by 2 (i = i + 2)
        }
        // Output: 2, 4, 6, 8, 10
    }
}
```

### Example 4: Print Even Numbers (Approach 2)
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        // Print even numbers using filtering
        int i = 1;              // Start from 1
        while (i <= 10) {      // Check all numbers 1 to 10
            if (i % 2 == 0) {   // Filter: only even numbers
                System.out.println(i);
            }
            i++;                // Increment by 1
        }
        // Output: 2, 4, 6, 8, 10
    }
}
```

### Example 5: Print Numbers with Even/Odd Labels
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 10) {
            if (i % 2 == 0) {
                System.out.println(i + " is even number");
            } else {
                System.out.println(i + " is odd number");
            }
            i++;
        }
        // Output: 1 is odd number, 2 is even number, etc.
    }
}
```

### Example 6: Print Numbers in Descending Order
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        // Print 10 to 1 in descending order
        int i = 10;             // Start from 10
        while (i >= 1) {       // Continue while i >= 1
            System.out.println(i);
            i--;                // Decrement by 1
        }
        // Output: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
    }
}
```

### Infinite Loop Example (Avoid This!)
```java
public class WhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 10) {
            System.out.println(i);
            // Missing i++ - infinite loop!
            // Will print 1 forever
        }
    }
}
```

---

## Do-While Loop

### Syntax
```java
// Initialization (before loop)
dataType variable = startValue;

do {
    // Statements to repeat
    // Increment/Decrement
} while (condition);  // Note: semicolon required
```

### Key Differences from While Loop

| Feature | While Loop | Do-While Loop |
|---------|------------|---------------|
| **Condition Check** | Before execution | After execution |
| **Minimum Executions** | 0 (if condition false) | 1 (always) |
| **Syntax** | `while (condition) { }` | `do { } while (condition);` |
| **Semicolon** | Not required | Required after while |

### Execution Flow
1. **Execute statements** first (without checking condition)
2. **Check condition** after execution
3. **If true:** Repeat from step 1
4. **If false:** Exit loop

### Example 1: Print 1 to 10 with Do-While
```java
package day5;

public class DoWhileLoopDemo {
    public static void main(String[] args) {
        int i = 1;              // Initialization
        do {
            System.out.println(i);
            i++;                // Increment
        } while (i <= 10);      // Condition (semicolon required)
        
        // Output: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
    }
}
```

### Example 2: Print 10 to 1 in Descending Order
```java
public class DoWhileLoopDemo {
    public static void main(String[] args) {
        int i = 10;             // Start from 10
        do {
            System.out.println(i);
            i--;                // Decrement
        } while (i >= 1);       // Continue while i >= 1
        
        // Output: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
    }
}
```

### Demonstrating the Key Difference
```java
package day5;

public class WhileVsDoWhile {
    public static void main(String[] args) {
        System.out.println("=== While Loop ===");
        int i = 10;             // Start with 10
        while (i <= 5) {       // Condition: 10 <= 5 (false)
            System.out.println(i);
            i++;
        }
        // Output: Nothing (condition false from start)
        
        System.out.println("=== Do-While Loop ===");
        int j = 10;             // Start with 10
        do {
            System.out.println(j);  // Executes once
            j++;
        } while (j <= 5);       // Condition: 11 <= 5 (false)
        // Output: 10 (executes at least once)
    }
}
```

**Key Insight:** Do-while executes at least once, even if condition is false initially.

---

## For Loop

### Why For Loop is Preferred
- **Most structured** format
- **All three components** in one line
- **Reduces code length** significantly
- **Preferred 80-90%** of the time

### Syntax
```java
for (initialization; condition; increment/decrement) {
    // Statements to repeat
}
```

### Syntax Breakdown
```java
for (int i = 1; i <= 10; i++) {
//   ↑         ↑        ↑
//   Init   Condition  Increment
    System.out.println(i);
}
```

### Execution Flow
1. **Initialization** (executes only once)
2. **Check condition**
3. **If true:** Execute statements
4. **Increment/Decrement**
5. **Repeat** steps 2-4 until condition becomes false

### Detailed Execution Steps
```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}

// Step-by-step execution:
// Step 1: i = 1 (initialization - once only)
// Step 2: Check 1 <= 5 (true) → Execute print(1) → i++ → i = 2
// Step 3: Check 2 <= 5 (true) → Execute print(2) → i++ → i = 3
// Step 4: Check 3 <= 5 (true) → Execute print(3) → i++ → i = 4
// Step 5: Check 4 <= 5 (true) → Execute print(4) → i++ → i = 5
// Step 6: Check 5 <= 5 (true) → Execute print(5) → i++ → i = 6
// Step 7: Check 6 <= 5 (false) → Exit loop
```

### Example 1: Print 1 to 10
```java
package day5;

public class ForLoopDemo {
    public static void main(String[] args) {
        // Print numbers 1 to 10
        for (int i = 1; i <= 10; i++) {
            System.out.println(i);
        }
    }
}
```

### Example 2: Print Even Numbers
```java
public class ForLoopDemo {
    public static void main(String[] args) {
        // Print even numbers between 1 to 10
        for (int i = 2; i <= 10; i += 2) {
            System.out.println(i);
        }
        // Output: 2, 4, 6, 8, 10
    }
}
```

### Example 3: Print Numbers with Even/Odd Labels
```java
public class ForLoopDemo {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                System.out.println(i + " is even number");
            } else {
                System.out.println(i + " is odd number");
            }
        }
    }
}
```

### Example 4: Print Numbers in Descending Order
```java
public class ForLoopDemo {
    public static void main(String[] args) {
        // Print 10 to 1 in descending order
        for (int i = 10; i >= 1; i--) {
            System.out.println(i);
        }
        // Output: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
    }
}
```

### Code Comparison: While vs For Loop

#### Using While Loop (Multiple Lines)
```java
// Requires 4+ lines
int i = 1;              // Line 1: Initialization
while (i <= 10) {      // Line 2: Condition
    System.out.println(i);  // Line 3: Statement
    i++;                // Line 4: Increment
}
```

#### Using For Loop (Single Line)
```java
// All in one line
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

**Result:** ~50% code reduction with for loops!

---

## Comparison: When to Use Which Loop

### Decision Matrix

| Scenario | Best Loop | Reason |
|----------|-----------|--------|
| **Know exact iterations** | `for` | Most structured, all components in one line |
| **Need at least one execution** | `do-while` | Executes before checking condition |
| **Don't know exact iterations** | `while` | Can use conditions like `while(true)` with break |

### Detailed Guidelines

#### Use For Loop When:
- **You know the number of iterations** in advance
- **You have clear start, condition, and increment**
- **Most common choice** (80-90% of cases)

```java
// Perfect for for-loop
for (int i = 1; i <= 100; i++) {
    System.out.println(i);
}
```

#### Use Do-While Loop When:
- **You need at least one execution** regardless of condition
- **Rare usage** in practice

```java
// Menu system - show menu at least once
String choice;
do {
    System.out.println("1. Option A");
    System.out.println("2. Option B");
    System.out.println("3. Exit");
    choice = scanner.next();
} while (!choice.equals("3"));
```

#### Use While Loop When:
- **You don't know exact iterations**
- **Condition-based termination**
- **Need infinite loop with break**

```java
// Example: Unknown iterations with break
int i = 1;
while (true) {          // Infinite loop
    System.out.println("Hello " + i);
    i++;
    if (i == 10) {      // Break based on condition
        break;          // Exit loop
    }
}
```

### Real-World Analogy

#### For Loop = Bike Travel
- **Know starting point** (source)
- **Know destination** (target)
- **Know fuel needed** (iterations)
- **Plan everything** in advance

#### Do-While Loop = Bus Travel
- **Get on bus first** (execute once)
- **Then buy ticket** (check condition)
- **No prior planning** needed

#### While Loop = Flight Travel
- **Buy ticket first** (check condition)
- **Then board flight** (execute statements)
- **Condition must be satisfied** before execution

---

## Jumping Statements

### Purpose
**Control the flow of execution within loops and conditional statements.**

### Types of Jumping Statements

| Statement | Purpose | Usage |
|-----------|---------|-------|
| **break** | Exit loop immediately | Exit loops, switch cases |
| **continue** | Skip current iteration | Skip to next iteration |

---

### Break Statement

#### Purpose
**Immediately exit from the loop, regardless of condition.**

#### Syntax
```java
for (int i = 1; i <= 10; i++) {
    if (someCondition) {
        break;  // Exit loop immediately
    }
    // Other statements
}
```

#### Example 1: Exit Loop at Specific Value
```java
package day5;

public class BreakStatement {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                break;  // Exit when i equals 5
            }
            System.out.println(i);
        }
        // Output: 1, 2, 3, 4 (5 and beyond are not printed)
    }
}
```

#### Step-by-Step Execution
```java
// i = 1: 1 != 5, print 1
// i = 2: 2 != 5, print 2  
// i = 3: 3 != 5, print 3
// i = 4: 4 != 5, print 4
// i = 5: 5 == 5, break executed → exit loop
// i = 6, 7, 8, 9, 10: never reached
```

#### Example 2: While Loop with Break
```java
public class BreakStatement {
    public static void main(String[] args) {
        int i = 1;
        while (true) {          // Infinite loop
            System.out.println("Hello " + i);
            i++;
            if (i == 11) {      // Break condition
                break;          // Exit loop
            }
        }
        // Prints Hello 1 through Hello 10, then exits
    }
}
```

#### Important Rules for Break
1. **Cannot have statements** after break in same block
2. **Unreachable code error** if you try

```java
// ❌ This will cause compilation error
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;
        System.out.println("This line is unreachable"); // Error!
    }
}
```

---

### Continue Statement

#### Purpose
**Skip the current iteration and jump to the next iteration.**

#### Syntax
```java
for (int i = 1; i <= 10; i++) {
    if (someCondition) {
        continue;  // Skip rest of current iteration
    }
    // These statements are skipped when continue executes
}
```

#### Example 1: Skip Specific Number
```java
package day5;

public class ContinueStatement {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                continue;  // Skip when i equals 5
            }
            System.out.println(i);
        }
        // Output: 1, 2, 3, 4, 6, 7, 8, 9, 10 (5 is skipped)
    }
}
```

#### Step-by-Step Execution
```java
// i = 1: 1 != 5, print 1
// i = 2: 2 != 5, print 2
// i = 3: 3 != 5, print 3
// i = 4: 4 != 5, print 4
// i = 5: 5 == 5, continue executed → skip print, go to i++
// i = 6: 6 != 5, print 6
// ... continues until i = 10
```

#### Example 2: Skip Multiple Numbers
```java
public class ContinueStatement {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i == 3 || i == 5 || i == 9) {
                continue;  // Skip 3, 5, and 9
            }
            System.out.println(i);
        }
        // Output: 1, 2, 4, 6, 7, 8, 10 (3, 5, 9 are skipped)
    }
}
```

### Break vs Continue Comparison

| Aspect | Break | Continue |
|--------|-------|----------|
| **Action** | Exit loop completely | Skip current iteration only |
| **Loop continues?** | No | Yes |
| **Remaining iterations** | Skipped | Execute normally |

#### Visual Comparison
```java
// Break example
for (int i = 1; i <= 5; i++) {
    if (i == 3) break;
    System.out.println(i);
}
// Output: 1, 2 (then exits)

// Continue example  
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.println(i);
}
// Output: 1, 2, 4, 5 (skips 3, continues with rest)
```

---

## Practice Assignments

### Assignment 1: Reverse a Number
**Goal:** Take a number and reverse its digits.

**Example:**
- Input: 1234
- Output: 4321

**Logic:**
1. **Extract last digit** using `%` operator
2. **Remove last digit** using `/` operator  
3. **Build reverse number** by adding extracted digits
4. **Repeat** until original number becomes 0

**Mathematical Process:**
```
Original: 1234, Reverse: 0
Step 1: Extract 4 (1234 % 10), Remove 4 (1234 / 10 = 123), Reverse: 0*10 + 4 = 4
Step 2: Extract 3 (123 % 10), Remove 3 (123 / 10 = 12), Reverse: 4*10 + 3 = 43  
Step 3: Extract 2 (12 % 10), Remove 2 (12 / 10 = 1), Reverse: 43*10 + 2 = 432
Step 4: Extract 1 (1 % 10), Remove 1 (1 / 10 = 0), Reverse: 432*10 + 1 = 4321
Step 5: Original = 0, stop
```

**Template:**
```java
package day5;

public class ReverseNumber {
    public static void main(String[] args) {
        int number = 1234;
        int reverse = 0;
        
        // Your code here using while loop
        // Use % operator to get last digit
        // Use / operator to remove last digit
        // Build reverse number
        
        System.out.println("Original: " + 1234);
        System.out.println("Reverse: " + reverse);
    }
}
```

### Assignment 2: Palindrome Number
**Goal:** Check if a number reads the same forwards and backwards.

**Examples:**
- 121 → Reverse: 121 → Palindrome ✓
- 123 → Reverse: 321 → Not Palindrome ✗

**Logic:**
1. **Reverse the number** (use Assignment 1 logic)
2. **Compare** original with reversed number
3. **If equal:** Palindrome
4. **If not equal:** Not palindrome

**Template:**
```java
package day5;

public class PalindromeNumber {
    public static void main(String[] args) {
        int number = 121;
        int original = number;  // Store original
        int reverse = 0;
        
        // Step 1: Reverse the number (same as Assignment 1)
        
        // Step 2: Compare original with reverse
        if (original == reverse) {
            System.out.println(number + " is a palindrome");
        } else {
            System.out.println(number + " is not a palindrome");
        }
    }
}
```

### Assignment 3: Count Digits in a Number
**Goal:** Count total number of digits in a number.

**Examples:**
- 12345 → 5 digits
- 999 → 3 digits

**Logic:**
1. **Remove last digit** using `/` operator
2. **Count each removal**
3. **Repeat** until number becomes 0

**Template:**
```java
package day5;

public class CountDigits {
    public static void main(String[] args) {
        int number = 12345;
        int count = 0;
        
        // Your code here
        // Keep dividing by 10 until number becomes 0
        // Count each division
        
        System.out.println("Number of digits: " + count);
    }
}
```

### Assignment 4: Count Even and Odd Digits
**Goal:** Count how many even and odd digits are in a number.

**Example:**
- Number: 12345
- Even digits: 2, 4 → Count: 2
- Odd digits: 1, 3, 5 → Count: 3

**Logic:**
1. **Extract each digit** using `%` operator
2. **Check if digit is even or odd** using `digit % 2`
3. **Count even and odd separately**
4. **Remove digit** and repeat

**Template:**
```java
package day5;

public class CountEvenOddDigits {
    public static void main(String[] args) {
        int number = 12345;
        int evenCount = 0;
        int oddCount = 0;
        
        // Your code here
        // Extract each digit
        // Check if digit % 2 == 0 (even) or != 0 (odd)
        // Count accordingly
        
        System.out.println("Even digits: " + evenCount);
        System.out.println("Odd digits: " + oddCount);
    }
}
```

### Assignment 5: Sum of Digits
**Goal:** Calculate the sum of all digits in a number.

**Example:**
- Number: 1234
- Sum: 1 + 2 + 3 + 4 = 10

**Logic:**
1. **Extract each digit** using `%` operator
2. **Add digit to sum**
3. **Remove digit** using `/` operator
4. **Repeat** until number becomes 0

**Template:**
```java
package day5;

public class SumOfDigits {
    public static void main(String[] args) {
        int number = 1234;
        int sum = 0;
        
        // Your code here
        // Extract each digit and add to sum
        
        System.out.println("Sum of digits: " + sum);
    }
}
```

### Common Patterns in All Assignments

#### Pattern 1: Extract Last Digit
```java
int lastDigit = number % 10;  // Gets rightmost digit
```

#### Pattern 2: Remove Last Digit
```java
number = number / 10;  // Removes rightmost digit
```

#### Pattern 3: Loop Until Number Becomes 0
```java
while (number > 0) {
    // Extract digit
    // Process digit
    // Remove digit
}
```

#### Pattern 4: Build New Number
```java
reverse = reverse * 10 + digit;  // Adds digit to right side
```

---

## Key Takeaways

### Loop Selection Guide
1. **For Loop (90% of cases):** When you know iterations
2. **While Loop (9% of cases):** When you don't know iterations
3. **Do-While Loop (1% of cases):** When you need at least one execution

### Essential Loop Components
1. **Initialization:** Where to start
2. **Condition:** When to stop  
3. **Increment/Decrement:** How to progress

### Jumping Statements
1. **Break:** Exit loop completely
2. **Continue:** Skip current iteration

### Best Practices
1. **Always include all three components** (initialization, condition, increment)
2. **Avoid infinite loops** by ensuring condition eventually becomes false
3. **Use meaningful variable names** (i, j, k for simple counters)
4. **Prefer for loops** for known iterations
5. **Use break and continue** sparingly and with clear purpose

### Common Mistakes to Avoid
1. **Missing increment/decrement** → Infinite loop
2. **Wrong condition** → Loop doesn't execute or runs forever
3. **Off-by-one errors** → Loop runs one time too many/few
4. **Unreachable code** after break statement

---

*This completes Session 5 on Looping and Jumping Statements. Practice all five assignments to master loop concepts. These patterns will be used extensively in upcoming sessions on arrays, strings, and methods!*