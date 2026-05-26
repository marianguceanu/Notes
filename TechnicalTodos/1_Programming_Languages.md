# Memory management

## C / C++ generalities
- Both languages share the same fundamental parts regarding memory management
    - Code, global / static, heap (dynamic alloc), stack (function calls)
1. **Local** variables (inside functions) usually live on the **stack**
    - Lifetime of variables ends when function returns
    - Allocation is extremely fast
    - With too large allocations / recursion -> stack overflow
    - eg: 
        - ```c 
            void func() {
                int x = 5;
            }
          ```
2. **Heap** memory 
    - Works the same on both, as both languages support dynamic memory allocation
3. **Pointer** arithemtic
    - Both allow direct memory manipulation

> ## C++
> Particularities 
- Rule of five
- ODR

