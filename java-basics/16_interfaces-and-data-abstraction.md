# Session 16: Interfaces and Data Abstraction in Java

## Table of Contents
1. [Introduction to Data Abstraction](#introduction-to-data-abstraction)
2. [What is an Interface?](#what-is-an-interface)
3. [Interface Components](#interface-components)
4. [Creating and Implementing Interfaces](#creating-and-implementing-interfaces)
5. [Multiple Inheritance with Interfaces](#multiple-inheritance-with-interfaces)
6. [Abstract Classes vs Interfaces](#abstract-classes-vs-interfaces)
7. [Real-World Usage of Interfaces](#real-world-usage-of-interfaces)
8. [Practice Assignments](#practice-assignments)

---

## Introduction to Data Abstraction

### What is Data Abstraction?
**Data Abstraction** is a process of hiding implementation details and showing only functionality to the user.

### Real-World Examples

| Example | What You See | What's Hidden |
|---------|--------------|---------------|
| **Mobile Phone** | Apps, buttons, screen | Internal hardware, circuit design |
| **Car** | Steering, pedals, gear | Engine mechanics, fuel injection |
| **ATM Machine** | Screen, keypad | Banking software, network protocols |

### Key Points About Abstraction
- **User Perspective**: Can use the functionality without knowing implementation
- **Security**: Implementation details are hidden
- **Simplicity**: Complex operations appear simple to users

### Achieving Data Abstraction in Java

| Method | Abstraction Level | Usage |
|--------|------------------|-------|
| **Abstract Class** | Partial (0-99%) | When some methods need implementation |
| **Interface** | Complete (100%) | When all methods should be abstract |

**Interface is preferred** because it provides 100% abstraction and supports multiple inheritance.

---

## What is an Interface?

### Definition
An **Interface** is a blueprint of a class that contains only abstract methods (and from Java 8+, default and static methods).

### Interface vs Class Syntax

**Class Syntax:**
```java
class ClassName {
    // variables and methods
}
```

**Interface Syntax:**
```java
interface InterfaceName {
    // variables and methods
}
```

### Why Use Interfaces?

**Development Scenario:**
1. **Initial Phase**: Developers have requirements but no detailed design
2. **Interface Creation**: Create abstract methods based on requirements
3. **Later Phase**: Implement interfaces when design is ready

**Example: Banking Application**
```java
interface BankingOperations {
    void fundTransfer();    // Requirement known, implementation unknown
    void login();          // Requirement known, implementation unknown
    void checkBalance();   // Requirement known, implementation unknown
}
```

---

## Interface Components

### 1. Variables in Interface

**Key Rules:**
- All variables are **final** and **static** by default
- No need to explicitly write `final` and `static` keywords
- Must be initialized when declared

```java
interface Shape {
    int length = 10;    // Automatically final and static
    int width = 20;     // Automatically final and static
    
    // Equivalent to:
    // final static int length = 10;
    // final static int width = 20;
}
```

### 2. Methods in Interface

**Three Types of Methods (Java 8+):**

| Method Type | Syntax | Implementation | Default Access |
|-------------|--------|----------------|----------------|
| **Abstract** | `void methodName();` | Not allowed | public |
| **Default** | `default void methodName() { }` | Required | public |
| **Static** | `static void methodName() { }` | Required | public |

### Abstract Methods
```java
interface Shape {
    void circle();      // Abstract method - no implementation
    void square();      // Abstract method - no implementation
}
```

### Default Methods (Java 8+)
```java
interface Shape {
    default void square() {
        System.out.println("This is a square");
    }
}
```

### Static Methods (Java 8+)
```java
interface Shape {
    static void rectangle() {
        System.out.println("This is a rectangle");
    }
}
```

---

## Creating and Implementing Interfaces

### Complete Interface Example

```java
// Interface definition
interface Shape {
    // Variables (automatically final and static)
    int length = 10;
    int width = 20;
    
    // Abstract method (no implementation)
    void circle();
    
    // Default method (has implementation)
    default void square() {
        System.out.println("This is a square");
    }
    
    // Static method (has implementation)
    static void rectangle() {
        System.out.println("This is a rectangle");
    }
}

// Class implementing the interface
class InterfaceDemo implements Shape {
    // Must implement all abstract methods from interface
    public void circle() {  // Must be public
        System.out.println("This is circle abstract method");
    }
    
    // Can add own methods
    void triangle() {
        System.out.println("This is triangle method");
    }
}
```

### Implementation Rules

| Rule | Description | Example |
|------|-------------|---------|
| **Implement Abstract Methods** | Must implement all abstract methods | `public void circle() { }` |
| **Public Access Modifier** | Interface methods are public, implementation must be public | Cannot reduce visibility |
| **Same Method Signature** | Exact same return type, name, parameters | `void circle()` not `int circle()` |

### Using the Interface

```java
public class Main {
    public static void main(String[] args) {
        // Scenario 1: Class reference and object
        InterfaceDemo obj1 = new InterfaceDemo();
        obj1.circle();      // Abstract method (implemented)
        obj1.square();      // Default method (inherited)
        obj1.triangle();    // Own method
        
        // Static method - access directly from interface
        Shape.rectangle();
        
        // Scenario 2: Interface reference, class object
        Shape obj2 = new InterfaceDemo();
        obj2.circle();      // Abstract method (implemented)
        obj2.square();      // Default method (inherited)
        // obj2.triangle(); // ❌ Error - not available in interface
        
        // Access static variables
        System.out.println(Shape.length * Shape.width);
    }
}
```

### Object Reference vs Instantiation

| Concept | Class | Interface |
|---------|-------|-----------|
| **Object Creation** | ✅ `new ClassName()` | ❌ `new InterfaceName()` |
| **Reference Variable** | ✅ `ClassName obj` | ✅ `InterfaceName obj` |

**Key Point**: Interface reference can hold object of implementing class.

```java
// ✅ Allowed - Interface reference holding class object
Shape obj = new InterfaceDemo();

// ❌ Not allowed - Cannot instantiate interface
Shape obj = new Shape();  // Compilation error
```

---

## Multiple Inheritance with Interfaces

### Why Multiple Inheritance with Classes Failed
```java
// This is NOT allowed in Java
class Child extends Parent1, Parent2 {  // ❌ Compilation error
    // Ambiguity: Which parent's method to inherit?
}
```

### Multiple Inheritance with Interfaces

**Example: Two Parent Interfaces**
```java
// Parent Interface 1
interface I1 {
    int x = 100;
    void m1();
}

// Parent Interface 2
interface I2 {
    int y = 200;
    void m2();
}

// Child class implementing both interfaces
class C1 implements I1, I2 {
    // Must implement all abstract methods
    public void m1() {
        System.out.println("M1 method: " + x);
    }
    
    public void m2() {
        System.out.println("M2 method: " + y);
    }
}

// Usage
public class MultipleInheritanceDemo {
    public static void main(String[] args) {
        C1 obj = new C1();
        obj.m1();  // Output: M1 method: 100
        obj.m2();  // Output: M2 method: 200
    }
}
```

### Combining Class Inheritance and Interface Implementation

```java
// Parent class
class C2 {
    int z = 300;
    void m3() {
        System.out.println("M3 method: " + z);
    }
}

// Child class extending class and implementing interfaces
class C1 extends C2 implements I1, I2 {
    public void m1() {
        System.out.println("M1 method: " + x);
    }
    
    public void m2() {
        System.out.println("M2 method: " + y);
    }
}

// Usage
public class HybridInheritanceDemo {
    public static void main(String[] args) {
        C1 obj = new C1();
        obj.m1();  // From I1 interface
        obj.m2();  // From I2 interface  
        obj.m3();  // From C2 class
    }
}
```

### Inheritance Rules Summary

| Relationship | Keyword | Limitation |
|--------------|---------|------------|
| **Class → Class** | `extends` | Only one parent class |
| **Interface → Interface** | `extends` | Multiple parent interfaces |
| **Class → Interface** | `implements` | Multiple interfaces |
| **Interface → Class** | ❌ Not possible | - |

**Syntax for Multiple Inheritance:**
```java
class Child extends ParentClass implements Interface1, Interface2, Interface3 {
    // Implementation
}
```

---

## Abstract Classes vs Interfaces

### What is an Abstract Class?

```java
abstract class AbstractClass {
    // Can have both abstract and concrete methods
    abstract void abstractMethod();  // No implementation
    
    void concreteMethod() {          // Has implementation
        System.out.println("Concrete method");
    }
}
```

### Detailed Comparison

| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| **Methods** | Abstract + Concrete methods | Only abstract (+ default/static in Java 8+) |
| **Multiple Inheritance** | ❌ Not supported | ✅ Supported |
| **Variables** | All types (final, non-final, static, non-static) | Only final and static |
| **Interface Implementation** | ✅ Can implement interfaces | ❌ Cannot implement abstract classes |
| **Class Extension** | ✅ Can extend one class | ❌ Cannot extend classes |
| **Access Modifiers** | All types (private, protected, public, default) | Only public |
| **Keyword for Declaration** | `abstract class` | `interface` |
| **Keyword for Inheritance** | `extends` | `implements` |
| **Abstract Method Declaration** | `abstract void method();` | `void method();` (abstract by default) |

### When to Use Which?

| Use Abstract Class When | Use Interface When |
|-------------------------|-------------------|
| Need some implemented methods | Need 100% abstraction |
| Want to share code among related classes | Want to specify contract for unrelated classes |
| Need non-public members | All members should be public |
| Want to provide common base functionality | Want to support multiple inheritance |

### Example Comparison

**Abstract Class Example:**
```java
abstract class Vehicle {
    String brand;  // Concrete variable
    
    abstract void start();  // Abstract method
    
    void stop() {           // Concrete method
        System.out.println("Vehicle stopped");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car started");
    }
}
```

**Interface Example:**
```java
interface Drivable {
    int MAX_SPEED = 200;  // final and static by default
    
    void accelerate();    // abstract by default
    void brake();         // abstract by default
    
    default void honk() { // default method (Java 8+)
        System.out.println("Honking...");
    }
}

class Car implements Drivable {
    public void accelerate() {
        System.out.println("Car accelerating");
    }
    
    public void brake() {
        System.out.println("Car braking");
    }
}
```

---

## Real-World Usage of Interfaces

### Selenium WebDriver Example

**WebDriver is an Interface:**
```java
// WebDriver interface (simplified)
interface WebDriver {
    void get(String url);
    WebElement findElement(By locator);
    void quit();
}

// Different browser implementations
class ChromeDriver implements WebDriver {
    public void get(String url) {
        // Chrome-specific implementation
    }
    // Other method implementations...
}

class FirefoxDriver implements WebDriver {
    public void get(String url) {
        // Firefox-specific implementation
    }
    // Other method implementations...
}

// Usage
WebDriver driver = new ChromeDriver();  // Interface reference
driver.get("https://example.com");
```

### Benefits in Real Projects

| Benefit | Description | Example |
|---------|-------------|---------|
| **Flexibility** | Switch implementations easily | Change from Chrome to Firefox driver |
| **Standardization** | Common contract for all implementations | All drivers have same methods |
| **Multiple Inheritance** | Combine multiple capabilities | Class can implement multiple interfaces |
| **Abstraction** | Hide implementation complexity | User doesn't need to know browser internals |

---

## Complete OOP Concepts Summary

### Object-Oriented Programming Concepts Covered

| Concept | Technical Implementation | Purpose |
|---------|-------------------------|---------|
| **1. Class** | Blueprint for objects | Define structure and behavior |
| **2. Object** | Instance of class | Actual entity with data and methods |
| **3. Polymorphism** | Method Overloading | One thing, many forms |
| **4. Encapsulation** | Getters and Setters | Data hiding and security |
| **5. Inheritance** | extends keyword, Method Overriding | Code reusability |
| **6. Data Abstraction** | Interface, Abstract Class | Hide implementation details |

### Inheritance Types Summary

| Type | Description | Support |
|------|-------------|---------|
| **Single** | One parent, one child | ✅ Classes & Interfaces |
| **Multi-level** | Chain inheritance (A→B→C) | ✅ Classes & Interfaces |
| **Hierarchical** | One parent, multiple children | ✅ Classes & Interfaces |
| **Multiple** | Multiple parents, one child | ❌ Classes, ✅ Interfaces |
| **Hybrid** | Combination of above types | ✅ With Interfaces |

---

## Practice Assignments

### Assignment 1: Basic Interface Implementation
Create a `Drawable` interface with:
- Abstract methods: `draw()`, `erase()`
- Default method: `display()` that prints "Drawing object"
- Static method: `getVersion()` that returns "1.0"
- Implement with `Circle` and `Rectangle` classes

### Assignment 2: Multiple Inheritance Example
Create interfaces `Flyable` and `Swimmable`:
- `Flyable`: methods `fly()`, `land()`
- `Swimmable`: methods `swim()`, `dive()`
- Create `Duck` class implementing both interfaces
- Demonstrate multiple inheritance

### Assignment 3: Banking System with Interfaces
Create `BankOperations` interface:
- Abstract methods: `deposit()`, `withdraw()`, `checkBalance()`
- Default method: `printStatement()`
- Implement with `SavingsAccount` and `CurrentAccount` classes
- Show different implementations for same interface

### Assignment 4: Shape Calculator
Create `Shape` interface with:
- Constants: `PI = 3.14159`
- Abstract methods: `calculateArea()`, `calculatePerimeter()`
- Implement with `Circle`, `Rectangle`, `Triangle` classes
- Use interface reference to hold different shape objects

### Assignment 5: Vehicle Management System
Create a hybrid inheritance system:
- `Vehicle` class with basic properties
- `Electric` interface with charging methods
- `GPS` interface with navigation methods
- `Tesla` class extending `Vehicle` and implementing both interfaces

---

## Interview Questions

1. **What is an interface? How is it different from a class?**
2. **Can we achieve multiple inheritance in Java? How?**
3. **What are the default access modifiers for interface methods and variables?**
4. **What is the difference between abstract class and interface?**
5. **Can we create an object of an interface? Explain with example.**
6. **What are default and static methods in interfaces? (Java 8)**
7. **Why are interface variables final and static by default?**
8. **Can a class implement multiple interfaces? Give example.**
9. **What is data abstraction? How do interfaces provide 100% abstraction?**
10. **Explain the concept of interface reference holding class object.**

---

**Next Session Preview**: We'll explore **Access Modifiers** (private, protected, public, default) - understanding visibility and scope of classes, methods, and variables, followed by **Exception Handling** - managing runtime errors gracefully in Java applications.