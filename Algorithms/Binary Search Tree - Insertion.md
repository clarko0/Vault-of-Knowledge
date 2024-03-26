1. Is the new `node` value greater or smaller than the current `node`?
2. If the value of the new `node` is greater than the current `node,` go to the right `subtree`. If the current `node` doesn’t have a `right child`, insert it there, or else backtrack to step #1.
3. If the value of the new `node` is smaller than the current `node`, go to the left `subtree`. If the current `node` doesn’t have a `left child`, insert it there, or else backtrack to step #1.
4. We did not handle special cases here. When the value of a new `node` is equal to the current value of the `node,` use rule number 3. Consider inserting equal values to the left side of the `subtree`.

![[Binary Search Tree Insert.png]]


```python
class BinarySearchTree:
    def __init__(self, value):
        self.value = value
        self.left_child = None
        self.right_child = None

    def insert_node(self, value):
        if value <= self.value and self.left_child:
            self.left_child.insert_node(value)
        elif value <= self.value:
            self.left_child = BinarySearchTree(value)
        elif value > self.value and self.right_child:
            self.right_child.insert_node(value)
        else:
            self.right_child = BinarySearchTree(value)
```
