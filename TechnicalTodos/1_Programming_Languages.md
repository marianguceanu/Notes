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
    - Destructor:               ```~ClassName()```
    - Copy constructor:         ```ClassName(const ClassName& other)```
    - Copy assignment operator: ```ClassName& operator=(const ClassName& other)```
    - Move constructor:         ```ClassName(ClassName&& other) noexcept //“noexcept” -> does not throw any exceptions```
    - Move assignment operator: ```ClassName& operator=(ClassName&& other) noexcept```
- ODR (One Definition Rule)
    - Class, Struct, Non-Inline Function, or Object - one definition in the entire program
    - Templates, types - one definition per translation unit

## JS / Python (languages with garbage collector, named GC)
- Memory management is automatic
- GC reclaims unused memory
- Developer productivity, safety are priority
- You create objects, runtime decides:
    - Where they live
    - When to free
    - How to optimize
- Python and JS both use stack, heap, code segment
- Almost all objects live on the heap
- Stack is used for: 
    - Function call frames
    - Local references, pointers
    - Temporary execution data
- Python has a cyclic GC
    - Periodically scans for unreachable cycles
- JS GC is **Non-Deterministic**
    - You do NOT know exactly *when* cleanup happens
- Most modern JS engines use **generational GC**
    - Objects surviving multiple GC cycles get promoted
