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



 # Week 1 – Day 2: Binary Search (O(log n) Time Complexity)



## 📖 Topic Covered
- Binary Search Algorithm
- Time Complexity Analysis: **O(log n)**
- Why Binary Search is more efficient than Linear Search

---

## ⚡ Explanation
Binary Search works on a **sorted array** by repeatedly dividing the search interval in half:
1. Compare the target with the middle element.
2. If the target equals the middle element → return index.
3. If the target is smaller → search the left half.
4. If the target is larger → search the right half.

This makes the complexity **O(log n)** because the search space reduces by half each step.

---

## 🧮 Example
Array = `[1, 3, 5, 7, 9, 11, 13]`  
Target = `7`  

Steps:  
- mid = 5 → 7 > 5 → search right half  
- mid = 9 → 7 < 9 → search left half  
- mid = 7 → Found ✅

---

## ⏱️ Time & Space Complexity
- **Time:** O(log n)  
- **Space:** O(1) (iterative) / O(log n) (recursive)

---

## 📂 Code File
See [`binary_search.cpp`](./binary_search.cpp)
📌 binary_search.cpp
#include<iostream>
#include<vector>
using namespace std;
int binarysearch(vector<int> arr1,int target){
    int st=0,end=arr1.size()-1;
    
    while(st<=end){
        int mid=(st+end)/2;
        if(arr1[mid]>target) {
           end=mid-1;
        }
        else if(arr1[mid]<target){
            st=mid+1;

        }
        else return mid;
    }
    return -1;
}
int main(){
    vector<int> arr1 = {-1,5,4,9,7,58,35};
    int target = 35;
    
    cout<<binarysearch(arr1,target)<<endl;
    return 0;
}

