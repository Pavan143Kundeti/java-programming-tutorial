# Session 12: Polymorphism and Encapsulation in Java

## Table of Contents
1. [Introduction to OOP Concepts](#introduction-to-oop-concepts)
2. [What is Polymorphism?](#what-is-polymorphism)
3. [Method Overloading](#method-overloading)
4. [Constructor Overloading](#constructor-overloading)
5. [What is Encapsulation?](#what-is-encapsulation)
6. [Implementing Encapsulation](#implementing-encapsulation)
7. [Overloading Main Method](#overloading-main-method)
8. [Practice Assignments](#practice-assignments)

---

## Introduction to OOP Concepts

So far in our Object-Oriented Programming journey, we have covered:
1. **Class** - Blueprint for creating objects
2. **Object** - Instance of a class
3. **Methods** - Functions inside classes

Today we'll explore two more important OOP concepts:
- **Polymorphism** - One thing having many forms
- **Encapsulation** - Wrapping data and methods for security

---

## What is Polymorphism?

### Definition
**Polymorphism** = **Poly** (many) + **Morphism** (forms)
- **Polymorphism means one thing can have many forms**

### Real-World Examples

| Example | Different Forms |
|---------|----------------|
| **Shape** | Circle, Square, Triangle, Rectangle |
| **Water** | Ice, Liquid, Vapor |
| **Vehicle** | Car, Bike, Bus, Truck |

### Polymorphism in Java
- **Theoretical Concept**: One thing can have many forms
- **Practical Implementation**: Achieved through **Overloading**
- **Overloading**: Creating multiple methods/constructors with same name but different parameters

---

## Method Overloading

### What is Method Overloading?
Method overloading allows us to create **multiple methods with the same name** in the same class by changing:
1. **Number of parameters**
2. **Data type of parameters** 
3. **Order of parameters**

### Rules for Method Overloading

| Rule | Description | Example |
|------|-------------|---------|
| **1. Same Method Name** | All overloaded methods must have same name | `sum()`, `sum()`, `sum()` |
| **2. Different Parameters** | Number of parameters should be different | `sum()`, `sum(int a)`, `sum(int a, int b)` |
| **3. Different Data Types** | If same number of parameters, data types should differ | `sum(int a, int b)`, `sum(double a, int b)` |
| **4. Different Order** | If same data types, order should be different | `sum(int a, double b)`, `sum(double a, int b)` |

### Why Use Method Overloading?

**Scenario 1: Without Overloading (Confusing)**
```java
addTwoNumbers(10, 20);
addThreeNumbers(10, 20, 30);
addFourNumbers(10, 20, 30, 40);
```

**Scenario 2: With Overloading (User-Friendly)**
```java
add(10, 20);           // Same method name
add(10, 20, 30);       // Same method name  
add(10, 20, 30, 40);   // Same method name
```

**User Perspective**: Scenario 2 is easier - remember only one method name!

### Practical Example: Adder Class

**Step 1: Create Adder Class**
```java
public class Adder {
    int a = 10;
    int b = 20;
    
    // Method 1: No parameters
    void sum() {
        System.out.println(a + b);
    }
    
    // Method 2: Two integer parameters
    void sum(int x, int y) {
        System.out.println(x + y);
    }
    
    // Method 3: Integer and double parameters
    void sum(int x, double y) {
        System.out.println(x + y);
    }
    
    // Method 4: Double and integer parameters
    void sum(double x, int y) {
        System.out.println(x + y);
    }
    
    // Method 5: Three integer parameters
    void sum(int a, int b, int c) {
        System.out.println(a + b + c);
    }
}
```

**Step 2: Using Overloaded Methods**
```java
public class AdderMain {
    public static void main(String[] args) {
        Adder obj = new Adder();
        
        obj.sum();              // Calls Method 1 → Output: 30
        obj.sum(100, 200);      // Calls Method 2 → Output: 300
        obj.sum(10.5, 20);      // Calls Method 4 → Output: 30.5
        obj.sum(10, 15.5);      // Calls Method 3 → Output: 25.5
        obj.sum(10, 20, 30);    // Calls Method 5 → Output: 60
    }
}
```

### How Java Chooses the Right Method

**Selection Process:**
1. **Check number of parameters** first
2. **Check data types** if number matches
3. **Check order** if data types match
4. **Call the matching method**

### Important Notes About Overloading

| What is Considered | What is NOT Considered |
|-------------------|----------------------|
| ✅ Number of parameters | ❌ Return type |
| ✅ Data type of parameters | ❌ Parameter names |
| ✅ Order of parameters | ❌ Method body |

**Example of Invalid Overloading:**
```java
// ❌ This will give error - same signature
void sum(int x, int y) { }
int sum(int a, int b) { }  // Only return type changed - NOT ALLOWED
```

---

## Constructor Overloading

### What is Constructor Overloading?
Just like methods, we can create **multiple constructors** with same name but different parameters.

### Practical Example: Box Class

```java
public class Box {
    double width, height, depth;
    
    // Constructor 1: Default constructor (no parameters)
    Box() {
        width = height = depth = 0;
    }
    
    // Constructor 2: Three parameters
    Box(double w, double h, double d) {
        width = w;
        height = h;
        depth = d;
    }
    
    // Constructor 3: One parameter (cube)
    Box(double length) {
        width = height = depth = length;
    }
    
    // Method to calculate volume
    double volume() {
        return width * height * depth;
    }
}
```

### Using Constructor Overloading

```java
public class BoxMain {
    public static void main(String[] args) {
        // Using different constructors
        Box b1 = new Box();              // Default constructor
        System.out.println(b1.volume()); // Output: 0.0
        
        Box b2 = new Box(10.5, 15.5, 5.0);  // Three parameters
        System.out.println(b2.volume());     // Output: 815.625
        
        Box b3 = new Box(10.5);          // One parameter (cube)
        System.out.println(b3.volume()); // Output: 1157.625
    }
}
```

---

## What is Encapsulation?

### Definition
**Encapsulation** = Wrapping up of data (variables) and methods into a single unit (class) with **restricted access**.

### Real-World Example: Medicine Capsule
- **Capsule** contains medicine inside
- **You can't see** what's inside the capsule
- **Medicine is hidden** and protected
- **You consume** the capsule, not direct medicine

### Banking Example
- **Bank** has your account details
- **You can't directly access** your account data
- **You provide authentication** (ID, password)
- **Bank provides specific information** you requested

### Encapsulation in Java
- **Variables are private** (hidden from outside)
- **Methods are public** (accessible from outside)
- **Variables can only be accessed through methods**

---

## Implementing Encapsulation

### Rules for Encapsulation

| Rule | Description |
|------|-------------|
| **1. Private Variables** | All variables should be declared as `private` |
| **2. Public Methods** | Create public methods to access private variables |
| **3. Getter Methods** | Methods to **get/read** data from variables |
| **4. Setter Methods** | Methods to **set/assign** data to variables |

### Step-by-Step Implementation

**Step 1: Create Class with Private Variables**
```java
public class Account {
    private String accountNumber;  // Private variable
    private String name;          // Private variable  
    private double amount;        // Private variable
}
```

**Step 2: Create Setter Methods (to assign data)**
```java
// Setter for accountNumber
public void setAccountNumber(String accountNumber) {
    this.accountNumber = accountNumber;  // 'this' refers to class variable
}

// Setter for name
public void setName(String name) {
    this.name = name;
}

// Setter for amount
public void setAmount(double amount) {
    this.amount = amount;
}
```

**Step 3: Create Getter Methods (to read data)**
```java
// Getter for accountNumber
public String getAccountNumber() {
    return accountNumber;
}

// Getter for name
public String getName() {
    return name;
}

// Getter for amount
public double getAmount() {
    return amount;
}
```

### Complete Encapsulation Example

```java
public class Account {
    private String accountNumber;
    private String name;
    private double amount;
    
    // Setter methods
    public void setAccountNumber(String accountNumber) {
        this.accountNumber = accountNumber;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public void setAmount(double amount) {
        this.amount = amount;
    }
    
    // Getter methods
    public String getAccountNumber() {
        return accountNumber;
    }
    
    public String getName() {
        return name;
    }
    
    public double getAmount() {
        return amount;
    }
}
```

### Using Encapsulated Class

```java
public class AccountMain {
    public static void main(String[] args) {
        Account acc = new Account();
        
        // ❌ This won't work - variables are private
        // acc.accountNumber = "101";  // Error!
        
        // ✅ Use setter methods to assign data
        acc.setAccountNumber("101");
        acc.setName("John Doe");
        acc.setAmount(50000.0);
        
        // ✅ Use getter methods to read data
        System.out.println("Account Number: " + acc.getAccountNumber());
        System.out.println("Name: " + acc.getName());
        System.out.println("Amount: " + acc.getAmount());
    }
}
```

### Eclipse Shortcut for Getters and Setters

**Manual creation is tedious for many variables. Use Eclipse shortcut:**

1. **Create all private variables first**
2. **Right-click in class** → **Source** → **Generate Getters and Setters**
3. **Select variables** you want getters/setters for
4. **Click Generate** - Eclipse creates all methods automatically!

### Understanding 'this' Keyword

**Problem: Same parameter and variable names**
```java
public void setAccountNumber(String accountNumber) {
    accountNumber = accountNumber;  // ❌ Confusing! Which is which?
}
```

**Solution: Use 'this' keyword**
```java
public void setAccountNumber(String accountNumber) {
    this.accountNumber = accountNumber;  // ✅ Clear! this.accountNumber = class variable
}
```

**Remember**: `this` keyword always refers to the **current class**

---

## Overloading Main Method

### Can We Overload Main Method?
**Yes!** Main method is also a method, so it can be overloaded.

### Example: Overloading Main Method

```java
public class OverloadingMainMethod {
    
    // Original main method (JVM looks for this signature)
    public static void main(String[] args) {
        System.out.println("Original main method");
        
        // Create object to call other main methods
        OverloadingMainMethod obj = new OverloadingMainMethod();
        
        obj.main(100);              // Call overloaded main with int
        obj.main("Hello");          // Call overloaded main with String
        obj.main("Hello", "World"); // Call overloaded main with 2 Strings
    }
    
    // Overloaded main method 1: int parameter
    public void main(int x) {
        System.out.println("Main with int: " + x);
    }
    
    // Overloaded main method 2: String parameter  
    public void main(String s) {
        System.out.println("Main with String: " + s);
    }
    
    // Overloaded main method 3: Two String parameters
    public void main(String s1, String s2) {
        System.out.println("Main with two Strings: " + s1 + " " + s2);
    }
}
```

**Output:**
```
Original main method
Main with int: 100
Main with String: Hello
Main with two Strings: Hello World
```

### Why Main Method Has String[] args?
- **Command Line Arguments**: We can pass parameters to main method from command line
- **String Array**: Allows multiple string parameters
- **JVM Recognition**: JVM looks for this specific signature to start execution

---

## Key Concepts Summary

### Polymorphism
| Concept | Description |
|---------|-------------|
| **Definition** | One thing can have many forms |
| **Implementation** | Method/Constructor Overloading |
| **Benefit** | User-friendly - same method name for similar operations |

### Method Overloading Rules
| Rule | Example |
|------|---------|
| **Same name** | `add()`, `add()`, `add()` |
| **Different parameters** | Number, data type, or order must differ |
| **Not considered** | Return type, parameter names |

### Encapsulation
| Concept | Description |
|---------|-------------|
| **Definition** | Wrapping data and methods with restricted access |
| **Implementation** | Private variables + Public getter/setter methods |
| **Benefit** | Data security and controlled access |

### Encapsulation Rules
| Rule | Implementation |
|------|---------------|
| **Private variables** | `private String name;` |
| **Public methods** | `public void setName(String name)` |
| **Getter methods** | Return variable value |
| **Setter methods** | Assign value to variable |

---

## Practice Assignments

### Assignment 1: Calculator with Method Overloading
Create a `Calculator` class with overloaded methods:
- `calculate(int a, int b)` - Addition
- `calculate(double a, double b)` - Addition with decimals
- `calculate(int a, int b, int c)` - Addition of three numbers
- `calculate(int a, int b, String operation)` - Different operations (+, -, *, /)

### Assignment 2: Student Class with Encapsulation
Create a `Student` class with:
- Private variables: `studentId`, `name`, `marks`, `grade`
- Public getter and setter methods for all variables
- Additional method: `calculateGrade()` based on marks
- Test the class by creating objects and using getter/setter methods

### Assignment 3: Shape Class with Constructor Overloading
Create a `Shape` class with:
- Constructor 1: Default (creates unit square)
- Constructor 2: One parameter (creates square with given side)
- Constructor 3: Two parameters (creates rectangle with length, width)
- Constructor 4: Three parameters (creates box with length, width, height)
- Methods: `area()`, `perimeter()`, `volume()` (where applicable)

### Assignment 4: Bank Account with Both Concepts
Create a `BankAccount` class combining both concepts:
- **Encapsulation**: Private variables for account details
- **Polymorphism**: Overloaded methods for different transaction types
- Methods: `deposit(double amount)`, `deposit(double amount, String description)`, `withdraw(int amount)`, `withdraw(double amount)`

### Assignment 5: Main Method Overloading
Create a class that demonstrates main method overloading:
- Original main method
- Overloaded main with different parameter combinations
- Show how each version is called from the original main method

---

## Interview Questions

1. **What is polymorphism? How is it achieved in Java?**
2. **What are the rules for method overloading?**
3. **Can we overload methods by changing only return type?**
4. **What is encapsulation? Why is it important?**
5. **What is the difference between getter and setter methods?**
6. **Can we overload the main method?**
7. **What is the purpose of 'this' keyword?**
8. **How does Java choose which overloaded method to call?**

---

**Next Session Preview**: We'll explore **Inheritance** - another fundamental OOP concept where classes can inherit properties and methods from other classes, and **Method Overriding** - a different type of polymorphism.