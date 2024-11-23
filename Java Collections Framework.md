# Java Collections Framework

| **Interface/Class**       | **Description**                                                                                         | **Common Implementations**                     | **Key Methods**                        |
|----------------------------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------|-----------------------------------------|
| **Collection**             | The root interface for all collection types.                                                          | (Abstract)                                    | `add()`, `remove()`, `size()`, `iterator()` |
| **List**                   | An ordered collection that allows duplicate elements.                                                  | `ArrayList`, `LinkedList`, `Vector`, `Stack`  | `get()`, `add()`, `remove()`, `set()`   |
| **Set**                    | A collection that does not allow duplicate elements.                                                  | `HashSet`, `LinkedHashSet`, `TreeSet`         | `add()`, `remove()`, `contains()`       |
| **Queue**                  | A collection that processes elements in a specific order (FIFO or LIFO).                              | `PriorityQueue`, `LinkedList`, `Deque`        | `offer()`, `poll()`, `peek()`           |
| **Deque**                  | A double-ended queue, supporting insertion and removal at both ends.                                  | `ArrayDeque`, `LinkedList`                   | `addFirst()`, `addLast()`, `pollFirst()`|
| **Map**                    | An object that maps keys to values, where each key is unique.                                         | `HashMap`, `LinkedHashMap`, `TreeMap`, `WeakHashMap` | `put()`, `get()`, `remove()`, `keySet()` |
| **HashSet**                | A set implementation backed by a hash table.                                                         | —                                             | Inherits from `Set`                     |
| **LinkedHashSet**          | A set implementation that maintains insertion order.                                                 | —                                             | Inherits from `Set`                     |
| **TreeSet**                | A sorted set backed by a Red-Black Tree.                                                             | —                                             | Inherits from `Set`                     |
| **ArrayList**              | A resizable array implementation of the `List` interface.                                            | —                                             | Inherits from `List`                    |
| **LinkedList**             | A doubly-linked list implementation of `List` and `Deque`.                                           | —                                             | Inherits from `List` and `Deque`        |
| **Vector**                 | A synchronized implementation of `List`. Deprecated in modern usage.                                 | —                                             | Inherits from `List`                    |
| **Stack**                  | A last-in, first-out (LIFO) stack based on `Vector`.                                                 | —                                             | `push()`, `pop()`, `peek()`             |
| **HashMap**                | A hash table-based implementation of `Map`. Allows `null` keys and values.                           | —                                             | Inherits from `Map`                     |
| **LinkedHashMap**          | A `HashMap` that maintains insertion order.                                                          | —                                             | Inherits from `Map`                     |
| **TreeMap**                | A `Map` implementation that maintains a sorted order of keys.                                        | —                                             | Inherits from `Map`                     |
| **WeakHashMap**            | A `Map` implementation where keys are weak references and can be garbage-collected.                  | —                                             | Inherits from `Map`                     |
| **PriorityQueue**          | A queue that orders elements based on their natural ordering or a custom comparator.                 | —                                             | Inherits from `Queue`                   |
| **ArrayDeque**             | A resizable array-based implementation of `Deque`.                                                  | —                                             | Inherits from `Deque`                   |

---

### Key Points:
1. **Hierarchies**:
   - `Collection` is the parent interface for most classes like `List`, `Set`, and `Queue`.
   - `Map` is a separate hierarchy for key-value pairs.
2. **Thread Safety**:
   - Synchronized collections: `Vector`, `Stack`, and `Hashtable`.
   - Use `java.util.concurrent` for modern thread-safe collections.
3. **When to Use**:
   - Use `ArrayList` for dynamic arrays and frequent access.
   - Use `LinkedList` for frequent insertions/removals.
   - Use `HashMap` for fast key-value lookups.
   - Use `TreeSet`/`TreeMap` for sorted collections.
