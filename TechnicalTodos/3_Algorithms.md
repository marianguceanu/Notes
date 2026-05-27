# Most common approaches

1. Divide and Conquer (DnC)
    - Split problems into smaller, non-overlapping problems that can be easily solved individually
    - Combine results of smaller problems to get final result
## Searches
1. Linear Seach
    - Iterate over array until you find element desired or at desired position
    - If element not found, user handles
2. Binary Search - DnC
    - Pre condition: array is sorted
    - Choose middle elem as pivot
    - REPEAT: go left of elem if search is smaller than pivot, right if bigger, change pivot to middle of left array
    - If index is 0 or last, element not found

## Sorts
1. Quicksort - DnC
    - Choose pivot (Divide): Best if randomly and not first or last
    - Partition: all elements smaller on the left, bigger on the right
    - Recursive (Conquer): apply pivot and partition again on the sub arrays until base case 
    - Base case: 1 element is left (already sorted)
2. Mergesort - DnC 
    - Divide: Keep splitting array in half until can't be split
    - Conquer: Each sub array, sorted individually using merge sort
    - Merge: Merge all sub arrays in sorted order

## Traversal - graphs
1. BFS
    - Start from source (root) node
    - Explore graph level by level
    - Explore adjacent nodes of root, then adjacent nodes of the children of root, ...
    - Build queue for notes next for visiting
    - Usually iterative
2. DFS
    - Traverse all adjacent nodes one by one
    - When a vertex is reached, you traverse all other vertices adjacent to it and then move forward
    - Build stack for visited nodes
    - Maps naturally to recursion
