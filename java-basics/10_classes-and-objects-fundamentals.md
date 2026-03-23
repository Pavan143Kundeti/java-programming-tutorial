# 10 - Classes and Objects Fundamentals in Java

## Table of Contents
1. [Introduction to Object-Oriented Programming](#introduction-to-object-oriented-programming)
2. [What is a Class?](#what-is-a-class)
3. [What is an Object?](#what-is-an-object)
4. [Class vs Object Comparison](#class-vs-object-comparison)
5. [Creating Classes in Java](#creating-classes-in-java)
6. [Creating and Using Objects](#creating-and-using-objects)
7. [Separating Main Method](#separating-main-method)
8. [Practical Examples](#practical-examples)

---

## Introduction to Object-Oriented Programming

### What is Object-Oriented Programming (OOP)?
**Object-Oriented Programming is a programming paradigm based on the concept of "objects" which contain data and code.**

### Six OOP Concepts in Java
1. **Class** - Blueprint for creating objects
2. **Object** - Instance of a class
3. **Polymorphism** - One interface, multiple implementations
4. **Encapsulation** - Data hiding and bundling
5. **Inheritance** - Acquiring properties from parent class
6. **Data Abstraction** - Hiding implementation details

### Why Java is OOP Language?
**Java supports all six OOP concepts, making it a purely object-oriented programming language.**

---

## What is a Class?

### Definition
**A class is a collection of attributes and behavior.**

### Real-World Analogies

#### Example 1: Animal Classification
```
Class: Animal (Category/Group)
Objects: Dog, Elephant, Horse (Physical entities)

Attributes: Color, Height, Weight
Behavior: Eating, Running, Sleeping
```

#### Example 2: Student Classification
```
Class: Student (Category/Group)
Objects: John, David, Scott (Physical entities)

Attributes: Student ID, Name, Grade
Behavior: Study, Attend classes, Take exams
```

#### Example 3: Employee Classification
```
Class: Employee (Category/Group)
Objects: John Smith, Mary Johnson (Physical entities)

Attributes: Employee ID, Name, Salary, Department
Behavior: Work, Attend meetings, Complete tasks
```

### Class as Blueprint
**A class is like an architectural blueprint:**
- **Blueprint:** House plan (Class)
- **Houses:** Multiple houses built from same plan (Objects)

### Key Characteristics of Class
1. **Collection of attributes and behavior**
2. **Logical entity** (not physical)
3. **Blueprint or template**
4. **Does not occupy memory space**
5. **Virtual entity** (cannot be seen or touched)

### Class in Java Context
**In Java, a class is a collection of variables and methods.**
- **Attributes = Variables**
- **Behavior = Methods**

---

## What is an Object?

### Definition
**An object is an instance of a class.**

### Key Characteristics of Object
1. **Physical entity** (has real existence)
2. **Derived from class**
3. **Occupies memory space**
4. **Has its own copy of variables and methods**
5. **Independent of other objects**

### Object Creation Process
1. **Class must exist first**
2. **Object is created using class blueprint**
3. **Object acquires variables and methods from class**
4. **Each object is independent**

---

## Class vs Object Comparison

| Aspect | Class | Object |
|--------|-------|--------|
| **Definition** | Collection of variables and methods | Instance of a class |
| **Nature** | Logical entity/Blueprint | Physical entity |
| **Memory** | Does not occupy memory | Occupies memory space |
| **Existence** | Virtual (cannot be seen) | Real (can be operated) |
| **Creation** | Created using `class` keyword | Created using `new` keyword |
| **Quantity** | One class can exist | Multiple objects from one class |
| **Purpose** | Template for objects | Actual working entity |

### Relationship Between Class and Object
- **Without class, no object can exist**
- **One class can have multiple objects**
- **Objects are derived from class**
- **Class is group of objects**

---

## Creating Classes in Java

### Basic Class Syntax
```java
class ClassName {
    // Variables (attributes)
    // Methods (behavior)
}
```

### Example 1: Employee Class

```java
package day10;

public class Employee {
    // Class variables (attributes)
    int employeeId;
    String employeeName;
    String job;
    double salary;
    
    // Class method (behavior)
    void display() {
        System.out.println("Employee ID: " + employeeId);
        System.out.println("Employee Name: " + employeeName);
        System.out.println("Job: " + job);
        System.out.println("Salary: " + salary);
    }
    
    // Main method for execution
    public static void main(String[] args) {
        // Object creation and usage will be here
    }
}
```

### Class Components Explanation

#### Variables (Attributes)
```java
int employeeId;      // Stores employee ID
String employeeName; // Stores employee name
String job;          // Stores job title
double salary;       // Stores salary amount
```

#### Methods (Behavior)
```java
void display() {
    // Method to print employee details
    // void = no return value
    // () = no parameters
}
```

#### Method Structure
```java
returnType methodName(parameters) {
    // Method body
}
```

### Important Notes About Classes
1. **Variables are not initialized in class** (values assigned through objects)
2. **Methods define behavior** that objects can perform
3. **Class is just a template** - no actual data until object is created
4. **All objects get their own copy** of variables and methods

---

## Creating and Using Objects

### Object Creation Syntax
```java
ClassName objectName = new ClassName();
```

### Example: Creating Employee Objects

```java
package day10;

public class Employee {
    // Class variables
    int employeeId;
    String employeeName;
    String job;
    double salary;
    
    // Class method
    void display() {
        System.out.println("Employee ID: " + employeeId);
        System.out.println("Employee Name: " + employeeName);
        System.out.println("Job: " + job);
        System.out.println("Salary: " + salary);
        System.out.println("------------------------");
    }
    
    public static void main(String[] args) {
        // Creating first object
        Employee emp1 = new Employee();
        
        // Assigning data to emp1 object
        emp1.employeeId = 101;
        emp1.employeeName = "John";
        emp1.job = "Manager";
        emp1.salary = 50000.0;
        
        // Calling method to display emp1 data
        emp1.display();
        
        // Creating second object
        Employee emp2 = new Employee();
        
        // Assigning data to emp2 object
        emp2.employeeId = 102;
        emp2.employeeName = "Mary";
        emp2.job = "Developer";
        emp2.salary = 45000.0;
        
        // Calling method to display emp2 data
        emp2.display();
    }
}
```

**Output:**
```
Employee ID: 101
Employee Name: John
Job: Manager
Salary: 50000.0
------------------------
Employee ID: 102
Employee Name: Mary
Job: Developer
Salary: 45000.0
------------------------
```

### Object Creation Process Explained

#### Step 1: Object Declaration and Creation
```java
Employee emp1 = new Employee();
```
- **Employee:** Class name (also data type)
- **emp1:** Object reference variable
- **new:** Keyword to create object
- **Employee():** Constructor call

#### Step 2: Object Gets Copy of Class Members
When `emp1` object is created:
- Gets its own copy of: `employeeId`, `employeeName`, `job`, `salary`
- Gets its own copy of: `display()` method

#### Step 3: Accessing Object Members
```java
emp1.employeeId = 101;    // Accessing variable
emp1.display();           // Calling method
```

### Multiple Objects Independence

```java
// Object 1
Employee emp1 = new Employee();
emp1.employeeId = 101;
emp1.employeeName = "John";

// Object 2  
Employee emp2 = new Employee();
emp2.employeeId = 102;
emp2.employeeName = "Mary";

// Objects are independent
System.out.println(emp1.employeeName); // John
System.out.println(emp2.employeeName); // Mary
```

**Key Points:**
- **Each object has separate memory space**
- **Changing one object doesn't affect another**
- **Objects are independent even from same class**

---

## Separating Main Method

### Why Separate Main Method?
In real-world projects:
1. **One main class** controls entire project
2. **Multiple regular classes** contain business logic
3. **Better organization** and maintainability
4. **Reusability** of classes across project

### Project Structure
```
Project
├── Package 1
│   ├── Class A (regular class)
│   ├── Class B (regular class)
│   └── Main Class (contains main method)
├── Package 2
│   ├── Class C (regular class)
│   └── Class D (regular class)
└── Package 3
    └── Class E (regular class)
```

### Example: Separated Classes

#### Employee.java (Regular Class)
```java
package day10;

public class Employee {
    // Class variables
    int employeeId;
    String employeeName;
    String job;
    double salary;
    
    // Class method
    void display() {
        System.out.println("Employee ID: " + employeeId);
        System.out.println("Employee Name: " + employeeName);
        System.out.println("Job: " + job);
        System.out.println("Salary: " + salary);
        System.out.println("------------------------");
    }
}
```

#### EmployeeMain.java (Main Class)
```java
package day10;

public class EmployeeMain {
    public static void main(String[] args) {
        // Creating objects of Employee class
        Employee emp1 = new Employee();
        emp1.employeeId = 101;
        emp1.employeeName = "John";
        emp1.job = "Manager";
        emp1.salary = 50000.0;
        emp1.display();
        
        Employee emp2 = new Employee();
        emp2.employeeId = 102;
        emp2.employeeName = "Mary";
        emp2.job = "Developer";
        emp2.salary = 45000.0;
        emp2.display();
    }
}
```

### Benefits of Separation
1. **Clean code organization**
2. **Reusable classes**
3. **Single point of execution**
4. **Better maintainability**
5. **Professional project structure**

---

## Practical Examples

### Example 1: Student Management System

#### Student.java
```java
package day10;

public class Student {
    // Student attributes
    int studentId;
    String studentName;
    char grade;
    
    // Method to print student data
    void printData() {
        System.out.println(studentId + " " + studentName + " " + grade);
    }
}
```

#### StudentMain.java
```java
package day10;

public class StudentMain {
    public static void main(String[] args) {
        // Creating first student
        Student stu1 = new Student();
        stu1.studentId = 101;
        stu1.studentName = "Smith";
        stu1.grade = 'A';
        stu1.printData();
        
        // Creating second student
        Student stu2 = new Student();
        stu2.studentId = 102;
        stu2.studentName = "Johnson";
        stu2.grade = 'B';
        stu2.printData();
    }
}
```

**Output:**
```
101 Smith A
102 Johnson B
```

### Example 2: Book Management System

#### Book.java
```java
package day10;

public class Book {
    // Book attributes
    int bookId;
    String title;
    String author;
    double price;
    
    // Method to display book information
    void displayBook() {
        System.out.println("Book ID: " + bookId);
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Price: $" + price);
        System.out.println("===================");
    }
}
```

#### BookMain.java
```java
package day10;

public class BookMain {
    public static void main(String[] args) {
        // Creating book objects
        Book book1 = new Book();
        book1.bookId = 1001;
        book1.title = "Java Programming";
        book1.author = "James Gosling";
        book1.price = 29.99;
        book1.displayBook();
        
        Book book2 = new Book();
        book2.bookId = 1002;
        book2.title = "Python Basics";
        book2.author = "Guido van Rossum";
        book2.price = 24.99;
        book2.displayBook();
    }
}
```

### Example 3: Common Data Across Objects

Sometimes all objects share common data:

```java
package day10;

public class Student {
    int studentId;
    String studentName;
    char grade;
    String schoolName = "ABC High School"; // Common for all students
    
    void printData() {
        System.out.println("ID: " + studentId);
        System.out.println("Name: " + studentName);
        System.out.println("Grade: " + grade);
        System.out.println("School: " + schoolName);
        System.out.println("-------------------");
    }
}
```

**When to use common data:**
- **All objects have same value** (like school name, company name)
- **Value never changes** across objects
- **Saves memory and coding effort**

---

## Key Concepts Summary

### Class Fundamentals
1. **Class is a blueprint** for creating objects
2. **Contains variables and methods**
3. **Logical entity** - doesn't occupy memory
4. **Created using `class` keyword**

### Object Fundamentals
1. **Object is instance of class**
2. **Physical entity** - occupies memory
3. **Has its own copy** of class variables and methods
4. **Created using `new` keyword**

### Best Practices
1. **Separate main method** in different class
2. **Don't initialize variables in class** (unless common data)
3. **Use meaningful names** for classes and objects
4. **One class per file** with same name as filename

### Memory Management
- **Class:** No memory allocation (blueprint only)
- **Objects:** Each object gets separate memory space
- **Independence:** Objects don't affect each other

### Access Pattern
```java
// Accessing object members
objectName.variableName = value;  // Set variable
objectName.methodName();          // Call method
```

---

## Important Notes

### Method Types
1. **User-defined methods:** Created by programmer (like `display()`)
2. **Built-in methods:** Provided by Java (like `length()`, `charAt()`)

### Return Types
- **void:** Method doesn't return any value
- **int, String, etc.:** Method returns specific type of value

### Project Organization
- **Real projects:** One main class, multiple regular classes
- **Learning:** Can have main method in same class for simplicity

### Package Access
- **Same package:** Direct access to classes
- **Different package:** Need `import` statement

---

*This completes Session 10 on Classes and Objects Fundamentals. These concepts form the foundation of Object-Oriented Programming. Practice creating different classes and objects to master these fundamental concepts before moving to advanced OOP topics!*