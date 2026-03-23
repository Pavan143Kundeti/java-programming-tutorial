# 11 - Methods and Constructors in Java

## Table of Contents
1. [Introduction to Methods](#introduction-to-methods)
2. [Types of Methods](#types-of-methods)
3. [Four Categories of Methods](#four-categories-of-methods)
4. [Creating and Calling Methods](#creating-and-calling-methods)
5. [Storing Data in Variables](#storing-data-in-variables)
6. [Introduction to Constructors](#introduction-to-constructors)
7. [Method vs Constructor Comparison](#method-vs-constructor-comparison)
8. [Types of Constructors](#types-of-constructors)

---

## Introduction to Methods

### What is a Method?
**A method is a block or group of statements that performs a specific task.**

### Why Use Methods?
1. **Avoid code repetition** - Write once, use multiple times
2. **Better organization** - Group related functionality
3. **Reusability** - Same method can be called from different places
4. **Maintainability** - Changes in one place affect all usages

### Method Execution
- **Methods are created inside classes**
- **Methods are called through objects**
- **Method executes only when called**
- **Logic inside method runs when invoked**

---

## Types of Methods

### 1. Built-in Methods
**Methods already available in Java classes.**

#### Examples from String Class:
```java
String s = "Welcome";

// length() method - no parameters, returns value
int len = s.length();

// substring() method - takes parameters, returns value  
String sub = s.substring(2, 5);

// charAt() method - takes parameter, returns value
char ch = s.charAt(0);
```

### 2. User-Defined Methods
**Methods created by programmers according to requirements.**

```java
// Example of user-defined method
void display() {
    System.out.println("Hello World");
}
```

---

## Four Categories of Methods

### Category 1: No Parameters, No Return Value
**Method doesn't take input and doesn't return output.**

### Category 2: No Parameters, Returns Value
**Method doesn't take input but returns output.**

### Category 3: Takes Parameters, No Return Value
**Method takes input but doesn't return output.**

### Category 4: Takes Parameters, Returns Value
**Method takes input and returns output.**

---

## Creating and Calling Methods

### Example Class: Greetings

#### Greetings.java
```java
package day11;

public class Greetings {
    
    // Category 1: No parameters, no return value
    void m1() {
        System.out.println("Hello");
    }
    
    // Category 2: No parameters, returns value
    String m2() {
        return "Hello, how are you?";
    }
    
    // Category 3: Takes parameters, no return value
    void m3(String name) {
        System.out.println("Hello " + name);
    }
    
    // Category 4: Takes parameters, returns value
    String m4(String name) {
        return "Hello " + name;
    }
}
```

#### GreetingsMain.java
```java
package day11;

public class GreetingsMain {
    public static void main(String[] args) {
        // Create object
        Greetings gr = new Greetings();
        
        // Category 1: No parameters, no return value
        gr.m1(); // Output: Hello
        
        // Category 2: No parameters, returns value
        String result = gr.m2();
        System.out.println(result); // Output: Hello, how are you?
        
        // Category 3: Takes parameters, no return value
        gr.m3("John"); // Output: Hello John
        
        // Category 4: Takes parameters, returns value
        String greeting = gr.m4("Mary");
        System.out.println(greeting); // Output: Hello Mary
    }
}
```

### Method Components Explained

#### Return Types
```java
void methodName()     // No return value
int methodName()      // Returns integer
String methodName()   // Returns string
double methodName()   // Returns double
```

#### Parameters
```java
void method()                    // No parameters
void method(int x)              // One parameter
void method(int x, String y)    // Multiple parameters
```

#### Method Calling
```java
// For void methods (no return value)
object.methodName();

// For methods that return values
dataType variable = object.methodName();
// OR
System.out.println(object.methodName());
```

---

## Storing Data in Variables

### Three Approaches to Store Data in Class Variables

#### Student.java
```java
package day11;

public class Student {
    // Class variables
    int sId;
    String sName;
    char grade;
    
    // Method to print student data
    void printStudentData() {
        System.out.println(sId + " " + sName + " " + grade);
    }
    
    // Method to set student data (Approach 2)
    void setStudentData(int id, String name, char gr) {
        sId = id;        // Assign parameter to class variable
        sName = name;    // Assign parameter to class variable
        grade = gr;      // Assign parameter to class variable
    }
    
    // Constructor (Approach 3)
    Student(int id, String name, char gr) {
        sId = id;
        sName = name;
        grade = gr;
    }
}
```

### Approach 1: Using Object Reference Variable

```java
package day11;

public class StudentMain {
    public static void main(String[] args) {
        // Approach 1: Direct access through object
        Student stu = new Student();
        
        // Directly assign data to variables
        stu.sId = 101;
        stu.sName = "David";
        stu.grade = 'A';
        
        // Print data
        stu.printStudentData(); // Output: 101 David A
    }
}
```

### Approach 2: Using Method

```java
package day11;

public class StudentMain {
    public static void main(String[] args) {
        // Approach 2: Using method to set data
        Student stu = new Student();
        
        // Call method to set data
        stu.setStudentData(102, "Smith", 'B');
        
        // Print data
        stu.printStudentData(); // Output: 102 Smith B
    }
}
```

### Approach 3: Using Constructor

```java
package day11;

public class StudentMain {
    public static void main(String[] args) {
        // Approach 3: Using constructor
        Student stu = new Student(103, "Johnson", 'A');
        
        // Print data (constructor already set the data)
        stu.printStudentData(); // Output: 103 Johnson A
    }
}
```

### Variable Types

#### Class Variables vs Local Variables
```java
public class Student {
    int sId;        // Class variable (accessible throughout class)
    String sName;   // Class variable (accessible throughout class)
    
    void setStudentData(int id, String name) {
        // id and name are local variables (only accessible in this method)
        sId = id;      // Assigning local variable to class variable
        sName = name;  // Assigning local variable to class variable
    }
}
```

**Key Differences:**
- **Class Variables:** Accessible throughout the class, in all methods
- **Local Variables:** Accessible only within the method where declared

---

## Introduction to Constructors

### What is a Constructor?
**A constructor is a special method used to initialize objects when they are created.**

### Constructor Characteristics
1. **Name same as class name**
2. **No return type** (not even void)
3. **Automatically called** when object is created
4. **Used for initializing data** in variables

### Constructor Syntax
```java
public class ClassName {
    // Constructor syntax
    ClassName() {
        // Initialization code
    }
}
```

### Constructor Example

#### Student.java with Constructor
```java
package day11;

public class Student {
    int sId;
    String sName;
    char grade;
    
    // Constructor
    Student(int id, String name, char gr) {
        sId = id;
        sName = name;
        grade = gr;
    }
    
    void printStudentData() {
        System.out.println(sId + " " + sName + " " + grade);
    }
}
```

#### Using Constructor
```java
package day11;

public class StudentMain {
    public static void main(String[] args) {
        // Constructor automatically called when object is created
        Student stu = new Student(101, "David", 'A');
        
        // Data is already initialized by constructor
        stu.printStudentData(); // Output: 101 David A
    }
}
```

### How Constructor Works
1. **Object creation:** `new Student(101, "David", 'A')`
2. **Constructor automatically invoked** with passed parameters
3. **Data assigned** to class variables
4. **Object ready** to use with initialized data

---

## Method vs Constructor Comparison

| Aspect | Method | Constructor |
|--------|--------|-------------|
| **Name** | Can be anything | Must be same as class name |
| **Return Type** | May or may not return value | Never returns value (not even void) |
| **Parameters** | Can take parameters | Can take parameters |
| **Invocation** | Called explicitly through object | Automatically called during object creation |
| **Purpose** | Implement logic/operations | Initialize data in variables |
| **When to use** | For business logic, calculations | For setting initial values |

### Detailed Comparison

#### Method Example
```java
// Method characteristics
void displayMessage() {        // Name can be anything
    System.out.println("Hi");  // Can contain any logic
}                              // void = no return value

// Method calling
object.displayMessage();       // Explicit call required
```

#### Constructor Example
```java
// Constructor characteristics
Student(String name) {         // Name same as class
    this.name = name;          // Only for initialization
}                              // No return type specified

// Constructor calling
Student s = new Student("John"); // Automatic call during object creation
```

### When to Use Which?

#### Use Methods When:
- **Implementing business logic**
- **Performing calculations**
- **Processing data**
- **Need to call multiple times**
- **Need return values**

#### Use Constructors When:
- **Initializing object data**
- **Setting up initial state**
- **Ensuring object is ready to use**
- **One-time setup during object creation**

---

## Types of Constructors

### 1. Default Constructor
**Constructor with no parameters.**

```java
package day11;

public class ConstructorDemo {
    int x, y;
    
    // Default constructor
    ConstructorDemo() {
        x = 100;  // Fixed values
        y = 200;
    }
    
    void sum() {
        System.out.println("Sum: " + (x + y));
    }
}
```

### 2. Parameterized Constructor
**Constructor with parameters.**

```java
package day11;

public class ConstructorDemo {
    int x, y;
    
    // Parameterized constructor
    ConstructorDemo(int a, int b) {
        x = a;    // Dynamic values
        y = b;
    }
    
    void sum() {
        System.out.println("Sum: " + (x + y));
    }
}
```

### Using Both Types of Constructors

```java
package day11;

public class ConstructorDemo {
    int x, y;
    
    // Default constructor
    ConstructorDemo() {
        x = 100;
        y = 200;
    }
    
    // Parameterized constructor
    ConstructorDemo(int a, int b) {
        x = a;
        y = b;
    }
    
    void sum() {
        System.out.println("Sum: " + (x + y));
    }
    
    public static void main(String[] args) {
        // Using default constructor
        ConstructorDemo cd1 = new ConstructorDemo();
        cd1.sum(); // Output: Sum: 300
        
        // Using parameterized constructor
        ConstructorDemo cd2 = new ConstructorDemo(10, 20);
        cd2.sum(); // Output: Sum: 30
    }
}
```

### Constructor Selection Rules
- **No parameters passed:** Default constructor is called
- **Parameters passed:** Parameterized constructor is called
- **Must match parameter count and types**

---

## Key Concepts Summary

### Method Fundamentals
1. **Block of code** that performs specific task
2. **Called through objects** explicitly
3. **Can take parameters** and return values
4. **Used for implementing logic**

### Constructor Fundamentals
1. **Special method** for object initialization
2. **Same name as class**
3. **No return type**
4. **Automatically called** during object creation
5. **Used for setting initial values**

### Data Storage Approaches
1. **Direct access:** Through object reference variable
2. **Method approach:** Using setter methods
3. **Constructor approach:** During object creation (preferred)

### Best Practices
1. **Use constructors** for initialization
2. **Use methods** for business logic
3. **Meaningful names** for methods
4. **Proper parameter ordering**
5. **Consistent return types**

### Important Notes
- **Constructor name must match class name exactly**
- **One object can call multiple methods**
- **One object creation calls only one constructor**
- **Parameters must match in count and type**
- **Local variables exist only within method scope**
- **Class variables accessible throughout class**

---

## Common Interview Questions

### 1. What is the difference between method and constructor?
**Answer:** Methods can have any name, may return values, called explicitly. Constructors have same name as class, never return values, called automatically during object creation.

### 2. Can we have multiple constructors in a class?
**Answer:** Yes, we can have multiple constructors with different parameters (constructor overloading).

### 3. What happens if we don't write any constructor?
**Answer:** Java provides a default no-argument constructor automatically.

### 4. Can constructors return values?
**Answer:** No, constructors never return values, not even void.

### 5. How many ways can we initialize variables in a class?
**Answer:** Three ways - direct access through object, using methods, using constructors.

---

*This completes Session 11 on Methods and Constructors. These concepts are fundamental to Object-Oriented Programming and form the basis for more advanced topics like method overloading, inheritance, and polymorphism!*