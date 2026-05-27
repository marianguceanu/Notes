# Common data structures
- Arrays
- Linked Lists
- Stacks
- Queues
- Hash Tables
- Trees
- Heaps
- Graphs

## Arrays
1. Traversal
    - Usually done with a for loop
    - In low level languages, it's a pointer increasing / decreasing depending on traversal order
2. Insertion
    - **At beginning**: Shift all elements to the right and fill the first position
    - **At end**: Check last index of array, increment it, assign value to the position of that index
        > [!CAUTION]
        > Here, in lower level languages such as C, we can do a pointer arithmetic that will allow us to go outside bounds of the array 
    - **At given position**: Shift all elements from given position to right, insert element on given pos
3. Deletion
    - **At beginning**: Shift all elements starting from the second one to the left, decrement count
    - **At position**: Shift all elements right of position to the left, decrement count
    - **At end**: decrement count

## Linked Lists
1. Traversal
    - Start with head note and go node by node until you reach the end node, which points to NULL usually
2. Insertion
    - **At beginning**: create new head node, make it point to former head node
    - **At position**: traverse until you reach the prev desired position is, make new node, make prev node point to new one and new one points to prev one
    - **At end**: traveres all list, make new node, point it to nothing and former last to new node
3. Deletion
    - Just like insertion, but instead of making new nodes, make prev ones point to next node after deleted one

