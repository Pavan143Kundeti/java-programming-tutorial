# 09 - String Reversal and Comparison in Java

## Table of Contents
1. [String Reversal Methods](#string-reversal-methods)
2. [Mutability vs Immutability](#mutability-vs-immutability)
3. [String vs StringBuffer vs StringBuilder](#string-vs-stringbuffer-vs-stringbuilder)
4. [String Comparison: == vs equals()](#string-comparison--vs-equals)
5. [Practice Assignments](#practice-assignments)

---

## String Reversal Methods

### What is String Reversal?
**String reversal means printing the string characters from last to first.**

**Example:**
- Original: "Welcome"
- Reversed: "emocleW"

### Important Note
**Java String class does NOT have a direct reverse() method.** We need to implement logic or use other classes.

---

## Approach 1: Using Logic with charAt() and length()

### Logic Explanation
1. **Start from the last character** of the string
2. **Extract each character** using charAt() method
3. **Concatenate characters** to a reverse string variable
4. **Continue until** we reach the first character (index 0)

### Step-by-Step Process
```
Original String: "Welcome"
Index:            0123456

Process:
- Start from index 6 (last): 'e'
- Move to index 5: 'm' 
- Move to index 4: 'o'
- Move to index 3: 'c'
- Move to index 2: 'l'
- Move to index 1: 'e'
- Move to index 0: 'W'

Result: "emocleW"
```

### Implementation

```java
package day9;

public class ReverseString {
    public static void main(String[] args) {
        // Approach 1: Using charAt() and length()
        String s = "Welcome";
        String reverse = ""; // Empty string to store result
        
        // Loop from last index to first index
        for (int i = s.length() - 1; i >= 0; i--) {
            reverse = reverse + s.charAt(i);
        }
        
        System.out.println("Original string: " + s);
        System.out.println("Reversed string: " + reverse);
    }
}
```

**Output:**
```
Original string: Welcome
Reversed string: emocleW
```

### Loop Breakdown
```java
String s = "Welcome"; // Length = 7, Last index = 6

// Loop execution:
// i = 6: reverse = "" + s.charAt(6) = "" + 'e' = "e"
// i = 5: reverse = "e" + s.charAt(5) = "e" + 'm' = "em"  
// i = 4: reverse = "em" + s.charAt(4) = "em" + 'o' = "emo"
// i = 3: reverse = "emo" + s.charAt(3) = "emo" + 'c' = "emoc"
// i = 2: reverse = "emoc" + s.charAt(2) = "emoc" + 'l' = "emocl"
// i = 1: reverse = "emocl" + s.charAt(1) = "emocl" + 'e' = "emocle"
// i = 0: reverse = "emocle" + s.charAt(0) = "emocle" + 'W' = "emocleW"
```

### Dynamic String Testing
```java
package day9;

public class ReverseString {
    public static void main(String[] args) {
        String s = "Java"; // Try different strings
        String reverse = "";
        
        for (int i = s.length() - 1; i >= 0; i--) {
            reverse = reverse + s.charAt(i);
        }
        
        System.out.println("Original: " + s);
        System.out.println("Reversed: " + reverse);
        // Output: Original: Java, Reversed: avaJ
    }
}
```

---

## Approach 2: Converting String to Character Array

### Logic Explanation
1. **Convert string to character array** using toCharArray()
2. **Read array elements from end to beginning**
3. **Concatenate characters** to reverse string
4. **No string methods used** (except toCharArray for conversion)

### Implementation

```java
package day9;

public class ReverseString {
    public static void main(String[] args) {
        // Approach 2: Using character array
        String s = "Welcome";
        String reverse = "";
        
        // Convert string to character array
        char[] a = s.toCharArray();
        
        // Read array from end to beginning
        for (int i = a.length - 1; i >= 0; i--) {
            reverse = reverse + a[i];
        }
        
        System.out.println("Original string: " + s);
        System.out.println("Reversed string: " + reverse);
    }
}
```

### Array Conversion Process
```java
String s = "Welcome";
char[] a = s.toCharArray();

// Array created:
// a[0] = 'W'
// a[1] = 'e' 
// a[2] = 'l'
// a[3] = 'c'
// a[4] = 'o'
// a[5] = 'm'
// a[6] = 'e'

// Reading from end: a[6], a[5], a[4], a[3], a[2], a[1], a[0]
// Result: 'e', 'm', 'o', 'c', 'l', 'e', 'W' = "emocleW"
```

---

## Approach 3: Using StringBuffer Class

### What is StringBuffer?
**StringBuffer is a mutable class in Java that provides a direct reverse() method.**

### Implementation

```java
package day9;

public class ReverseString {
    public static void main(String[] args) {
        // Approach 3: Using StringBuffer
        StringBuffer s = new StringBuffer("Welcome");
        
        System.out.println("Original string: " + s);
        System.out.println("Reversed string: " + s.reverse());
    }
}
```

**Output:**
```
Original string: Welcome
Reversed string: emocleW
```

### Key Points about StringBuffer
1. **Has built-in reverse() method**
2. **Mutable class** - can modify original content
3. **Must use `new` keyword** for creation
4. **Direct assignment not allowed:** `StringBuffer s = "Welcome";` ❌

---

## Approach 4: Using StringBuilder Class

### What is StringBuilder?
**StringBuilder is similar to StringBuffer - mutable class with reverse() method.**

### Implementation

```java
package day9;

public class ReverseString {
    public static void main(String[] args) {
        // Approach 4: Using StringBuilder
        StringBuilder s = new StringBuilder("Welcome");
        
        System.out.println("Original string: " + s);
        System.out.println("Reversed string: " + s.reverse());
    }
}
```

### StringBuffer vs StringBuilder
- **Both are mutable** classes
- **Both have reverse() method**
- **StringBuilder is faster** (not synchronized)
- **StringBuffer is thread-safe** (synchronized)

---

## Mutability vs Immutability

### What is Mutability?
**Mutable:** Objects that can be changed after creation.
**Immutable:** Objects that cannot be changed after creation.

### Example: Mutable (Array)

```java
package day9;
import java.util.Arrays;

public class MutableExample {
    public static void main(String[] args) {
        int[] a = {40, 10, 30, 20};
        
        System.out.println("Before sorting: " + Arrays.toString(a));
        Arrays.sort(a); // This changes the original array
        System.out.println("After sorting: " + Arrays.toString(a));
    }
}
```

**Output:**
```
Before sorting: [40, 10, 30, 20]
After sorting: [10, 20, 30, 40]
```

**Analysis:** The `Arrays.sort()` method **changed the original array**. This is **mutable behavior**.

### Example: Immutable (String)

```java
package day9;

public class ImmutableExample {
    public static void main(String[] args) {
        String s = "Welcome";
        
        System.out.println("Before concat: " + s);
        s.concat(" to Java"); // This does NOT change original string
        System.out.println("After concat: " + s);
        
        // To get concatenated result, store in variable
        String result = s.concat(" to Java");
        System.out.println("Concatenated result: " + result);
    }
}
```

**Output:**
```
Before concat: Welcome
After concat: Welcome
Concatenated result: Welcome to Java
```

**Analysis:** The `concat()` method **did NOT change the original string**. This is **immutable behavior**.

---

## String vs StringBuffer vs StringBuilder

### Comparison Example

```java
package day9;

public class StringComparison {
    public static void main(String[] args) {
        // String (Immutable)
        String s = "Welcome";
        s.concat(" to Java");
        System.out.println("String after concat: " + s); // Still "Welcome"
        
        // StringBuffer (Mutable)
        StringBuffer sb = new StringBuffer("Welcome");
        sb.append(" to Java");
        System.out.println("StringBuffer after append: " + sb); // "Welcome to Java"
        
        // StringBuilder (Mutable)
        StringBuilder sbuilder = new StringBuilder("Welcome");
        sbuilder.append(" to Java");
        System.out.println("StringBuilder after append: " + sbuilder); // "Welcome to Java"
    }
}
```

**Output:**
```
String after concat: Welcome
StringBuffer after append: Welcome to Java
StringBuilder after append: Welcome to Java
```

### Key Differences

| Feature | String | StringBuffer | StringBuilder |
|---------|--------|--------------|---------------|
| **Mutability** | Immutable | Mutable | Mutable |
| **Methods change original?** | No | Yes | Yes |
| **Concatenation method** | `concat()` | `append()` | `append()` |
| **Has reverse() method?** | No | Yes | Yes |
| **Creation syntax** | `String s = "text"` | `new StringBuffer("text")` | `new StringBuilder("text")` |
| **Thread safety** | N/A | Thread-safe | Not thread-safe |
| **Performance** | Slower for multiple operations | Slower than StringBuilder | Fastest |

### When to Use Which?
1. **String:** For simple operations, when content doesn't change frequently
2. **StringBuffer:** When you need thread safety and mutability
3. **StringBuilder:** When you need mutability and performance (most common choice)

---

## String Comparison: == vs equals()

### The Problem
When comparing strings, we can use `==` or `equals()` method. But they work differently!

### Rule to Remember
- **`==` compares objects** (memory references)
- **`equals()` compares values** (actual content)

---

## Scenario 1: Direct String Assignment

```java
package day9;

public class StringComparison {
    public static void main(String[] args) {
        // Scenario 1: Direct assignment
        String s1 = "Welcome";
        String s2 = "Welcome";
        
        System.out.println("s1 == s2: " + (s1 == s2));           // true
        System.out.println("s1.equals(s2): " + s1.equals(s2));   // true
    }
}
```

**Output:**
```
s1 == s2: true
s1.equals(s2): true
```

**Explanation:** When using direct assignment, Java optimizes by storing same strings in same memory location. Both comparisons work.

---

## Scenario 2: Using new Keyword

```java
package day9;

public class StringComparison {
    public static void main(String[] args) {
        // Scenario 2: Using new keyword
        String s1 = new String("Welcome");
        String s2 = new String("Welcome");
        
        System.out.println("Values: s1=" + s1 + ", s2=" + s2);
        System.out.println("s1 == s2: " + (s1 == s2));           // false
        System.out.println("s1.equals(s2): " + s1.equals(s2));   // true
    }
}
```

**Output:**
```
Values: s1=Welcome, s2=Welcome
s1 == s2: false
s1.equals(s2): true
```

**Explanation:**
- **`new` keyword creates separate objects** in memory
- **`==` compares objects:** s1 and s2 are different objects → false
- **`equals()` compares values:** Both contain "Welcome" → true

---

## Scenario 3: Mixed Assignment

```java
package day9;

public class StringComparison {
    public static void main(String[] args) {
        // Scenario 3: Mixed assignment
        String s1 = "ABC";                    // Direct assignment
        String s2 = new String("ABC");       // Object creation
        
        System.out.println("s1 == s2: " + (s1 == s2));           // false
        System.out.println("s1.equals(s2): " + s1.equals(s2));   // true
    }
}
```

**Output:**
```
s1 == s2: false
s1.equals(s2): true
```

**Explanation:**
- **s1 is a string literal, s2 is an object** → Different memory locations
- **`==` returns false** (different objects)
- **`equals()` returns true** (same values)

---

## Scenario 4: Object Reference Assignment

```java
package day9;

public class StringComparison {
    public static void main(String[] args) {
        // Scenario 4: Object reference assignment
        String s1 = "ABC";
        String s2 = new String("ABC");
        String s3 = s2;  // s3 refers to same object as s2
        
        System.out.println("s1 == s2: " + (s1 == s2));           // false
        System.out.println("s1.equals(s2): " + s1.equals(s2));   // true
        
        System.out.println("s2 == s3: " + (s2 == s3));           // true
        System.out.println("s2.equals(s3): " + s2.equals(s3));   // true
        
        System.out.println("s1 == s3: " + (s1 == s3));           // false
        System.out.println("s1.equals(s3): " + s1.equals(s3));   // true
    }
}
```

**Output:**
```
s1 == s2: false
s1.equals(s2): true
s2 == s3: true
s2.equals(s3): true
s1 == s3: false
s1.equals(s3): true
```

**Explanation:**
- **s3 = s2:** Both variables point to the same object
- **s2 == s3:** Same object reference → true
- **s1 == s3:** Different objects → false
- **All equals() comparisons:** Same values → true

---

## Best Practices for String Comparison

### 1. Always Use equals() for Value Comparison
```java
// ✅ Correct approach
if (str1.equals(str2)) {
    System.out.println("Strings are equal");
}

// ❌ Avoid this (unreliable)
if (str1 == str2) {
    System.out.println("May not work as expected");
}
```

### 2. Handle Null Values
```java
// ✅ Safe comparison
if (str1 != null && str1.equals(str2)) {
    System.out.println("Strings are equal");
}

// ✅ Alternative safe approach
if (Objects.equals(str1, str2)) {
    System.out.println("Strings are equal");
}
```

### 3. Use equalsIgnoreCase() for Case-Insensitive Comparison
```java
String s1 = "Welcome";
String s2 = "WELCOME";

System.out.println(s1.equals(s2));           // false
System.out.println(s1.equalsIgnoreCase(s2)); // true
```

---

## Summary of Key Concepts

### String Reversal
1. **No direct reverse() method** in String class
2. **Four approaches:** charAt() logic, array conversion, StringBuffer, StringBuilder
3. **Logic-based approaches** are preferred in interviews
4. **Built-in methods** (StringBuffer/StringBuilder) are for quick solutions

### Mutability
1. **String is immutable** - methods don't change original value
2. **StringBuffer and StringBuilder are mutable** - methods change original value
3. **Arrays are mutable** - methods can change original array

### String Comparison
1. **`==` compares object references** (memory locations)
2. **`equals()` compares actual values** (content)
3. **Always use equals()** for reliable string comparison
4. **Difference is visible** only when using `new` keyword

### Interview Tips
1. **Explain logic first** before mentioning built-in methods
2. **Demonstrate understanding** of mutability concepts
3. **Show multiple approaches** for string reversal
4. **Explain == vs equals()** with examples

---

## Practice Assignments

### Assignment 1: Check if String is Palindrome
**Goal:** Check if a string reads the same forwards and backwards.

**Examples:**
- "madam" → Palindrome ✓
- "hello" → Not Palindrome ✗

**Logic:**
1. **Reverse the string** using any method above
2. **Compare original with reversed** using equals()
3. **If equal:** Palindrome, **If not equal:** Not palindrome

**Template:**
```java
package day9;

public class PalindromeCheck {
    public static void main(String[] args) {
        String original = "madam";
        String reverse = "";
        
        // Your code here: Reverse the string
        
        // Compare original with reversed
        if (original.equals(reverse)) {
            System.out.println(original + " is a palindrome");
        } else {
            System.out.println(original + " is not a palindrome");
        }
    }
}
```

### Assignment 2: Remove Special Characters
**Goal:** Remove all special characters and keep only letters and numbers.

**Example:**
- Input: "Wel@come#123$"
- Output: "Welcome123"

**Hint:** Use replace() method or check each character using charAt().

### Assignment 3: Remove White Spaces
**Goal:** Remove all spaces from a string.

**Example:**
- Input: "W e l c o m e"
- Output: "Welcome"

**Hint:** Use replace() method to replace spaces with empty string.

### Assignment 4: Count Character Occurrences
**Goal:** Count how many times a specific character appears in a string.

**Example:**
- String: "programming"
- Character: 'r'
- Count: 2

**Logic:** Loop through string and count matches.

### Assignment 5: Count Words in String
**Goal:** Count the number of words in a string.

**Example:**
- Input: "Welcome to Java Programming"
- Output: 4 words

**Hint:** Use split() method with space as delimiter.

---

*This completes Session 9 on String Reversal and Comparison. These concepts are fundamental for interviews and practical programming. Practice all assignments to master string manipulation techniques!*