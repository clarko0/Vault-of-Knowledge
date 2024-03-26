### Overview
An array is a data structure consisting of a collection of elements (values or variables), of same memory size, each identified by at least one array index.

An array is stored such that the position of each element can be computed from its index tuple by a mathematical formula.

An array of: `10`, `32int (4 bytes)` may be stored as 10 words at memory addresses: `2000`, `2004`, `2008`, ..., `2036` (in hexadecimal: `0x7D0`, `0x7D4`, `0x7D8`, ..., `0x7F4`).

In c++, to define an array, it looks like:
```cpp
int my_ints[4] = {10, 20, 30, 40};
```

### Pros:
- Constant time indexing
- Easily cacheable (data isn't fragmented in memory)
### Cons:
- Linear time deletion
- Linear time search