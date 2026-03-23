# 04 - Control Statements: Conditional Statements in Java

## Table of Contents
1. [What are Control Statements?](#what-are-control-statements)
2. [Types of Control Statements](#types-of-control-statements)
3. [Conditional Statements Overview](#conditional-statements-overview)
4. [If Statement](#if-statement)
5. [If-Else Statement](#if-else-statement)
6. [If-Else-If (Ladder) Statement](#if-else-if-ladder-statement)
7. [Nested If-Else Statement](#nested-if-else-statement)
8. [Switch-Case Statement](#switch-case-statement)
9. [Practice Assignments](#practice-assignments)

---

## What are Control Statements?

### Normal Program Execution
**By default, Java programs execute statements from top to bottom in sequential order.**

```java
Statement 1  ← Executes first
Statement 2  ← Executes second  
Statement 3  ← Executes third
Statement 4  ← Executes fourth
```

### What Control Statements Do
**Control statements allow us to:**
1. **Execute specific statements** based on conditions
2. **Skip certain statements** based on conditions
3. **Repeat statements** multiple times
4. **Jump to different parts** of the program

### Simple Example
```java
// Without control statements - all execute
System.out.println("Statement 1");
System.out.println("Statement 2");
System.out.println("Statement 3");

// With control statements - execute based on condition
if (age >= 18) {
    System.out.println("Eligible to vote");  // Only if condition is true
}
```

---

## Types of Control Statements

Java provides **3 main types** of control statements:

| Type | Purpose | Examples |
|------|---------|----------|
| **Conditional Statements** | Execute code based on conditions | `if`, `if-else`, `switch-case` |
| **Looping/Iterative Statements** | Repeat code multiple times | `for`, `while`, `do-while` |
| **Jumping Statements** | Jump to different parts of code | `break`, `continue`, `return` |

**Today's Focus:** Conditional Statements

---

## Conditional Statements Overview

### Purpose
**Execute different blocks of code based on different conditions.**

### Types of Conditional Statements

| Statement | When to Use | Example |
|-----------|-------------|---------|
| **if** | Single condition to check | Check if person is adult |
| **if-else** | Two possible outcomes | Eligible or not eligible |
| **if-else-if** | Multiple conditions | Grade calculation (A, B, C, D, F) |
| **switch-case** | Many fixed values to compare | Day of week, menu selection |

---

## If Statement

### Purpose
**Execute code only when a specific condition is true.**

### Syntax
```java
if (condition) {
    // Statements to execute if condition is true
}
```

### Key Points
- **Condition must be Boolean** (true or false)
- **No semicolon** after if statement
- **Curly braces optional** for single statement
- **Statements execute only if condition is true**

### Eclipse Example: Voting Eligibility
```java
package day4;

public class IfConditionDemo {
    public static void main(String[] args) {
        // Create variable
        int personAge = 25;
        
        // Check eligibility using if statement
        if (personAge >= 18) {
            System.out.println("Eligible for voting");
        }
        
        // This will print because 25 >= 18 is true
    }
}
```

### Testing Different Values
```java
// Test 1: Age = 25 (Adult)
int personAge = 25;
if (personAge >= 18) {
    System.out.println("Eligible for voting");  // This will execute
}

// Test 2: Age = 15 (Minor)  
int personAge = 15;
if (personAge >= 18) {
    System.out.println("Eligible for voting");  // This will NOT execute
}
```

### Understanding Boolean Expressions
```java
// All these are valid if conditions
if (true) {                    // Direct boolean value
    System.out.println("Always executes");
}

if (10 > 5) {                  // Expression that returns true
    System.out.println("10 is greater than 5");
}

if (age >= 18) {               // Variable comparison
    System.out.println("Adult");
}
```

### Single Statement - Curly Braces Optional
```java
// With curly braces (recommended)
if (age >= 18) {
    System.out.println("Adult");
}

// Without curly braces (only for single statement)
if (age >= 18)
    System.out.println("Adult");
```

**Recommendation:** Always use curly braces for clarity.

---

## If-Else Statement

### Purpose
**Execute one block if condition is true, another block if condition is false.**

### Syntax
```java
if (condition) {
    // Statements if condition is true
} else {
    // Statements if condition is false
}
```

### Key Points
- **Exactly one block executes** (either if or else)
- **Provides alternative** when condition is false
- **No condition needed** for else block

### Example 1: Voting Eligibility with Else
```java
package day4;

public class IfElseCondition {
    public static void main(String[] args) {
        int personAge = 15;
        
        if (personAge >= 18) {
            System.out.println("Eligible for voting");
        } else {
            System.out.println("Not eligible for voting");
        }
        
        // Output: "Not eligible for voting"
    }
}
```

### Example 2: Even or Odd Number
```java
package day4;

public class EvenOrOddNumber {
    public static void main(String[] args) {
        int number = 10;
        
        // Logic: Even numbers give remainder 0 when divided by 2
        if (number % 2 == 0) {
            System.out.println("Even number");
        } else {
            System.out.println("Odd number");
        }
        
        // Output: "Even number" (because 10 % 2 = 0)
    }
}
```

### Testing Even/Odd Logic
```java
// Test different numbers
int number = 10;  // 10 % 2 = 0 → Even
int number = 15;  // 15 % 2 = 1 → Odd
int number = 7;   // 7 % 2 = 1 → Odd
int number = 20;  // 20 % 2 = 0 → Even
```

### Mathematical Logic Behind Even/Odd
- **Even number:** Divisible by 2 with remainder 0
- **Odd number:** Not divisible by 2 (remainder is 1)
- **Modulo operator (%):** Returns remainder after division

---

## If-Else-If (Ladder) Statement

### Purpose
**Check multiple conditions in sequence.**

### Syntax
```java
if (condition1) {
    // Execute if condition1 is true
} else if (condition2) {
    // Execute if condition2 is true
} else if (condition3) {
    // Execute if condition3 is true
} else {
    // Execute if none of the conditions are true
}
```

### Key Points
- **Conditions checked in order** (top to bottom)
- **First true condition executes** its block
- **Remaining conditions skipped** after match
- **else block executes** if no conditions match

### Example 1: Positive, Negative, or Zero
```java
package day4;

public class PositiveOrNegativeNumber {
    public static void main(String[] args) {
        int number = 0;
        
        if (number > 0) {
            System.out.println("Positive number");
        } else if (number < 0) {
            System.out.println("Negative number");
        } else {
            System.out.println("Zero");
        }
        
        // Output: "Zero"
    }
}
```

### Example 2: Largest of Three Numbers
```java
package day4;

public class LargestOfThreeNumbers {
    public static void main(String[] args) {
        int a = 10, b = 20, c = 30;
        
        // Logic: Compare each number with other two
        if (a > b && a > c) {
            System.out.println("a is largest: " + a);
        } else if (b > a && b > c) {
            System.out.println("b is largest: " + b);
        } else {
            System.out.println("c is largest: " + c);
        }
        
        // Output: "c is largest: 30"
    }
}
```

### Understanding Logical Operators in Conditions
```java
// AND operator (&&) - Both conditions must be true
if (a > b && a > c) {  // a must be greater than BOTH b and c
    System.out.println("a is largest");
}

// Breaking down the logic:
// For a=10, b=20, c=30:
// a > b → 10 > 20 → false
// a > c → 10 > 30 → false  
// false && false → false (condition fails)

// For b=20:
// b > a → 20 > 10 → true
// b > c → 20 > 30 → false
// true && false → false (condition fails)

// For c=30:
// Since both previous conditions failed, else block executes
```

### Example 3: Week Day Names
```java
package day4;

public class PrintWeekNames {
    public static void main(String[] args) {
        int weekNumber = 1;
        
        if (weekNumber == 1) {
            System.out.println("Sunday");
        } else if (weekNumber == 2) {
            System.out.println("Monday");
        } else if (weekNumber == 3) {
            System.out.println("Tuesday");
        } else if (weekNumber == 4) {
            System.out.println("Wednesday");
        } else if (weekNumber == 5) {
            System.out.println("Thursday");
        } else if (weekNumber == 6) {
            System.out.println("Friday");
        } else if (weekNumber == 7) {
            System.out.println("Saturday");
        } else {
            System.out.println("Invalid week number");
        }
        
        // Output: "Sunday"
    }
}
```

**Problem with this approach:** Too much code for simple comparisons!
**Solution:** Use Switch-Case statement (covered next).

---

## Nested If-Else Statement

### Purpose
**Place if-else statements inside other if-else statements.**

### Syntax
```java
if (outerCondition) {
    if (innerCondition) {
        // Execute if both conditions are true
    } else {
        // Execute if outer is true, inner is false
    }
} else {
    // Execute if outer condition is false
}
```

### Example: Nested Conditions
```java
package day4;

public class NestedIfElse {
    public static void main(String[] args) {
        // Example with direct boolean values
        if (true) {                    // Outer condition
            if (true) {                // Inner condition  
                System.out.println("ABC");
            } else {
                System.out.println("XYZ");
            }
        } else {
            System.out.println("123");
        }
        
        // Output: "ABC"
    }
}
```

### Step-by-Step Execution
```java
// Test Case 1: Both true
if (true) {          // ✓ Enter outer if block
    if (true) {      // ✓ Enter inner if block
        System.out.println("ABC");  // ← This executes
    } else {
        System.out.println("XYZ");  // Skipped
    }
} else {
    System.out.println("123");      // Skipped
}
// Output: ABC

// Test Case 2: Outer true, inner false  
if (true) {          // ✓ Enter outer if block
    if (false) {     // ✗ Skip inner if, go to inner else
        System.out.println("ABC");  // Skipped
    } else {
        System.out.println("XYZ");  // ← This executes
    }
} else {
    System.out.println("123");      // Skipped
}
// Output: XYZ

// Test Case 3: Outer false
if (false) {         // ✗ Skip entire outer if block
    if (true) {      // Not evaluated
        System.out.println("ABC");  // Skipped
    } else {
        System.out.println("XYZ");  // Skipped
    }
} else {
    System.out.println("123");      // ← This executes
}
// Output: 123
```

### Practical Nested Example
```java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {                    // Check if adult
    if (hasLicense) {               // Check if has license
        System.out.println("Can drive");
    } else {
        System.out.println("Cannot drive - no license");
    }
} else {
    System.out.println("Cannot drive - too young");
}
```

---

## Switch-Case Statement

### Purpose
**Efficient way to compare a variable against multiple fixed values.**

### When to Use Switch-Case
- **Multiple fixed values** to compare (like 1, 2, 3, 4...)
- **Reduces code length** compared to multiple if-else
- **Better performance** for many comparisons
- **Cleaner code** for menu-like selections

### Syntax
```java
switch (variable) {
    case value1:
        // Statements for value1
        break;
    case value2:
        // Statements for value2
        break;
    case value3:
        // Statements for value3
        break;
    default:
        // Statements if no case matches
        break;  // Optional for default
}
```

### Key Components
- **switch (variable):** Variable to compare
- **case value:** Specific value to match
- **break:** Exit switch block after execution
- **default:** Execute if no case matches (like else)

### Example: Week Names with Switch-Case
```java
package day4;

public class SwitchCaseDemo {
    public static void main(String[] args) {
        int weekNumber = 1;
        
        switch (weekNumber) {
            case 1:
                System.out.println("Sunday");
                break;
            case 2:
                System.out.println("Monday");
                break;
            case 3:
                System.out.println("Tuesday");
                break;
            case 4:
                System.out.println("Wednesday");
                break;
            case 5:
                System.out.println("Thursday");
                break;
            case 6:
                System.out.println("Friday");
                break;
            case 7:
                System.out.println("Saturday");
                break;
            default:
                System.out.println("Invalid week number");
        }
        
        // Output: "Sunday"
    }
}
```

### Code Comparison: If-Else vs Switch-Case

#### If-Else Approach (40+ lines)
```java
if (weekNumber == 1) {
    System.out.println("Sunday");
} else if (weekNumber == 2) {
    System.out.println("Monday");
} else if (weekNumber == 3) {
    System.out.println("Tuesday");
} else if (weekNumber == 4) {
    System.out.println("Wednesday");
} else if (weekNumber == 5) {
    System.out.println("Thursday");
} else if (weekNumber == 6) {
    System.out.println("Friday");
} else if (weekNumber == 7) {
    System.out.println("Saturday");
} else {
    System.out.println("Invalid week number");
}
```

#### Switch-Case Approach (20+ lines)
```java
switch (weekNumber) {
    case 1: System.out.println("Sunday"); break;
    case 2: System.out.println("Monday"); break;
    case 3: System.out.println("Tuesday"); break;
    case 4: System.out.println("Wednesday"); break;
    case 5: System.out.println("Thursday"); break;
    case 6: System.out.println("Friday"); break;
    case 7: System.out.println("Saturday"); break;
    default: System.out.println("Invalid week number");
}
```

**Result:** ~50% code reduction!

### Why Break Statement is Important

#### Without Break (Wrong)
```java
int weekNumber = 1;
switch (weekNumber) {
    case 1:
        System.out.println("Sunday");
        // No break - continues to next case
    case 2:
        System.out.println("Monday");
        // No break - continues to next case
    case 3:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Invalid");
}

// Output:
// Sunday
// Monday  
// Tuesday
```

#### With Break (Correct)
```java
int weekNumber = 1;
switch (weekNumber) {
    case 1:
        System.out.println("Sunday");
        break;  // Exits switch block
    case 2:
        System.out.println("Monday");
        break;
    case 3:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Invalid");
}

// Output:
// Sunday
```

### Break Statement Rules
- **Required after each case** (except default)
- **Exits the switch block** immediately
- **Prevents fall-through** to next case
- **Not required for default** (last statement)

### Switch with Strings
```java
String weekName = "Sunday";

switch (weekName) {
    case "Sunday":
        System.out.println("1");
        break;
    case "Monday":
        System.out.println("2");
        break;
    case "Tuesday":
        System.out.println("3");
        break;
    default:
        System.out.println("Invalid day");
}
```

### Switch-Case Limitations
- **Only works with:** int, char, String, enum
- **Cannot use:** float, double, long, boolean
- **Cannot use expressions:** Only fixed values
- **Cannot use ranges:** Like (1-10)

---

## Practice Assignments

### Assignment 1: Largest of Two Numbers
**Goal:** Find the larger number between two numbers.

**Requirements:**
- Use two different approaches
- Method 1: if-else statement
- Method 2: Ternary operator (single line)

**Template:**
```java
package day4;

public class LargestOfTwoNumbers {
    public static void main(String[] args) {
        int a = 10, b = 20;
        
        // Method 1: Using if-else
        if (a > b) {
            System.out.println("a is larger: " + a);
        } else {
            System.out.println("b is larger: " + b);
        }
        
        // Method 2: Using ternary operator
        int largest = (a > b) ? a : b;
        System.out.println("Largest: " + largest);
    }
}
```

### Assignment 2: Smallest of Three Numbers
**Goal:** Find the smallest number among three numbers.

**Requirements:**
- Use if-else-if statements
- Compare each number with other two
- Handle all possible cases

**Logic:**
```java
// If a is smallest: a < b AND a < c
// If b is smallest: b < a AND b < c  
// If c is smallest: c < a AND c < b
```

**Template:**
```java
package day4;

public class SmallestOfThreeNumbers {
    public static void main(String[] args) {
        int a = 30, b = 10, c = 20;
        
        // Your code here
        // Use if-else-if to find smallest
        
        // Expected output: "b is smallest: 10"
    }
}
```

### Assignment 3: Week Number from Week Name
**Goal:** Take week name as input and print corresponding week number.

**Requirements:**
- Use switch-case statement
- Input: String (week name)
- Output: int (week number)
- Handle invalid input

**Template:**
```java
package day4;

public class WeekNumberFromName {
    public static void main(String[] args) {
        String weekName = "Sunday";  // Input
        
        switch (weekName) {
            case "Sunday":
                System.out.println("1");
                break;
            // Add cases for other days
            // Monday → 2, Tuesday → 3, etc.
            default:
                System.out.println("Invalid week name");
        }
    }
}
```

### Assignment Solutions Approach

#### Assignment 1 - Ternary Operator
```java
// Single line solution
int largest = (a > b) ? a : b;
```

#### Assignment 2 - Logic Breakdown
```java
if (a < b && a < c) {
    // a is smallest
} else if (b < a && b < c) {
    // b is smallest  
} else {
    // c is smallest (no condition needed)
}
```

#### Assignment 3 - String Cases
```java
case "Sunday": System.out.println("1"); break;
case "Monday": System.out.println("2"); break;
// Continue for all 7 days
```

---

## Key Takeaways

### Conditional Statements Summary
1. **if:** Single condition check
2. **if-else:** Two possible outcomes
3. **if-else-if:** Multiple conditions in sequence
4. **switch-case:** Multiple fixed values comparison

### When to Use Each Statement

| Scenario | Best Choice | Reason |
|----------|-------------|--------|
| Single condition | `if` | Simple and direct |
| Two outcomes | `if-else` | Clear alternative paths |
| Multiple conditions | `if-else-if` | Sequential checking |
| Many fixed values | `switch-case` | Cleaner, more efficient |

### Best Practices
1. **Always use curly braces** for clarity
2. **Use meaningful variable names**
3. **Add comments** for complex conditions
4. **Use switch-case** for multiple fixed comparisons
5. **Always include break** in switch cases
6. **Handle invalid input** with default/else

### Common Mistakes to Avoid
1. **Forgetting break** in switch-case
2. **Using = instead of ==** in conditions
3. **Missing curly braces** for multiple statements
4. **Not handling all cases** in if-else-if
5. **Complex nested conditions** (keep it simple)

### Boolean Expression Tips
- **Conditions must return true/false**
- **Use relational operators** for comparisons
- **Use logical operators** for multiple conditions
- **Can use direct boolean values** (true/false)
- **Parentheses help** with complex expressions

---

*This completes Session 4 on Conditional Statements. Practice the assignments to reinforce your understanding. In the next session, we will learn about Looping Statements (for, while, do-while) to repeat code execution!*