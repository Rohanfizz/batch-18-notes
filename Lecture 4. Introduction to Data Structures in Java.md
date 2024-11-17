
#### 1. **Lists**
- **Definition**: A List is an ordered collection that allows duplicate elements.
- **Common Implementation**: `ArrayList`
  - Resizable array.
  - Elements are indexed, starting from `0`.
- **Common Use Cases**:
  - Maintaining an ordered collection.
  - Frequently accessing elements by index.
  - Allowing duplicates (e.g., a shopping cart with the same items multiple times).
- **Key Methods**:
  ```java
  ArrayList<String> list = new ArrayList<>();
  list.add("Apple");       // Add an element
  list.get(0);             // Access element at index 0
  list.remove("Apple");    // Remove element
  list.size();             // Get size of the list
  list.contains("Apple");  // Check if element exists
  ```

#### 2. **Sets**
- **Definition**: A Set is a collection that does not allow duplicate elements.
- **Common Implementation**: `HashSet`
  - Backed by a hash table.
  - No guarantee of order.
- **Common Use Cases**:
  - Ensuring uniqueness in a collection (e.g., storing unique usernames).
  - Efficient lookups and deletions.
- **Key Methods**:
  ```java
  HashSet<Integer> set = new HashSet<>();
  set.add(10);            // Add an element
  set.contains(10);       // Check if element exists
  set.remove(10);         // Remove element
  set.size();             // Get size of the set
  ```

#### 3. **Maps**
- **Definition**: A Map is a collection that maps keys to values, with no duplicate keys.
- **Common Implementation**: `HashMap`
  - Backed by a hash table.
  - Keys must be unique; values can be duplicated.
- **Common Use Cases**:
  - Associating keys with values (e.g., storing student IDs and their grades).
  - Fast lookups by key.
- **Key Methods**:
  ```java
  HashMap<String, Integer> map = new HashMap<>();
  map.put("Apple", 3);       // Add key-value pair
  map.get("Apple");          // Retrieve value for key
  map.containsKey("Apple");  // Check if key exists
  map.remove("Apple");       // Remove key-value pair
  map.size();                // Get size of the map
  ```

#### **Differences**
| Feature        | List               | Set                 | Map                     |
|----------------|--------------------|---------------------|-------------------------|
| Duplicates     | Allowed            | Not allowed         | Keys: Not allowed; Values: Allowed |
| Order          | Preserved          | Not guaranteed      | Not guaranteed          |
| Null elements  | Allowed            | Allowed (1 null)    | Keys: 1 null; Values: Multiple nulls |
| Common Use Case| Ordered collections| Unique elements     | Key-value pairs         |

---

### Practice Problems
#### **Easy**
1. Write a program to create a list of integers, add elements, and print the elements in reverse order.
2. Write a program to store unique strings using a `HashSet`. Check if a specific string exists in the set.
3. Write a program to create a `HashMap` with city names as keys and their populations as values. Retrieve and print the population for a specific city.

#### **Medium**
4. Given a list of integers, return a list with duplicates removed, preserving the original order.  
5. Write a program to count the frequency of characters in a given string using a `HashMap`.  
6. Implement a program to find the intersection of two sets of integers.

#### **Hard**
7. Write a program to group anagrams together using a `HashMap`. Example input: `["bat", "tab", "cat"]`, Output: `[["bat", "tab"], ["cat"]]`.  
8. Implement a Least Recently Used (LRU) Cache using `LinkedHashMap`.  
9. Write a program to perform a word frequency count from a file and display the top 3 most frequent words.  