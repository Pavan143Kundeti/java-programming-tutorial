# Session 20: Collections Framework in Java

## Table of Contents
1. [Introduction to Collections](#introduction-to-collections)
2. [Collections Hierarchy](#collections-hierarchy)
3. [ArrayList - List Collection](#arraylist---list-collection)
4. [HashSet - Set Collection](#hashset---set-collection)
5. [HashMap - Map Collection](#hashmap---map-collection)
6. [Comparison of Collections](#comparison-of-collections)
7. [When to Use Which Collection](#when-to-use-which-collection)
8. [Practice Examples](#practice-examples)
9. [Real-World Applications](#real-world-applications)

---

## Introduction to Collections

### What is a Collection?
**Collection** in English means a group of elements. In Java, **Collection** is a predefined interface that provides a framework for representing and manipulating groups of objects.

### Key Points About Collections
- **Collection** = Group of objects/elements/items
- **Collections Framework** = Set of interfaces and classes to handle groups of objects
- **Only Objects Allowed** = Collections can store only object types, not primitive types
- **Dynamic Size** = Collections can grow and shrink dynamically
- **Predefined Methods** = Rich set of methods for manipulation

### Why Use Collections?
- **Dynamic Size**: Unlike arrays, collections can grow/shrink at runtime
- **Rich Functionality**: Built-in methods for common operations
- **Object-Oriented**: Designed specifically for object manipulation
- **Type Safety**: Generic support for type-safe operations
- **Performance**: Optimized implementations for different use cases

---

## Collections Hierarchy

### Collection Interface Hierarchy
```
Collection (Interface)
├── List (Interface)
│   └── ArrayList (Class)
│   └── LinkedList (Class)
└── Set (Interface)
    └── HashSet (Class)
    └── LinkedHashSet (Class)

Map (Interface) - Independent
└── HashMap (Class)
└── LinkedHashMap (Class)
```

### Key Interfaces and Classes

| Interface | Implementation | Purpose |
|-----------|----------------|---------|
| **Collection** | Root interface | Base for all collections |
| **List** | ArrayList, LinkedList | Ordered, allows duplicates |
| **Set** | HashSet, LinkedHashSet | No duplicates allowed |
| **Map** | HashMap, LinkedHashMap | Key-value pairs |

### Important Notes
- **Collection** is the root interface
- **List** and **Set** extend Collection interface
- **Map** is independent (not part of Collection hierarchy)
- **Classes implement interfaces** (ArrayList implements List)
- **Common methods** available across similar collections

---
## ArrayList - List Collection

### What is ArrayList?
**ArrayList** is a class that implements the List interface. It's a dynamic array that can store heterogeneous objects and maintains insertion order.

### ArrayList Properties

| Property | Description | Example |
|----------|-------------|---------|
| **Heterogeneous Data** | Can store different types of objects | Integer, String, Boolean in same list |
| **Insertion Order Preserved** | Maintains the order of insertion | Elements stored as added |
| **Duplicates Allowed** | Same values can be stored multiple times | [100, 200, 100] is valid |
| **Multiple Nulls Allowed** | Can store multiple null values | [null, "data", null] is valid |
| **Indexing Supported** | Uses indexing algorithm (0, 1, 2...) | Access by index like arrays |
| **Dynamic Size** | No fixed size limitation | Can grow/shrink as needed |

### ArrayList Declaration

#### Different Ways to Declare ArrayList

```java
// 1. Basic Declaration (allows heterogeneous data)
ArrayList myList = new ArrayList();

// 2. Using List interface (polymorphism)
List myList = new ArrayList();

// 3. Generic Declaration (homogeneous data only)
ArrayList<String> stringList = new ArrayList<String>();
ArrayList<Integer> intList = new ArrayList<Integer>();
ArrayList<Employee> empList = new ArrayList<Employee>();

// 4. Using List interface with generics
List<String> stringList = new List<String>();
```

### ArrayList Operations

#### 1. Adding Elements
```java
import java.util.ArrayList;
import java.util.List;

public class ArrayListDemo {
    public static void main(String[] args) {
        // Create ArrayList
        ArrayList myList = new ArrayList();
        
        // Adding heterogeneous data
        myList.add(100);           // Integer (wrapper class)
        myList.add(10.5);          // Double (wrapper class)
        myList.add("Welcome");     // String
        myList.add('A');           // Character (wrapper class)
        myList.add(true);          // Boolean (wrapper class)
        myList.add(100);           // Duplicate allowed
        myList.add(null);          // Null allowed
        myList.add(null);          // Multiple nulls allowed
        
        System.out.println("ArrayList: " + myList);
        System.out.println("Size: " + myList.size());
    }
}
```

**Output:**
```
ArrayList: [100, 10.5, Welcome, A, true, 100, null, null]
Size: 8
```

#### 2. Removing Elements

##### Remove by Index
```java
public class ArrayListRemoveExample {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add(100);
        myList.add(10.5);
        myList.add("Welcome");
        myList.add('A');
        myList.add(true);
        
        System.out.println("Before removal: " + myList);
        
        // Remove element at index 2
        myList.remove(2);  // Removes "Welcome"
        
        System.out.println("After removal: " + myList);
    }
}
```

##### Remove Multiple Elements
```java
public class ArrayListRemoveMultiple {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add(100);
        myList.add("Welcome");
        myList.add(10.5);
        myList.add('A');
        
        // Create another list with elements to remove
        ArrayList toRemove = new ArrayList();
        toRemove.add(100);
        toRemove.add("Welcome");
        
        // Remove multiple elements
        myList.removeAll(toRemove);
        
        System.out.println("After removing multiple: " + myList);
    }
}
```

##### Clear All Elements
```java
// Remove all elements
myList.clear();
System.out.println("After clear: " + myList);
System.out.println("Is empty: " + myList.isEmpty()); // true
```

#### 3. Inserting Elements (Middle Position)
```java
public class ArrayListInsertExample {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add(100);
        myList.add(10.5);
        myList.add("Welcome");
        
        System.out.println("Before insertion: " + myList);
        
        // Insert "Java" at index 2
        myList.add(2, "Java");
        
        System.out.println("After insertion: " + myList);
    }
}
```

**Output:**
```
Before insertion: [100, 10.5, Welcome]
After insertion: [100, 10.5, Java, Welcome]
```

#### 4. Modifying Elements
```java
public class ArrayListModifyExample {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add("Java");
        myList.add("Python");
        myList.add("C++");
        
        System.out.println("Before modification: " + myList);
        
        // Replace element at index 1
        myList.set(1, "JavaScript");
        
        System.out.println("After modification: " + myList);
    }
}
```

#### 5. Accessing Elements
```java
public class ArrayListAccessExample {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add("Java");
        myList.add("Python");
        myList.add("C++");
        
        // Access specific element by index
        Object element = myList.get(1);
        System.out.println("Element at index 1: " + element);
        
        // Check if list contains specific element
        boolean contains = myList.contains("Java");
        System.out.println("Contains Java: " + contains);
    }
}
```

### Reading All Elements from ArrayList

#### Method 1: Normal For Loop
```java
public class ArrayListReadNormalFor {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add("Java");
        myList.add("Python");
        myList.add("C++");
        
        // Using normal for loop
        System.out.println("Using normal for loop:");
        for (int i = 0; i < myList.size(); i++) {
            System.out.println(myList.get(i));
        }
    }
}
```

#### Method 2: Enhanced For Loop (For-Each)
```java
public class ArrayListReadEnhancedFor {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add("Java");
        myList.add("Python");
        myList.add("C++");
        
        // Using enhanced for loop
        System.out.println("Using enhanced for loop:");
        for (Object element : myList) {
            System.out.println(element);
        }
    }
}
```

#### Method 3: Iterator
```java
import java.util.ArrayList;
import java.util.Iterator;

public class ArrayListReadIterator {
    public static void main(String[] args) {
        ArrayList myList = new ArrayList();
        myList.add("Java");
        myList.add("Python");
        myList.add("C++");
        
        // Using Iterator
        System.out.println("Using Iterator:");
        Iterator it = myList.iterator();
        while (it.hasNext()) {
            System.out.println(it.next());
        }
    }
}
```

### ArrayList with Generics (Type Safety)

#### String ArrayList
```java
import java.util.ArrayList;

public class ArrayListGenericsExample {
    public static void main(String[] args) {
        // Only String objects allowed
        ArrayList<String> stringList = new ArrayList<String>();
        
        stringList.add("Java");
        stringList.add("Python");
        stringList.add("JavaScript");
        // stringList.add(100); // Compile-time error
        
        System.out.println("String List: " + stringList);
        
        // Type-safe iteration
        for (String language : stringList) {
            System.out.println("Language: " + language.toUpperCase());
        }
    }
}
```

#### Custom Object ArrayList
```java
// Employee class
class Employee {
    private int id;
    private String name;
    
    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }
    
    @Override
    public String toString() {
        return "Employee{id=" + id + ", name='" + name + "'}";
    }
}

// Using Employee ArrayList
public class EmployeeArrayListExample {
    public static void main(String[] args) {
        ArrayList<Employee> employees = new ArrayList<Employee>();
        
        employees.add(new Employee(101, "John"));
        employees.add(new Employee(102, "Alice"));
        employees.add(new Employee(103, "Bob"));
        
        System.out.println("Employees:");
        for (Employee emp : employees) {
            System.out.println(emp);
        }
    }
}
```

---
## HashSet - Set Collection

### What is HashSet?
**HashSet** is a class that implements the Set interface. It uses hashing algorithm to store elements and doesn't maintain insertion order.

### HashSet Properties

| Property | Description | Example |
|----------|-------------|---------|
| **Heterogeneous Data** | Can store different types of objects | Integer, String, Boolean in same set |
| **Insertion Order NOT Preserved** | Does not maintain insertion order | Elements may appear in different order |
| **Duplicates NOT Allowed** | Automatically removes duplicate values | [100, 200, 100] becomes [100, 200] |
| **Single Null Allowed** | Only one null value allowed | Multiple nulls become single null |
| **No Indexing** | Uses hashing algorithm, no index concept | Cannot access by index |
| **Dynamic Size** | No fixed size limitation | Can grow/shrink as needed |

### HashSet Declaration

```java
// 1. Basic Declaration (allows heterogeneous data)
HashSet mySet = new HashSet();

// 2. Using Set interface (polymorphism)
Set mySet = new HashSet();

// 3. Generic Declaration (homogeneous data only)
HashSet<String> stringSet = new HashSet<String>();
HashSet<Integer> intSet = new HashSet<Integer>();

// 4. Using Set interface with generics
Set<String> stringSet = new HashSet<String>();
```

### HashSet Operations

#### 1. Adding Elements
```java
import java.util.HashSet;

public class HashSetDemo {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        
        // Adding heterogeneous data
        mySet.add(100);
        mySet.add(10.5);
        mySet.add("Welcome");
        mySet.add('A');
        mySet.add(true);
        mySet.add(100);        // Duplicate - will be ignored
        mySet.add(null);
        mySet.add(null);       // Multiple nulls - only one will remain
        
        System.out.println("HashSet: " + mySet);
        System.out.println("Size: " + mySet.size());
    }
}
```

**Output (order may vary):**
```
HashSet: [null, A, 100, Welcome, 10.5, true]
Size: 6
```

**Key Observations:**
1. **Insertion order not preserved** - elements appear in different order
2. **Duplicates removed** - only one 100 remains
3. **Single null** - multiple nulls become one

#### 2. Removing Elements

##### Remove by Value (Not Index)
```java
public class HashSetRemoveExample {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        mySet.add(100);
        mySet.add("Welcome");
        mySet.add(10.5);
        
        System.out.println("Before removal: " + mySet);
        
        // Remove by value (not index)
        mySet.remove(10.5);
        
        System.out.println("After removal: " + mySet);
    }
}
```

**Important:** HashSet doesn't support removal by index because it doesn't use indexing.

##### Clear All Elements
```java
// Remove all elements
mySet.clear();
System.out.println("After clear: " + mySet);
System.out.println("Is empty: " + mySet.isEmpty()); // true
```

#### 3. Accessing Elements

##### Cannot Access by Index
```java
// This is NOT possible in HashSet
// mySet.get(0); // No get() method available
```

##### Check if Element Exists
```java
public class HashSetAccessExample {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        mySet.add("Java");
        mySet.add("Python");
        mySet.add("C++");
        
        // Check if element exists
        boolean contains = mySet.contains("Java");
        System.out.println("Contains Java: " + contains);
        
        // Get size
        System.out.println("Size: " + mySet.size());
    }
}
```

##### Convert HashSet to ArrayList for Index Access
```java
import java.util.ArrayList;
import java.util.HashSet;

public class HashSetToArrayListExample {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        mySet.add("Java");
        mySet.add("Python");
        mySet.add("C++");
        
        // Convert HashSet to ArrayList
        ArrayList al = new ArrayList(mySet);
        
        // Now can access by index
        System.out.println("Element at index 0: " + al.get(0));
        System.out.println("Element at index 1: " + al.get(1));
    }
}
```

### Reading All Elements from HashSet

#### Method 1: Enhanced For Loop (Recommended)
```java
public class HashSetReadEnhancedFor {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        mySet.add("Java");
        mySet.add("Python");
        mySet.add("C++");
        
        // Using enhanced for loop
        System.out.println("Using enhanced for loop:");
        for (Object element : mySet) {
            System.out.println(element);
        }
    }
}
```

**Note:** Normal for loop is NOT possible because HashSet doesn't support indexing.

#### Method 2: Iterator
```java
import java.util.HashSet;
import java.util.Iterator;

public class HashSetReadIterator {
    public static void main(String[] args) {
        HashSet mySet = new HashSet();
        mySet.add("Java");
        mySet.add("Python");
        mySet.add("C++");
        
        // Using Iterator
        System.out.println("Using Iterator:");
        Iterator it = mySet.iterator();
        while (it.hasNext()) {
            System.out.println(it.next());
        }
    }
}
```

### HashSet with Generics

#### String HashSet
```java
import java.util.HashSet;

public class HashSetGenericsExample {
    public static void main(String[] args) {
        // Only String objects allowed
        HashSet<String> languages = new HashSet<String>();
        
        languages.add("Java");
        languages.add("Python");
        languages.add("JavaScript");
        languages.add("Java"); // Duplicate - will be ignored
        
        System.out.println("Languages: " + languages);
        System.out.println("Size: " + languages.size()); // 3, not 4
        
        // Type-safe iteration
        for (String language : languages) {
            System.out.println("Language: " + language);
        }
    }
}
```

### HashSet Limitations

| Operation | ArrayList | HashSet |
|-----------|-----------|---------|
| **Access by Index** | ✅ Supported | ❌ Not Supported |
| **Insertion at Specific Position** | ✅ Supported | ❌ Not Supported |
| **Maintain Insertion Order** | ✅ Yes | ❌ No |
| **Allow Duplicates** | ✅ Yes | ❌ No |
| **Multiple Nulls** | ✅ Yes | ❌ Only One |

### When to Use HashSet

Use HashSet when:
- ✅ You need to ensure **no duplicate elements**
- ✅ **Order doesn't matter**
- ✅ You need **fast lookup** operations
- ✅ You want to **eliminate duplicates** from data
- ✅ You don't need **index-based access**

Don't use HashSet when:
- ❌ You need to **maintain insertion order**
- ❌ You need **index-based access**
- ❌ You need to **allow duplicates**
- ❌ You need **multiple null values**

---
## HashMap - Map Collection

### What is HashMap?
**HashMap** is a class that implements the Map interface. It stores data in **key-value pairs** and uses hashing algorithm for storage.

### HashMap Properties

| Property | Description | Example |
|----------|-------------|---------|
| **Key-Value Pairs** | Data stored as pairs | {101="John", 102="Alice"} |
| **Unique Keys** | Keys cannot be duplicated | Same key overwrites old value |
| **Duplicate Values Allowed** | Values can be repeated | {101="John", 102="John"} |
| **No Insertion Order** | Uses hashing algorithm | Order may vary |
| **No Indexing** | No index-based access | Access by key only |
| **Dynamic Size** | Can grow/shrink as needed | No size limitation |

### HashMap Declaration

```java
// 1. Basic Declaration (allows any key-value types)
HashMap hm = new HashMap();

// 2. Using Map interface (polymorphism)
Map hm = new HashMap();

// 3. Generic Declaration (specify key and value types)
HashMap<Integer, String> empMap = new HashMap<Integer, String>();
HashMap<String, String> countryMap = new HashMap<String, String>();

// 4. Using Map interface with generics
Map<Integer, String> empMap = new HashMap<Integer, String>();
```

### HashMap Operations

#### 1. Adding Key-Value Pairs
```java
import java.util.HashMap;

public class HashMapDemo {
    public static void main(String[] args) {
        // Employee ID and Name mapping
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        
        // Adding key-value pairs using put() method
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        hm.put(104, "Diana");
        hm.put(102, "Charlie"); // Duplicate key - will replace Alice
        
        System.out.println("HashMap: " + hm);
        System.out.println("Size: " + hm.size());
    }
}
```

**Output:**
```
HashMap: {101=John, 102=Charlie, 103=Bob, 104=Diana}
Size: 4
```

**Key Observations:**
1. **Duplicate key handling** - 102 key value changed from "Alice" to "Charlie"
2. **Size is 4, not 5** - duplicate key doesn't increase size

#### 2. Accessing Values

##### Get Value by Key
```java
public class HashMapAccessExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Access value by key
        String name = hm.get(102);
        System.out.println("Employee 102: " + name);
        
        // Check if key exists
        boolean hasKey = hm.containsKey(104);
        System.out.println("Has key 104: " + hasKey);
        
        // Check if value exists
        boolean hasValue = hm.containsValue("John");
        System.out.println("Has value John: " + hasValue);
    }
}
```

##### Get All Keys
```java
public class HashMapKeysExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Get all keys
        System.out.println("All keys: " + hm.keySet());
    }
}
```

**Output:**
```
All keys: [101, 102, 103]
```

##### Get All Values
```java
public class HashMapValuesExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Get all values
        System.out.println("All values: " + hm.values());
    }
}
```

**Output:**
```
All values: [John, Alice, Bob]
```

##### Get All Key-Value Pairs
```java
public class HashMapEntriesExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Get all key-value pairs
        System.out.println("All entries: " + hm.entrySet());
    }
}
```

**Output:**
```
All entries: [101=John, 102=Alice, 103=Bob]
```

#### 3. Removing Pairs
```java
public class HashMapRemoveExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        System.out.println("Before removal: " + hm);
        
        // Remove by key
        hm.remove(102);
        
        System.out.println("After removal: " + hm);
    }
}
```

#### 4. Updating Values
```java
public class HashMapUpdateExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        
        System.out.println("Before update: " + hm);
        
        // Update value for existing key
        hm.put(101, "Johnny"); // Same key, new value
        
        System.out.println("After update: " + hm);
    }
}
```

### Reading All Data from HashMap

#### Method 1: Enhanced For Loop with keySet()
```java
import java.util.HashMap;

public class HashMapReadEnhancedFor {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Iterate through keys and get values
        System.out.println("Using Enhanced For Loop:");
        for (Integer key : hm.keySet()) {
            String value = hm.get(key);
            System.out.println(key + " = " + value);
        }
    }
}
```

#### Method 2: Iterator with entrySet()
```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map.Entry;

public class HashMapReadIterator {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        hm.put(101, "John");
        hm.put(102, "Alice");
        hm.put(103, "Bob");
        
        // Using Iterator with entrySet
        System.out.println("Using Iterator:");
        Iterator<Entry<Integer, String>> it = hm.entrySet().iterator();
        
        while (it.hasNext()) {
            Entry<Integer, String> entry = it.next();
            System.out.println(entry.getKey() + " = " + entry.getValue());
        }
    }
}
```

### Real-World HashMap Examples

#### Example 1: Country-Capital Mapping
```java
import java.util.HashMap;

public class CountryCapitalExample {
    public static void main(String[] args) {
        HashMap<String, String> countries = new HashMap<String, String>();
        
        // Add country-capital pairs
        countries.put("India", "New Delhi");
        countries.put("USA", "Washington DC");
        countries.put("UK", "London");
        countries.put("Japan", "Tokyo");
        
        // Display all countries and capitals
        System.out.println("Countries and Capitals:");
        for (String country : countries.keySet()) {
            String capital = countries.get(country);
            System.out.println(country + " -> " + capital);
        }
        
        // Find capital of specific country
        String capital = countries.get("India");
        System.out.println("\nCapital of India: " + capital);
    }
}
```

#### Example 2: Student Grades Management
```java
import java.util.HashMap;

public class StudentGradesExample {
    public static void main(String[] args) {
        HashMap<String, Integer> grades = new HashMap<String, Integer>();
        
        // Add student grades
        grades.put("Alice", 95);
        grades.put("Bob", 87);
        grades.put("Charlie", 92);
        grades.put("Diana", 88);
        
        // Display all grades
        System.out.println("Student Grades:");
        for (String student : grades.keySet()) {
            Integer grade = grades.get(student);
            System.out.println(student + ": " + grade);
        }
        
        // Update a grade
        grades.put("Bob", 90); // Bob's grade improved
        System.out.println("\nBob's updated grade: " + grades.get("Bob"));
        
        // Calculate average grade
        int total = 0;
        for (Integer grade : grades.values()) {
            total += grade;
        }
        double average = (double) total / grades.size();
        System.out.println("Average grade: " + average);
    }
}
```

#### Example 3: Phone Directory
```java
import java.util.HashMap;

public class PhoneDirectoryExample {
    public static void main(String[] args) {
        HashMap<String, String> phoneBook = new HashMap<String, String>();
        
        // Add contacts
        phoneBook.put("John", "123-456-7890");
        phoneBook.put("Alice", "987-654-3210");
        phoneBook.put("Bob", "555-123-4567");
        
        // Search for a contact
        String johnPhone = phoneBook.get("John");
        System.out.println("John's phone: " + johnPhone);
        
        // Add new contact
        phoneBook.put("Diana", "111-222-3333");
        
        // Display all contacts
        System.out.println("\nPhone Directory:");
        for (String name : phoneBook.keySet()) {
            System.out.println(name + ": " + phoneBook.get(name));
        }
        
        // Remove a contact
        phoneBook.remove("Bob");
        System.out.println("\nAfter removing Bob: " + phoneBook);
    }
}
```

### HashMap Utility Methods

#### Check Empty and Clear
```java
public class HashMapUtilityExample {
    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<Integer, String>();
        
        // Check if empty
        System.out.println("Is empty: " + hm.isEmpty()); // true
        
        // Add some data
        hm.put(1, "One");
        hm.put(2, "Two");
        
        System.out.println("Size: " + hm.size()); // 2
        System.out.println("Is empty: " + hm.isEmpty()); // false
        
        // Clear all data
        hm.clear();
        
        System.out.println("After clear - Size: " + hm.size()); // 0
        System.out.println("Is empty: " + hm.isEmpty()); // true
    }
}
```

### HashMap Limitations

| Operation | ArrayList | HashSet | HashMap |
|-----------|-----------|---------|---------|
| **Access by Index** | ✅ Yes | ❌ No | ❌ No |
| **Access by Key** | ❌ No | ❌ No | ✅ Yes |
| **Maintain Order** | ✅ Yes | ❌ No | ❌ No |
| **Allow Duplicates** | ✅ Yes | ❌ No | Keys: ❌ Values: ✅ |
| **Store Pairs** | ❌ No | ❌ No | ✅ Yes |

---
## Comparison of Collections

### ArrayList vs HashSet vs HashMap

| Feature | ArrayList | HashSet | HashMap |
|---------|-----------|---------|---------|
| **Interface** | List | Set | Map |
| **Data Storage** | Single objects | Single objects | Key-Value pairs |
| **Duplicates** | ✅ Allowed | ❌ Not allowed | Keys: ❌ Values: ✅ |
| **Insertion Order** | ✅ Preserved | ❌ Not preserved | ❌ Not preserved |
| **Indexing** | ✅ Supported (0,1,2...) | ❌ Not supported | ❌ Not supported |
| **Null Values** | ✅ Multiple nulls | ✅ Single null | Keys: Single, Values: Multiple |
| **Access Method** | By index: `get(index)` | No direct access | By key: `get(key)` |
| **Search Performance** | O(n) - Linear | O(1) - Constant | O(1) - Constant |
| **Use Case** | Ordered list with duplicates | Unique elements | Key-value mapping |

### Algorithm Comparison

| Collection | Algorithm | Order Maintained | Performance |
|------------|-----------|------------------|-------------|
| **ArrayList** | Indexing | ✅ Yes | Access: O(1), Search: O(n) |
| **HashSet** | Hashing | ❌ No | Access: O(1), Search: O(1) |
| **HashMap** | Hashing | ❌ No | Access: O(1), Search: O(1) |

---

## When to Use Which Collection

### Use ArrayList When:
- ✅ You need to **maintain insertion order**
- ✅ **Duplicate elements** are required
- ✅ You need **index-based access** (get, set, insert at position)
- ✅ You need to **allow multiple null values**
- ✅ **Sequential access** is more common than random access
- ✅ You're working with **ordered data** like lists, sequences

**Example Use Cases:**
- Shopping cart items
- Student grades in a class
- Steps in a process
- Menu items in order

### Use HashSet When:
- ✅ You need to **eliminate duplicates**
- ✅ **Order doesn't matter**
- ✅ You need **fast lookup** operations
- ✅ You want to check **membership** efficiently
- ✅ **Unique elements** are required

**Example Use Cases:**
- Unique user IDs
- Set of permissions
- Unique tags or categories
- Visited pages tracking

### Use HashMap When:
- ✅ You need **key-value pair** storage
- ✅ You need **fast lookup by key**
- ✅ You want to **associate data** (mapping)
- ✅ **Keys are unique** but values can be duplicate
- ✅ You need **dictionary-like** functionality

**Example Use Cases:**
- User ID to User details mapping
- Country to Capital mapping
- Configuration settings (key-value)
- Caching mechanisms
- Phone directory (name to number)

---

## Practice Examples

### Practice 1: Student Management System
```java
import java.util.*;

public class StudentManagementSystem {
    public static void main(String[] args) {
        // ArrayList for maintaining order of students
        ArrayList<String> studentNames = new ArrayList<String>();
        studentNames.add("Alice");
        studentNames.add("Bob");
        studentNames.add("Charlie");
        studentNames.add("Alice"); // Duplicate allowed
        
        // HashSet for unique subjects
        HashSet<String> subjects = new HashSet<String>();
        subjects.add("Math");
        subjects.add("Science");
        subjects.add("English");
        subjects.add("Math"); // Duplicate ignored
        
        // HashMap for student grades
        HashMap<String, Integer> grades = new HashMap<String, Integer>();
        grades.put("Alice", 95);
        grades.put("Bob", 87);
        grades.put("Charlie", 92);
        
        // Display results
        System.out.println("Students (with duplicates): " + studentNames);
        System.out.println("Unique subjects: " + subjects);
        System.out.println("Student grades: " + grades);
    }
}
```

### Practice 2: E-commerce Application
```java
import java.util.*;

public class EcommerceExample {
    public static void main(String[] args) {
        // ArrayList for shopping cart (order matters, duplicates allowed)
        ArrayList<String> shoppingCart = new ArrayList<String>();
        shoppingCart.add("Laptop");
        shoppingCart.add("Mouse");
        shoppingCart.add("Keyboard");
        shoppingCart.add("Mouse"); // Same item added again
        
        // HashSet for product categories (unique categories)
        HashSet<String> categories = new HashSet<String>();
        categories.add("Electronics");
        categories.add("Books");
        categories.add("Clothing");
        categories.add("Electronics"); // Duplicate ignored
        
        // HashMap for product prices
        HashMap<String, Double> productPrices = new HashMap<String, Double>();
        productPrices.put("Laptop", 999.99);
        productPrices.put("Mouse", 29.99);
        productPrices.put("Keyboard", 79.99);
        
        // Calculate total cart value
        double total = 0;
        for (String item : shoppingCart) {
            if (productPrices.containsKey(item)) {
                total += productPrices.get(item);
            }
        }
        
        System.out.println("Shopping Cart: " + shoppingCart);
        System.out.println("Categories: " + categories);
        System.out.println("Product Prices: " + productPrices);
        System.out.println("Total Cart Value: $" + total);
    }
}
```

### Practice 3: Library Management System
```java
import java.util.*;

public class LibraryManagementSystem {
    public static void main(String[] args) {
        // ArrayList for book checkout history (order and duplicates matter)
        ArrayList<String> checkoutHistory = new ArrayList<String>();
        checkoutHistory.add("Java Programming");
        checkoutHistory.add("Data Structures");
        checkoutHistory.add("Java Programming"); // Same book checked out again
        
        // HashSet for unique authors
        HashSet<String> authors = new HashSet<String>();
        authors.add("James Gosling");
        authors.add("Robert Martin");
        authors.add("Joshua Bloch");
        authors.add("James Gosling"); // Duplicate ignored
        
        // HashMap for book availability
        HashMap<String, Integer> bookInventory = new HashMap<String, Integer>();
        bookInventory.put("Java Programming", 5);
        bookInventory.put("Data Structures", 3);
        bookInventory.put("Clean Code", 7);
        
        // Display library information
        System.out.println("Checkout History: " + checkoutHistory);
        System.out.println("Unique Authors: " + authors);
        System.out.println("Book Inventory: " + bookInventory);
        
        // Check availability of a specific book
        String bookToCheck = "Java Programming";
        if (bookInventory.containsKey(bookToCheck)) {
            int available = bookInventory.get(bookToCheck);
            System.out.println(bookToCheck + " - Available copies: " + available);
        }
    }
}
```

---

## Real-World Applications

### 1. Web Application User Management
```java
import java.util.*;

public class UserManagementSystem {
    public static void main(String[] args) {
        // HashMap for user credentials
        HashMap<String, String> userCredentials = new HashMap<String, String>();
        userCredentials.put("john_doe", "password123");
        userCredentials.put("alice_smith", "securePass456");
        userCredentials.put("bob_wilson", "myPassword789");
        
        // HashSet for user permissions
        HashSet<String> adminPermissions = new HashSet<String>();
        adminPermissions.add("READ");
        adminPermissions.add("WRITE");
        adminPermissions.add("DELETE");
        adminPermissions.add("ADMIN");
        
        // ArrayList for user activity log
        ArrayList<String> activityLog = new ArrayList<String>();
        activityLog.add("john_doe logged in");
        activityLog.add("alice_smith created new post");
        activityLog.add("bob_wilson updated profile");
        activityLog.add("john_doe logged out");
        
        // Simulate login
        String username = "john_doe";
        String password = "password123";
        
        if (userCredentials.containsKey(username) && 
            userCredentials.get(username).equals(password)) {
            System.out.println("Login successful for: " + username);
            activityLog.add(username + " logged in successfully");
        } else {
            System.out.println("Invalid credentials");
        }
        
        System.out.println("Recent Activity: " + activityLog);
    }
}
```

### 2. Data Processing and Analytics
```java
import java.util.*;

public class DataAnalyticsExample {
    public static void main(String[] args) {
        // ArrayList for raw data (preserves order and duplicates)
        ArrayList<Integer> salesData = new ArrayList<Integer>();
        salesData.add(1000);
        salesData.add(1500);
        salesData.add(1200);
        salesData.add(1000); // Duplicate sale amount
        salesData.add(1800);
        
        // HashSet for unique customers
        HashSet<String> uniqueCustomers = new HashSet<String>();
        uniqueCustomers.add("Customer_A");
        uniqueCustomers.add("Customer_B");
        uniqueCustomers.add("Customer_C");
        uniqueCustomers.add("Customer_A"); // Duplicate ignored
        
        // HashMap for product sales count
        HashMap<String, Integer> productSales = new HashMap<String, Integer>();
        productSales.put("Laptop", 25);
        productSales.put("Mouse", 150);
        productSales.put("Keyboard", 75);
        productSales.put("Monitor", 40);
        
        // Analytics calculations
        int totalSales = 0;
        for (Integer sale : salesData) {
            totalSales += sale;
        }
        double averageSale = (double) totalSales / salesData.size();
        
        // Find best selling product
        String bestProduct = "";
        int maxSales = 0;
        for (String product : productSales.keySet()) {
            int sales = productSales.get(product);
            if (sales > maxSales) {
                maxSales = sales;
                bestProduct = product;
            }
        }
        
        // Display analytics
        System.out.println("Sales Data: " + salesData);
        System.out.println("Unique Customers: " + uniqueCustomers.size());
        System.out.println("Total Sales: $" + totalSales);
        System.out.println("Average Sale: $" + averageSale);
        System.out.println("Best Selling Product: " + bestProduct + " (" + maxSales + " units)");
    }
}
```

### 3. Configuration Management
```java
import java.util.*;

public class ConfigurationManager {
    public static void main(String[] args) {
        // HashMap for application configuration
        HashMap<String, String> appConfig = new HashMap<String, String>();
        appConfig.put("database.url", "jdbc:mysql://localhost:3306/mydb");
        appConfig.put("database.username", "admin");
        appConfig.put("database.password", "secret123");
        appConfig.put("app.version", "1.0.0");
        appConfig.put("debug.enabled", "true");
        
        // ArrayList for configuration loading order
        ArrayList<String> configLoadOrder = new ArrayList<String>();
        configLoadOrder.add("database.properties");
        configLoadOrder.add("application.properties");
        configLoadOrder.add("security.properties");
        
        // HashSet for required configurations
        HashSet<String> requiredConfigs = new HashSet<String>();
        requiredConfigs.add("database.url");
        requiredConfigs.add("database.username");
        requiredConfigs.add("app.version");
        
        // Validate configuration
        boolean isValid = true;
        for (String required : requiredConfigs) {
            if (!appConfig.containsKey(required)) {
                System.out.println("Missing required config: " + required);
                isValid = false;
            }
        }
        
        if (isValid) {
            System.out.println("Configuration is valid");
            System.out.println("App Version: " + appConfig.get("app.version"));
            System.out.println("Debug Mode: " + appConfig.get("debug.enabled"));
        }
        
        System.out.println("Config Load Order: " + configLoadOrder);
    }
}
```

---

## Key Takeaways

### Collections Framework Summary
- **Collections** provide dynamic, object-oriented data structures
- **Three main types**: List (ArrayList), Set (HashSet), Map (HashMap)
- **Choose based on requirements**: order, duplicates, access pattern

### Best Practices
1. **Use Generics** for type safety: `ArrayList<String>` instead of `ArrayList`
2. **Choose appropriate collection** based on use case requirements
3. **Use interface references** when possible: `List<String> list = new ArrayList<String>()`
4. **Consider performance** implications of different collections
5. **Handle null values** appropriately based on collection type

### Performance Guidelines
- **ArrayList**: Best for indexed access and sequential processing
- **HashSet**: Best for uniqueness checks and fast lookups
- **HashMap**: Best for key-based access and mapping relationships

### Common Use Cases in Automation Testing
- **ArrayList**: Test data lists, step sequences, result collections
- **HashSet**: Unique test IDs, environment configurations
- **HashMap**: Test parameters, configuration settings, data-driven testing

---

**Next Session Preview**: We have completed the core Java fundamentals! In upcoming sessions, we'll start applying these concepts in **Selenium WebDriver automation**, where you'll see how collections, OOP concepts, and exception handling are used in real-world test automation scenarios.