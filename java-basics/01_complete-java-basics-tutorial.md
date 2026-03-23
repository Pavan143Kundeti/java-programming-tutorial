# 01 - Complete Java Basics Tutorial

## Table of Contents
1. [What is Java?](#what-is-java)
2. [Object-Oriented Programming](#object-oriented-programming)
3. [Java Features](#java-features)
4. [Java Components (JDK, JRE, JVM)](#java-components)
5. [Core Java vs Advanced Java](#core-java-vs-advanced-java)
6. [Java Versions](#java-versions)
7. [Installation Guide](#installation-guide)
8. [Eclipse IDE Setup](#eclipse-ide-setup)
9. [Creating Your First Java Program](#creating-your-first-java-program)
10. [Java Naming Conventions](#java-naming-conventions)
11. [Comments in Java](#comments-in-java)
12. [Practice Tips](#practice-tips)

---

## What is Java?

**Java is an object-oriented programming language.**

### Types of Programming Languages

There are **3 main types** of programming languages in the market:

| Type | Description | Examples | What it supports |
|------|-------------|----------|------------------|
| **Structured** | Does not support OOP concepts | C | Basic programming without classes |
| **Object-Based** | Supports only class and object | VB, VB Script | Class and object only |
| **Object-Oriented** | Supports all 6 OOP concepts | C++, Java, C#, Python | All OOP features |

### Special Case: Python
Python is an **all-rounder** language that can work in all three categories:
- Structured programming (without classes)
- Object-based programming (with classes only)
- Object-oriented programming (with all OOP concepts)

---

## Object-Oriented Programming

### The 6 OOP Concepts (OOPS)

For any language to be called "object-oriented," it must support these **6 concepts**:

1. **Class**
2. **Object**
3. **Polymorphism**
4. **Inheritance**
5. **Abstraction**
6. **Encapsulation**

### Why Java is Purely Object-Oriented

- Java supports **all 6 OOP concepts**
- **You cannot write a single line of code in Java without creating a class**
- This makes Java **purely object-oriented** (unlike C++ or Python where you can write code without classes)

### Language Categories Explained

#### Structured Programming Languages
- Do **not support** any OOP concepts
- You can write programs but without classes/objects
- Example: **C language**

#### Object-Based Programming Languages
- Support **only class and object**
- Do **not support** other OOP features (inheritance, polymorphism, etc.)
- Examples: **VB, VB Script**

#### Object-Oriented Programming Languages
- Support **all 6 OOP concepts**
- Examples: **C++, Java, C#**

---

## Java Features

### 1. Platform Independent

**What does Platform Independent mean?**

- **Install Java on any operating system:**
  - Windows
  - Mac
  - Unix
  - Linux
  - Almost every operating system

- **Write once, run anywhere:**
  - Write your Java program on Windows
  - The **same program** can run on Mac, Linux, Unix
  - **No code changes needed** when moving between operating systems

**Example:**
```
Windows (write code) → Mac (run same code) ✓
Windows (write code) → Linux (run same code) ✓
Mac (write code) → Windows (run same code) ✓
```

### 2. Case Sensitive Language

**What does Case Sensitive mean?**

- Java **treats lowercase and uppercase letters differently**
- `x` and `X` are **completely different** variables

**Example:**
```java
int x = 10;    // lowercase x
int X = 20;    // uppercase X
// These are TWO DIFFERENT variables!
```

**Comparison with other languages:**
- **VB and VB Script**: NOT case sensitive (x and X are the same)
- **Python**: NOT case sensitive for some things
- **Java**: ALWAYS case sensitive

---

## Java Components

### Three Important Java Components

| Component | Full Form | Purpose |
|-----------|-----------|---------|
| **JDK** | Java Development Kit | Complete Java software for development |
| **JRE** | Java Runtime Environment | Environment to run Java applications |
| **JVM** | Java Virtual Machine | Converts and executes Java code |

### 1. JDK (Java Development Kit)

**What is JDK?**
- **Complete Java software** that you download from the internet
- When you search "download Java," you actually download **JDK**
- **Full-fledged software** with all development tools

**When do you need JDK?**
- When you want to **write Java programs**
- When you want to **develop Java applications**
- When you want to **create new software** using Java

### 2. JRE (Java Runtime Environment)

**What is JRE?**
- **Environment needed to run** Java applications
- **Subset of JDK** (smaller than JDK)

**When do you need JRE?**
- When you want to **run Java applications** (not develop them)
- When someone else created a Java program and you just want to **use it**
- When you **don't need to write code**, just run existing programs

**Important Notes:**
- If you install **JDK**, you automatically get **JRE**
- You can install **JRE separately** if you only want to run programs

### 3. JVM (Java Virtual Machine)

**What is JVM?**
- **Java Virtual Machine** (Virtual = Invisible)
- **Heart of Java** - most important component
- **Not a separate software** you can download
- **Part of JRE** (comes automatically with JRE and JDK)

**What does JVM do?**

#### Code Conversion Process:
```
English Code (Java) → Byte Code → Machine Understanding
```

1. **Code Conversion:**
   - You write Java code in **English statements**
   - Machines **cannot understand English**
   - JVM **converts** your code to **byte code**
   - Byte code can be understood by **any machine/operating system**

2. **Compilation:**
   - **Checks for errors** in your code
   - **Finds syntax mistakes** and notifies you
   - **Validates** your program before running

3. **Execution:**
   - **Runs the byte code**
   - **Provides the final result**
   - **Manages program execution**

### Component Relationship

```
┌─────────────────────────────────────┐
│              JDK                    │
│  ┌───────────────────────────────┐  │
│  │            JRE                │  │
│  │  ┌─────────────────────────┐  │  │
│  │  │         JVM             │  │  │
│  │  │                         │  │  │
│  │  └─────────────────────────┘  │  │
│  └───────────────────────────────┘  │
└─────────────────────────────────────┘
```

**What Should You Download?**
- **For Development (Writing Code):** Download **JDK** (includes JRE and JVM)
- **For Running Programs Only:** Download **JRE** only (includes JVM)

---

## Core Java vs Advanced Java

### Core Java Concepts
**Basic concepts we will learn:**
- Language fundamentals
- Operators
- Data types
- Conditional statements
- Variables
- Looping statements
- Working with strings
- Object-oriented programming concepts

### Advanced Java Concepts
**Advanced concepts (not needed for testing/automation):**
- Collections
- Data structures
- JDBC
- Swing

**Note:** For automation testing, **Core Java concepts are enough**. Basic OOP concepts are sufficient for automation work.

---

## Java Versions

### Version History

| Version Range | Company | Notes |
|---------------|---------|-------|
| **Java 1 to 8** | Sun Microsystems | Open-source, no license |
| **Java 9 onwards** | Oracle | Oracle acquired Sun Microsystems |

### Current Requirements

**For Selenium (Automation Testing):**
- **Minimum:** Java 11
- **Recommended:** JDK 11+ (any version after Java 11)
- **Current versions:** Up to Java 20 or 21
- **Not supported:** Java 8, 9, 10 (old versions not supported by Selenium)

**Both JDK and Eclipse are open source and free.**

---

## Installation Guide

### Step 1: Download JDK

1. **Go to Google and search:** "download jdk"
2. **Visit Oracle website:** Java downloads page
3. **Choose version:** JDK 11, 17, 20, or latest version
4. **Select your operating system:**
   - **Windows:** Download .exe file (x64 installer)
   - **Mac:** Download .dmg file
   - **Linux:** Download appropriate package

### Step 2: Create Oracle Account

**Before downloading, you need to:**
1. Sign up for Oracle account (free)
2. Provide valid email address
3. Create password
4. Login to download JDK

### Step 3: Install JDK

**Installation Process:**
1. **Double-click** the downloaded installer
2. **Click "Next"** through installation screens
3. **Remember the installation path** (important for setting Java path)
4. **Default path:** `C:\Program Files\Java\jdk-[version]`
5. **Complete installation**

### Step 4: Set Java Path (Windows Only)

**Why set Java path?**
- Windows doesn't automatically know where Java is installed
- We must manually tell Windows the Java location
- **Mac users:** No need to set path (automatic in latest versions)

**How to set Java path:**

1. **Find Java installation location:**
   - Go to `C:\Program Files\Java\jdk-[version]\bin`
   - **Copy this complete path**

2. **Open Environment Variables:**
   - Search "environment variables" in Windows
   - Click "Edit the system environment variables"
   - Click "Environment Variables" button

3. **Add Java path:**
   - Under "System variables" find "Path"
   - Click "Edit"
   - Click "New"
   - **Paste the Java bin path**
   - Click OK, OK, OK

**Alternative method (using JAVA_HOME):**
1. Create new system variable: `JAVA_HOME`
2. Value: `C:\Program Files\Java\jdk-[version]` (without \bin)
3. In Path variable, add: `%JAVA_HOME%\bin`

### Step 5: Verify Installation

**Test if Java is working:**
1. **Open Command Prompt** (Windows) or **Terminal** (Mac)
2. **Type:** `java -version`
3. **Expected result:** Shows Java version number
4. **If error:** "command not found" means path is not set correctly

---

## Eclipse IDE Setup

### What is IDE?

**IDE = Integrated Development Environment**
- Software to write and run Java programs
- Like using Notepad for writing notes, we need IDE for Java
- **Popular Java IDEs:** Eclipse, IntelliJ IDEA, VS Code

### Download Eclipse

1. **Google search:** "download eclipse"
2. **Visit:** eclipse.org/downloads
3. **Download latest version** (e.g., Eclipse IDE 2023-09)
4. **No sign-up required** (free download)

### Install Eclipse

1. **Double-click** downloaded installer
2. **Choose:** "Eclipse IDE for Java Developers"
3. **Installation location:** Default is fine
4. **Create shortcuts:** Leave default settings
5. **Click "Install"**
6. **Launch Eclipse** when installation completes

### First Time Setup

**Workspace Setup:**
1. **First launch** asks for workspace location
2. **Workspace** = folder where all your Java projects will be saved
3. **Create new folder** (e.g., `C:\JavaWorkspace\2023-Batch`)
4. **Browse and select** your workspace folder
5. **Check "Use this as default"** to avoid asking every time
6. **Click "Launch"**

**Eclipse Window Setup:**
1. **Close welcome screen**
2. **Close unnecessary panels:** Task List, Outline, Problems
3. **Keep Package Explorer** (most important panel)
4. **Increase font size:** Ctrl + Plus (multiple times)

---

## Creating Your First Java Program

### Step 1: Create Java Project

**Three ways to create project:**
1. Click "Create a Java project" link in Package Explorer
2. Go to File → New → Java Project
3. Click the "New" icon → Java Project

**Project creation:**
1. **Project name:** JavaProgramming (no spaces)
2. **Use default settings** (Eclipse will detect installed Java)
3. **Click "Finish"**

### Step 2: Create Package

**What is a package?**
- Package = folder in Java
- Helps organize your programs
- We'll create daily packages (day1, day2, day3, etc.)

**Create package:**
1. **Right-click on "src"** folder
2. **Select:** New → Package
3. **Package name:** day1 (no spaces, lowercase)
4. **Click "Finish"**
5. **Delete module-info.java** if created (not needed)

### Step 3: Create Class

**What is a class?**
- **You cannot write any Java code without creating a class first**
- Class is the basic building block of Java programs

**Create class:**
1. **Right-click on package** (day1)
2. **Select:** New → Class
3. **Class name:** FirstJavaProgram (must start with uppercase)
4. **Don't check any options**
5. **Click "Finish"**

### Step 4: Write Your First Program

**Basic class structure created:**
```java
package day1;

public class FirstJavaProgram {

}
```

**Add main method:**
```java
package day1;

public class FirstJavaProgram {
    public static void main(String[] args) {
        
    }
}
```

**Add print statement:**
```java
package day1;

public class FirstJavaProgram {
    public static void main(String[] args) {
        System.out.println("Welcome to Java");
    }
}
```

### Step 5: Run Your Program

**Three ways to run:**
1. **Right-click in code** → Run As → Java Application
2. **Menu:** Run → Run (Ctrl+F11)
3. **Click run icon** in toolbar

**First time running:**
- Eclipse asks to save before running
- **Check "Always save resources before launching"**
- **Click OK**

**Output:**
- See result in **Console window** at bottom
- Output: `Welcome to Java`

### Understanding the Code

**Line by line explanation:**

1. **`package day1;`**
   - Shows which package this class belongs to
   - Semicolon (;) marks end of statement

2. **`public class FirstJavaProgram`**
   - `public` = access modifier
   - `class` = keyword meaning this is a class
   - `FirstJavaProgram` = name of the class
   - `{ }` = starting and ending of class scope

3. **`public static void main(String[] args)`**
   - This is the **main method**
   - **Every Java program must have main method**
   - **Program execution starts from main method**
   - JVM looks for main method to run the program

4. **`System.out.println("Welcome to Java");`**
   - **Print statement** to display output
   - `System.out.println` = command to print
   - Text in double quotes is printed exactly as written
   - Semicolon marks end of statement

### Adding More Statements

**Multiple print statements:**
```java
public static void main(String[] args) {
    System.out.println("Welcome to Java");
    System.out.println("Hello World");
    System.out.println(10 + 20);
}
```

**Output:**
```
Welcome to Java
Hello World
30
```

### Double Quotes vs No Quotes

**With double quotes (String):**
```java
System.out.println("10 + 20");  // Output: 10 + 20
```

**Without double quotes (Calculation):**
```java
System.out.println(10 + 20);    // Output: 30
```

**Rule:**
- **Text/Strings:** Use double quotes
- **Numbers/Calculations:** No double quotes

### Shortcut for System.out.println

**Instead of typing full statement:**
1. Type: `syso`
2. Press: **Ctrl + Space** (Windows) or **Cmd + Space** (Mac)
3. **Automatically expands** to `System.out.println()`

---

## Java Naming Conventions

### Class Naming Rules

**Must follow these rules:**

1. **Start with uppercase letter**
   - ✅ `MyClass`
   - ❌ `myClass`

2. **Cannot start with number**
   - ❌ `123Class`
   - ✅ `MyClass123`

3. **No spaces allowed**
   - ❌ `My First Class`
   - ✅ `MyFirstClass`

4. **Only underscore allowed from special characters**
   - ✅ `My_Class`
   - ❌ `My@Class`
   - ❌ `My-Class`

5. **Can contain numbers (but not at start)**
   - ✅ `MyClass1`
   - ✅ `Class123`
   - ❌ `1MyClass`

**Examples of valid class names:**
- `FirstJavaProgram`
- `MyClass`
- `Student_Details`
- `Calculator2023`

**Examples of invalid class names:**
- `firstJavaProgram` (doesn't start with uppercase)
- `123Program` (starts with number)
- `My Class` (contains space)
- `My@Class` (contains special character)

### Case Sensitivity in Java

**Java keywords must be lowercase:**
- ✅ `public class`
- ❌ `Public Class`

**Some words must be uppercase:**
- ✅ `String`
- ❌ `string`
- ✅ `System`
- ❌ `system`

**Eclipse helps identify mistakes:**
- Shows **syntax errors** with red underlines
- Helps you fix case sensitivity issues

---

## Comments in Java

### What are Comments?

**Comments are used to:**
- **Improve code readability**
- **Explain what your code does**
- **Temporarily disable code** (without deleting)
- **Help others understand your code**

### Types of Comments

#### 1. Single Line Comments

**Syntax:** `// comment text`

**Example:**
```java
public static void main(String[] args) {
    System.out.println("This will run");
    // System.out.println("This will NOT run");
    System.out.println("This will also run");
}
```

**Output:**
```
This will run
This will also run
```

#### 2. Multi-Line Comments

**Syntax:** `/* comment text */`

**Example:**
```java
public static void main(String[] args) {
    System.out.println("This will run");
    /*
    System.out.println("This will NOT run");
    System.out.println("This will also NOT run");
    System.out.println("None of these will run");
    */
    System.out.println("This will run");
}
```

**Output:**
```
This will run
This will run
```

### When to Use Comments

1. **Explain complex logic:**
```java
// Calculate total price with tax
double totalPrice = price + (price * 0.18);
```

2. **Temporarily disable code:**
```java
System.out.println("Debug: Program started");
// System.out.println("Debug: This debug line is disabled");
```

3. **Document your code:**
```java
/*
This program calculates student grades
Created by: [Your Name]
Date: [Date]
*/
```

---

## Practice Tips

### For Beginners

1. **Start with environment setup:**
   - Install JDK properly
   - Set Java path correctly
   - Install Eclipse IDE
   - Create workspace

2. **Practice basic steps:**
   - Create Java project (one time)
   - Create packages daily (day1, day2, day3...)
   - Create classes for each program
   - Write simple programs

3. **Common beginner mistakes:**
   - Forgetting semicolons (;)
   - Wrong case for keywords (Public vs public)
   - Missing curly braces { }
   - Not setting Java path

4. **Eclipse will help you:**
   - Shows syntax errors in red
   - Auto-completes code
   - Formats code automatically

### Daily Practice Structure

**Create this structure:**
```
JavaProgramming (Project)
├── src
    ├── day1 (Package)
    │   ├── FirstProgram.java
    │   ├── SecondProgram.java
    ├── day2 (Package)
    │   ├── Variables.java
    │   ├── DataTypes.java
    ├── day3 (Package)
        ├── Operators.java
        ├── Conditions.java
```

### System Requirements

- **RAM:** 8GB minimum
- **Operating System:** Windows, Mac, or Linux
- **Java:** Version 11 or higher
- **Eclipse:** Latest version

### Troubleshooting Tips

1. **If Java doesn't work after installation:**
   - Check if Java path is set correctly
   - Restart command prompt
   - Try `java -version` command

2. **If Eclipse doesn't start:**
   - Run as administrator (Windows)
   - Check if Java is installed properly

3. **If programs don't run:**
   - Make sure main method is present
   - Check for syntax errors (red underlines)
   - Save file before running

### Next Steps

**After mastering basics:**
1. Learn about variables and data types
2. Understand operators
3. Study conditional statements
4. Practice loops
5. Learn object-oriented programming concepts

**Remember:** 
- Practice daily
- Make mistakes and learn from them
- Eclipse will guide you with error messages
- Don't worry about understanding everything immediately
- Focus on following the structure for first few sessions

---

## Summary

**What we covered today:**

1. ✅ **Understood what Java is** - Object-oriented programming language
2. ✅ **Learned OOP concepts** - 6 main concepts that make Java object-oriented
3. ✅ **Java features** - Platform independent and case sensitive
4. ✅ **Java components** - JDK, JRE, JVM and their differences
5. ✅ **Installation** - Downloaded and installed JDK with path setup
6. ✅ **Eclipse setup** - Installed IDE and created workspace
7. ✅ **First program** - Created project, package, class, and ran first Java program
8. ✅ **Naming conventions** - Rules for creating class names
9. ✅ **Comments** - Single-line and multi-line comments

**For next session, make sure you have:**
- JDK installed and working (`java -version` command works)
- Eclipse installed with workspace created
- Ability to create and run basic Java programs
- Understanding of project → package → class structure

**Practice assignment:**
- Create 3-4 different classes in day1 package
- Write different print statements
- Try using comments
- Experiment with the Eclipse interface
- Get comfortable with the basic workflow

---

*This completes the first session of Java programming. In the next session, we will learn about variables, data types, and operators.*