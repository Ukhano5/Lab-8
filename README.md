# Lab-8
Muhammad Umair
12370
SE 3rdC
# Q1: Write a function to search for a value in a BST.
def search_bst(root, key):
    if root is None or root.key == key:
        return root
    if key < root.key:
        return search_bst(root.left, key)
    return search_bst(root.right, key)

# Output for Q1: No direct output, as it is a function definition.

# Q2: Implement a function to delete a node from a BST.
def delete_node(root, key):
    if root is None:
        return root
    if key < root.key:
        root.left = delete_node(root.left, key)
    elif key > root.key:
        root.right = delete_node(root.right, key)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        root.key = find_min(root.right).key
        root.right = delete_node(root.right, root.key)
    return root

# Output for Q2: No direct output, as it is a function definition.

# Q3: Create a function to find the minimum and maximum values in a BST.
def find_min(root):
    while root.left is not None:
        root = root.left
    return root

def find_max(root):
    while root.right is not None:
        root = root.right
    return root

# Output for Q3: No direct output, as it is a function definition.

# Q4: Write a function to find the in-order successor and predecessor of a node in a BST.
def find_inorder_successor_predecessor(root, key):
    successor = None
    predecessor = None

    while root:
        if key < root.key:
            successor = root
            root = root.left
        elif key > root.key:
            predecessor = root
            root = root.right
        else:
            if root.right:
                successor = find_min(root.right)
            if root.left:
                predecessor = find_max(root.left)
            break

    return successor, predecessor

# Output for Q4: No direct output, as it is a function definition.

# Q5: Implement a function to find the k-th smallest element in a BST.
def kth_smallest_element(root, k):
    if root is None or k <= 0:
        return None

    stack = []
    count = 0
    current = root

    while current or stack:
        while current:
            stack.append(current)
            current = current.left

        current = stack.pop()
        count += 1

        if count == k:
            return current.key

        current = current.right

# Output for Q5: No direct output, as it is a function definition.
```
