# 08 - String Methods in Java

## Table of Contents
1. [What are String Methods?](#what-are-string-methods)
2. [String Creation Methods](#string-creation-methods)
3. [Basic String Methods](#basic-string-methods)
4. [String Comparison Methods](#string-comparison-methods)
5. [String Manipulation Methods](#string-manipulation-methods)
6. [String Extraction Methods](#string-extraction-methods)
7. [String Case Conversion](#string-case-conversion)
8. [String Splitting Methods](#string-splitting-methods)
9. [Combining Multiple Methods](#combining-multiple-methods)
10. [Practice Examples](#practice-examples)

---

## What are String Methods?

### Definition
**String methods are built-in functions provided by Java to perform various operations on string data.**

### Types of Methods in Java
1. **Built-in Methods:** Already implemented by Java (we just use them)
2. **User-defined Methods:** Custom methods we create ourselves

### How String Methods Work
```java
String s = "Welcome";
int length = s.length(); // Calling built-in method
System.out.println(length); // Output: 7
```

### Key Concepts
- **String is a predefined class** in Java
- **Methods belong to String class** and can be applied to string variables
- **Methods perform specific tasks** and return results
- **Dot notation** is used to call methods: `variable.methodName()`

---

## String Creation Methods

### Method 1: Direct Assignment (Most Common)
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome"; // Direct assignment
        System.out.println(s); // Output: Welcome
    }
}
```

### Method 2: Using String Constructor
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = new String("Welcome"); // Using constructor
        System.out.println(s); // Output: Welcome
    }
}
```

### Difference Between Two Methods
- **Direct assignment:** More commonly used, simpler syntax
- **Constructor method:** Creates String object explicitly
- **Both produce same output** but have internal differences (covered in advanced topics)
- **Use direct assignment** for regular programming

---

## Basic String Methods

### 1. length() Method
**Purpose:** Find the number of characters in a string.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        
        // Method 1: Store in variable
        int l = s.length();
        System.out.println("Length: " + l); // Output: Length: 7
        
        // Method 2: Direct printing
        System.out.println("Length: " + s.length()); // Output: Length: 7
        
        // Method 3: Direct on string value
        System.out.println("Length: " + "Welcome".length()); // Output: Length: 7
    }
}
```

### 2. concat() Method
**Purpose:** Join two or more strings together.

#### Basic Concatenation
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s1 = "Welcome";
        String s2 = "to Java";
        
        // Using + operator
        System.out.println(s1 + s2); // Output: Welcometo Java
        
        // Using concat() method
        System.out.println(s1.concat(s2)); // Output: Welcometo Java
    }
}
```

#### Concatenating Multiple Strings
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s1 = "Welcome";
        String s2 = "to Java";
        String s3 = "Automation";
        
        // Using + operator (easier for multiple strings)
        System.out.println(s1 + s2 + s3);
        
        // Using concat() method (chaining required)
        System.out.println(s1.concat(s2).concat(s3));
        
        // Mixed approach
        System.out.println(s1.concat(s2 + s3));
    }
}
```

#### Direct Value Concatenation
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        // Without variables
        System.out.println("Welcome" + "to Java");
        System.out.println("Welcome".concat("to Java"));
    }
}
```

### 3. trim() Method
**Purpose:** Remove spaces from the beginning and end of a string.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "   Welcome   "; // 3 spaces before and after
        
        System.out.println("Before trimming: '" + s + "'");
        System.out.println("Length before: " + s.length()); // 13 characters
        
        System.out.println("After trimming: '" + s.trim() + "'");
        System.out.println("Length after: " + s.trim().length()); // 7 characters
    }
}
```

**Output:**
```
Before trimming: '   Welcome   '
Length before: 13
After trimming: 'Welcome'
Length after: 7
```

### 4. charAt() Method
**Purpose:** Extract a specific character from a string based on index.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        //         0123456 (indices)
        
        // Extract specific characters
        System.out.println("Character at index 0: " + s.charAt(0)); // W
        System.out.println("Character at index 3: " + s.charAt(3)); // c
        System.out.println("Character at index 6: " + s.charAt(6)); // e
    }
}
```

**Important:** Index starts from 0, not 1.

---

## String Comparison Methods

### 1. contains() Method
**Purpose:** Check if a string contains another string as a substring.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        
        // Check if substring exists
        System.out.println(s.contains("Welcome")); // true
        System.out.println(s.contains("come"));    // true
        System.out.println(s.contains("W"));       // true
        System.out.println(s.contains("w"));       // false (case sensitive)
        System.out.println(s.contains("xyz"));     // false
    }
}
```

#### Important Rules for contains()
1. **Case sensitive:** 'W' and 'w' are different
2. **Sequence matters:** Characters must be in exact order
3. **Position doesn't matter:** Substring can be anywhere
4. **Returns boolean:** Always true or false

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        
        // Sequence must match exactly
        System.out.println(s.contains("Wel"));  // true
        System.out.println(s.contains("Wlm"));  // false (sequence broken)
        System.out.println(s.contains("come")); // true
        System.out.println(s.contains("moc"));  // false (reverse order)
    }
}
```

### 2. equals() Method
**Purpose:** Compare two strings for exact equality (case sensitive).

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s1 = "Welcome";
        String s2 = "Welcome";
        String s3 = "welcome";
        
        // Case sensitive comparison
        System.out.println(s1.equals(s2));        // true
        System.out.println(s1.equals(s3));        // false
        System.out.println(s1.equals("Welcome")); // true
        System.out.println(s1.equals("WELCOME")); // false
    }
}
```

### 3. equalsIgnoreCase() Method
**Purpose:** Compare two strings ignoring case differences.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s1 = "Welcome";
        
        // Case insensitive comparison
        System.out.println(s1.equals("welcome"));           // false
        System.out.println(s1.equalsIgnoreCase("welcome")); // true
        System.out.println(s1.equalsIgnoreCase("WELCOME")); // true
        System.out.println(s1.equalsIgnoreCase("WeLcOmE")); // true
    }
}
```

### Comparison: equals() vs equalsIgnoreCase()

| Method | Case Sensitive | "Welcome" vs "welcome" | "Welcome" vs "WELCOME" |
|--------|----------------|------------------------|------------------------|
| `equals()` | Yes | false | false |
| `equalsIgnoreCase()` | No | true | true |

---

## String Manipulation Methods

### 1. replace() Method
**Purpose:** Replace characters or substrings in a string.

#### Replacing Single Characters
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome to Selenium Java Selenium Python Selenium C#";
        
        // Replace single character
        System.out.println("Original: " + s);
        System.out.println("Replace 'e' with 'X': " + s.replace('e', 'X'));
    }
}
```

**Output:**
```
Original: Welcome to Selenium Java Selenium Python Selenium C#
Replace 'e' with 'X': WXlcomX to SXlXnium Java SXlXnium Python SXlXnium C#
```

#### Replacing Substrings
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome to Selenium Java Selenium Python Selenium C#";
        
        // Replace substring
        System.out.println("Replace 'Selenium' with 'Playwright':");
        System.out.println(s.replace("Selenium", "Playwright"));
    }
}
```

**Output:**
```
Replace 'Selenium' with 'Playwright':
Welcome to Playwright Java Playwright Python Playwright C#
```

#### Removing Characters/Substrings
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String amount = "$15,20,55";
        
        // Remove dollar sign and commas
        String cleanAmount = amount.replace("$", "").replace(",", "");
        System.out.println("Original: " + amount);
        System.out.println("Cleaned: " + cleanAmount);
    }
}
```

**Output:**
```
Original: $15,20,55
Cleaned: 152055
```

#### Multiple Character Replacement
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "abcaaccc";
        
        // Replace multiple different characters
        String result = s.replace('a', 'X').replace('c', 'Y');
        System.out.println("Original: " + s);
        System.out.println("After replacement: " + result);
        // Output: XbYXXYYY
    }
}
```

---

## String Extraction Methods

### 1. substring() Method
**Purpose:** Extract a portion of a string based on starting and ending indices.

#### Basic Syntax
```java
string.substring(startIndex, endIndex)
```

#### Important Rules
1. **Starting index:** Count from 0
2. **Ending index:** Count from 1 (or startIndex + 1)
3. **Ending index is exclusive:** Character at ending index is not included

#### Thumb Rule for substring()
- **Starting index:** Count from 0
- **Ending index:** Count from 1

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        //         0123456 (indices for reference)
        
        // Extract first 3 characters (W, e, l)
        System.out.println("First 3 chars: " + s.substring(0, 3)); // "Wel"
        
        // Extract "come" (indices 3, 4, 5, 6)
        System.out.println("Extract 'come': " + s.substring(3, 7)); // "come"
        
        // Extract single character
        System.out.println("Single char: " + s.substring(0, 1)); // "W"
        
        // Extract middle portion
        System.out.println("Middle portion: " + s.substring(1, 4)); // "elc"
    }
}
```

#### Practical Examples
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Selenium";
        //         01234567
        
        // Extract first 3 characters
        System.out.println("First 3: " + s.substring(0, 3)); // "Sel"
        
        // Extract last 4 characters  
        System.out.println("Last 4: " + s.substring(4, 8)); // "nium"
        
        // Extract middle portion
        System.out.println("Middle: " + s.substring(1, 5)); // "elen"
    }
}
```

#### substring() vs charAt()
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome";
        
        // Both extract single character at index 0
        System.out.println("Using substring: " + s.substring(0, 1)); // "W"
        System.out.println("Using charAt: " + s.charAt(0));           // 'W'
        
        // charAt returns char, substring returns String
    }
}
```

---

## String Case Conversion

### 1. toUpperCase() Method
**Purpose:** Convert entire string to uppercase.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome to Java";
        
        System.out.println("Original: " + s);
        System.out.println("Uppercase: " + s.toUpperCase());
    }
}
```

**Output:**
```
Original: Welcome to Java
Uppercase: WELCOME TO JAVA
```

### 2. toLowerCase() Method
**Purpose:** Convert entire string to lowercase.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "Welcome to Java";
        
        System.out.println("Original: " + s);
        System.out.println("Lowercase: " + s.toLowerCase());
    }
}
```

**Output:**
```
Original: Welcome to Java
Lowercase: welcome to java
```

### Mixed Case Example
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "WeLcOmE tO jAvA";
        
        System.out.println("Original: " + s);
        System.out.println("Uppercase: " + s.toUpperCase());
        System.out.println("Lowercase: " + s.toLowerCase());
    }
}
```

---

## String Splitting Methods

### 1. split() Method
**Purpose:** Split a string into multiple parts based on a delimiter.

#### Basic Email Example
```java
package day8;
import java.util.Arrays;

public class StringMethods {
    public static void main(String[] args) {
        String email = "abc@gmail.com";
        
        // Split based on @ symbol
        String[] parts = email.split("@");
        
        // Print all parts
        System.out.println("All parts: " + Arrays.toString(parts));
        
        // Extract username and domain
        System.out.println("Username: " + parts[0]); // "abc"
        System.out.println("Domain: " + parts[1]);   // "gmail.com"
    }
}
```

#### Why split() is Better Than substring()
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        // Problem with substring: Fixed indices
        String email1 = "abc@gmail.com";
        System.out.println("Username: " + email1.substring(0, 3)); // Works for "abc"
        
        String email2 = "abc123@gmail.com";
        System.out.println("Username: " + email2.substring(0, 3)); // Only gets "abc", not "abc123"
        
        // Solution with split: Dynamic extraction
        String[] parts1 = email1.split("@");
        String[] parts2 = email2.split("@");
        
        System.out.println("Username 1: " + parts1[0]); // "abc"
        System.out.println("Username 2: " + parts2[0]); // "abc123"
    }
}
```

#### Complex Splitting Example
```java
package day8;
import java.util.Arrays;

public class StringMethods {
    public static void main(String[] args) {
        String data = "ABC,123@XYZ";
        
        // Step 1: Split by comma
        String[] arr1 = data.split(",");
        System.out.println("After comma split: " + Arrays.toString(arr1));
        // Result: ["ABC", "123@XYZ"]
        
        // Step 2: Split second part by @
        String[] arr2 = arr1[1].split("@");
        System.out.println("After @ split: " + Arrays.toString(arr2));
        // Result: ["123", "XYZ"]
        
        // Extract all three parts
        System.out.println("Part 1: " + arr1[0]);  // "ABC"
        System.out.println("Part 2: " + arr2[0]);  // "123"
        System.out.println("Part 3: " + arr2[1]);  // "XYZ"
    }
}
```

#### Splitting by Space
```java
package day8;
import java.util.Arrays;

public class StringMethods {
    public static void main(String[] args) {
        String sentence = "ABC 123";
        
        // Split by space
        String[] words = sentence.split(" ");
        System.out.println("Words: " + Arrays.toString(words));
        // Output: ["ABC", "123"]
        
        // Multiple words
        String sentence2 = "ABC 123 XYZ";
        String[] words2 = sentence2.split(" ");
        System.out.println("Multiple words: " + Arrays.toString(words2));
        // Output: ["ABC", "123", "XYZ"]
    }
}
```

#### Important Notes about split()
1. **Returns String array:** Always store result in String[] variable
2. **Cannot print directly:** Use Arrays.toString() to print array
3. **Some symbols restricted:** Cannot use *, %, [], etc. as delimiters
4. **Common delimiters:** Space, comma, @, dot, colon, semicolon work fine

---

## Combining Multiple Methods

### Example 1: Case-Insensitive Contains Check
**Problem:** Check if "John" exists in "John Kennedy" ignoring case.

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String name = "John Kennedy";
        
        // This will return false (case sensitive)
        System.out.println(name.contains("john")); // false
        
        // Solution 1: Replace specific character
        System.out.println(name.replace("J", "j").contains("john")); // true
        
        // Solution 2: Convert entire string to lowercase
        System.out.println(name.toLowerCase().contains("john")); // true
    }
}
```

### Example 2: Clean and Extract Number
**Problem:** Extract clean number from "$15,20,55".

```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String amount = "$15,20,55";
        
        // Remove $ and commas
        String cleanAmount = amount.replace("$", "").replace(",", "");
        System.out.println("Original: " + amount);
        System.out.println("Clean: " + cleanAmount); // "152055"
    }
}
```

### Example 3: Multiple Method Chaining
```java
package day8;

public class StringMethods {
    public static void main(String[] args) {
        String s = "  Welcome to Java  ";
        
        // Chain multiple methods
        String result = s.trim().toUpperCase().replace(" ", "_");
        System.out.println("Original: '" + s + "'");
        System.out.println("Result: '" + result + "'");
        // Output: "WELCOME_TO_JAVA"
    }
}
```

---

## Practice Examples

### Example 1: Email Validation
```java
package day8;

public class StringPractice {
    public static void main(String[] args) {
        String email = "user@gmail.com";
        
        // Check if email contains @ and .com
        boolean hasAt = email.contains("@");
        boolean hasGmail = email.contains("gmail.com");
        
        System.out.println("Valid email format: " + (hasAt && hasGmail));
        
        // Extract username
        String[] parts = email.split("@");
        System.out.println("Username: " + parts[0]);
    }
}
```

### Example 2: Name Processing
```java
package day8;

public class StringPractice {
    public static void main(String[] args) {
        String fullName = "  john doe  ";
        
        // Clean and format name
        String cleanName = fullName.trim().toLowerCase();
        String[] nameParts = cleanName.split(" ");
        
        String firstName = nameParts[0].substring(0, 1).toUpperCase() + 
                          nameParts[0].substring(1);
        String lastName = nameParts[1].substring(0, 1).toUpperCase() + 
                         nameParts[1].substring(1);
        
        System.out.println("Formatted name: " + firstName + " " + lastName);
        // Output: "John Doe"
    }
}
```

### Example 3: Text Analysis
```java
package day8;

public class StringPractice {
    public static void main(String[] args) {
        String text = "Java is awesome. Java is powerful.";
        
        // Count occurrences of "Java"
        String[] words = text.split(" ");
        int javaCount = 0;
        
        for (String word : words) {
            if (word.replace(".", "").equals("Java")) {
                javaCount++;
            }
        }
        
        System.out.println("Text: " + text);
        System.out.println("'Java' appears " + javaCount + " times");
        System.out.println("Total words: " + words.length);
        System.out.println("Text length: " + text.length());
    }
}
```

### Example 4: Password Validation
```java
package day8;

public class StringPractice {
    public static void main(String[] args) {
        String password = "MyPass123";
        
        // Check password criteria
        boolean hasUpper = !password.equals(password.toLowerCase());
        boolean hasLower = !password.equals(password.toUpperCase());
        boolean hasNumber = password.contains("1") || password.contains("2") || 
                           password.contains("3") || password.contains("4") || 
                           password.contains("5") || password.contains("6") || 
                           password.contains("7") || password.contains("8") || 
                           password.contains("9") || password.contains("0");
        boolean validLength = password.length() >= 8;
        
        System.out.println("Password: " + password);
        System.out.println("Has uppercase: " + hasUpper);
        System.out.println("Has lowercase: " + hasLower);
        System.out.println("Has number: " + hasNumber);
        System.out.println("Valid length: " + validLength);
        System.out.println("Strong password: " + (hasUpper && hasLower && hasNumber && validLength));
    }
}
```

---

## Key Takeaways

### String Method Categories
1. **Information Methods:** `length()`, `charAt()`, `contains()`
2. **Comparison Methods:** `equals()`, `equalsIgnoreCase()`
3. **Manipulation Methods:** `concat()`, `replace()`, `trim()`
4. **Extraction Methods:** `substring()`, `split()`
5. **Conversion Methods:** `toUpperCase()`, `toLowerCase()`

### Important Rules
1. **String methods are case-sensitive** unless specified otherwise
2. **Index always starts from 0** in Java
3. **Methods can be chained** for complex operations
4. **Original string is not modified** - methods return new strings
5. **Import Arrays class** when using `Arrays.toString()` with split()

### Best Practices
1. **Use appropriate method** for the task (contains vs equals vs substring)
2. **Chain methods** when performing multiple operations
3. **Handle case sensitivity** explicitly when needed
4. **Use split() for dynamic extraction** instead of fixed substring indices
5. **Combine methods creatively** to solve complex problems

### Common Use Cases in Automation
1. **Text validation:** Checking page titles, error messages
2. **Data extraction:** Getting usernames from emails, extracting numbers
3. **String formatting:** Cleaning data, converting cases
4. **Content verification:** Checking if expected text exists on page
5. **Data processing:** Splitting CSV data, parsing responses

---

*This completes Session 8 on String Methods in Java. These methods are fundamental for text processing and are extensively used in automation testing. Practice combining different methods to solve complex string manipulation problems!*