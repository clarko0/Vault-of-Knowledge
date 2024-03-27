### Deletion:

- If we delete the element from the heap it always deletes the root element of the tree and replaces it with the last element of the tree.
- Since we delete the root element from the heap it will distort the properties of the heap so we need to perform [[Heap - Heapify]] operations so that it maintains the property of the heap. 

It takes **O(logN)** time.

**Example:**

>
  Assume initially heap(taking max-heap) is as follows  
>            15  
>          /   \\  
>       5     7  
>    /  \  
> 2     3
> 
> Now if we delete 15 into the heap it will be replaced by leaf node of the tree for temporary.  
>            3  
>         /   \\  
>      5     7  
>    /      
> 2
> 
> After Heapify operation final heap will be look like this  
>            7  
>         /   \\
>      5     3  
>    /     
> 2


```python
def delete_key(self, index):
	self.increase_key(index, float("inf"))
	self.remove_max()
```