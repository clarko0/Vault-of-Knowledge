### Insertion:

- If we insert a new element into the heap since we are adding a new element into the heap so it will distort the properties of the heap so we need to perform the [[Heap - Heapify]] operation so that it maintains the property of the heap.

This operation also takes **O(logN)** time.

**Examples:**

>
   Assume initially heap(taking **max-heap**) is as follows
> 
>            8  
>         /   \\
>      4     5  
>    / \   /
> 1   2
> 
> Now if we insert 10 into the heap  
>              8  
>         /      \\  
>       4       5  
>    /  \\      /  
> 1    2  10 
> 
> After Heapify operation final heap will be look like this  
>            10  
>          /    \
>       4      8  
>    /  \\     /  
>1    2  5
>

```python
def insert_key(self, key):
	if self.heap_size == self.max_size:
		raise OverflowError("Cannot exceed heap's max size")

	self.heap_size += 1
	index = self.heap_size - 1
	self.array[index] = x

	self.max_heapify(0)
```