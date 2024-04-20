It is the process to rearrange the elements to maintain the property of heap data structure. It is done when a certain node creates an imbalance in the heap due to some operations on that node. It takes **O(log N)** to balance the tree. 

- For **max-heap,** it **balances** in such a way that the maximum element is the root of that binary tree and 
- For **min-heap,** it balances in such a way that the minimum element is the root of that binary tree.


```python
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
