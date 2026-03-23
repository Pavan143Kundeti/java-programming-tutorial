# 03 - Operators in Java

## Table of Contents
1. [What are Operators?](#what-are-operators)
2. [Types of Operators](#types-of-operators)
3. [Arithmetic Operators](#arithmetic-operators)
4. [Relational/Comparison Operators](#relationalcomparison-operators)
5. [Logical Operators](#logical-operators)
6. [Increment and Decrement Operators](#increment-and-decrement-operators)
7. [Assignment Operators](#assignment-operators)
8. [Conditional/Ternary Operator](#conditionalternary-operator)
9. [Operator Categories (Unary, Binary, Ternary)](#operator-categories)
10. [Practice Assignment](#practice-assignment)

---

## What are Operators?

### Simple Definition
**An operator is a symbol that performs a certain operation.**

### Basic Example
```java
int a = 10;
int b = 20;
int result = a + b;  // '+' is an operator
```

### Key Terms
- **Variables:** `a` and `b` are variables
- **Expression:** `a + b` is an expression
- **Operators:** `+` and `=` are operators
- **Operands:** `a` and `b` are operands (variables used in expression)

### What Each Operator Does
- **`+` operator:** Performs addition of two numbers
- **`=` operator:** Assigns the result to the variable (assignment operator)

---

## Types of Operators

Java provides **6 main types** of operators:

| Type | Operators | Purpose |
|------|-----------|---------|
| **Arithmetic** | `+`, `-`, `*`, `/`, `%` | Mathematical calculations |
| **Relational/Comparison** | `>`, `>=`, `<`, `<=`, `!=`, `==` | Compare values |
| **Logical** | `&&`, `\|\|`, `!` | Boolean operations |
| **Increment/Decrement** | `++`, `--` | Increase/decrease by 1 |
| **Assignment** | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | Assign values |
| **Conditional/Ternary** | `? :` | Conditional assignment |

---

## Arithmetic Operators

### Purpose
**Used to perform mathematical calculations on numeric data.**

### Available Operators

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` | Addition | `10 + 20` | `30` |
| `-` | Subtraction | `20 - 10` | `10` |
| `*` | Multiplication | `10 * 2` | `20` |
| `/` | Division | `10 / 2` | `5` |
| `%` | Modulo (Remainder) | `10 % 3` | `1` |

### Important: Division vs Modulo
```java
int result1 = 5 / 2;   // Result: 2 (quotient)
int result2 = 5 % 2;   // Result: 1 (remainder)
```

### Eclipse Example
```java
package day3;

public class OperatorsDemo {
    public static void main(String[] args) {
        // Create variables
        int a = 10, b = 20;
        
        // Arithmetic operations
        System.out.println("Sum of a and b is: " + (a + b));
        System.out.println("Difference of a and b is: " + (b - a));
        System.out.println("Multiplication of a and b is: " + (a * b));
        System.out.println("Division of a and b is: " + (a / b));
        System.out.println("Modulo of a and b is: " + (a % b));
    }
}
```

### Important Note: Parentheses in Concatenation
```java
// Wrong way - will concatenate instead of adding
System.out.println("Sum: " + a + b);  // Output: Sum: 1020

// Correct way - parentheses force addition first
System.out.println("Sum: " + (a + b));  // Output: Sum: 30
```

### Two Ways to Use Results

#### Method 1: Direct Expression
```java
System.out.println("Sum: " + (a + b));  // Direct calculation
```

#### Method 2: Store in Variable
```java
int result = a + b;                      // Store result
System.out.println("Sum: " + result);   // Print variable
```

---

## Relational/Comparison Operators

### Purpose
**Used to compare values and return Boolean results (true/false).**

### Available Operators

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `>` | Greater than | `20 > 10` | `true` |
| `>=` | Greater than or equal | `20 >= 20` | `true` |
| `<` | Less than | `10 < 20` | `true` |
| `<=` | Less than or equal | `10 <= 10` | `true` |
| `!=` | Not equal to | `10 != 20` | `true` |
| `==` | Equal to | `10 == 10` | `true` |

### Key Points
- **Always return Boolean values** (true or false)
- **Used for comparisons** between two values
- **Very important** for conditional statements and loops

### Examples
```java
package day3;

public class RelationalOperators {
    public static void main(String[] args) {
        int a = 20, b = 10;
        
        System.out.println(a > b);   // true (20 > 10)
        System.out.println(a < b);   // false (20 < 10)
        System.out.println(a >= b);  // true (20 >= 10)
        System.out.println(a <= b);  // false (20 <= 10)
        System.out.println(a != b);  // true (20 != 10)
        System.out.println(a == b);  // false (20 == 10)
    }
}
```

### Understanding >= and <=
**These operators check TWO conditions:**

#### Greater than or Equal (>=)
- Returns `true` if **either condition** is satisfied:
  1. First value is **greater than** second value, OR
  2. First value is **equal to** second value

#### Less than or Equal (<=)
- Returns `true` if **either condition** is satisfied:
  1. First value is **less than** second value, OR
  2. First value is **equal to** second value

### Example with Equal Values
```java
int a = 20, b = 20;  // Both values are equal

System.out.println(a >= b);  // true (because a equals b)
System.out.println(a <= b);  // true (because a equals b)
System.out.println(a == b);  // true (because a equals b)
System.out.println(a != b);  // false (because a equals b)
```

### Storing Boolean Results
```java
boolean result = a > b;  // Store comparison result
System.out.println(result);  // Print the boolean value
```

### Important: Single = vs Double ==

| Operator | Type | Purpose | Example |
|----------|------|---------|---------|
| `=` | Assignment | Assigns value to variable | `a = 10;` |
| `==` | Comparison | Compares two values | `a == b` |

---

## Logical Operators

### Purpose
**Used to perform logical operations on Boolean values.**

### Available Operators

| Operator | Name | Symbol | Purpose |
|----------|------|--------|---------|
| `&&` | AND | Double ampersand | Both conditions must be true |
| `\|\|` | OR | Double pipe | At least one condition must be true |
| `!` | NOT | Exclamation mark | Opposite of the value |

### Key Points
- **Work only with Boolean values** (true/false)
- **Always return Boolean results** (true/false)
- **Different from relational operators:** Relational works with any data type, Logical works only with Boolean

### Truth Table

| X | Y | X && Y | X \|\| Y | !X | !Y |
|---|---|--------|----------|----|----|
| true | true | **true** | **true** | false | false |
| true | false | **false** | **true** | false | true |
| false | true | **false** | **true** | true | false |
| false | false | **false** | **false** | true | true |

### Understanding Each Operator

#### AND Operator (&&)
- Returns `true` **only if BOTH values are true**
- Returns `false` in **all other cases**

#### OR Operator (||)
- Returns `true` **if AT LEAST ONE value is true**
- Returns `false` **only if BOTH values are false**

#### NOT Operator (!)
- Returns the **opposite** of the value
- `!true` becomes `false`
- `!false` becomes `true`

### Examples
```java
package day3;

public class LogicalOperators {
    public static void main(String[] args) {
        boolean x = true;
        boolean y = false;
        
        // AND operator
        System.out.println(x && y);  // false (true && false)
        
        // OR operator
        System.out.println(x || y);  // true (true || false)
        
        // NOT operator
        System.out.println(!x);      // false (!true)
        System.out.println(!y);      // true (!false)
    }
}
```

### Using with Relational Operators
```java
// Store comparison results in Boolean variables
boolean b1 = 10 > 20;   // false
boolean b2 = 20 > 10;   // true

// Use logical operators
System.out.println(b1 && b2);  // false (false && true)
System.out.println(b1 || b2);  // true (false || true)
```

### Direct Expression Combinations
```java
// Combine relational and logical operators directly
System.out.println((10 < 20) && (20 > 10));  // true && true = true
System.out.println((10 > 20) || (20 > 10));  // false || true = true
```

---

## Increment and Decrement Operators

### Purpose
**Used to increase or decrease variable values by 1.**

### Available Operators

| Operator | Name | Purpose |
|----------|------|---------|
| `++` | Increment | Increase value by 1 |
| `--` | Decrement | Decrease value by 1 |

### Basic Usage
```java
int a = 10;
a++;           // Same as: a = a + 1
System.out.println(a);  // Output: 11

int b = 10;
b--;           // Same as: b = b - 1
System.out.println(b);  // Output: 9
```

### Two Types: Pre and Post

#### Post-Increment (a++)
```java
int a = 10;
int result = a++;  // First assign, then increment
System.out.println(result);  // Output: 10 (old value)
System.out.println(a);       // Output: 11 (incremented)
```

**How it works:**
1. **First:** Assign current value (10) to result
2. **Then:** Increment a to 11

#### Pre-Increment (++a)
```java
int a = 10;
int result = ++a;  // First increment, then assign
System.out.println(result);  // Output: 11 (new value)
System.out.println(a);       // Output: 11 (incremented)
```

**How it works:**
1. **First:** Increment a to 11
2. **Then:** Assign new value (11) to result

### Complete Example
```java
package day3;

public class IncrementOperator {
    public static void main(String[] args) {
        // Case 1: Simple increment
        int a = 10;
        a++;
        System.out.println(a);  // Output: 11
        
        // Case 2: Post-increment
        int b = 10;
        int result1 = b++;
        System.out.println(result1);  // Output: 10
        System.out.println(b);        // Output: 11
        
        // Case 3: Pre-increment
        int c = 10;
        int result2 = ++c;
        System.out.println(result2);  // Output: 11
        System.out.println(c);        // Output: 11
    }
}
```

### Decrement Operators

#### Post-Decrement (a--)
```java
int a = 100;
int result = a--;  // First assign, then decrement
System.out.println(result);  // Output: 100 (old value)
System.out.println(a);       // Output: 99 (decremented)
```

#### Pre-Decrement (--a)
```java
int a = 100;
int result = --a;  // First decrement, then assign
System.out.println(result);  // Output: 99 (new value)
System.out.println(a);       // Output: 99 (decremented)
```

### Summary Table

| Operation | Before | After | Result Variable |
|-----------|--------|-------|-----------------|
| `result = a++` | a=10 | a=11 | result=10 |
| `result = ++a` | a=10 | a=11 | result=11 |
| `result = a--` | a=10 | a=9 | result=10 |
| `result = --a` | a=10 | a=9 | result=9 |

---

## Assignment Operators

### Purpose
**Used to assign values to variables, including shorthand operations.**

### Basic Assignment
```java
int a = 10;  // Assigns 10 to variable a
```

### Shorthand Assignment Operators

| Operator | Long Form | Short Form | Example |
|----------|-----------|------------|---------|
| `+=` | `a = a + 5` | `a += 5` | Add and assign |
| `-=` | `a = a - 5` | `a -= 5` | Subtract and assign |
| `*=` | `a = a * 5` | `a *= 5` | Multiply and assign |
| `/=` | `a = a / 5` | `a /= 5` | Divide and assign |
| `%=` | `a = a % 5` | `a %= 5` | Modulo and assign |

### Examples

#### Addition Assignment (+=)
```java
int a = 10;
a += 5;    // Same as: a = a + 5
System.out.println(a);  // Output: 15
```

#### Subtraction Assignment (-=)
```java
int a = 10;
a -= 5;    // Same as: a = a - 5
System.out.println(a);  // Output: 5
```

#### Multiplication Assignment (*=)
```java
int a = 10;
a *= 2;    // Same as: a = a * 2
System.out.println(a);  // Output: 20
```

#### Division Assignment (/=)
```java
int a = 10;
a /= 2;    // Same as: a = a / 2
System.out.println(a);  // Output: 5
```

#### Modulo Assignment (%=)
```java
int a = 10;
a %= 3;    // Same as: a = a % 3
System.out.println(a);  // Output: 1
```

### Complete Example
```java
package day3;

public class AssignmentOperators {
    public static void main(String[] args) {
        // Example 1: Addition assignment
        int a = 10;
        a += 5;  // a = a + 5
        System.out.println("After += : " + a);  // Output: 15
        
        // Example 2: Subtraction assignment
        int b = 10;
        b -= 5;  // b = b - 5
        System.out.println("After -= : " + b);  // Output: 5
        
        // Example 3: Multiplication assignment
        int c = 10;
        c *= 2;  // c = c * 2
        System.out.println("After *= : " + c);  // Output: 20
        
        // Example 4: Division assignment
        int d = 10;
        d /= 2;  // d = d / 2
        System.out.println("After /= : " + d);  // Output: 5
        
        // Example 5: Modulo assignment
        int e = 10;
        e %= 3;  // e = e % 3
        System.out.println("After %= : " + e);  // Output: 1
    }
}
```

### When to Use
- **Increment/Decrement by 1:** Use `++` or `--`
- **Change by other amounts:** Use shorthand operators (`+=`, `-=`, etc.)
- **Complex operations:** Use regular assignment with full expressions

---

## Conditional/Ternary Operator

### Purpose
**A shorthand way to write simple if-else conditions.**

### Syntax
```java
variable = (condition) ? result1 : result2;
```

### How It Works
1. **Check condition:** If true, use result1
2. **If false:** Use result2
3. **Assign result** to variable

### Basic Example
```java
int a = 200, b = 100;
int largest = (a > b) ? a : b;
System.out.println(largest);  // Output: 200
```

**Explanation:**
- `a > b` is `true` (200 > 100)
- Since condition is true, `a` (200) is assigned to `largest`

### Step-by-Step Breakdown
```java
// Step 1: Define variables
int a = 200, b = 100;

// Step 2: Write ternary expression
int x = (a > b) ? a : b;
//      ↑       ↑   ↑
//   condition  if  else
//             true false

// Step 3: Evaluate
// a > b = 200 > 100 = true
// Since true, x gets value of a (200)
```

### More Examples

#### Example 1: Simple Numbers
```java
int x = (1 == 1) ? 100 : 200;
System.out.println(x);  // Output: 100 (because 1 == 1 is true)
```

#### Example 2: False Condition
```java
int x = (1 == 2) ? 200 : 100;
System.out.println(x);  // Output: 100 (because 1 == 2 is false)
```

#### Example 3: Age Eligibility Check
```java
int personAge = 30;
String result = (personAge >= 18) ? "Eligible" : "Not Eligible";
System.out.println(result);  // Output: "Eligible"
```

**Change age to see different result:**
```java
int personAge = 15;
String result = (personAge >= 18) ? "Eligible" : "Not Eligible";
System.out.println(result);  // Output: "Not Eligible"
```

### Complete Example
```java
package day3;

public class TernaryOperator {
    public static void main(String[] args) {
        // Example 1: Find largest of two numbers
        int a = 200, b = 100;
        int largest = (a > b) ? a : b;
        System.out.println("Largest: " + largest);  // Output: 200
        
        // Example 2: Simple condition
        int x = (1 == 1) ? 100 : 200;
        System.out.println("x: " + x);  // Output: 100
        
        // Example 3: Age eligibility
        int personAge = 30;
        String eligibility = (personAge >= 18) ? "Eligible" : "Not Eligible";
        System.out.println("Status: " + eligibility);  // Output: Eligible
        
        // Example 4: Change age
        personAge = 15;
        eligibility = (personAge >= 18) ? "Eligible" : "Not Eligible";
        System.out.println("Status: " + eligibility);  // Output: Not Eligible
    }
}
```

### Benefits of Ternary Operator
1. **Shorter code** than if-else statements
2. **Single line** conditional assignment
3. **Easy to read** for simple conditions

### When to Use
- **Simple conditions** with two possible outcomes
- **Assigning values** based on conditions
- **Short, readable expressions**

---

## Operator Categories

### Based on Number of Operands

Java operators are categorized by how many variables/values they work with:

| Category | Meaning | Number of Variables | Examples |
|----------|---------|-------------------|----------|
| **Unary** | One | 1 variable | `++`, `--`, `!`, `+=`, `-=` |
| **Binary** | Two | 2 variables | `+`, `-`, `>`, `<`, `&&`, `\|\|` |
| **Ternary** | Three | 3 values | `? :` |

### Unary Operators
**Work with single variable:**

```java
int a = 10;
a++;        // Unary - only 'a' is used
a--;        // Unary - only 'a' is used
a += 5;     // Unary - only 'a' is used (even though 5 is added)
boolean b = true;
!b;         // Unary - only 'b' is used
```

**List of Unary Operators:**
- `++` (increment)
- `--` (decrement)
- `+=`, `-=`, `*=`, `/=`, `%=` (assignment operators)
- `=` (simple assignment)
- `!` (NOT operator)

### Binary Operators
**Work with two variables:**

```java
int a = 10, b = 20;
a + b;      // Binary - uses both 'a' and 'b'
a > b;      // Binary - compares 'a' and 'b'
a && b;     // Binary - uses both boolean values
```

**List of Binary Operators:**
- **Arithmetic:** `+`, `-`, `*`, `/`, `%`
- **Relational:** `>`, `>=`, `<`, `<=`, `==`, `!=`
- **Logical:** `&&`, `||` (NOT `!` - that's unary)

### Ternary Operators
**Work with three values:**

```java
int result = (condition) ? value1 : value2;
//           ↑          ↑       ↑
//           1st        2nd     3rd
```

**Only one ternary operator:** `? :`

### Summary Table

| Operator Type | Count | Examples | Usage |
|---------------|-------|----------|-------|
| **Unary** | 1 operand | `a++`, `--b`, `!flag` | Single variable operations |
| **Binary** | 2 operands | `a + b`, `x > y`, `p && q` | Operations between two values |
| **Ternary** | 3 operands | `(a > b) ? a : b` | Conditional selection |

---

## Practice Assignment

### Assignment: Swapping Two Numbers

**Goal:** Interchange values between two variables **without using a temporary variable.**

### The Challenge
```java
// Before swapping
int a = 10;
int b = 20;

// After swapping (your goal)
// a should become 20
// b should become 10
```

### What NOT to Use
**Don't use the common temporary variable method:**
```java
// ❌ Don't use this approach
int temp = a;  // Don't create extra variable
a = b;
b = temp;
```

### What TO Use
**Use only arithmetic operators and the original two variables:**
- ✅ Use `+`, `-`, `*`, `/` operators
- ✅ Use only variables `a` and `b`
- ✅ No additional variables allowed

### Your Task
1. **Create two variables** with initial values
2. **Write code** to swap their values
3. **Use only arithmetic operators**
4. **Print values** before and after swapping
5. **Test your solution**

### Expected Output
```
Before swapping:
a = 10
b = 20

After swapping:
a = 20
b = 10
```

### Hints
- Think about mathematical operations that can reverse each other
- Consider what happens when you add and subtract the same values
- There are multiple solutions using different arithmetic operators
- Try different combinations of `+`, `-`, `*`, `/`

### Solution Approaches
There are **4-5 different ways** to solve this problem:
1. Using addition and subtraction
2. Using multiplication and division
3. Using XOR operations (advanced)
4. Using combination of operations

### Try It Yourself First!
Before looking up solutions:
1. **Think** about the mathematical relationships
2. **Experiment** with different operator combinations
3. **Test** your logic with different numbers
4. **Verify** that swapping actually works

### Template to Start
```java
package day3;

public class SwappingNumbers {
    public static void main(String[] args) {
        // Initial values
        int a = 10;
        int b = 20;
        
        // Print before swapping
        System.out.println("Before swapping:");
        System.out.println("a = " + a);
        System.out.println("b = " + b);
        
        // YOUR CODE HERE - Swap without temporary variable
        // Use only arithmetic operators and variables a, b
        
        // Print after swapping
        System.out.println("After swapping:");
        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }
}
```

### Why This Assignment is Important
1. **Reinforces operator understanding**
2. **Develops logical thinking**
3. **Practices variable manipulation**
4. **Prepares for complex programming challenges**

---

## Key Takeaways

### Operators Summary
1. **Arithmetic:** Mathematical calculations (`+`, `-`, `*`, `/`, `%`)
2. **Relational:** Compare values, return boolean (`>`, `<`, `==`, `!=`)
3. **Logical:** Boolean operations (`&&`, `||`, `!`)
4. **Increment/Decrement:** Change by 1 (`++`, `--`)
5. **Assignment:** Assign values (`=`, `+=`, `-=`, etc.)
6. **Ternary:** Conditional assignment (`? :`)

### Important Concepts
- **Operands:** Variables used in expressions
- **Expressions:** Combinations of operators and operands
- **Boolean results:** true/false values from comparisons
- **Pre vs Post:** Different timing of increment/decrement
- **Shorthand operators:** Efficient ways to modify variables

### Best Practices
1. **Use parentheses** in complex expressions for clarity
2. **Choose appropriate operators** for your needs
3. **Understand precedence** - some operators execute before others
4. **Practice regularly** - operators are fundamental to programming
5. **Test your logic** - verify results match expectations

### Common Mistakes to Avoid
1. **Confusing `=` and `==`** - assignment vs comparison
2. **Forgetting parentheses** in concatenation with arithmetic
3. **Mixing up pre and post** increment/decrement
4. **Wrong operator types** - using arithmetic with strings incorrectly
5. **Logical operator confusion** - `&&` vs `||` behavior

---

*This completes Session 3 on Operators in Java. Practice the swapping assignment and experiment with different operator combinations. In the next session, we will learn about Conditional Statements (if-else) where these operators become very useful!*