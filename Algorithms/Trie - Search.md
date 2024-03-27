Search operation in Trie is performed in a similar way as the insertion operation but the only difference is that whenever we find that the array of pointers in ****curr node**** does not point to the ****current character**** of the ****word**** then return false instead of creating a new node for that current character of the word. 

This operation is used to search whether a string is present in the Trie data structure or not. There are two search approaches in the Trie data structure.

1. Find whether the given word exists in Trie.
2. Find whether any word that starts with the given prefix exists in Trie.

There is a similar search pattern in both approaches. The first step in searching a given word in Trie is to convert the word to characters and then compare every character with the trie node from the root node. If the current character is present in the node, move forward to its children. Repeat this process until all characters are found.

Search for the prefix “ ***an*** ” in the Trie Data Structure.
![[Search for prefix an in Trie.png]]

Prefix search:
```python
a_ASCII_VALUE = ord('a')

def prefix_exits(root, key):
	current_node = root
	
	for char in key:
		char_ascii_value = ord(char)
		index = char_ascii_value - a_ASCII_VALUE
		child_value = current_node.children[index]

		if child_value is None:
			return False

		current_node = child_value

	return True
```

Word search:

```python
def search_word(root, word):
	current_node = root

	for char in word:
		char_ascii_value = ord(char)
		index = char_ascii_value - a_ASCII_VALUE
		if current_node.children[index] is None:
			return False

	return current_node.word_count > 0
```
