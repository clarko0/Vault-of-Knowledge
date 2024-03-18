We start with the `root` `node` as our current `node`. Is the given value smaller than the current `node` value? If yes, then we will search for it on the left `subtree`.
2. Is the given value greater than the current `node` value? If yes, then we will search for it on the right `subtree`.
3. If rules #1 and #2 are both false, we can compare the current `node` value and the given value if they are equal. If the comparison returns `true`, then we can say, “Yeah! Our `tree` has the given value,” otherwise, we say, “No, it hasn’t.”

![[Pasted image 20240318125051.png]]

The code:
```python
class BinarySearchTree:
    def __init__(self, value):
        self.value = value
        self.left_child = None
        self.right_child = None

    def find_node(self, value):
        if value < self.value and self.left_child:
            return self.left_child.find_node(value)
        if value > self.value and self.right_child:
            return self.right_child.find_node(value)

        return value == self.value
```
