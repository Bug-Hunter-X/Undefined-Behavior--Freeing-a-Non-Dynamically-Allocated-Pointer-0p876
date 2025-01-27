# Undefined Behavior: Freeing a Non-Dynamically Allocated Pointer

This repository demonstrates a common yet subtle error in C programming: attempting to free a pointer that was not allocated dynamically using `malloc()`, `calloc()`, or similar functions. This leads to undefined behavior, meaning the program might crash, corrupt data, or seemingly work correctly, but with hidden risks.

The `bug.c` file contains the erroneous code.  The `bugSolution.c` file shows the corrected version.

**Understanding the Problem**

In C, `free()` is used to release memory that has been dynamically allocated from the heap. Attempting to use `free()` on a pointer that points to memory allocated on the stack (like local variables), or on a pointer that hasn't been allocated at all, can cause serious problems.  The behavior is undefined – the compiler and runtime are not obligated to do anything specific in such cases, hence the unexpected results.

**The Solution**

The solution is simple: avoid calling `free()` on pointers that don't point to dynamically allocated memory.  Local variables and other automatically allocated variables are handled automatically by the system when they go out of scope.