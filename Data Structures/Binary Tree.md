A `binary tree` is that it is a collection of `nodes`. Each `node` has three attributes: `value`, `left_child`, and `right_child`.

```python
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left_child = None
        self.right_child = None
```


Rules to insert to left:
- If the current `node` doesn’t have a `left child`, we just create a new `node`and set it to the current node’s `left_child`.
- If it does have the `left child`, we create a new node and put it in the current `left child`’s place. Allocate this `left child node` to the new node’s `left child`.

```python
def insert_left(self, value):
    if self.left_child == None:
        self.left_child = BinaryTree(value)
    else:
        new_node = BinaryTree(value)
        new_node.left_child = self.left_child
        self.left_child = new_node
```

It is similar to insert right:
```python
def insert_right(self, value):
    if self.right_child == None:
        self.right_child = BinaryTree(value)
    else:
        new_node = BinaryTree(value)
        new_node.right_child = self.right_child
        self.right_child = new_node
```
