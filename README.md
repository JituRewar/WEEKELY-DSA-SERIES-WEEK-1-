# WEEKELY-DSA-SERIES-WEEK-1-

# Week 1 – Day 1: Pointer Basics & Pointer Arithmetic

## 📌 Topic
Today I learned about **pointers in C++** and how pointer arithmetic works.  

---

## ✨ Key Learnings
- A **pointer** is a variable that stores the memory address of another variable.
- `&` → address of operator.  
- `*` → dereference operator (value at address).  
- Pointer arithmetic allows:
  - `p++` → move to next element.  
  - `p--` → move to previous element.  
  - `p + n` → move forward by `n`.  
  - `p - n` → move backward by `n`.  

---

## 🧩 Example Code (C++)
```cpp
#include<iostream>
using namespace std;
int main(){
    int a=5;
    int*ptr = &a;
    int**q = &ptr;
    cout<<*ptr<<endl;
    cout<<**q<<endl;
    cout<<ptr<<endl;
    cout<<*q<<endl;
    return 0;
}

📖 Notes

Pointer arithmetic depends on data type size.
For int (4 bytes), p+1 moves by 4 bytes.

Pointers are useful in arrays, dynamic memory allocation, and data structures.

