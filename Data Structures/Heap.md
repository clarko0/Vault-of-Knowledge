A Heap is a special Tree-based Data Structure in which the tree is a complete [[Binary Tree]].

### Type of heaps:

1. Max-Heap: In this heap, the value of the root node must be the greatest among all its child nodes and the same this must be done for its left and right sub-tree also.
2. Min-Heap: In this heap, the value of the root node must be the smallest among all its child nodes and the same thing must be done for its left and right sub-tree also.

![[Heap.png]]

## Properties of Heap:

#### Heap has the following Properties:

- **Complete Binary Tree:** A heap tree is a complete binary tree, meaning all levels of the tree are fully filled except possibly the last level, which is filled from left to right. This property ensures that the tree is efficiently represented using an array.
- **Heap Property:** This property ensures that the minimum (or maximum) element is always at the root of the tree according to the heap type.
- **Parent-Child Relationship:** The relationship between a parent node at index **‘i’** and its children is given by the formulas: left child at index **2i+1** and right child at index **2i+2** for 0-based indexing of node numbers.
- **Efficient Insertion and Removal:** Insertion and removal operations in heap trees are efficient. New elements are inserted at the next available position in the bottom-rightmost level, and the heap property is restored by comparing the element with its parent and swapping if necessary. Removal of the root element involves replacing it with the last element and heapifying down.
- **Efficient Access to External Elements:** The minimum or maximum element is always at the root of the heap, allowing constant-time access.

In code the class would look like:

```python
class MaxHeap:

	def __init__(self, max_size):
		self.max_size = max_size
		self.array = [None] * max_size
		self.heap_size = 0

	def parent(self, index):
		return (index - 1) // 2

	def left_child(self, index):
		return 2 * i + 1

	def right_child(self, index):
		return 2 * i + 2

	def get_max(self):
		return self.array[0]

	def insert_key(self, key):
		if self.heap_size == self.max_size:
			raise OverflowError("Cannot exceed heap's max size")
	
		self.heap_size += 1
		index = self.heap_size - 1
		self.array[index] = x

		self.max_heapify(0)

	def delete_key(self, index):
		self.increase_key(index, float("inf"))
		self.remove_max()

	def increase_key(self, index, new_value):
		self.array[index] = new_value
		self.max_heapify(0)

	def max_heapify(self, index):
		left = self.left_child(index)
		right = self.right_child(index)
		largest = index
		if left < self.heap_size and self.array[left] > self.array[index]:
			largest = left
		if right < self.heap_size and self.array[right] > self.array[largest]:
			largest = right
		if largest != index:
			temp = self.array[index]
			self.array[index] = self.array[largest]
			self.array[largest] = temp
			self.max_heapify(largest)
```

Algorithms for the heap are:
- [[Heap - Heapify]]
- [[Heap - Insertion]]
- [[Heap - Deletion]]
