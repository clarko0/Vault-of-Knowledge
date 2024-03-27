Trie data structure is defined as a Tree based data structure that is used for storing some collection of strings and performing efficient search operations on them. The word Trie is derived from re***TRIE***val.

Trie follows a property that If two strings have a common prefix then they will have the same ancestor in the trie. A trie can be used to sort a collection of strings alphabetically as well as search whether a string with a given prefix is present in the trie or not.

## Need for Trie Data Structure?

A Trie data structure is used for storing and retrieval of data and the same operations could be done using another data structure which is Hash Table but Trie can perform these operations more efficiently than a Hash Table. Moreover, Trie has its own advantage over the Hash table. A Trie data structure can be used for ****prefix-based**** searching whereas a Hash table can’t be used in the same way.

![[Trie.png]]

```python
class TrieNode:

	def __init__(self):
		self.children = [None] * 26
		self.word_count = 0
```

Common algorithms for the Trie are:
- [[Trie - Insertion]]
- [[Trie - Search]]
- [[Trie - Deletion]]