### Overview
A dynamic array, growable array, resizable array, dynamic table, mutable array, or array list is a random access, variable-size list data structure that allows elements to be added or removed. It is supplied with standard libraries in many modern mainstream programming languages. Dynamic arrays overcome a limit of static arrays, which have a fixed capacity that needs to be specified at allocation.

### Pros:
- Constant time append, except if new element is out of capacity bounds.
- Data is easily cacheable.
- Allows for an array with dynamic length.
- Indexing takes constant time
### Cons:
- If a new element is out of bounds, it requires reallocation, which takes linear time, due to it moving all items in the array to a new allocation in memory.

In c++, the struct would look like:
```cpp
struct ArrayList {
    int* array;
    size_t size;
    size_t capacity;
}
```
