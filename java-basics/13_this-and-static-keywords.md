# Session 13: 'this' and 'static' Keywords in Java

## Table of Contents
1. [Introduction to Java Keywords](#introduction-to-java-keywords)
2. [Types of Variables in Java](#types-of-variables-in-java)
3. [Understanding 'this' Keyword](#understanding-this-keyword)
4. [Understanding 'static' Keyword](#understanding-static-keyword)
5. [Static vs Non-Static Access Rules](#static-vs-non-static-access-rules)
6. [Understanding System.out.println()](#understanding-systemoutprintln)
7. [Understanding Main Method](#understanding-main-method)
8. [Practice Assignments](#practice-assignments)

---

## Introduction to Java Keywords

Java has many important keywords that serve specific purposes:
- **this** - Refers to current class/object
- **static** - Makes variables/methods belong to class rather than instance
- **final** - Makes variables constant, methods non-overridable
- **public, private, protected** - Access modifiers

Today we'll focus on **'this'** and **'static'** keywords in detail.

---

## Types of Variables in Java

### Variable Classification

| Variable Type | Location | Scope | Also Known As |
|---------------|----------|-------|---------------|
| **Class Variables** | Declared inside class, outside methods | Accessible in all methods of the class | Instance Variables |
| **Local Variables** | Declared inside methods or as parameters | Accessible only within that method | Method Variables |

### Important Note: No Global Variables in Java
- **Global Variables**: Variables defined outside of any class
- **Java Rule**: Everything must be inside a class
- **Result**: Java has NO global variables, only class and local variables

### Example: Variable Types

```java
public class VariableTypes {
    int x, y;  // Class variables (instance variables)
    
    public VariableTypes(int a, int b) {  // a, b are local variables (parameters)
        int temp = 10;  // temp is local variable
        x = a;  // Assigning local to class variable
        y = b;
    }
    
    public void display() {
        int result = x + y;  // result is local variable
        System.out.println("Sum: " + result);
    }
}
```

---

## Understanding 'this' Keyword

### What is 'this' Keyword?
- **'this'** always refers to the **current class** or **current object**
- Used to differentiate between class variables and local variables when they have the same name

### When to Use 'this' Keyword?

**Problem: Same Variable Names**
```java
public class ThisKeyword {
    int x, y;  // Class variables
    
    // Constructor with same parameter names
    public ThisKeyword(int x, int y) {
        x = x;  // ❌ Confusing! Which x is which?
        y = y;  // ❌ This will assign default values (0)
    }
}
```

**Solution: Use 'this' Keyword**
```java
public class ThisKeyword {
    int x, y;  // Class variables
    
    // Constructor with same parameter names
    public ThisKeyword(int x, int y) {
        this.x = x;  // ✅ Clear! this.x = class variable, x = parameter
        this.y = y;  // ✅ this.y = class variable, y = parameter
    }
    
    void display() {
        System.out.println("x = " + x);
        System.out.println("y = " + y);
    }
}
```

### Complete Example: Using 'this' Keyword

```java
public class ThisKeyword {
    int x, y;  // Class variables
    
    // Constructor using 'this' keyword
    public ThisKeyword(int x, int y) {
        this.x = x;  // this.x refers to class variable
        this.y = y;  // this.y refers to class variable
    }
    
    // Method using 'this' keyword
    void setData(int x, int y) {
        this.x = x;  // Differentiate class variable from parameter
        this.y = y;
    }
    
    void display() {
        System.out.println("x = " + x);
        System.out.println("y = " + y);
    }
}

// Main class to test
public class ThisKeywordMain {
    public static void main(String[] args) {
        ThisKeyword obj = new ThisKeyword(100, 200);
        obj.display();  // Output: x = 100, y = 200
        
        obj.setData(300, 400);
        obj.display();  // Output: x = 300, y = 400
    }
}
```

### Key Points About 'this' Keyword

| Point | Description |
|-------|-------------|
| **Always refers to class** | `this.variableName` = class variable |
| **Solves naming conflicts** | When parameter and class variable have same name |
| **Works in constructors** | Can be used in constructors |
| **Works in methods** | Can be used in regular methods |
| **Optional when no conflict** | If names are different, 'this' is optional |

---

## Understanding 'static' Keyword

### What is 'static' Keyword?
- **static** makes variables and methods belong to the **class** rather than individual objects
- **Static members** are **shared** among all objects of the class
- **Static members** can be accessed **directly** using class name

### When to Use 'static' Keyword?

**Scenario: Common Data Problem**

Imagine you have multiple Employee objects:
```java
Employee emp1 = new Employee("John", 101, 50000, 10);    // Department 10
Employee emp2 = new Employee("Jane", 102, 60000, 10);    // Department 10  
Employee emp3 = new Employee("Bob", 103, 55000, 10);     // Department 10
```

**Problems:**
1. **Duplication**: Same department number (10) repeated in every object
2. **Memory Waste**: Each object stores separate copy of department number
3. **Update Difficulty**: If department changes, must update all objects

**Solution: Use 'static' for Common Data**
```java
public class Employee {
    String name;           // Non-static (different for each employee)
    int empId;            // Non-static (different for each employee)
    double salary;        // Non-static (different for each employee)
    static int deptNo = 10;  // Static (same for all employees)
}
```

### Benefits of 'static' Keyword

| Benefit | Description |
|---------|-------------|
| **Memory Efficient** | Only one copy stored in memory |
| **Easy Updates** | Change once, reflects everywhere |
| **Shared Access** | All objects share the same value |
| **Direct Access** | Can access using class name |

### Types of Variables and Methods

| Type | Declaration | Access | Memory |
|------|-------------|--------|---------|
| **Static Variable** | `static int x = 10;` | Class-level, shared | One copy for all objects |
| **Non-Static Variable** | `int y = 20;` | Object-level, individual | Separate copy for each object |
| **Static Method** | `static void display()` | Class-level, shared | One copy for all objects |
| **Non-Static Method** | `void show()` | Object-level, individual | Separate copy for each object |

### Practical Example: Static vs Non-Static

```java
public class StaticDemo {
    static int a = 10;      // Static variable
    int b = 20;             // Non-static variable
    
    static void m1() {      // Static method
        System.out.println("This is M1 static method");
    }
    
    void m2() {             // Non-static method
        System.out.println("This is M2 non-static method");
    }
    
    public static void main(String[] args) {
        // Accessing static members directly (no object needed)
        System.out.println(a);  // ✅ Direct access to static variable
        m1();                    // ✅ Direct access to static method
        
        // Accessing non-static members requires object
        StaticDemo obj = new StaticDemo();
        System.out.println(obj.b);  // ✅ Access through object
        obj.m2();                    // ✅ Access through object
    }
}
```

---

## Static vs Non-Static Access Rules

### Rule 1: Static Methods Can Access Static Members Directly

```java
public class AccessRules {
    static int a = 10;      // Static variable
    int b = 20;             // Non-static variable
    
    static void m1() {      // Static method
        System.out.println("M1 static method");
    }
    
    void m2() {             // Non-static method
        System.out.println("M2 non-static method");
    }
    
    public static void main(String[] args) {
        // ✅ Static method can access static members directly
        System.out.println(a);  // Works - both static
        m1();                    // Works - both static
        
        // ❌ Static method cannot access non-static members directly
        // System.out.println(b);  // Error!
        // m2();                   // Error!
    }
}
```

### Rule 2: Static Methods Can Access Non-Static Members Through Objects

```java
public static void main(String[] args) {
    // ✅ Access non-static members through object
    AccessRules obj = new AccessRules();
    System.out.println(obj.b);  // Works - through object
    obj.m2();                    // Works - through object
}
```

### Rule 3: Non-Static Methods Can Access Everything Directly

```java
void m3() {  // Non-static method
    // ✅ Can access static members directly
    System.out.println(a);  // Works
    m1();                    // Works
    
    // ✅ Can access non-static members directly
    System.out.println(b);  // Works
    m2();                    // Works
    
    // No restrictions for non-static methods!
}
```

### Access Rules Summary Table

| From Method Type | To Static Members | To Non-Static Members |
|------------------|-------------------|----------------------|
| **Static Method** | ✅ Direct Access | ✅ Through Object Only |
| **Non-Static Method** | ✅ Direct Access | ✅ Direct Access |

### Accessing Static Members from Different Classes

**Same Class:**
```java
public class SameClass {
    static int x = 10;
    
    public static void main(String[] args) {
        System.out.println(x);  // ✅ Direct access - no class name needed
    }
}
```

**Different Class:**
```java
public class DifferentClass {
    public static void main(String[] args) {
        System.out.println(SameClass.x);  // ✅ Must specify class name
    }
}
```

---

## Understanding System.out.println()

### Breaking Down System.out.println()

Now that we understand static keyword, let's understand what `System.out.println()` really means:

```java
System.out.println("Hello World");
```

**Component Analysis:**

| Component | Type | Description |
|-----------|------|-------------|
| **System** | Class | Predefined class in Java |
| **out** | Static Variable | Static variable of PrintStream type |
| **println()** | Method | Method belonging to PrintStream class |

### Detailed Explanation

**Step 1: System Class**
```java
// Simplified version of System class
public class System {
    public static PrintStream out;  // Static variable of PrintStream type
}
```

**Step 2: PrintStream Class**
```java
// Simplified version of PrintStream class  
public class PrintStream {
    public void println(String message) {
        // Code to print message to console
    }
    
    public void print(String message) {
        // Code to print message without newline
    }
}
```

**Step 3: How It Works**
```java
System.out.println("Hello");
//  |     |     |
//  |     |     └── Method from PrintStream class
//  |     └────────── Static variable of PrintStream type
//  └──────────────── Predefined class in Java
```

### Comparison Example

**Our Custom Example:**
```java
public class Test {
    static String s = "Welcome";  // Static string variable
}

// Accessing from another class:
int length = Test.s.length();  // Test.s (static variable) + .length() (String method)
```

**System.out.println Example:**
```java
System.out.println("Hello");  // System.out (static variable) + .println() (PrintStream method)
```

**Both Follow Same Pattern:**
- **ClassName.staticVariable.method()**

---

## Understanding Main Method

### Main Method Signature
```java
public static void main(String[] args)
```

### Breaking Down Each Component

| Component | Purpose | Explanation |
|-----------|---------|-------------|
| **public** | Access Modifier | JVM can access from anywhere in project |
| **static** | Keyword | JVM can call directly without creating object |
| **void** | Return Type | Main method doesn't return any value |
| **main** | Method Name | JVM looks for this specific name |
| **String[] args** | Parameter | Array to accept command line arguments |

### Why Each Component is Required?

**1. Why public?**
- JVM needs to access main method from anywhere in the project
- Main method can be in any class, so it must be publicly accessible

**2. Why static?**
- JVM needs to call main method directly without creating any object
- Static allows direct access using class name

**3. Why void?**
- Main method is entry point, doesn't need to return anything
- JVM just needs to start execution from here

**4. Why String[] args?**
- Allows passing command line arguments to the program
- Array can hold multiple string parameters

### Valid Main Method Variations

**✅ Valid Variations:**
```java
// Standard format
public static void main(String[] args) { }

// Keywords can be interchanged
static public void main(String[] args) { }

// Parameter name can be different
public static void main(String[] xyz) { }

// Array notation variations
public static void main(String args[]) { }
```

**❌ Invalid Variations:**
```java
// Return type in wrong position
public void static main(String[] args) { }  // Error!

// Extra keywords after parameter
public static void main(String[] args) static { }  // Error!

// Wrong parameter type
public static void main(int[] args) { }  // Valid method, but not main method JVM looks for
```

### Main Method Recognition by JVM

**JVM looks for EXACTLY this signature:**
```java
public static void main(String[] args)
```

**Other main methods are treated as overloaded methods:**
```java
public class MainOverloading {
    // This is the method JVM recognizes
    public static void main(String[] args) {
        System.out.println("Actual main method");
        
        // Call overloaded main methods
        MainOverloading obj = new MainOverloading();
        obj.main(100);
        obj.main("Hello");
    }
    
    // Overloaded main methods (JVM ignores these)
    public void main(int x) {
        System.out.println("Main with int: " + x);
    }
    
    public void main(String s) {
        System.out.println("Main with String: " + s);
    }
}
```

---

## Key Concepts Summary

### 'this' Keyword
| Concept | Description |
|---------|-------------|
| **Purpose** | Differentiate class variables from local variables |
| **Usage** | When parameter and class variable have same name |
| **Refers to** | Current class/object |
| **Mandatory** | Only when names conflict |

### 'static' Keyword
| Concept | Description |
|---------|-------------|
| **Purpose** | Share data/methods among all objects |
| **Memory** | Single copy for entire class |
| **Access** | Direct access using class name |
| **Use Case** | Common data across multiple objects |

### Access Rules
| From | To Static | To Non-Static |
|------|-----------|---------------|
| **Static Method** | ✅ Direct | ✅ Through Object |
| **Non-Static Method** | ✅ Direct | ✅ Direct |

---

## Practice Assignments

### Assignment 1: Employee Management with Static
Create an `Employee` class with:
- Non-static variables: `name`, `empId`, `salary`
- Static variables: `companyName`, `totalEmployees`
- Constructor that increments `totalEmployees`
- Static method: `getCompanyInfo()`
- Non-static method: `displayEmployee()`

### Assignment 2: Bank Account with 'this' Keyword
Create a `BankAccount` class with:
- Variables: `accountNumber`, `balance`, `customerName`
- Constructor using 'this' keyword with same parameter names
- Methods: `deposit(double amount)`, `withdraw(double amount)` using 'this'
- Display method showing account details

### Assignment 3: Static vs Non-Static Access
Create a class demonstrating all access rules:
- Static and non-static variables
- Static and non-static methods
- Show what works and what doesn't from different method types
- Include examples of accessing from same class and different class

### Assignment 4: Understanding System.out.println()
Create your own version:
- Create a class `MySystem` with static variable `out` of type `MyPrintStream`
- Create `MyPrintStream` class with `println()` method
- Demonstrate: `MySystem.out.println("Hello")`

### Assignment 5: Main Method Variations
Create a class showing:
- Valid main method variations
- Overloaded main methods
- Demonstrate which one JVM calls and how to call others

---

## Interview Questions

1. **What is the difference between 'this' keyword and static keyword?**
2. **When do we use 'this' keyword? Give practical examples.**
3. **What happens if we don't use 'this' keyword when parameter and instance variable have same name?**
4. **Explain static keyword with real-world example.**
5. **What are the access rules for static and non-static members?**
6. **Can we access non-static members from static methods? How?**
7. **Explain System.out.println() statement in detail.**
8. **Why is main method static? What if we remove static from main method?**
9. **Can we overload main method? Give examples.**
10. **What are the valid variations of main method signature?**

---

**Next Session Preview**: We'll explore **Inheritance** - one of the most important OOP concepts where classes can inherit properties and methods from other classes, enabling code reusability and establishing parent-child relationships.