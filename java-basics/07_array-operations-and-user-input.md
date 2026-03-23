# 07 - Array Operations and User Input in Java

## Table of Contents
1. [Searching Elements in Arrays](#searching-elements-in-arrays)
2. [Finding Duplicate Elements](#finding-duplicate-elements)
3. [Sorting Arrays](#sorting-arrays)
4. [Reversing Arrays](#reversing-arrays)
5. [Taking User Input with Scanner](#taking-user-input-with-scanner)
6. [Reading Data into Arrays at Runtime](#reading-data-into-arrays-at-runtime)
7. [Practice Assignments](#practice-assignments)

---

## Searching Elements in Arrays

### What is Linear Search?
**Linear search is the simplest searching algorithm where we compare each element with the target element one by one.**

### Problem Statement
Given an array of elements, check if a specific element is present in the array or not.

### Logic Development
**Before writing code, understand the manual process:**

```
Array: [300, 500, 100, 200, 600]
Search Element: 100

Manual Process:
1. Compare 300 with 100 → Not equal, continue
2. Compare 500 with 100 → Not equal, continue  
3. Compare 100 with 100 → Equal! Element found
4. Stop searching (no need to check remaining elements)
```

### Algorithm Steps
1. **Read each element** from array one by one
2. **Compare** each element with search element
3. **If match found:** Print "Element found" and exit loop
4. **If no match after checking all elements:** Print "Element not found"

### Important Points
- **Don't exit immediately** if first element doesn't match
- **Check all elements** before saying "not found"
- **Use break statement** when element is found
- **Use boolean flag** to track search status

---

## Linear Search Implementation

### Example 1: Basic Linear Search

```java
package day7;

public class SearchingInArray {
    public static void main(String[] args) {
        // Create array with sample data
        int[] a = {10, 20, 30, 40, 50};
        int searchElement = 30;
        boolean status = false; // Flag to track if element is found
        
        // Search using normal for loop
        for (int i = 0; i < a.length; i++) {
            if (a[i] == searchElement) {
                System.out.println("Element found");
                status = true;
                break; // Exit loop when element is found
            }
        }
        
        // Check if element was not found
        if (status == false) {
            System.out.println("Element not found");
        }
    }
}
```

### Example 2: Linear Search with Enhanced For Loop

```java
package day7;

public class SearchingInArray {
    public static void main(String[] args) {
        int[] a = {10, 20, 30, 40, 50};
        int searchElement = 30;
        boolean status = false;
        
        // Search using enhanced for loop
        for (int x : a) {
            if (x == searchElement) {
                System.out.println("Element found");
                status = true;
                break;
            }
        }
        
        if (status == false) {
            System.out.println("Element not found");
        }
    }
}
```

### Why Boolean Flag is Required?

**Wrong Approach (Don't do this):**
```java
for (int i = 0; i < a.length; i++) {
    if (a[i] == searchElement) {
        System.out.println("Element found");
        break;
    } else {
        System.out.println("Element not found"); // ❌ Wrong!
    }
}
```

**Problem:** This will print "Element not found" for every non-matching element.

**Correct Approach:**
```java
boolean status = false;
for (int i = 0; i < a.length; i++) {
    if (a[i] == searchElement) {
        System.out.println("Element found");
        status = true;
        break;
    }
}
if (status == false) {
    System.out.println("Element not found"); // ✓ Correct!
}
```

### Handling Duplicate Elements
```java
package day7;

public class SearchingInArray {
    public static void main(String[] args) {
        // Array with duplicates
        int[] a = {10, 20, 30, 30, 30, 40, 50};
        int searchElement = 30;
        boolean status = false;
        
        for (int x : a) {
            if (x == searchElement) {
                System.out.println("Element found");
                status = true;
                break; // Exits after finding first occurrence
            }
        }
        
        if (status == false) {
            System.out.println("Element not found");
        }
    }
}
```

**Note:** Linear search finds the **first occurrence** and exits. It doesn't count duplicates.

---

## Finding Duplicate Elements

### Problem Statement
Count how many times a specific element appears in an array.

### Logic
1. **Read each element** from array
2. **Compare** with target element
3. **If match found:** Increment counter
4. **Don't break the loop** - continue checking all elements
5. **Print final count**

### Implementation

```java
package day7;

public class FindDuplicates {
    public static void main(String[] args) {
        // Array with duplicate elements
        int[] a = {100, 200, 100, 300, 100, 400, 100};
        int number = 100; // Element to count
        int count = 0;    // Counter for duplicates
        
        // Count occurrences using enhanced for loop
        for (int value : a) {
            if (value == number) {
                count++; // Increment counter when match found
            }
        }
        
        System.out.println("Number " + number + " appears " + count + " times");
        // Output: Number 100 appears 4 times
    }
}
```

### Difference Between Search and Count

| Operation | Purpose | Loop Behavior | Output |
|-----------|---------|---------------|---------|
| **Search** | Find if element exists | Break after first match | "Found" or "Not found" |
| **Count** | Count occurrences | Continue till end | Number of occurrences |

### Dynamic Element Counting
```java
package day7;

public class FindDuplicates {
    public static void main(String[] args) {
        int[] a = {100, 200, 100, 300, 200, 400, 200};
        
        // Count different elements
        int[] elementsToCount = {100, 200, 300, 500};
        
        for (int number : elementsToCount) {
            int count = 0;
            for (int value : a) {
                if (value == number) {
                    count++;
                }
            }
            System.out.println("Number " + number + " appears " + count + " times");
        }
    }
}
```

---

## Sorting Arrays

### What is Sorting?
**Sorting means arranging elements in a specific order (ascending or descending).**

### Built-in Sorting Method
Java provides `Arrays.sort()` method for easy sorting.

### Sorting Numbers

```java
package day7;
import java.util.Arrays;

public class SortingElements {
    public static void main(String[] args) {
        // Array with random order
        int[] a = {100, 600, 200, 500, 400};
        
        // Print before sorting
        System.out.println("Before sorting: " + Arrays.toString(a));
        
        // Sort the array
        Arrays.sort(a);
        
        // Print after sorting
        System.out.println("After sorting: " + Arrays.toString(a));
    }
}
```

**Output:**
```
Before sorting: [100, 600, 200, 500, 400]
After sorting: [100, 200, 400, 500, 600]
```

### Sorting Strings

```java
package day7;
import java.util.Arrays;

public class SortingStrings {
    public static void main(String[] args) {
        // String array in random order
        String[] names = {"Scott", "Mary", "John", "David"};
        
        System.out.println("Before sorting: " + Arrays.toString(names));
        
        // Sort strings alphabetically
        Arrays.sort(names);
        
        System.out.println("After sorting: " + Arrays.toString(names));
    }
}
```

**Output:**
```
Before sorting: [Scott, Mary, John, David]
After sorting: [David, John, Mary, Scott]
```

### How String Sorting Works
**Strings are sorted alphabetically based on:**
1. **First character comparison** (A < B < C ... < Z)
2. **If first characters are same,** compare second characters
3. **Continue until difference is found**

**Example:**
- "Apple" vs "Banana" → 'A' < 'B' → "Apple" comes first
- "Apple" vs "Application" → First 5 characters same → "Apple" is shorter → "Apple" comes first

### Sorting Characters

```java
package day7;
import java.util.Arrays;

public class SortingCharacters {
    public static void main(String[] args) {
        // Character array
        String[] chars = {"d", "a", "c", "b"};
        
        System.out.println("Before sorting: " + Arrays.toString(chars));
        Arrays.sort(chars);
        System.out.println("After sorting: " + Arrays.toString(chars));
    }
}
```

### Important Notes about Arrays.sort()
1. **Ascending order only** - Built-in method sorts in ascending order
2. **For descending order** - Need custom logic or Collections.reverseOrder()
3. **Import required** - `import java.util.Arrays;`
4. **Works with all data types** - int, double, String, char, etc.

---

## Reversing Arrays

### Problem Statement
Print array elements in reverse order (from last to first).

### Logic
1. **Start from last index** (length - 1)
2. **Decrement index** in each iteration
3. **Continue until index reaches 0**
4. **Use normal for loop** (enhanced for loop won't work)

### Implementation

```java
package day7;

public class ReverseArray {
    public static void main(String[] args) {
        int[] a = {100, 200, 300, 400, 500};
        
        // Print original array
        System.out.println("Original order:");
        for (int x : a) {
            System.out.println(x);
        }
        
        // Print in reverse order
        System.out.println("Reverse order:");
        for (int i = a.length - 1; i >= 0; i--) {
            System.out.println(a[i]);
        }
    }
}
```

**Output:**
```
Original order:
100
200
300
400
500
Reverse order:
500
400
300
200
100
```

### Understanding the Loop
```java
int[] a = {100, 200, 300, 400, 500};
//         0    1    2    3    4     (indices)

// For reverse printing:
// Start: i = a.length - 1 = 4
// Condition: i >= 0
// Decrement: i--

// Execution:
// i = 4: print a[4] = 500
// i = 3: print a[3] = 400  
// i = 2: print a[2] = 300
// i = 1: print a[1] = 200
// i = 0: print a[0] = 100
// i = -1: condition false, exit
```

### Why Enhanced For Loop Doesn't Work?
```java
// Enhanced for loop always reads from index 0 to last
for (int x : a) {
    System.out.println(x); // Always prints in original order
}

// Cannot control the iteration order in enhanced for loop
```

---

## Taking User Input with Scanner

### What is Scanner Class?
**Scanner is a built-in Java class used to read input from keyboard/console at runtime.**

### Basic Setup
```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
```

### Reading Different Data Types

#### Reading Integer
```java
package day7;
import java.util.Scanner;

public class TakingInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter a number: ");
        int number = sc.nextInt();
        
        System.out.println("Given number is: " + number);
    }
}
```

#### Reading Decimal Number
```java
package day7;
import java.util.Scanner;

public class TakingInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter a decimal number: ");
        double number = sc.nextDouble();
        
        System.out.println("Given value is: " + number);
    }
}
```

#### Reading String
```java
package day7;
import java.util.Scanner;

public class TakingInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter your city: ");
        String city = sc.next();
        
        System.out.println("Your city is: " + city);
    }
}
```

### Scanner Methods for Different Data Types

| Data Type | Method | Example |
|-----------|--------|---------|
| **int** | `nextInt()` | `int num = sc.nextInt();` |
| **double** | `nextDouble()` | `double val = sc.nextDouble();` |
| **float** | `nextFloat()` | `float val = sc.nextFloat();` |
| **String** | `next()` | `String str = sc.next();` |
| **boolean** | `nextBoolean()` | `boolean flag = sc.nextBoolean();` |
| **long** | `nextLong()` | `long val = sc.nextLong();` |

### Taking Multiple Inputs

```java
package day7;
import java.util.Scanner;

public class MultipleInputs {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Take two numbers
        System.out.print("Enter first number: ");
        int number1 = sc.nextInt();
        
        System.out.print("Enter second number: ");
        int number2 = sc.nextInt();
        
        // Perform operation
        int sum = number1 + number2;
        System.out.println("Addition of two numbers: " + sum);
    }
}
```

### Mixed Data Types Input

```java
package day7;
import java.util.Scanner;

public class MixedInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Take different types of input
        System.out.print("Enter your name: ");
        String name = sc.next();
        
        System.out.print("Enter your age: ");
        int age = sc.nextInt();
        
        System.out.print("Enter unknown value: ");
        Object value = sc.next(); // Takes as string format
        
        System.out.println("Your name is: " + name);
        System.out.println("Your age is: " + age);
        System.out.println("Unknown value: " + value);
    }
}
```

### Important Notes about Scanner
1. **Import required:** `import java.util.Scanner;`
2. **One Scanner object** can be used for multiple inputs
3. **Variable types must match** the input method
4. **next() method** accepts everything as string format
5. **Data type compatibility:** double can accept int, but int cannot accept double

---

## Reading Data into Arrays at Runtime

### Problem Statement
Create an empty array and fill it with user input at runtime.

### Logic
1. **Create empty array** with fixed size
2. **Use for loop** to iterate through array indices
3. **Take input from user** for each position
4. **Store input** in corresponding array position
5. **Print array** after all inputs are taken

### Implementation

```java
package day7;
import java.util.Scanner;
import java.util.Arrays;

public class ReadingDataIntoArray {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Create empty array with 5 positions
        int[] a = new int[5];
        
        // Fill array with user input
        for (int i = 0; i < a.length; i++) {
            System.out.print("Enter value for position " + i + ": ");
            a[i] = sc.nextInt(); // Store input at index i
        }
        
        // Print array elements
        System.out.println("Array elements: " + Arrays.toString(a));
    }
}
```

**Sample Execution:**
```
Enter value for position 0: 100
Enter value for position 1: 200
Enter value for position 2: 300
Enter value for position 3: 400
Enter value for position 4: 500
Array elements: [100, 200, 300, 400, 500]
```

### Step-by-Step Execution
```java
int[] a = new int[5]; // Creates: [0, 0, 0, 0, 0]

// Loop execution:
// i = 0: Ask input for position 0, store in a[0]
// i = 1: Ask input for position 1, store in a[1]  
// i = 2: Ask input for position 2, store in a[2]
// i = 3: Ask input for position 3, store in a[3]
// i = 4: Ask input for position 4, store in a[4]
// i = 5: Condition false, exit loop
```

### Alternative: Print Each Element Individually

```java
package day7;
import java.util.Scanner;

public class ReadingDataIntoArray {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] a = new int[5];
        
        // Fill array with user input
        for (int i = 0; i < a.length; i++) {
            System.out.print("Enter value for position " + i + ": ");
            a[i] = sc.nextInt();
        }
        
        // Print array elements individually
        System.out.println("Array elements:");
        for (int i = 0; i < a.length; i++) {
            System.out.println("Position " + i + ": " + a[i]);
        }
    }
}
```

### Dynamic Array Size

```java
package day7;
import java.util.Scanner;
import java.util.Arrays;

public class DynamicArrayInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Ask user for array size
        System.out.print("Enter array size: ");
        int size = sc.nextInt();
        
        // Create array with user-specified size
        int[] a = new int[size];
        
        // Fill array with user input
        for (int i = 0; i < a.length; i++) {
            System.out.print("Enter value for position " + i + ": ");
            a[i] = sc.nextInt();
        }
        
        // Print array
        System.out.println("Array elements: " + Arrays.toString(a));
    }
}
```

---

## Practice Assignments

### Assignment 1: Sorting Elements Using Loops
**Goal:** Implement sorting without using built-in `Arrays.sort()` method.

**Hint:** Use bubble sort algorithm - compare adjacent elements and swap if needed.

**Logic:**
1. **Compare adjacent elements** in the array
2. **Swap if first > second** (for ascending order)
3. **Repeat for all elements** multiple times
4. **Continue until no swaps needed**

**Template:**
```java
package day7;

public class BubbleSort {
    public static void main(String[] args) {
        int[] a = {64, 34, 25, 12, 22, 11, 90};
        
        System.out.println("Before sorting:");
        printArray(a);
        
        // Your bubble sort logic here
        // Hint: Use nested loops
        // Outer loop: number of passes
        // Inner loop: compare adjacent elements
        
        System.out.println("After sorting:");
        printArray(a);
    }
    
    static void printArray(int[] arr) {
        for (int value : arr) {
            System.out.print(value + " ");
        }
        System.out.println();
    }
}
```

### Assignment 2: Find Missing Number in Array
**Goal:** Find the missing number in a sequence.

**Prerequisites:**
1. **Numbers should be in range** (e.g., 1 to 5)
2. **No duplicates** allowed
3. **Only one number missing**

**Example:**
- Array: [1, 4, 5, 3] (Range: 1 to 5)
- Missing number: 2

**Logic:**
1. **Calculate expected sum** of complete sequence
2. **Calculate actual sum** of given array
3. **Difference = Missing number**

**Mathematical Formula:**
```
Expected sum of 1 to n = n * (n + 1) / 2
Missing number = Expected sum - Actual sum
```

**Template:**
```java
package day7;

public class FindMissingNumber {
    public static void main(String[] args) {
        int[] a = {1, 4, 5, 3}; // Missing: 2
        int n = 5; // Range is 1 to 5
        
        // Calculate expected sum
        int expectedSum = n * (n + 1) / 2;
        
        // Calculate actual sum
        int actualSum = 0;
        // Your code here - calculate sum of array elements
        
        // Find missing number
        int missingNumber = expectedSum - actualSum;
        System.out.println("Missing number: " + missingNumber);
    }
}
```

### Assignment 3: Find Largest Number in Array
**Goal:** Find the maximum element in an array.

**Logic:**
1. **Assume first element is largest**
2. **Compare with each remaining element**
3. **Update largest if current element is bigger**
4. **Return final largest value**

**Template:**
```java
package day7;

public class FindLargest {
    public static void main(String[] args) {
        int[] a = {23, 45, 12, 67, 34, 89, 56};
        
        // Your code here
        // Initialize largest with first element
        // Compare with remaining elements
        // Update largest when needed
        
        System.out.println("Largest number: " + /* your result */);
    }
}
```

### Assignment 4: Find Smallest Number in Array
**Goal:** Find the minimum element in an array.

**Logic:** Similar to finding largest, but update when current element is smaller.

**Template:**
```java
package day7;

public class FindSmallest {
    public static void main(String[] args) {
        int[] a = {23, 45, 12, 67, 34, 89, 56};
        
        // Your code here
        // Initialize smallest with first element
        // Compare with remaining elements  
        // Update smallest when needed
        
        System.out.println("Smallest number: " + /* your result */);
    }
}
```

---

## Key Takeaways

### Array Operations
1. **Linear Search:** Compare each element sequentially
2. **Counting Duplicates:** Don't break loop, count all matches
3. **Sorting:** Use `Arrays.sort()` for built-in sorting
4. **Reversing:** Use normal for loop with decreasing index

### Scanner Class
1. **Import required:** `java.util.Scanner`
2. **Different methods** for different data types
3. **One Scanner object** can handle multiple inputs
4. **Data type compatibility** is important

### Best Practices
1. **Use boolean flags** for search operations
2. **Provide clear messages** when taking user input
3. **Import Arrays class** when using utility methods
4. **Handle edge cases** (empty arrays, invalid inputs)

### Common Mistakes to Avoid
1. **Don't use else immediately** after if in search operations
2. **Don't break loop** when counting duplicates
3. **Enhanced for loop** cannot be used for reverse iteration
4. **Variable types must match** Scanner methods

---

*This completes Session 7 on Array Operations and User Input. Practice all assignments to master these concepts. These operations form the foundation for more advanced programming problems and real-world applications!*