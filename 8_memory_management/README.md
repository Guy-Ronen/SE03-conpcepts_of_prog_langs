# Memory management

## Static vs stack vs heap
In a computer program, memory management refers to the process of allocating and deallocating memory to store and retrieve data. There are three main types of memory management: static, stack, and heap.

![static_stack_heap](static_stack_heap.png)

### Static Memory Management:
Static memory management is used to allocate memory to data that does not change during the lifetime of the program. 

This data is allocated during compile time and is stored in a special region of memory known as the data segment.
<strong>
Examples of static data include global variables and constants.
</strong>

Static memory management is the simplest form of memory management, but it has several drawbacks: 

1. Static data cannot be modified at runtime, which means that it cannot be used to store data that changes during the lifetime of the program. 

2. Static data is also stored in a fixed location in memory, which means that it cannot be moved around to make room for other data.

### Stack Memory Management:
Stack memory management is used to allocate memory to data that is local to a function and is created when the function is called. 
This data is stored in a special region of memory known as the stack. 

The stack is a last-in-first-out (LIFO) data structure, which means that the last data to be added to the stack is the first data to be removed from it.

<strong>
Examples of stack data include function parameters, local variables, and return addresses.
</strong>

A stack can run out of memory if it is not managed properly. 
This can happen if a function calls itself recursively, or if a function allocates too much memory to local variables. In these cases, the stack will overflow and the program will crash.

### Heap Memory Management:
Heap memory management is used to allocate memory to data that is dynamically created during the lifetime of the program. This data is stored in a region of memory known as the heap. 
Unlike the stack, the heap is a non-linear data structure, which means that data can be allocated and deallocated in any order. 
<strong>
Examples of heap data include objects created with the new operator in Java or C++, and dynamic arrays.
</strong>


A heap can run out of memory if it is not managed properly.

This can happen if the programmer forgets to deallocate memory after it is no longer needed, or if the programmer allocates too much memory to the heap. 

In these cases, the heap will overflow and the program will crash.

Thats why we have garbage collection in Java, C#, Python, JavaScript and many others. 
It automatically deallocates memory that is no longer needed by the program.

![heap](heap.png)

