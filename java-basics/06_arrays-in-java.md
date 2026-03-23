# 06 - Arrays in Java

## Table of Contents
1. [What are Arrays?](#what-are-arrays)
2. [Why Use Arrays?](#why-use-arrays)
3. [Single Dimensional Arrays](#single-dimensional-arrays)
4. [Two Dimensional Arrays](#two-dimensional-arrays)
5. [Object Arrays (Heterogeneous Data)](#object-arrays-heterogeneous-data)
6. [Practice Assignments](#practice-assignments)

---

## What are Arrays?

### Definition
**An array is a collection of elements of the same data type.**

### Key Concepts
- **Derived Data Type:** Arrays belong to derived data types (not primitive)
- **Multiple Values:** Can store multiple values in one single variable
- **Homogeneous Data:** All elements must be of the same data type
- **Index-Based:** Each element is accessed using an index number

### Data Types Classification

| Type | Description | Examples |
|------|-------------|----------|
| **Primitive** | Store only one value at a time | int, double, char, boolean |
| **Derived** | Store multiple values in one variable | Arrays, Classes, Interfaces |

### Homogeneous vs Heterogeneous Data

| Data Type | Description | Example |
|-----------|-------------|---------|
| **Homogeneous** | All data belongs to same type | [10, 20, 30, 40] (all integers) |
| **Heterogeneous** | Data belongs to different types | [10, "Hello", 3.14, true] (mixed types) |

---

## Why Use Arrays?

### Problem Without Arrays
**To store 100 student IDs, you would need 100 separate variables:**

```java
int student1 = 101;
int student2 = 102;
int student3 = 103;
// ... 97 more variables
int student100 = 200;
```

### Problems with Multiple Variables
1. **Difficult to manage** 100+ variables
2. **Hard to perform operations** on all values
3. **Code becomes lengthy** and unmanageable
4. **No easy way to iterate** through all values

### Solution with Arrays
**Same 100 student IDs in one variable:**

```java
int[] studentIds = {101, 102, 103, ..., 200}; // All 100 IDs in one array
```

### Benefits of Arrays
1. **Single variable** holds multiple values
2. **Easy to manage** and operate on data
3. **Supports iteration** using loops
4. **Reduces code length** significantly
5. **Better organization** of related data

---

## Single Dimensional Arrays

### What is Single Dimensional Array?
- **Only rows** are present (no columns)
- **Linear structure** with sequential elements
- **Index starts from 0** and goes up to (length-1)

### Array Structure
```
Array: [100, 200, 300, 400, 500]
Index:   0    1    2    3    4
```

### Memory Allocation
When you declare `int[] a = new int[5];`, it creates:
```
Locations: [  _  ][  _  ][  _  ][  _  ][  _  ]
Index:        0     1     2     3     4
```

### Important Rules
1. **Index starts from 0** (not 1)
2. **Maximum index = Array length - 1**
3. **Array Index Out of Bounds Exception** occurs if you access invalid index
4. **Fixed size** once declared (for Approach 1)

---

## Declaration and Initialization

### Approach 1: Declaration then Assignment (Fixed Size)

#### Step 1: Declaration
```java
int[] a = new int[5]; // Creates array with 5 locations
```

#### Step 2: Assignment
```java
a[0] = 100;  // Store 100 at index 0
a[1] = 200;  // Store 200 at index 1
a[2] = 300;  // Store 300 at index 2
a[3] = 400;  // Store 400 at index 3
a[4] = 500;  // Store 500 at index 4
```

#### Complete Eclipse Example
```java
package day6;

public class SingleDimensionalArray {
    public static void main(String[] args) {
        // Approach 1: Declaration and Assignment
        int[] a = new int[5];  // Declaration
        
        // Assignment
        a[0] = 100;
        a[1] = 200;
        a[2] = 300;
        a[3] = 400;
        a[4] = 500;
        
        System.out.println("Array created with approach 1");
    }
}
```

### Approach 2: Declaration and Assignment in One Line (Dynamic)

```java
package day6;

public class SingleDimensionalArray {
    public static void main(String[] args) {
        // Approach 2: Declaration and Assignment together
        int[] a = {100, 200, 300, 400, 500};
        
        System.out.println("Array created with approach 2");
    }
}
```

### When to Use Which Approach?

| Criteria | Approach 1 (Fixed) | Approach 2 (Dynamic) |
|----------|-------------------|----------------------|
| **Know exact size** | ✓ Use this | Can use this |
| **Don't know size** | ✗ Cannot use | ✓ Use this |
| **Future additions** | ✗ Not possible | ✓ Possible |
| **Memory efficiency** | May waste memory | Efficient |
| **Flexibility** | Low | High |

### Alternative Bracket Notations
All these declarations are valid:

```java
// Method 1: Brackets after data type
int[] a = new int[5];

// Method 2: Brackets after variable name  
int a[] = new int[5];

// Method 3: Mixed (not recommended)
int[] a = new int[5];
```

---

## Basic Array Operations

### 1. Finding Length of Array

```java
package day6;

public class ArrayOperations {
    public static void main(String[] args) {
        int[] a = {100, 200, 300, 400, 500};
        
        // Find length of array
        System.out.println("Length of array: " + a.length);
        // Output: Length of array: 5
    }
}
```

### 2. Reading Single Value from Array

```java
package day6;

public class ArrayOperations {
    public static void main(String[] args) {
        int[] a = {100, 200, 300, 400, 500};
        
        // Read specific values
        System.out.println("Value at index 0: " + a[0]); // 100
        System.out.println("Value at index 4: " + a[4]); // 500
    }
}
```

### 3. Reading All Values Using Normal For Loop

```java
package day6;

public class ArrayOperations {
    public static void main(String[] args) {
        int[] a = {100, 200, 300, 400, 500};
        
        // Read all values using normal for loop
        System.out.println("=== Using Normal For Loop ===");
        for (int i = 0; i < a.length; i++) {
            System.out.println(a[i]);
        }
    }
}
```

#### Loop Condition Options
```java
// Option 1: Using less than
for (int i = 0; i < a.length; i++) {
    System.out.println(a[i]);
}

// Option 2: Using less than or equal to
for (int i = 0; i <= a.length - 1; i++) {
    System.out.println(a[i]);
}

// Both are correct, Option 1 is preferred
```

### 4. Reading All Values Using Enhanced For Loop

```java
package day6;

public class ArrayOperations {
    public static void main(String[] args) {
        int[] a = {100, 200, 300, 400, 500};
        
        // Read all values using enhanced for loop
        System.out.println("=== Using Enhanced For Loop ===");
        for (int x : a) {
            System.out.println(x);
        }
    }
}
```

### Enhanced For Loop Execution Flow
```java
int[] a = {100, 200, 300, 400, 500};
for (int x : a) {
    System.out.println(x);
}

// Execution:
// Round 1: x = 100, print 100
// Round 2: x = 200, print 200  
// Round 3: x = 300, print 300
// Round 4: x = 400, print 400
// Round 5: x = 500, print 500
// No more elements, exit loop
```

### Normal For Loop vs Enhanced For Loop

| Feature | Normal For Loop | Enhanced For Loop |
|---------|----------------|-------------------|
| **Index access** | ✓ Available | ✗ Not available |
| **Syntax complexity** | More complex | Simpler |
| **Condition handling** | Manual | Automatic |
| **Preferred for arrays** | Sometimes | Most times |
| **Code length** | Longer | Shorter |

---

## Two Dimensional Arrays

### What is Two Dimensional Array?
- **Rows and Columns** both are present
- **Tabular format** like a table or matrix
- **Two indices required** - one for row, one for column
- **Both indices start from 0**

### Array Structure
```
Two Dimensional Array:
     Col0  Col1
Row0 [100] [200]
Row1 [300] [400] 
Row2 [500] [600]

Access: array[row][column]
Example: array[1][0] = 300
```

### Index System
```
Rows:    0, 1, 2 (start from 0)
Columns: 0, 1    (start from 0)

Position [2][1] means:
- Row index: 2 (third row)
- Column index: 1 (second column)
- Value: 600
```

---

## Two Dimensional Array Operations

### Approach 1: Declaration then Assignment

```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        // Approach 1: Declaration
        int[][] a = new int[3][2]; // 3 rows, 2 columns
        
        // Assignment
        a[0][0] = 100;  // Row 0, Column 0
        a[0][1] = 200;  // Row 0, Column 1
        a[1][0] = 300;  // Row 1, Column 0
        a[1][1] = 400;  // Row 1, Column 1
        a[2][0] = 500;  // Row 2, Column 0
        a[2][1] = 600;  // Row 2, Column 1
        
        System.out.println("2D Array created");
    }
}
```

### Approach 2: Declaration and Assignment Together

```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        // Approach 2: Direct assignment
        int[][] a = {
            {100, 200},  // Row 0
            {300, 400},  // Row 1  
            {500, 600}   // Row 2
        };
        
        System.out.println("2D Array created");
    }
}
```

### Alternative Bracket Notations for 2D Arrays
```java
// All these are valid:
int[][] a = new int[3][2];  // Recommended
int a[][] = new int[3][2];
int[] a[] = new int[3][2];
```

---

## Finding Size of 2D Array

### Number of Rows
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Find number of rows
        System.out.println("Number of rows: " + a.length);
        // Output: Number of rows: 3
    }
}
```

### Number of Columns
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Find number of columns in row 0
        System.out.println("Number of columns: " + a[0].length);
        // Output: Number of columns: 2
    }
}
```

### Complete Size Information
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        System.out.println("Number of rows: " + a.length);
        System.out.println("Number of columns: " + a[0].length);
    }
}
```

---

## Reading Values from 2D Array

### Reading Single Value
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Read specific values
        System.out.println("Value at [0][0]: " + a[0][0]); // 100
        System.out.println("Value at [2][1]: " + a[2][1]); // 600
    }
}
```

### Reading All Values Using Nested For Loop
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Read all values using nested for loop
        System.out.println("=== All values ===");
        for (int r = 0; r < a.length; r++) {           // Outer loop for rows
            for (int c = 0; c < a[r].length; c++) {    // Inner loop for columns
                System.out.println(a[r][c]);
            }
        }
    }
}
```

### Nested For Loop Execution Flow
```java
// Array: {{100, 200}, {300, 400}, {500, 600}}

// Execution steps:
// r=0: Enter outer loop (row 0)
//   c=0: a[0][0] = 100, print 100
//   c=1: a[0][1] = 200, print 200
//   c=2: condition false, exit inner loop
// r=1: Continue outer loop (row 1)  
//   c=0: a[1][0] = 300, print 300
//   c=1: a[1][1] = 400, print 400
//   c=2: condition false, exit inner loop
// r=2: Continue outer loop (row 2)
//   c=0: a[2][0] = 500, print 500  
//   c=1: a[2][1] = 600, print 600
//   c=2: condition false, exit inner loop
// r=3: condition false, exit outer loop
```

### Reading All Values in Table Format
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Print in table format
        System.out.println("=== Table Format ===");
        for (int r = 0; r < a.length; r++) {
            for (int c = 0; c < a[r].length; c++) {
                System.out.print(a[r][c] + " ");  // Print with space
            }
            System.out.println(); // New line after each row
        }
    }
}
```

**Output:**
```
100 200 
300 400 
500 600 
```

---

## Enhanced For Loop with 2D Arrays

### Syntax and Example
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Enhanced for loop for 2D array
        System.out.println("=== Enhanced For Loop ===");
        for (int[] arr : a) {        // Outer loop gets each row
            for (int x : arr) {      // Inner loop gets each element
                System.out.println(x);
            }
        }
    }
}
```

### Enhanced For Loop Execution Flow
```java
int[][] a = {{100, 200}, {300, 400}, {500, 600}};

for (int[] arr : a) {
    for (int x : arr) {
        System.out.println(x);
    }
}

// Execution:
// Round 1: arr = {100, 200} (first row)
//   x = 100, print 100
//   x = 200, print 200
// Round 2: arr = {300, 400} (second row)  
//   x = 300, print 300
//   x = 400, print 400
// Round 3: arr = {500, 600} (third row)
//   x = 500, print 500
//   x = 600, print 600
```

### Why Single Dimensional Array Variable?
**Question:** Why do we use `int[] arr` in the outer loop?

**Answer:** Because each row of a 2D array is itself a 1D array:
- `a[0]` returns `{100, 200}` (1D array)
- `a[1]` returns `{300, 400}` (1D array)  
- `a[2]` returns `{500, 600}` (1D array)

So we need a 1D array variable to hold each row.

### Enhanced For Loop in Table Format
```java
package day6;

public class TwoDimensionalArray {
    public static void main(String[] args) {
        int[][] a = {
            {100, 200},
            {300, 400},
            {500, 600}
        };
        
        // Table format with enhanced for loop
        System.out.println("=== Table Format ===");
        for (int[] arr : a) {
            for (int x : arr) {
                System.out.print(x + " ");
            }
            System.out.println(); // New line after each row
        }
    }
}
```

---

## Object Arrays (Heterogeneous Data)

### What are Object Arrays?
- **Store different data types** in one array
- **Uses Object class** as the array type
- **Object is the root class** of all classes in Java
- **Not recommended** for regular use (use ArrayList instead)
- **Useful to know** for interviews

### Why Object Type?
```java
// Primitive types can store only one type:
int x = 10;        // Only integers
double y = 3.14;   // Only decimals  
char z = 'A';      // Only characters
String s = "Hi";   // Only strings
boolean b = true;  // Only boolean

// Object type can store ANY type:
Object obj1 = 10;      // Integer
Object obj2 = 3.14;    // Double
Object obj3 = 'A';     // Character  
Object obj4 = "Hi";    // String
Object obj5 = true;    // Boolean
```

### Creating Object Array
```java
package day6;

public class ObjectArray {
    public static void main(String[] args) {
        // Object array with different data types
        Object[] a = {100, 10.5, 'A', "Welcome", true};
        
        System.out.println("Object array created with mixed data types");
    }
}
```

### Reading Object Array with Enhanced For Loop
```java
package day6;

public class ObjectArray {
    public static void main(String[] args) {
        Object[] a = {100, 10.5, 'A', "Welcome", true};
        
        // Read using enhanced for loop
        System.out.println("=== Object Array Values ===");
        for (Object x : a) {
            System.out.println(x);
        }
    }
}
```

**Output:**
```
100
10.5
A
Welcome
true
```

### Reading Object Array with Normal For Loop
```java
package day6;

public class ObjectArray {
    public static void main(String[] args) {
        Object[] a = {100, 10.5, 'A', "Welcome", true};
        
        // Read using normal for loop
        System.out.println("=== Using Index ===");
        for (int i = 0; i < a.length; i++) {
            System.out.println(a[i]);
        }
    }
}
```

### Important Notes about Object Arrays
1. **Variable type must be Object** to hold different data types
2. **Less type safety** compared to specific type arrays
3. **ArrayList is preferred** for heterogeneous data
4. **Mainly used in advanced scenarios** or legacy code

---

## Practice Assignments

### Assignment 1: Sum of Elements in Array
**Goal:** Calculate the total sum of all elements in an array.

**Example:**
- Array: [10, 20, 30, 40, 50]
- Sum: 10 + 20 + 30 + 40 + 50 = 150

**Logic:**
1. **Initialize sum to 0**
2. **Read each element** using loop
3. **Add each element to sum**
4. **Print final sum**

**Template:**
```java
package day6;

public class SumOfElements {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        int sum = 0;
        
        // Your code here
        // Use enhanced for loop to read each number
        // Add each number to sum
        
        System.out.println("Sum of elements: " + sum);
    }
}
```

**Solution Approach:**
```java
package day6;

public class SumOfElements {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        int sum = 0;
        
        // Calculate sum using enhanced for loop
        for (int num : numbers) {
            sum = sum + num;  // Add each number to sum
        }
        
        System.out.println("Sum of elements: " + sum);
        // Output: Sum of elements: 150
    }
}
```

### Assignment 2: Print Even and Odd Numbers from Array
**Goal:** Separate and count even and odd numbers from an array.

**Example:**
- Array: [12, 15, 18, 21, 24, 27]
- Even numbers: 12, 18, 24 (Count: 3)
- Odd numbers: 15, 21, 27 (Count: 3)

**Logic:**
1. **Read each element** using loop
2. **Check if number % 2 == 0** (even) or not (odd)
3. **Print and count** even and odd numbers separately

**Template:**
```java
package day6;

public class EvenOddNumbers {
    public static void main(String[] args) {
        int[] numbers = {12, 15, 18, 21, 24, 27};
        int evenCount = 0;
        int oddCount = 0;
        
        System.out.println("Even numbers:");
        // Your code here - print even numbers and count them
        
        System.out.println("Odd numbers:");
        // Your code here - print odd numbers and count them
        
        System.out.println("Total even numbers: " + evenCount);
        System.out.println("Total odd numbers: " + oddCount);
    }
}
```

**Solution Approach:**
```java
package day6;

public class EvenOddNumbers {
    public static void main(String[] args) {
        int[] numbers = {12, 15, 18, 21, 24, 27};
        int evenCount = 0;
        int oddCount = 0;
        
        System.out.println("Even numbers:");
        for (int num : numbers) {
            if (num % 2 == 0) {
                System.out.println(num);
                evenCount++;
            }
        }
        
        System.out.println("Odd numbers:");
        for (int num : numbers) {
            if (num % 2 != 0) {
                System.out.println(num);
                oddCount++;
            }
        }
        
        System.out.println("Total even numbers: " + evenCount);
        System.out.println("Total odd numbers: " + oddCount);
    }
}
```

### Assignment 3: Find Prime Numbers in Array
**Goal:** Identify and print all prime numbers from an array.

**What is a Prime Number?**
- A number greater than 1
- Has exactly two factors: 1 and itself
- Examples: 2, 3, 5, 7, 11, 13, 17, 19, 23...

**Logic:**
1. **For each number in array**
2. **Check if it's prime** using nested loop
3. **Print prime numbers**

**Template:**
```java
package day6;

public class PrimeNumbers {
    public static void main(String[] args) {
        int[] numbers = {2, 4, 5, 6, 7, 8, 9, 11, 12, 13};
        
        System.out.println("Prime numbers in array:");
        
        // Your code here
        // For each number, check if it's prime
        // A number is prime if it has only 2 factors: 1 and itself
    }
}
```

**Prime Number Check Logic:**
```java
// To check if a number is prime:
boolean isPrime = true;
if (num <= 1) {
    isPrime = false;
} else {
    for (int i = 2; i < num; i++) {
        if (num % i == 0) {
            isPrime = false;
            break;
        }
    }
}
```

---

## Key Takeaways

### Array Fundamentals
1. **Arrays store multiple values** of the same data type
2. **Index starts from 0** and goes to (length-1)
3. **Fixed size** once declared (Approach 1)
4. **Dynamic size** possible (Approach 2)

### Single vs Two Dimensional Arrays
1. **Single Dimensional:** Only rows (linear structure)
2. **Two Dimensional:** Rows and columns (tabular structure)
3. **Access pattern:** array[index] vs array[row][column]

### Loop Preferences
1. **Enhanced For Loop:** Preferred for reading all elements
2. **Normal For Loop:** When you need index access
3. **Nested Loops:** Required for 2D arrays

### Best Practices
1. **Use meaningful variable names** for arrays
2. **Prefer enhanced for loop** when possible
3. **Check array bounds** to avoid exceptions
4. **Use ArrayList** for dynamic operations
5. **Object arrays** only when necessary

### Common Mistakes to Avoid
1. **Array Index Out of Bounds** - accessing invalid index
2. **Off-by-one errors** - wrong loop conditions
3. **Null Pointer Exception** - uninitialized arrays
4. **Mixing data types** in regular arrays

---

*This completes Session 6 on Arrays in Java. Practice all assignments to master array concepts. Arrays are fundamental to many programming problems and will be used extensively in upcoming sessions on strings, collections, and advanced topics!*