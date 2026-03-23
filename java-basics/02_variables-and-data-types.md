# 02 - Variables and Data Types in Java

## Table of Contents
1. [What are Variables?](#what-are-variables)
2. [Why Do We Need Variables?](#why-do-we-need-variables)
3. [What are Data Types?](#what-are-data-types)
4. [Creating Variables in Java](#creating-variables-in-java)
5. [Different Ways to Create Variables](#different-ways-to-create-variables)
6. [Types of Data Types](#types-of-data-types)
7. [Primitive Data Types](#primitive-data-types)
8. [Non-Primitive Data Types](#non-primitive-data-types)
9. [Data Type Ranges and Sizes](#data-type-ranges-and-sizes)
10. [Practical Examples](#practical-examples)
11. [Variables vs Constants](#variables-vs-constants)
12. [Statically vs Dynamically Typed Languages](#statically-vs-dynamically-typed-languages)

---

## What are Variables?

### Simple Definition
**A variable is a container that can hold some data.**

### Real-Life Example
Think of a variable like a box with a label:
- The **box** = variable (container)
- The **label** = variable name
- The **contents** = data/value stored inside

### Mathematical Example
```
x = 100
```
- `x` = variable (container)
- `100` = value (data stored)
- Later you can change: `x = 200`

### Programming Examples
```java
itemPrice = 10.25    // itemPrice is variable, 10.25 is value
age = 30             // age is variable, 30 is value  
name = "John"        // name is variable, "John" is value
```

---

## Why Do We Need Variables?

### Purpose of Variables
1. **Store data** - Keep information for later use
2. **Represent data** - Give meaningful names to values
3. **Change values** - Update data when needed
4. **Organize code** - Make programs easier to read

### Key Points
- Variables **represent data**
- Variable values can **always change** (that's why called "variable")
- Variables make programs **flexible and reusable**

---

## What are Data Types?

### Simple Definition
**Data type tells Java what kind of data we are storing in a variable.**

### Why Data Types are Needed
- In Java, you **cannot create variables directly**
- You **must specify data type** before creating variable
- Data type helps Java understand how to handle the data

### Wrong Way (Not Allowed in Java)
```java
x = 100        // ❌ Error - no data type specified
name = "John"  // ❌ Error - no data type specified
```

### Correct Way (Required in Java)
```java
int x = 100           // ✅ Correct - int data type specified
String name = "John"; // ✅ Correct - String data type specified
```

### How to Choose Data Type
**Choose data type based on what kind of data you want to store:**

| Data | Data Type | Example |
|------|-----------|---------|
| Whole numbers | `int` | `int x = 100;` |
| Decimal numbers | `float` | `float price = 10.25f;` |
| Text/Words | `String` | `String name = "John";` |
| Single letter | `char` | `char grade = 'A';` |

---

## Creating Variables in Java

### Basic Syntax
```java
dataType variableName = value;
```

### Two-Step Process

#### Step 1: Declaration
```java
int a;  // Just creating variable, no value assigned
```
- This is called **declaration**
- Variable exists but has no value

#### Step 2: Assignment  
```java
a = 100;  // Assigning value to existing variable
```
- This is called **assignment**
- Now variable has a value

#### One-Step Process (Declaration + Assignment)
```java
int a = 100;  // Declaration and assignment together
```

### Important Rules
1. **Cannot declare same variable twice**
   ```java
   int a = 100;
   int a = 200;  // ❌ Error - 'a' already exists
   ```

2. **Can change value without data type**
   ```java
   int a = 100;  // First time - need data type
   a = 200;      // Changing value - no data type needed
   ```

---

## Different Ways to Create Variables

### Approach 1: Individual Variables (Different Data Types)
```java
int a = 100;
float b = 10.5f;
String c = "Hello";
```
**Use when:** Variables have different data types

### Approach 2: Multiple Variables, Same Data Type (Separate Declaration)
```java
int a, b, c;    // Declare multiple variables
a = 100;        // Assign values separately
b = 200;
c = 300;
```

### Approach 3: Multiple Variables with Values (Same Data Type)
```java
int a = 100, b = 200, c = 300;  // All in one line
```

### When to Use Each Approach

| Approach | When to Use | Example |
|----------|-------------|---------|
| **Approach 1** | Different data types | `int age = 25; String name = "John";` |
| **Approach 2** | Same data type, values unknown initially | `int a, b, c;` |
| **Approach 3** | Same data type, values known | `int a = 10, b = 20, c = 30;` |

---

## Types of Data Types

### Two Main Categories

```
Data Types
├── Primitive Data Types
│   ├── Numbers (byte, short, int, long)
│   ├── Decimals (float, double)
│   ├── Characters (char)
│   └── Boolean (boolean)
└── Non-Primitive Data Types
    ├── String
    ├── Arrays
    ├── ArrayList
    └── HashMap, etc.
```

### Key Differences

| Primitive | Non-Primitive |
|-----------|---------------|
| **Lowercase** names (int, float) | **Uppercase** names (String, ArrayList) |
| Store **single value** | Store **multiple values** |
| Built into Java | Created from classes |

---

## Primitive Data Types

### 1. Number Data Types (Without Decimals)

| Data Type | Size | Range | Example |
|-----------|------|-------|---------|
| `byte` | 1 byte | -128 to 127 | `byte b = 25;` |
| `short` | 2 bytes | -32,768 to 32,767 | `short s = 3500;` |
| `int` | 4 bytes | -2,147,483,648 to 2,147,483,647 | `int i = 100000;` |
| `long` | 8 bytes | Very large numbers | `long l = 123456789L;` |

**Most commonly used:** `int`

### 2. Decimal Number Data Types

| Data Type | Size | Decimal Places | Example |
|-----------|------|----------------|---------|
| `float` | 4 bytes | Up to 7 decimal places | `float f = 15.5f;` |
| `double` | 8 bytes | Up to 15 decimal places | `double d = 15.123456789;` |

**Most commonly used:** `double`

### 3. Character Data Type
```java
char grade = 'A';        // Single character in single quotes
char letter = 'x';       // Only ONE character allowed
```

### 4. Boolean Data Type
```java
boolean isActive = true;   // Only true or false allowed
boolean isComplete = false;
```

### Important Notes About Literals

**Literals are special characters added to some data types:**

#### Long Literal
```java
long bigNumber = 123456789L;  // Must add 'L' or 'l' at end
```

#### Float Literal  
```java
float price = 15.5f;  // Must add 'f' or 'F' at end
```

**Why literals are needed:**
- Java needs to know the exact data type
- Without literals, Java might guess wrong data type

---

## Non-Primitive Data Types

### String Data Type
```java
String name = "John";        // Multiple characters in double quotes
String message = "Hello World";
String singleChar = "A";     // Even single character is OK in String
```

### Key Differences: char vs String

| Feature | char | String |
|---------|------|--------|
| **Quotes** | Single quotes `'A'` | Double quotes `"Hello"` |
| **Characters** | Only ONE character | One or more characters |
| **Data Type** | Primitive | Non-primitive |
| **Example** | `char c = 'A';` | `String s = "Hello";` |

### Valid and Invalid Examples

#### Character Examples
```java
char c = 'A';      // ✅ Valid - single character, single quotes
char c = 'AB';     // ❌ Invalid - multiple characters
char c = "A";      // ❌ Invalid - double quotes not allowed
```

#### String Examples  
```java
String s = "Hello";   // ✅ Valid - multiple characters, double quotes
String s = "A";       // ✅ Valid - single character in double quotes is OK
String s = 'Hello';   // ❌ Invalid - single quotes not allowed for String
```

#### Boolean Examples
```java
boolean b = true;     // ✅ Valid - no quotes
boolean b = false;    // ✅ Valid - no quotes  
boolean b = "true";   // ❌ Invalid - quotes make it String
```

---

## Data Type Ranges and Sizes

### Memory and Range Table

| Data Type | Memory Size | Range | When to Use |
|-----------|-------------|-------|-------------|
| `byte` | 1 byte | -128 to 127 | Very small numbers |
| `short` | 2 bytes | -32,768 to 32,767 | Small numbers |
| `int` | 4 bytes | -2 billion to +2 billion | **Most common** for numbers |
| `long` | 8 bytes | Very large numbers | Big numbers only |
| `float` | 4 bytes | 7 decimal places | Small decimal numbers |
| `double` | 8 bytes | 15 decimal places | **Most common** for decimals |
| `char` | 2 bytes | Single character | Letters, symbols |
| `boolean` | 1 bit | true or false | Yes/No values |

### Choosing Right Data Type

#### Based on Number Size
```java
// Small number - can use any type, but int is preferred
int small = 100;

// Big number - must use long
long big = 123456789L;

// Decimal - double is preferred  
double price = 15.99;
```

#### Memory Consideration
```java
// Wasteful - using big data type for small number
long x = 10;  // Wastes memory

// Efficient - using right size
int x = 10;   // Uses appropriate memory
```

---

## Practical Examples

### Creating Eclipse Project

#### Step 1: Create New Package
1. Right-click on `src` folder
2. Select `New` → `Package`  
3. Name: `day2`
4. Click `Finish`

#### Step 2: Create New Class
1. Right-click on `day2` package
2. Select `New` → `Class`
3. Class name: `VariablesDemo`
4. Check `public static void main(String[] args)`
5. Click `Finish`

### Example 1: Basic Variables
```java
package day2;

public class VariablesDemo {
    public static void main(String[] args) {
        // Creating variables
        int a = 100;
        
        // Printing variable value
        System.out.println(a);  // Output: 100
        
        // Changing variable value
        a = 200;
        System.out.println(a);  // Output: 200
    }
}
```

### Example 2: Multiple Variables
```java
public class DataTypesDemo {
    public static void main(String[] args) {
        // Numeric data types
        int a = 100, b = 200;
        
        // Printing with meaningful messages
        System.out.println("The value of a is: " + a);
        System.out.println("The value of b is: " + b);
        System.out.println("The sum of a and b is: " + (a + b));
    }
}
```

### Example 3: All Data Types
```java
public class AllDataTypes {
    public static void main(String[] args) {
        // Numeric data types
        byte by = 25;
        short sh = 3500;  
        int i = 100000;
        long l = 123456789L;  // Note the 'L'
        
        // Decimal data types
        float itemPrice = 15.5f;  // Note the 'f'
        double dbl = 15.123456789;
        
        // Character data type
        char grade = 'A';
        
        // String data type  
        String name = "John";
        
        // Boolean data type
        boolean isActive = true;
        
        // Printing all values
        System.out.println("Byte: " + by);
        System.out.println("Short: " + sh);
        System.out.println("Int: " + i);
        System.out.println("Long: " + l);
        System.out.println("Float: " + itemPrice);
        System.out.println("Double: " + dbl);
        System.out.println("Char: " + grade);
        System.out.println("String: " + name);
        System.out.println("Boolean: " + isActive);
    }
}
```

### Important: Concatenation vs Addition

#### Problem with Addition in Concatenation
```java
int a = 100, b = 200;
System.out.println("Sum: " + a + b);  // Output: Sum: 100200 (Wrong!)
```

#### Solution: Use Parentheses
```java
int a = 100, b = 200;
System.out.println("Sum: " + (a + b));  // Output: Sum: 300 (Correct!)
```

**Why this happens:**
- Without parentheses: String + number + number = concatenation
- With parentheses: String + (number + number) = String + result

---

## Variables vs Constants

### Normal Variables (Values Can Change)
```java
int a = 100;    // Initial value
a = 200;        // ✅ Can change - this is allowed
a = 300;        // ✅ Can change again
```

### Constant Variables (Values Cannot Change)
```java
final int a = 100;  // 'final' makes it constant
a = 200;            // ❌ Error - cannot change constant
```

### When to Use Constants
- **Fixed values** that should never change
- **Configuration values** like maximum limits
- **Mathematical constants** like PI

### Examples of Constants
```java
final double PI = 3.14159;
final int MAX_STUDENTS = 50;
final String COMPANY_NAME = "TechCorp";
```

---

## Statically vs Dynamically Typed Languages

### Java is Statically Typed

**What this means:**
- Must specify data type when creating variable
- Cannot change data type later
- Data type is checked at compile time

#### Example in Java
```java
int x = 100;        // x is integer type
x = 200;            // ✅ OK - same data type (int)
x = "Welcome";      // ❌ Error - cannot store String in int variable
```

### Python is Dynamically Typed

**What this means:**
- No need to specify data type
- Can change data type anytime
- Data type is determined at runtime

#### Example in Python
```python
x = 100        # x becomes integer automatically
x = "Welcome"  # x becomes string automatically - this is OK
```

### Comparison Table

| Feature | Java (Statically Typed) | Python (Dynamically Typed) |
|---------|-------------------------|----------------------------|
| **Declare data type** | Required | Not required |
| **Change data type** | Not allowed | Allowed |
| **Type checking** | Compile time | Runtime |
| **Example** | `int x = 100;` | `x = 100` |

### Advantages of Each Approach

#### Static Typing (Java)
- **Catches errors early** (at compile time)
- **Better performance** (type known in advance)
- **Clearer code** (data types are explicit)

#### Dynamic Typing (Python)  
- **More flexible** (can change types)
- **Less code** (no type declarations)
- **Faster development** (less typing required)

---

## Key Takeaways

### Variables
1. **Variables are containers** that hold data
2. **Values can change** (that's why called "variable")
3. **Must specify data type** in Java before creating variable
4. **Use meaningful names** for variables

### Data Types
1. **Two main categories:** Primitive and Non-primitive
2. **Choose based on data:** numbers, text, true/false, etc.
3. **Consider memory usage:** don't waste memory with wrong types
4. **Remember literals:** 'L' for long, 'f' for float

### Best Practices
1. **Use `int` for whole numbers** (most common)
2. **Use `double` for decimal numbers** (most common)
3. **Use `String` for text** (multiple characters)
4. **Use `char` for single characters** only
5. **Use `boolean` for true/false** values

### Common Mistakes to Avoid
1. **Don't put quotes around boolean values**
2. **Don't forget literals** for long and float
3. **Don't use wrong quotes** (single vs double)
4. **Don't try to change data type** of existing variable

---

## Practice Exercises

### Exercise 1: Create Variables
Create variables for:
- Your age (whole number)
- Your height (decimal number)  
- Your first name (text)
- Your grade (single letter)
- Whether you are a student (true/false)

### Exercise 2: Calculate and Print
Create two integer variables with values 50 and 30. Calculate and print:
- Sum
- Difference  
- Product

### Exercise 3: Fix the Errors
Find and fix errors in this code:
```java
int age = 25;
String name = 'John';
char grade = "A";
boolean isStudent = "true";
float price = 15.5;
long bigNumber = 123456789;
```

---

*This completes Session 2 on Variables and Data Types. In the next session, we will learn about Operators in Java.*