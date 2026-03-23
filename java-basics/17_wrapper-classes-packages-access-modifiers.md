# Session 17: Wrapper Classes, Packages, and Access Modifiers

## Table of Contents
1. [Introduction to Wrapper Classes](#introduction-to-wrapper-classes)
2. [Data Conversion Methods](#data-conversion-methods)
3. [Wrapper Classes in Collections](#wrapper-classes-in-collections)
4. [Packages in Java](#packages-in-java)
5. [Access Modifiers](#access-modifiers)
6. [Practice Assignments](#practice-assignments)

---

## Introduction to Wrapper Classes

### What are Wrapper Classes?
**Wrapper Classes** are special classes in Java that provide object representation for primitive data types.

### Data Storage Formats in Java

| Format | Example | Usage |
|--------|---------|-------|
| **Primitive** | `int x = 100;` | Direct value storage |
| **Object** | `Integer x = new Integer(100);` | Object-based storage |

### Why Wrapper Classes?

**String Example:**
```java
// Two ways to create String
String s1 = "Welcome";           // Primitive-like
String s2 = new String("Welcome"); // Object format
```

**Primitive Types Need Object Format:**
```java
// Primitive format
int x = 100;

// Object format using Wrapper Class
Integer x = new Integer(100);  // Deprecated in newer Java versions
Integer x = Integer.valueOf(100); // Recommended approach
```

### Wrapper Classes for All Primitive Types

| Primitive Type | Wrapper Class | Example |
|----------------|---------------|---------|
| `byte` | `Byte` | `Byte b = Byte.valueOf((byte)10);` |
| `short` | `Short` | `Short s = Short.valueOf((short)100);` |
| `int` | `Integer` | `Integer i = Integer.valueOf(100);` |
| `long` | `Long` | `Long l = Long.valueOf(1000L);` |
| `float` | `Float` | `Float f = Float.valueOf(10.5f);` |
| `double` | `Double` | `Double d = Double.valueOf(10.5);` |
| `char` | `Character` | `Character c = Character.valueOf('A');` |
| `boolean` | `Boolean` | `Boolean b = Boolean.valueOf(true);` |

### Key Points About Wrapper Classes

| Concept | Description |
|---------|-------------|
| **Special Classes** | Only for primitive types, not regular classes |
| **Built-in Methods** | Contain methods for data conversion |
| **Object Format** | Allow primitive data to be treated as objects |
| **Collections Support** | Required for using primitives in collections |

---

## Data Conversion Methods

### Why Data Conversion is Needed?

**Real-World Scenarios:**

**Scenario 1: Price Calculation**
```java
// Prices received as strings from web application
String price1 = "150.50";
String price2 = "120.50";

// Cannot perform arithmetic on strings
// String total = price1 + price2;  // Results in "150.50120.50" (concatenation)

// Need to convert to numbers first
double num1 = Double.parseDouble(price1);
double num2 = Double.parseDouble(price2);
double total = num1 + num2;  // Results in 271.0 (addition)
```

**Scenario 2: Web Automation**
```java
// Phone number as integer
int phoneNumber = 1234567890;

// Text fields accept only String format
// webElement.sendKeys(phoneNumber);  // Error! Cannot pass int to text field

// Need to convert to String
webElement.sendKeys(String.valueOf(phoneNumber));  // Works!
```

### Data Conversion Types

| Conversion Type | Methods Used | Use Cases |
|----------------|--------------|-----------|
| **String → Primitive** | `parseInt()`, `parseDouble()`, etc. | Reading data from UI, files |
| **Primitive → String** | `String.valueOf()` | Sending data to UI, display |
| **Primitive → Primitive** | Not directly possible | Use String as intermediate |

---

### String to Primitive Conversions

**Prerequisites for Conversion:**
```java
// ✅ Valid - numeric content in string
String validNumber = "123";
int result = Integer.parseInt(validNumber);  // Works

// ❌ Invalid - non-numeric content
String invalidNumber = "Welcome";
int result = Integer.parseInt(invalidNumber);  // Throws NumberFormatException
```

### String to Integer
```java
public class StringToInteger {
    public static void main(String[] args) {
        // String values containing numbers
        String s1 = "10";
        String s2 = "20";
        
        // Convert strings to integers
        int num1 = Integer.parseInt(s1);
        int num2 = Integer.parseInt(s2);
        
        // Now can perform arithmetic operations
        int sum = num1 + num2;
        System.out.println("Sum: " + sum);  // Output: Sum: 30
        
        // Direct calculation in one line
        System.out.println("Direct: " + (Integer.parseInt(s1) + Integer.parseInt(s2)));
    }
}
```

### String to Double
```java
public class StringToDouble {
    public static void main(String[] args) {
        String s1 = "10.5";
        String s2 = "20.5";
        
        // Convert strings to double
        double num1 = Double.parseDouble(s1);
        double num2 = Double.parseDouble(s2);
        
        double sum = num1 + num2;
        System.out.println("Sum: " + sum);  // Output: Sum: 31.0
    }
}
```

### String to Boolean
```java
public class StringToBoolean {
    public static void main(String[] args) {
        String s1 = "true";
        String s2 = "false";
        String s3 = "anything";
        
        boolean b1 = Boolean.parseBoolean(s1);  // true
        boolean b2 = Boolean.parseBoolean(s2);  // false
        boolean b3 = Boolean.parseBoolean(s3);  // false (anything other than "true")
        
        System.out.println("b1: " + b1);  // Output: b1: true
        System.out.println("b2: " + b2);  // Output: b2: false
        System.out.println("b3: " + b3);  // Output: b3: false
    }
}
```

### String to Character - Not Possible
```java
// ❌ This conversion is not possible
String s = "Hello";
// char c = Character.parseChar(s);  // No such method exists

// Why? String contains multiple characters, char holds only one
// Cannot convert multiple characters to single character
```

### Conversion Methods Summary

| Target Type | Wrapper Class | Method | Example |
|-------------|---------------|--------|---------|
| `int` | `Integer` | `parseInt(String)` | `Integer.parseInt("123")` |
| `double` | `Double` | `parseDouble(String)` | `Double.parseDouble("12.5")` |
| `float` | `Float` | `parseFloat(String)` | `Float.parseFloat("12.5f")` |
| `long` | `Long` | `parseLong(String)` | `Long.parseLong("123456")` |
| `boolean` | `Boolean` | `parseBoolean(String)` | `Boolean.parseBoolean("true")` |
| `char` | ❌ | Not Available | Cannot convert String to char |

---

### Primitive to String Conversions

**Universal Method: String.valueOf()**
- **One method for all primitive types**
- **Overloaded method** (Polymorphism concept)
- **Static method** - call directly from String class

```java
public class PrimitiveToString {
    public static void main(String[] args) {
        // Different primitive types
        int intValue = 10;
        double doubleValue = 10.5;
        char charValue = 'A';
        boolean boolValue = true;
        
        // Convert all to String using String.valueOf()
        String s1 = String.valueOf(intValue);    // "10"
        String s2 = String.valueOf(doubleValue); // "10.5"
        String s3 = String.valueOf(charValue);   // "A"
        String s4 = String.valueOf(boolValue);   // "true"
        
        System.out.println("Integer to String: " + s1);
        System.out.println("Double to String: " + s2);
        System.out.println("Character to String: " + s3);
        System.out.println("Boolean to String: " + s4);
    }
}
```

### Why Character to String is Possible?
```java
char c = 'A';           // Single character
String s = String.valueOf(c);  // "A" - String with single character

// String can contain single character or multiple characters
// So char → String is possible
// But String → char is not possible (multiple → single)
```

### Method Overloading in String.valueOf()
```java
// String.valueOf() is overloaded for different parameter types
String.valueOf(int i)       // For integer
String.valueOf(double d)    // For double
String.valueOf(char c)      // For character
String.valueOf(boolean b)   // For boolean
String.valueOf(char[] data) // For character array
// ... and more
```

---

## Wrapper Classes in Collections

### Why Wrapper Classes in Collections?

**ArrayList Example:**
```java
import java.util.ArrayList;

public class CollectionsExample {
    public static void main(String[] args) {
        // ❌ Cannot use primitive types in collections
        // ArrayList<int> list = new ArrayList<int>();  // Compilation error
        
        // ✅ Must use wrapper classes
        ArrayList<Integer> list = new ArrayList<Integer>();
        
        // Adding elements
        list.add(100);    // Auto-boxing: int → Integer
        list.add(200);
        list.add(300);
        
        // Accessing elements
        int value = list.get(0);  // Auto-unboxing: Integer → int
        System.out.println("First element: " + value);
        
        // Display all elements
        System.out.println("All elements: " + list);
    }
}
```

### Collections Require Object Types

| Collection Type | Primitive (❌) | Wrapper Class (✅) |
|----------------|----------------|-------------------|
| `ArrayList` | `ArrayList<int>` | `ArrayList<Integer>` |
| `HashSet` | `HashSet<double>` | `HashSet<Double>` |
| `HashMap` | `HashMap<int, String>` | `HashMap<Integer, String>` |

### Auto-boxing and Auto-unboxing

**Auto-boxing:** Automatic conversion from primitive to wrapper
```java
ArrayList<Integer> list = new ArrayList<>();
list.add(100);  // int 100 automatically converted to Integer object
```

**Auto-unboxing:** Automatic conversion from wrapper to primitive
```java
ArrayList<Integer> list = new ArrayList<>();
list.add(100);
int value = list.get(0);  // Integer object automatically converted to int
```

---

## Packages in Java

### What is a Package?
A **Package** is like a folder that organizes related classes and interfaces.

### Java Project Hierarchy
```
Project
├── Package 1
│   ├── Class1.java
│   ├── Class2.java
│   └── Class3.java
├── Package 2
│   ├── Class4.java
│   └── Class5.java
└── Package 3
    └── Class6.java
```

### Why Use Packages?

| Benefit | Description | Example |
|---------|-------------|---------|
| **Organization** | Group related classes together | All database classes in `com.company.database` |
| **Namespace** | Avoid naming conflicts | Two `User` classes in different packages |
| **Access Control** | Control visibility of classes | Package-private classes |
| **Maintenance** | Easier to find and maintain code | Separate packages for different modules |

### Types of Packages

| Type | Description | Examples |
|------|-------------|----------|
| **Built-in Packages** | Pre-defined by Java | `java.util`, `java.io`, `java.lang` |
| **User-defined Packages** | Created by developers | `com.company.project`, `day17` |

### Built-in Packages Examples

```java
import java.util.Arrays;    // For Arrays.toString()
import java.util.Scanner;   // For user input
import java.util.ArrayList; // For dynamic arrays

public class BuiltInPackagesExample {
    public static void main(String[] args) {
        // Using Arrays class from java.util package
        int[] arr = {1, 2, 3, 4, 5};
        System.out.println(Arrays.toString(arr));
        
        // Using Scanner class from java.util package
        Scanner scanner = new Scanner(System.in);
        
        // Using ArrayList class from java.util package
        ArrayList<String> list = new ArrayList<>();
    }
}
```

### Creating Sub-packages

**Sub-package Structure:**
```
day17
└── pack1
    ├── Class1.java
    └── subpack1
        └── Class2.java
```

**Creating Sub-package in Eclipse:**
1. Right-click on parent package
2. New → Package
3. Name: `parentpackage.subpackage` (e.g., `day17.pack1`)

### Import Statements

**Importing Specific Class:**
```java
import java.util.Scanner;  // Import only Scanner class
```

**Importing All Classes from Package:**
```java
import java.util.*;  // Import all classes from java.util package
```

**Importing User-defined Classes:**
```java
import day17.pack1.TestClass;  // Import TestClass from day17.pack1 package
```

---

## Access Modifiers

### What are Access Modifiers?
**Access Modifiers** define the scope and visibility of variables, methods, and classes.

### Four Types of Access Modifiers

| Access Modifier | Scope | Visibility |
|----------------|-------|------------|
| **private** | Class level | Only within the same class |
| **default** | Package level | Within the same package |
| **protected** | Project level | Within package + subclasses in other packages |
| **public** | Project level | Everywhere in the project |

### Access Levels Hierarchy

```
private < default < protected < public
(Most Restrictive)              (Least Restrictive)
```

### Project Structure for Examples
```
Project
├── day17.pack1
│   └── TestOne.java
└── day17.pack2
    └── TestTwo.java
```

---

### 1. Private Access Modifier

**TestOne.java (day17.pack1):**
```java
package day17.pack1;

public class TestOne {
    private int x = 100;        // Private variable
    
    private void m1() {         // Private method
        System.out.println("This is M1 from TestOne");
    }
    
    public void accessPrivateMembers() {
        // ✅ Can access private members within same class
        System.out.println("Private variable x: " + x);
        m1();  // Can call private method
    }
}
```

**TestTwo.java (day17.pack1) - Same Package:**
```java
package day17.pack1;

public class TestTwo {
    public static void main(String[] args) {
        TestOne t1 = new TestOne();
        
        // ❌ Cannot access private members from different class
        // System.out.println(t1.x);  // Compilation error
        // t1.m1();                   // Compilation error
        
        // ✅ Can access through public method
        t1.accessPrivateMembers();
    }
}
```

### 2. Default Access Modifier

**TestOne.java (day17.pack1):**
```java
package day17.pack1;

public class TestOne {
    int x = 100;        // Default variable (no modifier specified)
    
    void m1() {         // Default method (no modifier specified)
        System.out.println("This is M1 from TestOne");
    }
}
```

**TestTwo.java (day17.pack1) - Same Package:**
```java
package day17.pack1;

public class TestTwo {
    public static void main(String[] args) {
        TestOne t1 = new TestOne();
        
        // ✅ Can access default members within same package
        System.out.println("Default variable x: " + t1.x);
        t1.m1();
    }
}
```

**TestTwo.java (day17.pack2) - Different Package:**
```java
package day17.pack2;
import day17.pack1.TestOne;  // Import required for external class

public class TestTwo {
    public static void main(String[] args) {
        TestOne t1 = new TestOne();
        
        // ❌ Cannot access default members from different package
        // System.out.println(t1.x);  // Compilation error
        // t1.m1();                   // Compilation error
    }
}
```

### 3. Protected Access Modifier

**TestOne.java (day17.pack1):**
```java
package day17.pack1;

public class TestOne {
    protected int x = 100;        // Protected variable
    
    protected void m1() {         // Protected method
        System.out.println("This is M1 from TestOne");
    }
}
```

**TestTwo.java (day17.pack2) - Different Package with Inheritance:**
```java
package day17.pack2;
import day17.pack1.TestOne;

public class TestTwo extends TestOne {  // Inheritance required
    public static void main(String[] args) {
        // ❌ Cannot access directly
        // TestOne t1 = new TestOne();
        // System.out.println(t1.x);  // Error
        
        // ✅ Can access through inheritance
        TestTwo t2 = new TestTwo();
        System.out.println("Protected variable x: " + t2.x);
        t2.m1();
    }
}
```

### 4. Public Access Modifier

**TestOne.java (day17.pack1):**
```java
package day17.pack1;

public class TestOne {
    public int x = 100;        // Public variable
    
    public void m1() {         // Public method
        System.out.println("This is M1 from TestOne");
    }
}
```

**TestTwo.java (day17.pack2) - Different Package:**
```java
package day17.pack2;
import day17.pack1.TestOne;  // Import still required for external class

public class TestTwo {
    public static void main(String[] args) {
        TestOne t1 = new TestOne();
        
        // ✅ Can access public members directly from anywhere
        System.out.println("Public variable x: " + t1.x);
        t1.m1();
    }
}
```

### Access Modifiers Summary Table

| Modifier | Same Class | Same Package | Different Package (Subclass) | Different Package (Non-subclass) |
|----------|------------|--------------|------------------------------|----------------------------------|
| **private** | ✅ | ❌ | ❌ | ❌ |
| **default** | ✅ | ✅ | ❌ | ❌ |
| **protected** | ✅ | ✅ | ✅ | ❌ |
| **public** | ✅ | ✅ | ✅ | ✅ |

### When to Use Which Access Modifier?

| Access Modifier | Use Case | Example |
|----------------|----------|---------|
| **private** | Internal implementation details | Helper methods, internal variables |
| **default** | Package-level utilities | Classes used only within same package |
| **protected** | Inheritance-based access | Methods meant for subclasses |
| **public** | Public API, main methods | Public interfaces, main methods |

### Important Notes

1. **Import Statement**: Always required when using classes from different packages
2. **Default Keyword**: No need to write `default` - absence of modifier means default
3. **Class Access**: Classes can only be `public` or default (package-private)
4. **Automation Testing**: Usually everything is made `public` for simplicity

---

## Complete Example: Data Conversion in Web Automation

```java
import java.util.ArrayList;

public class WebAutomationExample {
    public static void main(String[] args) {
        // Scenario: Reading prices from web application
        // Prices are received as strings from UI
        ArrayList<String> pricesFromUI = new ArrayList<>();
        pricesFromUI.add("150.50");
        pricesFromUI.add("200.75");
        pricesFromUI.add("99.99");
        
        // Convert string prices to double for calculation
        ArrayList<Double> numericPrices = new ArrayList<>();
        double totalPrice = 0.0;
        
        for (String priceStr : pricesFromUI) {
            double price = Double.parseDouble(priceStr);  // String to double
            numericPrices.add(price);
            totalPrice += price;
        }
        
        System.out.println("Original prices (String): " + pricesFromUI);
        System.out.println("Converted prices (Double): " + numericPrices);
        System.out.println("Total price: $" + totalPrice);
        
        // Convert total back to string for display in UI
        String totalForDisplay = String.valueOf(totalPrice);
        System.out.println("Total for UI display: " + totalForDisplay);
        
        // Scenario: Sending phone number to text field
        long phoneNumber = 1234567890L;
        String phoneForUI = String.valueOf(phoneNumber);
        System.out.println("Phone number for text field: " + phoneForUI);
    }
}
```

---

## Practice Assignments

### Assignment 1: Price Calculator
Create a program that:
- Takes string prices: "25.50", "30.75", "15.25"
- Converts them to double and calculates total
- Applies 10% discount
- Converts final amount back to string for display

### Assignment 2: Data Type Converter
Create a utility class with methods:
- `stringToInt(String s)` - with exception handling
- `stringToDouble(String s)` - with exception handling
- `primitiveToString(Object obj)` - generic converter
- Test with valid and invalid inputs

### Assignment 3: Package Organization
Create a project structure:
- `com.company.utils` - utility classes
- `com.company.models` - data classes
- `com.company.main` - main application
- Demonstrate different access modifiers between packages

### Assignment 4: Collection with Wrapper Classes
Create a student management system:
- Use `ArrayList<Integer>` for student IDs
- Use `ArrayList<Double>` for grades
- Use `HashMap<Integer, String>` for ID-name mapping
- Implement methods to add, remove, and calculate average grades

### Assignment 5: Access Modifier Demonstration
Create classes showing all four access modifiers:
- Same class access
- Same package access
- Different package with inheritance
- Different package without inheritance
- Document what works and what doesn't

---

## Interview Questions

1. **What are wrapper classes? Why are they needed?**
2. **How do you convert String to int? What happens if String contains non-numeric data?**
3. **What is the difference between parseInt() and valueOf() methods?**
4. **Why can't we use primitive types in Collections?**
5. **What is auto-boxing and auto-unboxing?**
6. **What are packages in Java? What are the types of packages?**
7. **What are access modifiers? Explain all four types.**
8. **What is the difference between protected and default access modifiers?**
9. **Can we access private members of a class from outside the class?**
10. **When do we need import statements? Give examples.**

---

**Next Session Preview**: We'll explore **Exception Handling** - managing runtime errors gracefully, understanding try-catch blocks, different types of exceptions, and creating custom exceptions, followed by **Collections Framework** - ArrayList, HashMap, HashSet and their practical applications.