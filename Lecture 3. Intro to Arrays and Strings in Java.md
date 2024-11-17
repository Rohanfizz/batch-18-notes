
### **1. Arrays in Java**  
#### What are Arrays?  
- In Java, arrays are objects used to store multiple values of the same type.  
- Types:  
  - **1D Arrays**: Linear structure (e.g., `int[] arr = {1, 2, 3};`).  
  - **2D Arrays**: Grid-like structure (e.g., `int[][] matrix = {{1, 2}, {3, 4}};`).  
  - Arrays can have indexes from 0 to arr.length-1, if you give any other index, it will throw IndexOutOfBounds Exception.
  - `arr.length` will give you number of elements in the array
  - n = arr.length, then last index will be on n-1

#### Operations on Arrays in Java:  
1. **Initialization**  
   ```java
   int[] arr = new int[5]; // Creates an array of size 5
   arr[0] = 10;           // Assigns value 10 to the first element
   ```

2. **Traversal**  
   ```java
   for (int i = 0; i < arr.length; i++) {
       System.out.println(arr[i]);
   }
   ```

3. **2D Arrays**  
   ```java
   int[][] matrix = {
       {1, 2, 3},
       {4, 5, 6},
       {7, 8, 9}
   };
   for (int i = 0; i < matrix.length; i++) {
       for (int j = 0; j < matrix[i].length; j++) {
           System.out.print(matrix[i][j] + " ");
       }
       System.out.println();
   }
   ```

---

### **2. String Manipulation in Java**  
#### Strings in Java  
- Strings in Java are objects of the `String` class, immutable by design.  
- Example:  
  ```java
  String str = "hello";
  ```

#### Common String Methods:  
- `str.length()`: Returns the length of the string.  
- `str.toLowerCase()` / `str.toUpperCase()`: Converts the string to lowercase/uppercase.  
- `str.substring(start, end)`: Extracts a substring.  
- `str.charAt(index)`: Returns the character at the specified index.  
- `str.indexOf(substring)`: Finds the index of a substring (first occurance).  Avoid using this function
- `str.equals(other)`: Compares strings for equality.  
- `str.replace(old, new)`: Replaces all occurrences of a substring. Avoid using this function

#### Example: String Reversal  
```java
public class Main {
    public static void main(String[] args) {
        String ans = reverseString("abcdef");  
	System.out.println(ans);
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

#### Example: Check Palindrome  
```java
public class Main {
    public static void main(String[] args) {
        String str = "racecar";
        boolean isPalindrome = str.equals(new StringBuilder(str).reverse().toString());
        System.out.println(isPalindrome); // Output: true
    }
}
```

---

### **3. Problem-Solving with Arrays and Strings**  
#### **Reverse an Array**  
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int n = arr.length;

        for (int i = 0; i < n / 2; i++) {
            int temp = arr[i];
            arr[i] = arr[n - i - 1];
            arr[n - i - 1] = temp;
        }

        System.out.println(Arrays.toString(arr)); // Output: [5, 4, 3, 2, 1]
    }
}
```

#### **Find the Largest Element in an Array**  
```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {10, 20, 5, 50, 30};
        int max = arr[0];

        for (int num : arr) {
            if (num > max) {
                max = num;
            }
        }

        System.out.println("Largest element: " + max); // Output: 50
    }
}
```

#### **Two Sum Problem (Array)**  
```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        int[] result = twoSum(nums, target);

        System.out.println("Indices: [" + result[0] + ", " + result[1] + "]");
    }

    public static int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

#### **Longest Substring Without Repeating Characters**  
```java
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        String s = "abcabcbb";
        int length = lengthOfLongestSubstring(s);
        System.out.println("Length of longest substring: " + length); // Output: 3
    }

    public static int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left++));
            }
            set.add(s.charAt(right));
            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}
```

#### **Spiral Matrix Traversal (2D Array)**  We can cover this in the end.
```java
public class Main {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        spiralOrder(matrix);
    }

    public static void spiralOrder(int[][] matrix) {
        int top = 0, bottom = matrix.length - 1;
        int left = 0, right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) {
                System.out.print(matrix[top][i] + " ");
            }
            top++;

            for (int i = top; i <= bottom; i++) {
                System.out.print(matrix[i][right] + " ");
            }
            right--;

            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    System.out.print(matrix[bottom][i] + " ");
                }
                bottom--;
            }

            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    System.out.print(matrix[i][left] + " ");
                }
                left++;
            }
        }
    }
}
```

---

### Suggested Homework  
- Implement all the examples above in Java.  
- Add edge case handling (e.g., empty arrays, single elements).  
- Research and try advanced problems like "Group Anagrams" and "Rotate a Matrix".  

# Default value of primitive data types

|               |                   |                    |                                                        |
| ------------- | ----------------- | ------------------ | ------------------------------------------------------ |
| **Data Type** | **Default Value** | **Default size**   | **Range**                                              |
| **byte**      | 0                 | 1 byte or 8 bits   | -128 to 127                                            |
| **short**     | 0                 | 2 bytes or 16 bits | -32,768 to 32,767                                      |
| **int**       | 0                 | 4 bytes or 32 bits | 2,147,483,648 to 2,147,483,647                         |
| **long**      | 0                 | 8 bytes or 64 bits | 9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| **float**     | 0.0f              | 4 bytes or 32 bits | 1.4e-045 to 3.4e+038                                   |
| **double**    | 0.0d              | 8 bytes or 64 bits | 4.9e-324 to 1.8e+308                                   |
| **char**      | ‘\u0000’          | 2 bytes or 16 bits | 0 to 65536                                             |
| **boolean**   | FALSE             | 1 byte or 2 bytes  | 0 or 1                                                 |
## Class codes
```java
  
public class Main {  
    public static void main(String[] args) {  
//        boolean[] arr = new boolean[5]; // Make an array of length 5  
//        System.out.println(arr[-1]);  
  
//        int[] arr = {1, 2, 30, 4, 5};  
//        int n = arr.length;  
//  
//        for (int i = 0; i < n; i++) {  
//            System.out.println(arr[i]);  
//        }  
  
//        int[][] arr = new int[4][3];  
//        arr[0][1] = 100;  
//        System.out.println(arr[0][1]);  
        int[][] arr = {  
                {1, 2, 3},  
                {4, 5, 6},  
                {7, 8, 9},  
                {10, 20, 30}  
        };  
//        System.out.println(arr[2][2]);  
        int n = arr.length; // 4  
        int m = arr[0].length; // 3  
        for (int i = 0; i < n; i++) {  
            for (int j = 0; j < m; j++) {  
                System.out.println(arr[i][j]);  
            }  
        }  
    }  
}
```