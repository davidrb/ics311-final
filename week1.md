# Week 1

## Topic 1
- Algorithms
  - A well-defined computational procedure that takes some values\(s\) as input
    and produces some value\(s\) as output.
  - Design & Analysis:
    - Step 1: Specification - What is it?
    - Step 2: Verification - Is is correct?
    - Step 3: Implementation - Realize the algorithm as executable code.
    - Step 4: Performance Evaluation - Predicted performance is verified
      empirically.
- Computational Complexity
  - Input Size
    - Number of bits needed to represent the input with a non redundant coding
      scheme.
  - Measures of Complexity
    - Run **time** to solve a problem of a given size
    - Storage **space** to solve a problem of a given size
- Models of Computation
  - All are equivalent to each other by the Church-Turing Thesis as long as
    they are deterministic and sequential.
  - Turing Machine & Random Access Machine are examples.
- Easy vs. Hard
  - Problems that cannot be solved: **unsolvable**, **undecidable**, or
    **incomputable**.
  - There is a complexity class heirarchy based on the minimum complexity of
    _any_ algorithm that solves the problem.

    ![complexity class
    heirarchy](https://www2.hawaii.edu/~nodari/teaching/s18/Notes/Topic-01/Complexity-Hierarchy.jpg)
  - Refers to problems, not algorithms
- Abstract Data Types
  - Data structures are defined by:
    - **Operations** - Specifications of external appearance of a data structure.
    - **Storage Structures** - Organizations of data implemented in lower level
      data structures. (We are almost always building abstractions on layers of
      abstractions above the actual physical implementation.)
    - **Algorithms** - Description of how to manipulate information in the
      storage structures to obtain the results defined for the operations
  - Abstract Data Types are defined by:
    - The **types** of data involved.
    - A set of opeartions that can be applied to those objects, and
    - a set of properties \(called axioms\) that all the objects and operations
      must satisfy.
  - Example - Stack ADT:
    - Objects: Stack, and Elements \(of arbitrary type\)
    - Operations:
      - Constructor: new() creates the empty stack and returns it
      - Accessors:
        - empty(s) returns whether stacks is empty
        - top(s) returns the element of stack s that has been inserted into s
          last
      - Mutators (Modifiers):
        - push(s, e) inserts an element into s
        - pop(s) deletes the top element from stack s
    - Properties:
      - top(push(s, e)) returns e
      - pop(push(s, e)) leaves s in same state
      - empty(new()) returns true
      - empty(push(s, i)) returns false
      - pop(new()) is an error
      - top(new()) is an error

## Topic 4
- Stacks
  - Follow **Last in, First out** principle.
  - Usefule when a problem has a goal-subgoal substructure.
  ```java
  public interface Stack {
  // ADT that stores and retrieves Objects in a LIFO manner

     public Stack( ); 
     // Create an instance of ADT Stack and initialize it to the empty stack.

     public void push(Object o); 
     // Insert object o at the top of the stack.

     public Object pop( ); 
     // Remove and return the top (most recently pushed) object on the stack.
     // Error occurs if the stack is empty. 

     public int size( ); 
     // Return the number of objects in the stack.

     public boolean isEmpty( ); 
     // Return a boolean indicating whether the stack is empty.

     public Object top( ); 
     // Return the top (most recently pushed) object on the stack, without 
     // removing it. Error occurs if the stack is empty.
  ```
  - Properties:
    - { push(s,e); s.top() } returns value e
    - { push(s,e); s.pop() } returns value e and leaves s in the same state
    - { s = new(); s.isEmpty() } returns true
    - { push(s,i); s.isEmpty() } returns false
    - if s.isEmpty() then s.top() is an error, and does not change s
    - if s.isEmpty() then s.pop() is an error, and does not change s
    - if s.isEmpty() then s.size() == 0
    - if s.size() == n then after s.push(o), s.size() == n+1
    - if ¬s.isEmpty() and s.size() == n then after s.pop(o), s.size() == n-1.
