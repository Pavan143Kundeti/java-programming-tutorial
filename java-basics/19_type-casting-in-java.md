# Session 19: Type Casting in Java

## Table of Contents
1. [Introduction to Type Casting](#introduction-to-type-casting)
2. [Types of Type Casting](#types-of-type-casting)
3. [Primitive Type Casting](#primitive-type-casting)
4. [Object Type Casting](#object-type-casting)
5. [Three Rules for Object Type Casting](#three-rules-for-object-type-casting)
6. [Predefined Classes Type Casting](#predefined-classes-type-casting)
7. [When to Use Different Approaches](#when-to-use-different-approaches)
8. [Practice Examples](#practice-examples)
9. [Real-World Applications](#real-world-applications)

---

## Introduction to Type Casting

### What is Type Casting?
**Type Casting** is the process of converting data from one type to another type. It allows us to convert values between different data types in Java.

### Simple Definition
- **Type Casting** = Converting data from one type to another type
- Can be applied to both **primitive data types** and **objects**
- Essential concept for flexible programming

### Key Points
- Type casting is used when you need to convert data types
- Java supports type casting for both primitive types and objects
- There are specific rules and limitations for each type of casting

---

## Types of Type Casting

### Two Main Types of Type Casting

| Type | Also Called | Direction | Process | Example |
|------|-------------|-----------|---------|---------|
| **Upcasting** | Widening | Smaller → Larger | Automatic | int → long |
| **Downcasting** | Narrowing | Larger → Smaller | Manual | long → int |

### Upcasting (Widening)
- **Definition**: Converting data from smaller type to larger type
- **Process**: Automatic (no explicit casting needed)
- **Safety**: Safe operation, no data loss
- **Example**: Storing int value in long variable

### Downcasting (Narrowing)
- **Definition**: Converting data from larger type to smaller type
- **Process**: Manual (explicit casting required)
- **Safety**: Risky operation, possible data loss
- **Example**: Storing long value in int variable

---

## Primitive Type Casting

### Data Type Size Hierarchy
```
byte (1 byte) → short (2 bytes) → int (4 bytes) → long (8 bytes)
float (4 bytes) → double (8 bytes)
```

### Upcasting Examples (Automatic)

#### Example 1: Integer to Long
```java
public class UpcastingExample {
    public static void main(String[] args) {
        // Upcasting - Automatic process
        int intValue = 100;
        long longValue = intValue;  // Smaller to larger - automatic
        
        System.out.println("Integer value: " + intValue);
        System.out.println("Long value: " + longValue);
    }
}
```

**Output:**
```
Integer value: 100
Long value: 100
```

#### Example 2: Float to Double
```java
public class FloatToDoubleExample {
    public static void main(String[] args) {
        // Upcasting - Float to Double
        float floatValue = 10.5f;  // Note: 'f' literal for float
        double doubleValue = floatValue;  // Automatic conversion
        
        System.out.println("Float value: " + floatValue);
        System.out.println("Double value: " + doubleValue);
    }
}
```

**Output:**
```
Float value: 10.5
Double value: 10.5
```

### Downcasting Examples (Manual)

#### Example 1: Long to Integer
```java
public class DowncastingExample {
    public static void main(String[] args) {
        // Downcasting - Manual process
        long longValue = 123456789L;
        int intValue = (int) longValue;  // Explicit casting required
        
        System.out.println("Long value: " + longValue);
        System.out.println("Integer value: " + intValue);
    }
}
```

#### Example 2: Double to Float
```java
public class DoubleToFloatExample {
    public static void main(String[] args) {
        // Downcasting with potential data loss
        double doubleValue = 125.55;
        float floatValue = (float) doubleValue;  // Manual casting
        
        System.out.println("Double value: " + doubleValue);
        System.out.println("Float value: " + floatValue);
    }
}
```

### Upcasting vs Downcasting Comparison

| Aspect | Upcasting | Downcasting |
|--------|-----------|-------------|
| **Process** | Automatic | Manual (explicit) |
| **Syntax** | `larger = smaller;` | `smaller = (type) larger;` |
| **Data Loss** | No data loss | Possible data loss |
| **Safety** | Always safe | Risky operation |
| **Example** | `long l = intValue;` | `int i = (int) longValue;` |

### Mixed Type Examples

#### Integer to Double (Upcasting)
```java
public class IntegerToDoubleExample {
    public static void main(String[] args) {
        int i = 100;
        double d = i;  // Automatic upcasting
        
        System.out.println("Integer: " + i);
        System.out.println("Double: " + d);  // Output: 100.0
    }
}
```

#### Double to Integer (Downcasting)
```java
public class DoubleToIntegerExample {
    public static void main(String[] args) {
        double d = 10.5;
        int i = (int) d;  // Manual downcasting - decimal part lost
        
        System.out.println("Double: " + d);
        System.out.println("Integer: " + i);  // Output: 10 (decimal part truncated)
    }
}
```

---

## Object Type Casting

### Basic Concept
Object type casting works with class hierarchies and inheritance relationships. It follows the same upcasting and downcasting principles but with additional rules.

### Class Hierarchy Example
```java
// Parent class
class Parent {
    String name = "John";
    
    void m1() {
        System.out.println("This is m1 from Parent");
    }
}

// Child class
class Child extends Parent {
    int id = 123;
    
    void m2() {
        System.out.println("This is m2 from Child");
    }
}
```

### Object Creation Approaches

#### Approach 1: Direct Object Creation
```java
public class DirectObjectCreation {
    public static void main(String[] args) {
        // Both object and reference variable are of Child type
        Child c = new Child();
        
        // Can access everything from both Parent and Child
        System.out.println(c.name);  // From Parent
        c.m1();                      // From Parent
        System.out.println(c.id);    // From Child
        c.m2();                      // From Child
    }
}
```

#### Approach 2: Upcasting (Child object in Parent variable)
```java
public class UpcastingObjectExample {
    public static void main(String[] args) {
        // Upcasting - Child object stored in Parent variable
        Parent p = new Child();  // Automatic upcasting
        
        // Can access only Parent class members
        System.out.println(p.name);  // ✅ Accessible (from Parent)
        p.m1();                      // ✅ Accessible (from Parent)
        
        // System.out.println(p.id);  // ❌ Error - not accessible
        // p.m2();                     // ❌ Error - not accessible
    }
}
```

### Upcasting Benefits and Limitations

#### Benefits
- **Polymorphism**: Enables polymorphic behavior
- **Flexibility**: Parent reference can hold any child object
- **Generic Programming**: Write code that works with parent type

#### Limitations
- **Limited Access**: Can only access parent class members
- **Child Features Hidden**: Cannot access child-specific methods/variables

### Downcasting Example
```java
public class DowncastingObjectExample {
    public static void main(String[] args) {
        // First create parent reference with child object
        Parent p = new Child();  // Upcasting
        
        // Now downcast to access child features
        Child c = (Child) p;  // Manual downcasting
        
        // Now can access everything
        System.out.println(c.name);  // From Parent
        c.m1();                      // From Parent
        System.out.println(c.id);    // From Child
        c.m2();                      // From Child
    }
}
```

---

## Three Rules for Object Type Casting

### Type Casting Expression Format
```java
A a = (C) d;
```
Where:
- **A**: Target class type
- **a**: Reference variable
- **C**: Casting type
- **d**: Source variable

### Rule 1: Conversion Validity
**Rule**: There must be some relationship between C and D (casting type and source variable type).

#### Valid Example
```java
// Animal and Cat have parent-child relationship
Animal a = new Dog();
Cat c = (Cat) a;  // ✅ Valid conversion (both related to Animal)
```

#### Invalid Example
```java
// Dog and Cat have no direct relationship
Dog d = new Dog();
Cat c = (Cat) d;  // ❌ Invalid - compile-time error
```

### Rule 2: Assignment Validity
**Rule**: C must be either same as A or child of A (after conversion, assignment should be valid).

#### Valid Example
```java
Animal a = new Dog();
Dog d = (Dog) a;  // ✅ Valid - Dog object assigned to Dog variable
```

#### Invalid Example
```java
Animal a = new Dog();
Cat c = (Cat) a;  // ❌ Invalid - Dog object cannot be assigned to Cat variable
```

### Rule 3: Runtime Object Compatibility
**Rule**: The underlying object of D must be either same or child class of C.

#### Valid Example
```java
Animal a = new Dog();  // Underlying object is Dog
Dog d = (Dog) a;       // ✅ Valid - Dog object cast to Dog type
```

#### Invalid Example
```java
Animal a = new Dog();  // Underlying object is Dog
Cat c = (Cat) a;       // ❌ Invalid - Dog object cannot be cast to Cat
                       // Runtime ClassCastException
```

### Complete Example with All Rules

#### Class Hierarchy
```java
class Animal { }
class Dog extends Animal { }
class Cat extends Animal { }
```

#### Rule Validation Examples
```java
public class TypeCastingRulesExample {
    public static void main(String[] args) {
        // Example 1: All rules satisfied ✅
        Animal a1 = new Dog();
        Dog d1 = (Dog) a1;
        // Rule 1: Dog and Animal have relationship ✅
        // Rule 2: Dog assigned to Dog variable ✅  
        // Rule 3: Underlying object (Dog) matches cast type (Dog) ✅
        
        // Example 2: Rule 3 fails ❌
        Animal a2 = new Dog();
        // Cat c2 = (Cat) a2;  // Runtime ClassCastException
        // Rule 1: Cat and Animal have relationship ✅
        // Rule 2: Cat assigned to Cat variable ✅
        // Rule 3: Underlying object (Dog) doesn't match cast type (Cat) ❌
        
        // Example 3: Rule 1 fails ❌
        Dog d3 = new Dog();
        // Cat c3 = (Cat) d3;  // Compile-time error
        // Rule 1: Cat and Dog have no relationship ❌
    }
}
```

### Error Types Based on Rule Failures

| Rule Failed | Error Type | When Occurs |
|-------------|------------|-------------|
| **Rule 1** | Compile-time error | No relationship between types |
| **Rule 2** | Compile-time error | Invalid assignment |
| **Rule 3** | Runtime error (ClassCastException) | Object type mismatch |

---

## Predefined Classes Type Casting

### Working with Built-in Java Classes

#### Example 1: Object to String
```java
public class ObjectToStringExample {
    public static void main(String[] args) {
        // Rule validation for Object to String casting
        Object o = new String("Welcome");
        String s = (String) o;
        
        // Rule 1: String and Object have relationship ✅
        // Rule 2: String assigned to String variable ✅
        // Rule 3: Underlying object (String) matches cast type (String) ✅
        
        System.out.println("String value: " + s);  // Output: Welcome
    }
}
```

#### Example 2: Invalid Casting
```java
public class InvalidCastingExample {
    public static void main(String[] args) {
        Object o = new String("Welcome");
        
        // This will cause ClassCastException at runtime
        // StringBuffer sb = (StringBuffer) o;  // ❌ Runtime error
        
        // Rule 1: StringBuffer and Object have relationship ✅
        // Rule 2: StringBuffer assigned to StringBuffer variable ✅
        // Rule 3: Underlying object (String) doesn't match cast type (StringBuffer) ❌
    }
}
```

### Multiple Examples with Rule Analysis

#### Example Set 1: Object and String Operations
```java
public class PredefinedClassCasting {
    public static void main(String[] args) {
        // Valid casting
        Object o1 = new String("Hello");
        String s1 = (String) o1;  // ✅ All rules satisfied
        System.out.println("Valid casting: " + s1);
        
        // Invalid casting (would cause runtime error)
        Object o2 = new String("World");
        // StringBuffer sb = (StringBuffer) o2;  // ❌ ClassCastException
        
        // Direct assignment (no casting needed)
        String s2 = new String("Direct");
        Object o3 = s2;  // ✅ Upcasting - automatic
        System.out.println("Upcasting: " + o3);
    }
}
```

---

## When to Use Different Approaches

### Scenario-Based Usage

#### Scenario 1: Known Object Type
```java
// When you know exactly what type of object you're working with
Child c = new Child();  // Direct approach
// Use when: You need access to all child-specific features
```

#### Scenario 2: Unknown Object Type at Runtime
```java
// When you don't know the exact type at compile time
Parent p = getObjectFromSomewhere();  // Could return any child type
// Use when: Working with polymorphic collections or generic methods
```

### Real-World Example: Array with Mixed Data
```java
public class MixedDataExample {
    public static void main(String[] args) {
        // Array containing different types of data
        Object[] data = {
            100,           // Integer
            25.5,          // Double  
            'A',           // Character
            "Hello",       // String
            true           // Boolean
        };
        
        // Processing unknown data types
        for (int i = 0; i < data.length; i++) {
            Object item = data[i];  // Generic Object reference
            
            // Check type and cast accordingly
            if (item instanceof String) {
                String s = (String) item;
                System.out.println("String: " + s.toUpperCase());
            } else if (item instanceof Integer) {
                Integer num = (Integer) item;
                System.out.println("Integer: " + (num * 2));
            } else if (item instanceof Double) {
                Double d = (Double) item;
                System.out.println("Double: " + (d + 10));
            } else {
                System.out.println("Other type: " + item);
            }
        }
    }
}
```

### When to Use Parent Reference vs Child Reference

| Use Parent Reference When | Use Child Reference When |
|---------------------------|--------------------------|
| You don't know exact object type | You know exact object type |
| Working with polymorphic collections | Need access to child-specific features |
| Writing generic/flexible code | Performance is critical |
| Following polymorphism principles | Simple, straightforward operations |

---

## Practice Examples

### Practice 1: Basic Type Casting Rules
Analyze the following code and determine if it's valid:

```java
class Vehicle { }
class Car extends Vehicle { }
class Bike extends Vehicle { }

public class Practice1 {
    public static void main(String[] args) {
        // Analyze each statement
        Vehicle v1 = new Car();        // Statement 1
        Car c1 = (Car) v1;            // Statement 2
        
        Vehicle v2 = new Car();        // Statement 3  
        Bike b1 = (Bike) v2;          // Statement 4
        
        Car c2 = new Car();           // Statement 5
        Bike b2 = (Bike) c2;          // Statement 6
    }
}
```

**Analysis:**
- Statement 1: ✅ Valid (upcasting)
- Statement 2: ✅ Valid (all rules satisfied)
- Statement 3: ✅ Valid (upcasting)
- Statement 4: ❌ Runtime error (Rule 3 fails)
- Statement 5: ✅ Valid (direct creation)
- Statement 6: ❌ Compile error (Rule 1 fails)

### Practice 2: Predefined Classes
```java
public class Practice2 {
    public static void main(String[] args) {
        Object o1 = new String("Java");
        String s1 = (String) o1;           // Valid?
        
        Object o2 = new String("Programming");
        StringBuffer sb1 = (StringBuffer) o2;  // Valid?
        
        String s2 = new String("Learning");
        Object o3 = s2;                    // Valid?
    }
}
```

**Analysis:**
- Line 3: ✅ Valid (all rules satisfied)
- Line 6: ❌ Runtime error (underlying object is String, not StringBuffer)
- Line 9: ✅ Valid (automatic upcasting)

### Practice 3: Complex Hierarchy
```java
class A { }
class B extends A { }
class C extends B { }

public class Practice3 {
    public static void main(String[] args) {
        A a1 = new B();    // Valid?
        A a2 = new C();    // Valid?
        B b1 = new C();    // Valid?
        
        A a3 = new C();
        B b2 = (B) a3;     // Valid?
        C c1 = (C) a3;     // Valid?
        
        B b3 = new B();
        C c2 = (C) b3;     // Valid?
    }
}
```

**Analysis:**
- Line 5: ✅ Valid (B is child of A)
- Line 6: ✅ Valid (C is grandchild of A)
- Line 7: ✅ Valid (C is child of B)
- Line 10: ✅ Valid (underlying object C can be cast to B)
- Line 11: ✅ Valid (underlying object C matches cast type)
- Line 14: ❌ Runtime error (underlying object B cannot be cast to C)

---

## Real-World Applications

### Application 1: Polymorphic Collections
```java
import java.util.ArrayList;
import java.util.List;

class Shape {
    void draw() {
        System.out.println("Drawing a shape");
    }
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing a circle");
    }
    
    void calculateArea() {
        System.out.println("Calculating circle area");
    }
}

class Rectangle extends Shape {
    void draw() {
        System.out.println("Drawing a rectangle");
    }
    
    void calculatePerimeter() {
        System.out.println("Calculating rectangle perimeter");
    }
}

public class PolymorphicCollectionExample {
    public static void main(String[] args) {
        // Using parent reference for polymorphism
        List<Shape> shapes = new ArrayList<>();
        shapes.add(new Circle());
        shapes.add(new Rectangle());
        shapes.add(new Circle());
        
        // Process all shapes polymorphically
        for (Shape shape : shapes) {
            shape.draw();  // Polymorphic method call
            
            // Type checking and casting for specific operations
            if (shape instanceof Circle) {
                Circle circle = (Circle) shape;
                circle.calculateArea();
            } else if (shape instanceof Rectangle) {
                Rectangle rectangle = (Rectangle) shape;
                rectangle.calculatePerimeter();
            }
        }
    }
}
```

### Application 2: Generic Data Processing
```java
public class GenericDataProcessor {
    
    // Method that accepts any type of object
    public static void processData(Object data) {
        System.out.println("Processing: " + data);
        
        // Type-specific processing
        if (data instanceof String) {
            String str = (String) data;
            System.out.println("String length: " + str.length());
        } else if (data instanceof Integer) {
            Integer num = (Integer) data;
            System.out.println("Number doubled: " + (num * 2));
        } else if (data instanceof Double) {
            Double decimal = (Double) data;
            System.out.println("Decimal rounded: " + Math.round(decimal));
        }
    }
    
    public static void main(String[] args) {
        // Process different types of data
        processData("Hello World");
        processData(42);
        processData(3.14159);
        processData(true);
    }
}
```

### Application 3: Framework Design Pattern
```java
// Simulating a simple framework design
abstract class DatabaseConnection {
    abstract void connect();
    abstract void disconnect();
}

class MySQLConnection extends DatabaseConnection {
    void connect() {
        System.out.println("Connecting to MySQL database");
    }
    
    void disconnect() {
        System.out.println("Disconnecting from MySQL");
    }
    
    void mysqlSpecificMethod() {
        System.out.println("MySQL specific operation");
    }
}

class PostgreSQLConnection extends DatabaseConnection {
    void connect() {
        System.out.println("Connecting to PostgreSQL database");
    }
    
    void disconnect() {
        System.out.println("Disconnecting from PostgreSQL");
    }
    
    void postgresSpecificMethod() {
        System.out.println("PostgreSQL specific operation");
    }
}

public class DatabaseFramework {
    // Factory method returns generic connection
    public static DatabaseConnection createConnection(String type) {
        if (type.equals("mysql")) {
            return new MySQLConnection();
        } else if (type.equals("postgresql")) {
            return new PostgreSQLConnection();
        }
        return null;
    }
    
    public static void main(String[] args) {
        // Generic reference, specific implementation
        DatabaseConnection conn = createConnection("mysql");
        
        // Common operations
        conn.connect();
        
        // Specific operations require casting
        if (conn instanceof MySQLConnection) {
            MySQLConnection mysqlConn = (MySQLConnection) conn;
            mysqlConn.mysqlSpecificMethod();
        }
        
        conn.disconnect();
    }
}
```

---

## Key Takeaways

### Type Casting Fundamentals
- **Upcasting**: Smaller to larger type (automatic, safe)
- **Downcasting**: Larger to smaller type (manual, risky)
- **Applies to**: Both primitive types and objects

### Object Type Casting Rules
1. **Rule 1**: Conversion validity - types must have relationship
2. **Rule 2**: Assignment validity - compatible assignment after casting
3. **Rule 3**: Runtime compatibility - underlying object must match cast type

### Best Practices
- Use **instanceof** operator before downcasting objects
- Prefer **upcasting** for polymorphic behavior
- Use **specific types** when you know exact object type
- Use **generic types** (Object/Parent) when type is unknown at runtime

### Error Prevention
- **Compile-time errors**: Rule 1 and Rule 2 violations
- **Runtime errors**: Rule 3 violations (ClassCastException)
- Always validate object types before casting in production code

### When to Use Type Casting
- **Polymorphic collections**: Store different child objects in parent references
- **Generic programming**: Write flexible code that works with multiple types
- **Framework development**: Create extensible and maintainable systems
- **Data processing**: Handle unknown data types at runtime

---

**Next Session Preview**: We'll explore **Collections Framework** - ArrayList, HashMap, HashSet, and their practical applications in data management, along with iterators and advanced collection operations for building scalable Java applications.