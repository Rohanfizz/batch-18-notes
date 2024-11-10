### 1. Java Virtual Machine (JVM)

- **Purpose:** JVM is responsible for running Java bytecode, making Java platform-independent. It acts as an interpreter between the compiled Java code and the host machine.
- **Functionality:** It provides core functions like memory management, garbage collection, and ensuring code security. It takes the `.class` files (compiled Java files) and converts them into machine code that can be executed on the host operating system.
- **Portability:** Since JVM abstracts the underlying platform, Java programs can run on any system with a compatible JVM, which is the cornerstone of Java’s "write once, run anywhere" capability.

### 2. Java Runtime Environment (JRE)

- **Purpose:** JRE provides the environment to execute Java applications.
- **Components:** It includes the JVM, along with standard libraries and supporting files necessary for running Java applications but does not include development tools.
- **Use Case:** When you just need to run Java applications without developing them, the JRE is sufficient. It’s commonly used by end-users who want to run Java applications on their systems.

### 3. Java Development Kit (JDK)

- **Purpose:** JDK is a development kit required to build Java applications.
- **Components:** It includes the JRE (which contains the JVM and libraries) and additional tools like the compiler (`javac`), Java debugger (`jdb`), and other tools for development.
- **Use Case:** Developers use the JDK to write, compile, and debug Java programs. The JDK is essential for creating new applications, whereas the JRE alone suffices for running them.
- ![[Pasted image 20241110174840.png]]

### Java Basics: Variables, Data Types, and Operators

#### 1. Variables
- **Definition:** Variables are containers for storing data values. Each variable in Java has a data type, which determines what kind of data it can hold.
- **Declaration:** Variables must be declared before use (e.g., `int num;`).
- **Types of Variables:**
  - **Local Variables:** Declared inside methods, constructors, or blocks.
  - **Instance Variables:** Declared inside a class but outside any method, and are specific to each instance of a class.
  - **Static Variables:** Declared with the `static` keyword and shared among all instances of a class.

#### 2. Data Types
- **Primitive Data Types:** Built-in types that store values directly.
  - Examples: `int`, `double`, `float`, `boolean`, `char`, `byte`, `short`, `long`
- **Reference Data Types:** Used to refer to objects.
  - Examples: `String`, arrays, user-defined objects.
  - int = -2^31 to 2^31-1 
  - long -2^63 to 2^63-1

#### 3. Operators
- **Arithmetic Operators:** `+`, `-`, `*`, `/`, `%`
- **Relational Operators:** `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical Operators:** `&&`, `||`, `!`
- **Assignment Operators:** `=`, `+=`, `-=`, `*=`, `/=`, etc.
- **Increment/Decrement Operators:** `++`, `--`

---

### Control Statements (If, Switch, Loops)

#### 1. If-Else Statements
- Used to execute a block of code if a condition is true; `else` provides an alternative when the condition is false.
  ```java
  if (condition) {
      // code to execute if condition is true
  } else {
      // code to execute if condition is false
  }
  ```

#### 2. Switch Statement
- Provides multiple options (cases) to be executed based on the value of a variable.
  ```java
  switch (expression) {
      case value1:
          // code
          break;
      case value2:
          // code
          break;
      default:
          // code
  }
  ```

#### 3. Loops
- **For Loop:** Executes a block of code a specific number of times.
  ```java
  for (int i = 0; i < 10; i++) {
      // code
  }
  ```
- **While Loop:** Repeats code as long as the condition is true.
  ```java
  while (condition) {
      // code
  }
  ```
- **Do-While Loop:** Similar to while, but ensures code runs at least once.
  ```java
  do {
      // code
  } while (condition);
  ```

---

### Introduction to Functions and Methods

- **Functions (Methods):** Blocks of code that perform a specific task, defined in a class, and executed when called.
  - **Syntax:** 
    ```java
    returnType methodName(parameters) {
        // code
        return value;
    }
    ```
- **Parameters and Return Types:** Methods can accept parameters and return values.
  - Example:
    ```java
    public int add(int a, int b) {
        return a + b;
    }
    ```
- **Calling Methods:** 
  - **Static Methods:** Called using the class name (e.g., `ClassName.methodName()`).
  - **Instance Methods:** Called on an instance of the class (e.g., `object.methodName()`).

---


# Activity 🙌
### Question 1: Print Right-Angled Triangle Pattern
- **Problem:** Given an integer `n`, print a right-angled triangle pattern of `*` with `n` rows.
- **Example:**

  ```plaintext
  Input:
  n = 4

  Output:
  *
  **
  ***
  ****
  ```

- **Explanation:** Each row contains `i` asterisks (`*`), where `i` is the row number (starting from 1).

---

### Question 2: Print Inverted Right-Angled Triangle Pattern
- **Problem:** Given an integer `n`, print an inverted right-angled triangle pattern of `*` with `n` rows.
- **Example:**

  ```plaintext
  Input:
  n = 4

  Output:
  ****
   ***
    **
     *
  ```

- **Explanation:** The first row contains `n` asterisks, and each subsequent row decreases by one asterisk. Each row is indented by one additional space compared to the previous row.

---

### Question 3: Print Pyramid Pattern
- **Problem:** Given an integer `n`, print a pyramid pattern of `*` with `n` rows. N will always be odd.
- **Example:**

  ```plaintext
  Input:
  n = 7

  Output:
     *
    ***
   *****
  *******
  ```

- **Explanation:** The pyramid pattern has `n` rows, where the `i`-th row has `(2 * i - 1)` asterisks, centered with spaces.

---

### Question 4: Print Diamond Pattern
- **Problem:** Given an integer `n`, print a diamond pattern of `*` with `n` rows on the top half and `n-1` rows on the bottom half. N will always be odd.
- **Example:**

  ```plaintext
  Input:
  n = 7

  Output:
     *
    ***
   *****
  *******
   *****
    ***
     *
  ```

- **Explanation:** The diamond pattern is essentially a pyramid followed by an inverted pyramid, where the top half has `n` rows and the bottom half has `n-1` rows.

___
### Basic Debugging in IntelliJ IDEA

#### 1. Setting Breakpoints
- **Breakpoint:** A marker to pause execution at a specific line.
- To set: Click in the gutter next to the line of code.

#### 2. Running in Debug Mode
- Start the application in Debug mode (usually by clicking the Debug icon).
- Execution will pause at breakpoints, allowing inspection of the program state.

#### 3. Stepping Through Code
- **Step Over (F8):** Executes the current line and moves to the next.
- **Step Into (F7):** Enters into any function/method called in the current line.
- **Step Out (Shift+F8):** Exits the current method and returns to the calling code.

#### 4. Inspecting Variables
- **Variables Window:** View values of variables in scope.
- **Evaluate Expression:** Allows manual inspection and evaluation of expressions to test assumptions or debug issues. 

