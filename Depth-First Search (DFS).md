### Overview
Depth-First Search (DFS) explores a path all the way to a leaf before backtracking and exploring another path. Let’s take a look at an example with this type of traversal.

![[Pasted image 20240318112638.png]]

The result for this algorithm will be 1–2–3–4–5–6–7.

### For Binary Trees:
#### Types of **DFS**: `pre-order`, `in-order`, and `post-order`:

##### Pre-order:
1. Print the value of the `node`.
2. Go to the `left child` and print it. This is if, and only if, it has a `left child`.
3. Go to the `right child` and print it. This is if, and only if, it has a `right child`.

```python
def pre_order(self):
    print(self.value)

    if self.left_child:
        self.left_child.pre_order()

    if self.right_child:
        self.right_child.pre_order()
```
##### In-order:
1. Go to the `left child` and print it. This is if, and only if, it has a `left child`.
2. Print the `node`’s value
3. Go to the `right child` and print it. This is if, and only if, it has a `right child`.

```python
def in_order(self):
    if self.left_child:
        self.left_child.in_order()

    print(self.value)

    if self.right_child:
        self.right_child.in_order()
```

The result of the in-order algorithm for this `tree` example is 3–2–4–1–6–5–7.

##### Post-order:

1. Go to the `left child` and print it. This is if, and only if, it has a `left child`.
2. Go to the `right child` and print it. This is if, and only if, it has a `right child`.
3. Print the `node`’s value

```python
def post_order(self):
    if self.left_child:
        self.left_child.post_order()

    if self.right_child:
        self.right_child.post_order()

    print(self.value)
```

The result of the `post order` algorithm for this `tree` example is 3–4–2–6–7–5–1.