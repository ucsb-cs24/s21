---
lecture_date: 2021-03-31
num: "lect02"
desc:  "C++ Memory Model, Pointers and References, Review (C++ classes)"
ready: true
pdfurl: /lectures/CS24_Lecture2.pdf
annotatedpdfurl: /lectures/CS24_Lecture2_ann.pdf
annotatedready: false

---

# Code from lecture:

[{{site.lect_repo}}/tree/main/{{page.num}}]({{site.lect_repo}}/tree/main/{{page.num}})


# Topics

# Structure of a program in memory
* Memory regions: Code (text), static, heap, stack

## C++ References
* Creating aliases with references


## Pointers

* Pointer declaration - difference/similarities with declaring basic types
* Accessing variables "indirectly" via pointers
* The address and indirection operators: "&" and "*"
* Differences between references and pointers
* Constant pointers and references, when and why to use them
* Pointers and arrays - similarities and differences
* Passing arrays to functions - specifically looking at how arrays degenerate to pointers on function calls.

#  Pointers: why do we need them? 


* Pointers allow arrays to be passed to functions efficiently
* Pointers allow arrays of large structs to be traversed effiently

# Pointer pitfalls
* Pointers can only point to one type of data (not generic)
* They don't automatically point - need to do some work
* Bugs in code that involves pointers can cause your program to irrecoverably crash (Segmentation fault)
* Examples: dereferencing a null pointer, out of bound array access, dereferncing a pointer that has junk value.



## Call by value, address and reference
* Understanding the differences via stack diagrams
* When and why to use each of these











