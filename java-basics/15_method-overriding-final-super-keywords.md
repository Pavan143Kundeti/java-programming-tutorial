# Session 15: Method Overriding, final and super Keywords

## Table of Contents
1. [Introduction to Method Overriding](#introduction-to-method-overriding)
2. [Method Overriding vs Method Overloading](#method-overriding-vs-method-overloading)
3. [Combining Overriding and Overloading](#combining-overriding-and-overloading)
4. [final Keyword](#final-keyword)
5. [super Keyword](#super-keyword)
6. [Practice Assignments](#practice-assignments)

---

## Introduction to Method Overriding

### What is Method Overriding?
**Method Overriding** is recreating the same method from parent class in child class with **same signature** but **different implementation**.

### Definition
- **Same method signature** = Same return type + Same method name + Same parameters
- **Different implementation** = Different method body
- **Purpose**: Customize parent class method behavior in child class

### Real-World Example: House Renovation
- **Parent** has an old house with old design
- **Child** inherits the same house
- **Child renovates** the house (same structure, new interior) = **Method Overriding**

### When is Method Overriding Needed?
- When parent class method implementation is **outdated**
- When child class needs **different behavior** for same method
- When you want to **customize** inherited functionality

### Rules for Method Overriding

| Rule | Description | Example |
|------|-------------|---------|
| **Same Return Type** | Must have identical return type | `void display()` in both classes |
| **Same Method Name** | Method name must be identical | `calculateInterest()` in both |
| **Same Parameters** | Number, type, and order must match | `(int amount, double rate)` |
| **Different Body** | Only implementation can change | Different calculation logic |

---

## Method Overriding Example

### Banking System Example

```java
// Parent class
class Bank {
    double rateOfInterest() {
        return 0.0;  // Default rate
    }
}

// Child class 1
class ICICI extends Bank {
    @Override
    double rateOfInterest() {
        return 10.5;  // ICICI specific rate
    }
}

// Child class 2  
class SBI extends Bank {
    @Override
    double rateOfInterest() {
        return 11.5;  // SBI specific rate
    }
}

// Main class
public class OverridingDemo {
    public static void main(String[] args) {
        // Create objects and call overridden methods
        ICICI icici = new ICICI();
        System.out.println("ICICI Rate: " + icici.rateOfInterest());  // Output: 10.5
        
        SBI sbi = new SBI();
        System.out.println("SBI Rate: " + sbi.rateOfInterest());      // Output: 11.5
        
        Bank bank = new Bank();
        System.out.println("Default Rate: " + bank.rateOfInterest()); // Output: 0.0
    }
}
```

### Key Points About Method Overriding

| Concept | Description |
|---------|-------------|
| **Inheritance Required** | Must have parent-child relationship |
| **Runtime Decision** | JVM decides which method to call at runtime |
| **@Override Annotation** | Optional but recommended for clarity |
| **Overridden Method Executes** | Child class method always executes when called through child object |

---

## Method Overriding vs Method Overloading

### Comparison Table

| Aspect | Method Overriding | Method Overloading |
|--------|------------------|-------------------|
| **Relationship** | Inheritance (Parent-Child) | Same class or Inheritance |
| **Method Signature** | Must be SAME | Must be DIFFERENT |
| **Implementation** | Must be DIFFERENT | Can be same or different |
| **Purpose** | Customize inherited behavior | Provide multiple ways to call method |
| **Concept** | Inheritance concept | Polymorphism concept |
| **Classes Required** | Minimum 2 classes | Can work with 1 class |

### Detailed Comparison

**Method Overriding:**
```java
// Parent class
class Parent {
    void display(int a) {
        System.out.println("Parent: " + a);
    }
}

// Child class
class Child extends Parent {
    @Override
    void display(int a) {  // Same signature
        System.out.println("Child: " + a);  // Different implementation
    }
}
```

**Method Overloading:**
```java
class Calculator {
    // Same method name, different parameters
    int add(int a, int b) {
        return a + b;
    }
    
    double add(double a, double b) {  // Different parameter types
        return a + b;
    }
    
    int add(int a, int b, int c) {    // Different number of parameters
        return a + b + c;
    }
}
```

---

## Combining Overriding and Overloading

### Example: Both Concepts Together

```java
// Parent class
class ABC {
    void m1(int a) {
        System.out.println("Parent M1: " + a);
    }
    
    void m2(int b) {
        System.out.println("Parent M2: " + b);
    }
}

// Child class
class XYZ extends ABC {
    // Method Overriding - same signature, different implementation
    @Override
    void m1(int a) {
        System.out.println("Child M1: " + (a * a));  // Square the value
    }
    
    // Method Overloading - same name, different signature
    void m2(int a, int b) {
        System.out.println("Child M2 Overloaded: " + (a + b));
    }
}

// Usage
public class OverridingVsOverloading {
    public static void main(String[] args) {
        XYZ obj = new XYZ();
        
        obj.m1(10);      // Calls overridden method → Output: Child M1: 100
        obj.m2(20);      // Calls inherited method → Output: Parent M2: 20
        obj.m2(10, 20);  // Calls overloaded method → Output: Child M2 Overloaded: 30
    }
}
```

### Method Count in Child Class

**In XYZ class, total methods available:**
1. `m1(int a)` - Overridden method (only child version exists)
2. `m2(int b)` - Inherited from parent
3. `m2(int a, int b)` - Overloaded method in child

**Total: 3 methods**

---

## final Keyword

### What is final Keyword?
The **final** keyword provides **security and privacy** by restricting modification of variables, methods, and classes.

### final Keyword Applications

| Level | Usage | Effect |
|-------|-------|--------|
| **Variables** | `final int x = 100;` | Value cannot be changed (constant) |
| **Methods** | `final void display()` | Method cannot be overridden |
| **Classes** | `final class MyClass` | Class cannot be extended |

---

### 1. final Variables

**Without final:**
```java
class Test {
    int x = 100;  // Regular variable
}

public class FinalVariableDemo {
    public static void main(String[] args) {
        Test t = new Test();
        System.out.println(t.x);  // Output: 100
        
        t.x = 200;  // ✅ Allowed - can change value
        System.out.println(t.x);  // Output: 200
    }
}
```

**With final:**
```java
class Test {
    final int x = 100;  // final variable
}

public class FinalVariableDemo {
    public static void main(String[] args) {
        Test t = new Test();
        System.out.println(t.x);  // Output: 100
        
        // t.x = 200;  // ❌ Error: Cannot assign to final variable
    }
}
```

### 2. final Methods

**Without final:**
```java
// Parent class
class TestOne {
    void m() {
        System.out.println("Method from TestOne");
    }
}

// Child class
class TestTwo extends TestOne {
    @Override
    void m() {  // ✅ Overriding allowed
        System.out.println("Method from TestTwo");
    }
}
```

**With final:**
```java
// Parent class
class TestOne {
    final void m() {  // final method
        System.out.println("Method from TestOne");
    }
}

// Child class
class TestTwo extends TestOne {
    // @Override
    // void m() {  // ❌ Error: Cannot override final method
    //     System.out.println("Method from TestTwo");
    // }
}
```

### 3. final Classes

**Without final:**
```java
class TestOne {
    void display() {
        System.out.println("TestOne method");
    }
}

class TestTwo extends TestOne {  // ✅ Inheritance allowed
    void show() {
        System.out.println("TestTwo method");
    }
}
```

**With final:**
```java
final class TestOne {  // final class
    void display() {
        System.out.println("TestOne method");
    }
}

// class TestTwo extends TestOne {  // ❌ Error: Cannot extend final class
//     void show() {
//         System.out.println("TestTwo method");
//     }
// }
```

### final Keyword Summary

| final Applied To | Restriction | Example |
|------------------|-------------|---------|
| **Variable** | Value cannot be changed | `final int MAX = 100;` |
| **Method** | Cannot be overridden in child class | `final void process()` |
| **Class** | Cannot be extended/inherited | `final class Utility` |

### Important Notes About final

| Concept | Description |
|---------|-------------|
| **Overloading Still Works** | final methods can still be overloaded |
| **Static vs final** | Different concepts - static = shared, final = constant |
| **Real Examples** | String class is final, Math class methods are final |

---

## super Keyword

### What is super Keyword?
The **super** keyword refers to the **immediate parent class** and is used to access parent class members even after overriding.

### When to Use super Keyword?

**Scenario**: You have overridden a variable/method in child class, but still want to access the parent class version.

### super for Variables

```java
// Parent class
class Animal {
    String color = "White";
}

// Child class
class Dog extends Animal {
    String color = "Black";  // Overriding parent variable
    
    void displayColor() {
        System.out.println("Child color: " + color);        // Prints: Black
        System.out.println("Parent color: " + super.color); // Prints: White
    }
}

// Usage
public class SuperVariableDemo {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.displayColor();
    }
}
```

**Output:**
```
Child color: Black
Parent color: White
```

### super for Methods

```java
// Parent class
class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

// Child class
class Dog extends Animal {
    @Override
    void eat() {
        System.out.println("Eating bread");
    }
    
    void callParentEat() {
        eat();        // Calls child method
        super.eat();  // Calls parent method
    }
}

// Usage
public class SuperMethodDemo {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.callParentEat();
    }
}
```

**Output:**
```
Eating bread
Eating
```

### super Keyword Rules

| Rule | Description | Example |
|------|-------------|---------|
| **Immediate Parent Only** | Works only with direct parent class | A→B→C: C can access B, not A directly |
| **Inheritance Required** | Must have parent-child relationship | Cannot use in standalone class |
| **Class Members Only** | Works with class variables/methods | Not applicable to interfaces |

### super in Multi-Level Inheritance

```java
class GrandParent {
    String name = "GrandParent";
}

class Parent extends GrandParent {
    String name = "Parent";
}

class Child extends Parent {
    String name = "Child";
    
    void displayNames() {
        System.out.println("Child: " + name);        // Child
        System.out.println("Parent: " + super.name); // Parent
        // Cannot directly access GrandParent name using super
    }
}
```

### Important Notes About super

| Concept | Description |
|---------|-------------|
| **Immediate Parent Only** | super refers to direct parent, not grandparent |
| **Multiple Inheritance** | Not applicable (Java doesn't support multiple inheritance with classes) |
| **Interface Limitation** | Cannot use super with interfaces |
| **Constructor Calls** | super() can call parent constructor (covered in advanced topics) |

---

## Complete Example: Banking System

```java
// Parent class
class Bank {
    String bankName = "Generic Bank";
    double baseRate = 5.0;
    
    final void regulatoryCompliance() {
        System.out.println("Following RBI guidelines");
    }
    
    double calculateInterest(double amount) {
        return amount * baseRate / 100;
    }
    
    void displayBankInfo() {
        System.out.println("Bank: " + bankName);
    }
}

// Child class
class HDFC extends Bank {
    String bankName = "HDFC Bank";  // Variable overriding
    final double hdfcRate = 8.5;    // final variable
    
    @Override
    double calculateInterest(double amount) {  // Method overriding
        return amount * hdfcRate / 100;
    }
    
    // Method overloading
    double calculateInterest(double amount, int years) {
        return amount * hdfcRate * years / 100;
    }
    
    void displayAllInfo() {
        System.out.println("Current Bank: " + bankName);      // HDFC Bank
        System.out.println("Parent Bank: " + super.bankName); // Generic Bank
        
        System.out.println("HDFC Interest: " + calculateInterest(1000));       // 85.0
        System.out.println("Generic Interest: " + super.calculateInterest(1000)); // 50.0
    }
}

// Usage
public class CompleteBankingExample {
    public static void main(String[] args) {
        HDFC hdfc = new HDFC();
        
        hdfc.displayAllInfo();
        hdfc.regulatoryCompliance();  // final method - cannot be overridden
        
        System.out.println("Simple Interest: " + hdfc.calculateInterest(1000));
        System.out.println("Compound Interest: " + hdfc.calculateInterest(1000, 2));
    }
}
```

---

## Key Concepts Summary

### Method Overriding
| Concept | Description |
|---------|-------------|
| **Purpose** | Customize parent class method in child class |
| **Requirement** | Inheritance relationship mandatory |
| **Signature** | Must be exactly same as parent method |
| **Implementation** | Must be different from parent method |

### final Keyword
| Level | Effect | Use Case |
|-------|--------|---------|
| **Variable** | Makes constant | Configuration values, mathematical constants |
| **Method** | Prevents overriding | Security-critical methods, utility methods |
| **Class** | Prevents inheritance | Utility classes, immutable classes |

### super Keyword
| Usage | Purpose | Limitation |
|-------|---------|------------|
| **super.variable** | Access parent class variable | Immediate parent only |
| **super.method()** | Call parent class method | Immediate parent only |
| **super()** | Call parent constructor | Must be first statement |

---

## Practice Assignments

### Assignment 1: Vehicle Inheritance with Overriding
Create a vehicle system:
- **Parent Class**: `Vehicle` with `start()`, `stop()`, `fuelType()` methods
- **Child Classes**: `Car`, `Motorcycle` - override `fuelType()` and `start()` methods
- Demonstrate method overriding with different implementations

### Assignment 2: final Keyword Exploration
Create examples showing:
- final variable that cannot be changed
- final method that cannot be overridden
- final class that cannot be extended
- Show compilation errors when trying to violate final restrictions

### Assignment 3: super Keyword Usage
Create a multi-level inheritance:
- **GrandParent**: `Person` with `name`, `age`, `introduce()` method
- **Parent**: `Employee` extends Person, adds `salary`, overrides `introduce()`
- **Child**: `Manager` extends Employee, adds `teamSize`, overrides `introduce()`
- Use super to access parent class variables and methods

### Assignment 4: Banking System Enhancement
Extend the banking example:
- Add more bank types (SBI, ICICI, Axis)
- Implement different interest calculation methods
- Use final for regulatory methods
- Use super to access parent bank features
- Combine overriding and overloading

### Assignment 5: Shape Hierarchy with All Concepts
Create a comprehensive shape system:
- **Parent**: `Shape` with area calculation methods
- **Children**: `Circle`, `Rectangle`, `Triangle`
- Use method overriding for area calculations
- Use final for constant values (PI, etc.)
- Use super to access parent class utilities
- Include method overloading for different parameter combinations

---

## Interview Questions

1. **What is method overriding? How is it different from method overloading?**
2. **What are the rules for method overriding?**
3. **Can we override static methods? Why or why not?**
4. **What is the purpose of @Override annotation?**
5. **Explain final keyword with examples for variables, methods, and classes.**
6. **Can we override final methods? What happens if we try?**
7. **What is super keyword? When and how do we use it?**
8. **Can we use super keyword to access grandparent class members directly?**
9. **What happens when we call an overridden method through parent class reference?**
10. **Can we have method overloading and overriding together in inheritance?**

---

**Next Session Preview**: We'll explore **Abstract Classes** and **Interfaces** - how they enable multiple inheritance, define contracts for classes, and provide a way to achieve 100% abstraction in Java.