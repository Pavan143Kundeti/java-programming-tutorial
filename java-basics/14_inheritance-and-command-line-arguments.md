# Session 14: Inheritance and Command Line Arguments in Java

## Table of Contents
1. [Command Line Arguments](#command-line-arguments)
2. [Introduction to Inheritance](#introduction-to-inheritance)
3. [Types of Inheritance](#types-of-inheritance)
4. [Single Inheritance](#single-inheritance)
5. [Multi-Level Inheritance](#multi-level-inheritance)
6. [Hierarchical Inheritance](#hierarchical-inheritance)
7. [Multiple Inheritance](#multiple-inheritance)
8. [Why Multiple Inheritance is Not Supported](#why-multiple-inheritance-is-not-supported)
9. [Practice Assignments](#practice-assignments)

---

## Command Line Arguments

### What are Command Line Arguments?
- **Main method** can accept parameters just like any other method
- **String[] args** - Array of strings passed to main method at runtime
- **Usage**: Pass data to program when it starts execution

### How to Pass Arguments in Eclipse

**Step 1: Create a Simple Program**
```java
public class PassingParamsToMain {
    public static void main(String[] args) {
        // Print number of arguments
        System.out.println("Number of arguments: " + args.length);
        
        // Print all arguments using enhanced for loop
        for (String value : args) {
            System.out.println(value);
        }
    }
}
```

**Step 2: Pass Arguments in Eclipse**
1. **Right-click** on your class → **Run As** → **Run Configurations**
2. Go to **Arguments** tab
3. **Enter arguments** separated by spaces: `welcome to Java selenium`
4. **Click Run** or **Apply and Close**

**Step 3: Understanding the Output**
```
Number of arguments: 4
welcome
to
Java
selenium
```

### Key Points About Command Line Arguments

| Concept | Description |
|---------|-------------|
| **Parameter Type** | `String[] args` - Array of strings |
| **Separation** | Arguments separated by spaces |
| **Data Type** | All arguments are treated as strings |
| **Access** | Use `args[index]` or enhanced for loop |
| **Length** | Use `args.length` to get number of arguments |

### Alternative Array Syntax
```java
// All these are valid main method signatures:
public static void main(String[] args)     // Standard
public static void main(String args[])     // Alternative 1
public static void main(String[] a)        // Different parameter name
```

### Example: Using Command Line Arguments
```java
public class CommandLineExample {
    public static void main(String[] args) {
        if (args.length == 0) {
            System.out.println("No arguments provided");
            return;
        }
        
        System.out.println("First argument: " + args[0]);
        System.out.println("Total arguments: " + args.length);
        
        // Print all arguments
        System.out.println("All arguments:");
        for (int i = 0; i < args.length; i++) {
            System.out.println("Argument " + i + ": " + args[i]);
        }
    }
}
```

---

## Introduction to Inheritance

### What is Inheritance?
**Inheritance** is acquiring all the properties (variables) and behaviors (methods) from one class to another class.

### Definition
- **Properties** = Variables
- **Behaviors** = Methods
- **Parent Class** = Class that provides properties and behaviors
- **Child Class** = Class that acquires properties and behaviors

### Real-World Example: Banking Application

**Without Inheritance:**
```
Personal Loan Module: 10 classes × 1 hour = 10 hours
Home Loan Module: 20 classes × 1 hour = 20 hours
Total Time: 30 hours
```

**With Inheritance:**
```
Common Loan Classes: 5 classes × 1 hour = 5 hours
Personal Loan Module: 5 common + 5 new = 5 hours
Home Loan Module: 5 common + 15 new = 15 hours
Total Time: 25 hours (5 hours saved!)
```

### Benefits of Inheritance

| Benefit | Description | Example |
|---------|-------------|---------|
| **Reusability** | Use existing code multiple times | Common loan processing methods |
| **Avoid Duplication** | Don't write same code again | Shared validation logic |
| **Time Saving** | Faster development | Reuse existing tested code |
| **Maintenance** | Update once, reflects everywhere | Change interest calculation once |

### Inheritance Terminology

| Term | Alternative Names | Description |
|------|------------------|-------------|
| **Parent Class** | Base Class, Super Class | Class that provides properties |
| **Child Class** | Sub Class, Derived Class | Class that inherits properties |
| **extends** | Keyword | Used to establish inheritance relationship |

### Basic Inheritance Syntax
```java
class Parent {
    // Parent class members
}

class Child extends Parent {
    // Child class members + inherited members
}
```

---

## Types of Inheritance

Java supports **4 types** of inheritance:

| Type | Description | Diagram |
|------|-------------|---------|
| **Single** | One parent, one child | A → B |
| **Multi-Level** | Chain of inheritance | A → B → C |
| **Hierarchical** | One parent, multiple children | A → B, A → C |
| **Multiple** | Multiple parents, one child | A,B → C (Not supported with classes) |

---

## Single Inheritance

### Definition
**Single Inheritance**: One parent class and one child class.

### Example: Single Inheritance
```java
// Parent class
class A {
    int a = 100;
    
    void display() {
        System.out.println("Value of a: " + a);
    }
}

// Child class
class B extends A {
    int b = 200;
    
    void show() {
        System.out.println("Value of b: " + b);
    }
}

// Main class
public class SingleInheritance {
    public static void main(String[] args) {
        // Create object of child class
        B obj = new B();
        
        // Access parent class members
        System.out.println("a = " + obj.a);      // From parent
        obj.display();                           // From parent
        
        // Access child class members
        System.out.println("b = " + obj.b);      // From child
        obj.show();                              // From child
    }
}
```

**Output:**
```
a = 100
Value of a: 100
b = 200
Value of b: 200
```

### Key Points: Single Inheritance

| Concept | Description |
|---------|-------------|
| **Child Object** | Can access both parent and child members |
| **Parent Object** | Can access only parent members |
| **Memory** | Child object contains parent + child members |
| **Relationship** | IS-A relationship (B is a type of A) |

---

## Multi-Level Inheritance

### Definition
**Multi-Level Inheritance**: Chain of inheritance where each class has one parent.

### Example: Multi-Level Inheritance
```java
// Grandparent class
class A {
    int a = 100;
    
    void display() {
        System.out.println("Method from class A");
    }
}

// Parent class
class B extends A {
    int b = 200;
    
    void show() {
        System.out.println("Method from class B");
    }
}

// Child class (Grandchild of A)
class C extends B {
    int c = 300;
    
    void print() {
        System.out.println("Method from class C");
    }
}

// Main class
public class MultiLevelInheritance {
    public static void main(String[] args) {
        // Create object of grandchild class
        C obj = new C();
        
        // Assign values through object
        obj.a = 100;  // From grandparent A
        obj.b = 200;  // From parent B
        obj.c = 300;  // From child C
        
        // Call all methods
        obj.display();  // From class A
        obj.show();     // From class B
        obj.print();    // From class C
    }
}
```

**Output:**
```
Method from class A
Method from class B
Method from class C
```

### Multi-Level Inheritance Chain

| Level | Class | Inherits From | Contains |
|-------|-------|---------------|----------|
| **1** | A | Object (default) | a, display() |
| **2** | B | A | a, display(), b, show() |
| **3** | C | B | a, display(), b, show(), c, print() |

---

## Hierarchical Inheritance

### Definition
**Hierarchical Inheritance**: One parent class with multiple child classes.

### Example: Hierarchical Inheritance
```java
// Parent class
class Parent {
    void display(int a) {
        System.out.println("Value from parent: " + a);
    }
}

// First child class
class Child1 extends Parent {
    void show(int b) {
        System.out.println("Value from Child1: " + b);
    }
}

// Second child class
class Child2 extends Parent {
    void print(int c) {
        System.out.println("Value from Child2: " + c);
    }
}

// Main class
public class HierarchicalInheritance {
    public static void main(String[] args) {
        // Create object of first child
        Child1 c1 = new Child1();
        c1.display(100);  // From parent
        c1.show(200);     // From Child1
        
        // Create object of second child
        Child2 c2 = new Child2();
        c2.display(500);  // From parent
        c2.print(2000);   // From Child2
    }
}
```

**Output:**
```
Value from parent: 100
Value from Child1: 200
Value from parent: 500
Value from Child2: 2000
```

### Hierarchical Inheritance Structure

| Class | Methods Available | Relationship |
|-------|------------------|--------------|
| **Parent** | display() | Root class |
| **Child1** | display(), show() | Child of Parent |
| **Child2** | display(), print() | Child of Parent |
| **Relationship** | Child1 and Child2 are siblings | No direct relationship between children |

---

## Multiple Inheritance

### Definition
**Multiple Inheritance**: One child class inheriting from multiple parent classes.

### Why Multiple Inheritance is Needed?
```java
// Scenario: Need features from both parents
class Father {
    void business() { /* Business skills */ }
}

class Mother {
    void cooking() { /* Cooking skills */ }
}

// Child wants both skills
class Child extends Father, Mother {  // ❌ Not allowed in Java
    // Want both business() and cooking()
}
```

### Problem: Not Supported with Classes
```java
// ❌ This syntax is NOT allowed
class Child extends Parent1, Parent2 {
    // Compilation error
}
```

**Error**: `extends` keyword supports only **one class** at a time.

---

## Why Multiple Inheritance is Not Supported

### Reason 1: Ambiguity Problem

**Scenario: Duplicate Methods**
```java
class Parent1 {
    void display() {
        System.out.println("Display from Parent1");
    }
}

class Parent2 {
    void display() {
        System.out.println("Display from Parent2");
    }
}

// If this was allowed (it's not):
class Child extends Parent1, Parent2 {
    // Which display() method should Child inherit?
    // Parent1.display() or Parent2.display()?
    // This creates AMBIGUITY!
}
```

### Reason 2: Object Class Problem

**Every class extends Object by default:**
```java
// Even empty classes have methods
class TestClass {
    // No methods written, but still has methods!
}

public class ObjectClassDemo {
    public static void main(String[] args) {
        TestClass obj = new TestClass();
        
        // These methods come from Object class:
        obj.equals(null);
        obj.getClass();
        obj.hashCode();
        obj.notify();
        obj.toString();
        obj.wait();
    }
}
```

**The Problem:**
```java
class Parent1 {
    // Inherits from Object: equals(), toString(), etc.
}

class Parent2 {
    // Also inherits from Object: equals(), toString(), etc.
}

// If multiple inheritance was allowed:
class Child extends Parent1, Parent2 {
    // Would inherit duplicate methods from Object class
    // through both Parent1 and Parent2
    // Which equals() method to use? Ambiguity!
}
```

### Default Object Class Inheritance

| Class | Implicit Inheritance | Available Methods |
|-------|---------------------|-------------------|
| **Any Class** | `extends Object` | equals(), getClass(), hashCode(), notify(), toString(), wait() |
| **Result** | All classes have common methods | Duplicate methods in multiple inheritance |

### Solution: Interface Concept
```java
// ✅ This will be possible with interfaces
interface Parent1 {
    void method1();
}

interface Parent2 {
    void method2();
}

class Child implements Parent1, Parent2 {
    // Can implement multiple interfaces
    public void method1() { /* Implementation */ }
    public void method2() { /* Implementation */ }
}
```

---

## Important Rules and Notes

### Class Naming Rules in Package
```java
// ❌ Cannot have duplicate class names in same package
class A { }
class A { }  // Error: Duplicate class

// ✅ Must use different names
class Parent { }
class Child1 { }
class Child2 { }
```

### Access Rules
```java
// ✅ Only ONE public class per file
public class MainClass {
    public static void main(String[] args) { }
}

// ✅ Other classes should not be public
class HelperClass1 { }
class HelperClass2 { }
```

### Object Creation and Access
```java
class Parent {
    int x = 10;
    void show() { }
}

class Child extends Parent {
    int y = 20;
    void display() { }
}

public class AccessDemo {
    public static void main(String[] args) {
        // Parent object - can access only parent members
        Parent p = new Parent();
        p.x;      // ✅ Allowed
        p.show(); // ✅ Allowed
        // p.y;      // ❌ Not allowed
        // p.display(); // ❌ Not allowed
        
        // Child object - can access both parent and child members
        Child c = new Child();
        c.x;        // ✅ Allowed (from parent)
        c.show();   // ✅ Allowed (from parent)
        c.y;        // ✅ Allowed (from child)
        c.display(); // ✅ Allowed (from child)
    }
}
```

---

## Summary Table

### Inheritance Types Comparison

| Type | Parents | Children | Example | Supported |
|------|---------|----------|---------|-----------|
| **Single** | 1 | 1 | A → B | ✅ Yes |
| **Multi-Level** | Chain | Chain | A → B → C | ✅ Yes |
| **Hierarchical** | 1 | Multiple | A → B, A → C | ✅ Yes |
| **Multiple** | Multiple | 1 | A,B → C | ❌ No (with classes) |

### Keywords Summary

| Keyword | Purpose | Example |
|---------|---------|---------|
| **extends** | Establish inheritance | `class Child extends Parent` |
| **Object** | Root class of all classes | Implicit parent of every class |
| **implements** | For interfaces (next session) | `class Child implements Interface` |

---

## Practice Assignments

### Assignment 1: Single Inheritance - Vehicle System
Create a vehicle inheritance system:
- **Parent Class**: `Vehicle` with properties `brand`, `model`, `year` and method `start()`
- **Child Class**: `Car` with additional property `doors` and method `honk()`
- Create objects and demonstrate inheritance

### Assignment 2: Multi-Level Inheritance - Animal Kingdom
Create a multi-level inheritance:
- **Level 1**: `Animal` with `name`, `eat()` method
- **Level 2**: `Mammal` extends `Animal`, adds `furColor`, `giveBirth()` method
- **Level 3**: `Dog` extends `Mammal`, adds `breed`, `bark()` method
- Demonstrate accessing all levels through Dog object

### Assignment 3: Hierarchical Inheritance - Employee System
Create hierarchical inheritance:
- **Parent**: `Employee` with `name`, `id`, `salary`, `work()` method
- **Child 1**: `Developer` with `programmingLanguage`, `code()` method
- **Child 2**: `Manager` with `teamSize`, `manage()` method
- Create objects of both children and show common parent functionality

### Assignment 4: Understanding Object Class
Create a simple class and demonstrate:
- Default methods available from Object class
- Use `toString()`, `equals()`, `hashCode()` methods
- Show that every class implicitly extends Object

### Assignment 5: Command Line Arguments Calculator
Create a calculator that:
- Takes operation and numbers as command line arguments
- Example: `java Calculator add 10 20`
- Supports: add, subtract, multiply, divide
- Handles error cases (insufficient arguments, invalid operation)

---

## Interview Questions

1. **What is inheritance? What are its advantages?**
2. **What are the different types of inheritance in Java?**
3. **Why is multiple inheritance not supported in Java using classes?**
4. **What is the diamond problem in multiple inheritance?**
5. **What is the Object class? Why is it important?**
6. **Can we achieve multiple inheritance in Java? How?**
7. **What is the difference between extends and implements?**
8. **What happens when we create an object of a child class?**
9. **Can a child class access private members of parent class?**
10. **How do command line arguments work in Java?**

---

**Next Session Preview**: We'll explore **Interfaces** - how they enable multiple inheritance, **Method Overriding** - runtime polymorphism, and additional keywords like **super** and **final** that work with inheritance.