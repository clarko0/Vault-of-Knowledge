### Overview
**BFS** algorithm traverses the `tree` level by level and depth by depth.

![[Tree Levels.png]]

So we traverse level by level. In this example, the result is 1–2–5–3–4–6–7.

- Level/Depth 0: only `node` with value 1
- Level/Depth 1: `nodes` with values 2 and 5
- Level/Depth 2: `nodes` with values 3, 4, 6, and 7
### For Binary Trees:

```python
def bfs(self):
    queue = Queue()
    queue.put(self)

    while not queue.empty():
        current_node = queue.get()
        print(current_node.value)

        if current_node.left_child:
            queue.put(current_node.left_child)

        if current_node.right_child:
            queue.put(current_node.right_child)
```

To implement a **BFS** algorithm, we use the [[Queue]] data structure to help.

![[Depth-First Search.png]]

1. First add the `root` `node` into the `queue` with the `put` method.
2. Iterate while the `queue` is not empty.
3. Get the first `node` in the `queue`, and then print its value.
4. Add both `left` and `right` `children` into the `queue` (if the current `node`has `children`).
5. Done. We will print the value of each `node,` level by level, with our `queue`helper.