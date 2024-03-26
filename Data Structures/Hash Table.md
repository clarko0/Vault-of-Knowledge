### Overview
A hash table, also known as a hash map or a hash set, is a data structure that implements an associative array, also called a dictionary, which is an abstract data type that maps keys to values. A hash table uses a hash function to compute an index, also called a hash code, into an array of buckets or slots, from which the desired value can be found. During lookup, the key is hashed and the resulting hash indicates where the corresponding value is stored.

### Pros
- Search, Insertion, and Delete actions can be completed in constant time
### Cons
- Uses more space than other array-like data structures.


A simple implementation of a Hash Table in c++ looks like:
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

struct HashEntry {
    string key;
    int value;
    HashEntry(string key, int value) : key(key), value(value) {}
};

class HashTable {
private:
    vector<vector<HashEntry>> table;
    int size;

    int hash(const string& key) {
        int hashValue = 0;
        for (char c : key) {
            hashValue += c;
        }
        return hashValue % size;
    }

public:
    HashTable(int size) : size(size) {
        table.resize(size);
    }

    void insert(const string& key, int value) {
        int index = hash(key);
        for (auto& entry : table[index]) {
            if (entry.key == key) {
                entry.value = value;
                return;
            }
        }
        table[index].emplace_back(key, value);
    }

    int get(const string& key) {
        int index = hash(key);
        for (const auto& entry : table[index]) {
            if (entry.key == key) {
                return entry.value;
            }
        }
        return -1;
    }
};
```