1. Define a function ****insert(TrieNode *root, string &word)**** which will take two parameters one for the root and the other for the string that we want to insert in the Trie data structure.
2. Now take another pointer ****currentNode**** and initialize it with the ****root**** node.
3. Iterate over the length of the given string and check if the value is ****NULL**** or not in the array of pointers at the current character of the string.
    - If It’s ****NULL**** then, make a new node and point the current character to this newly created node.
    - Move the curr to the newly created node.
4. Finally, increment the **wordCount*** of the last **currentNode,*** this implies that there is a string ending currentNode.

Below is the implementation of the above algorithm:

```python
a_ASCII_VALUE = ord('a')

def insert_key(root, key):
	current_node = root
	
	for char in key:
		char_ascii_value = ord(char)
		index = char_ascii_value - a_ASCII_VALUE

		if current_node.children[index] == None:
			new_node = TrieNode()
			current_node.children[index] = new_node

		current_node = current_node.children[index]

	current_node.word_count += 1
```
