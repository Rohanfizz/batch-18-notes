
#### 1. ArrayList
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
  - No indexing is there
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
  map.getOrDefault("Apple",1) // if apple not found return 1, else return apple ki value
  ```

#### **Differences**
| Feature         | List                | Set              | Map                                  |
| --------------- | ------------------- | ---------------- | ------------------------------------ |
| Duplicates      | Allowed             | Not allowed      | Keys: Not allowed; Values: Allowed   |
| Order           | Preserved           | Not guaranteed   | Not guaranteed                       |
| Null elements   | Allowed             | Allowed (1 null) | Keys: 1 null; Values: Multiple nulls |
| Common Use Case | Ordered collections | Unique elements  | Key-value pairs                      |

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

# Class Codes
Two Sum: https://leetcode.com/problems/two-sum/
```java
public int[] twoSum(int[] nums, int target) {

        HashMap<Integer,Integer> hm = new HashMap<>();

  

        for(int i = 0; i < nums.length;i++){

            int partner = target - nums[i];

  

            // if partner exists in hm

            if(hm.containsKey(partner)){

                int[] ans = new int[2];

                ans[0] = hm.get(partner);

                ans[1] = i;

                return ans;

            }else{ // partner does not exist in hm

                // add myself

                hm.put(nums[i],i);

            }

        }

        return new int[0];

    }
```

class codes:
```java
import java.util.*;  
  
public class Main {  
    public static void main(String[] args) {  
//        boolean[] arr = new boolean[5]; // Make an array of length 5  
//        System.out.println(arr[-1]);  
//  
//        int[] arr = {1, 2, 30, 4, 5};  
//        arr[0] = 10;  
//        int n = arr.length;  
//  
//        for (int i = 0; i < n; i++) {  
//            System.out.println(arr[i]);  
//        }  
  
//        int[][] arr = new int[4][3];  
//        arr[0][1] = 100;  
//        System.out.println(arr);  
//        int[][] arr = {  
//                {1, 2, 3},  
//                {4, 5, 6},  
//                {7, 8, 9},  
//                {10, 20, 30}  
//        };  
//        System.out.println(arr[2][2]);  
//        int n = arr.length; // 4  
//        int m = arr[0].length; // 3  
//        for (int i = 0; i < n; i++) {  
//            for (int j = 0; j < m; j++) {  
//                System.out.println(arr[i][j]);  
//            }  
//        }  
//        stringIntro();  
  
//        String ans = reverseString("abcdef");  
//        System.out.println(ans);  
  
//        arrayListPractice();  
//        setPractice();  
//        hashmapPractice();  
        ArrayList<Integer> arr = new ArrayList<>();  
        arr.add(1);  
        arr.add(2);  
        arr.add(3);  
        arr.add(2);  
        arr.add(1);  
        printBarChart(arr);  
    }  
  
    private static void printBarChart(ArrayList<Integer> arr) {  
        // width  
        int w = arr.size();  
        // height  
        int h = getMaxEle(arr);  
  
        for (int curr = h; curr > 0; curr--) {  
            String str = "";  
            for (int i = 0; i < arr.size(); i++) {  
                // Check if arr[i] will be able to reach curr or not  
                if( arr.get(i) >= curr ){  
                    str = str + "*";  
                }else{  
                    str = str + " ";  
                }  
            }  
            System.out.println(str);  
        }  
    }  
  
    private static int getMaxEle(ArrayList<Integer> arr) {  
        int maxi = Integer.MIN_VALUE;  
        for (int i = 0; i < arr.size(); i++) {  
            if (arr.get(i) > maxi) {  
                maxi = arr.get(i);  
            }  
        }  
        return maxi;  
    }  
  
  
    private static void setPractice() {  
        HashSet<Integer> set = new HashSet<>();  
        set.add(10);  
        set.add(10);  
        set.remove(10);  
        set.add(20);  
        System.out.println(set.contains(10));  
    }  
  
    private static void hashmapPractice() {  
        HashMap<String, Integer> hm = new HashMap<>();  
        hm.put("Rohan", 123);  
        hm.put("Shwetank", 123);  
        hm.put("Vinod", 456);  
        hm.put("Vinod", 101);  
        System.out.println(hm.get("Vinod"));  
        hm.remove("Rohan");  
        System.out.println(hm.containsKey("Rohan"));  
    }  
  
    private static void arrayListPractice() {  
        ArrayList<Integer> arr = new ArrayList<>();  
        System.out.println(arr.size()); // 0  
        arr.add(10);  
        arr.add(20);  
        arr.add(30);  
        arr.add(40);  
        System.out.println(arr); // [10, 20, 30, 40]  
        System.out.println(arr.get(1));  
        arr.remove(arr.size() - 1);  
        System.out.println(arr);  
        System.out.println(arr.contains(50));  
    }  
  
    public static void stringIntro() {  
        String str = "AbbcabBc";  
        int len = str.length();  
        System.out.println(str.length()); // 8  
  
        str = str.toLowerCase();  
        System.out.println(str); // abbcabbc  
  
        str = str.toUpperCase();  
        System.out.println(str); // ABBCABBC  
  
        String substr = str.substring(3, 6);  
        System.out.println(substr); // CAB  
  
        System.out.println(str.charAt(len - 1));  
  
        System.out.println(str.indexOf("BB"));  
  
        System.out.println(str.equals("ACBCABBC ")); // false  
  
        String newStr = str.replace("BB", "XX");  
        System.out.println(newStr);  
  
        String s = str + " " + newStr;  
        System.out.println(s);  
    }  
  
    public static String reverseString(String s) {  
        String ans = "";  
        for (int i = s.length() - 1; i >= 0; i--) {  
            ans = ans + s.charAt(i);  
        }  
        return ans;  
    }  
}
```