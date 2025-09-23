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
#include <bits/stdc++.h>
using namespace std;

// Iterative Binary Search
int binarySearch(vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2; // prevents overflow

        if (arr[mid] == target)
            return mid; // target found
        else if (arr[mid] < target)
            left = mid + 1; // search right half
        else
            right = mid - 1; // search left half
    }
    return -1; // target not found
}

int main() {
    vector<int> arr = {1, 3, 5, 7, 9, 11, 13};
    int target = 7;

    int result = binarySearch(arr, target);

    if (result != -1)
        cout << "Element " << target << " found at index " << result << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}




# 📅 Day 3 - Sorting & Search in Rotated Sorted Array

## 📖 Topics Covered
- Basics of **Array Sorting**
- Problem solving with **Binary Search** on rotated arrays

---

## 🔥 Problem: [LeetCode #33 - Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

### Problem Statement
Given a rotated sorted array `nums` and an integer `target`, return the index of `target` if it exists, otherwise return `-1`.

- Array `nums` is sorted in ascending order and then rotated at some pivot.
- Must be solved in **O(log n)** time.

---

### 🧩 Example


code

 while (st <= end) {
        int mid = st + (end - st) / 2;

        if (arr[mid] == target) {
            return mid;
        }

        // Left half is sorted
        if (arr[st] <= arr[mid]) {
            if (arr[st] <= target && target <= arr[mid]) {
                end = mid - 1;
            } else {
                st = mid + 1;
            }
        }
        // Right half is sorted
        else {
            if (arr[mid] <= target && target <= arr[end]) {
                st = mid + 1;
            } else {
                end = mid - 1;
            }
        }
    }

    return -1; // target not found
}


# Week 1 / Day 4 — LeetCode 852: Peak Index in a Mountain Array

**Folder structure (ready for GitHub)**

```
Week-1/
  Day-4_LeetCode-852_Peak-Index-in-a-Mountain-Array/
    README.md
    solution.py
    solution.cpp
    tests/
      README.md
      test_cases.txt
```

---

## README.md (contents)

### Title

**Day 4 — LeetCode 852: Peak Index in a Mountain Array**

### Problem (short)

Given an integer array `arr` that is guaranteed to be a mountain (strictly increasing then strictly decreasing), return *any* index `i` such that `arr[i]` is the peak of the mountain (i.e., maximum element). The peak is not at the ends.

Constraints: `3 <= arr.length <= 10^4`, elements are distinct and form a mountain.

### Key idea / Approach

The peak is the maximum element. We can solve this in:

* **O(n)** time by scanning for the maximum index. Simple and fine for many cases.
* **O(log n)** time using **binary search** by comparing `arr[mid]` with `arr[mid+1]`:

  * If `arr[mid] < arr[mid+1]`, the peak lies to the right, move `low = mid + 1`.
  * Else, the peak is at `mid` or to the left, move `high = mid`.
    This is similar to finding a local maximum in a unimodal array.

### Complexity

* Binary search solution: **Time:** O(log n), **Space:** O(1)
* Linear scan solution: **Time:** O(n), **Space:** O(1)


---

code
 while(st<=end){
            int mid=st+(end-st)/2;
            if(arr[mid]>arr[mid+1] && arr[mid]>arr[mid-1]){
                
                 return mid;
            }
            else{
                if(arr[mid]>arr[mid-1]){
                    st=mid+1;
                }
               else{
                end=mid-1;
               }
            }
        }


Week 1 · Day 5 — LeetCode 540: Single Element in a Sorted Array

Problem (short)

Given a sorted array where every element appears exactly twice except for one element which appears once, find that single element in O(log n) time and O(1) space.


Idea / Approach

Because the array is sorted and pairs are adjacent, we can use a binary search variant. Observe:

Pairs start at even indices (0-based) until the single element appears.

If mid is even and nums[mid] == nums[mid+1], the single element is to the right.

If mid is even and nums[mid] != nums[mid+1], the single element is at or to the left.

For odd mid, compare with mid-1 instead (or adjust mid to be even).

This yields a loop that halves the search space each time (O(log n)).

Time & Space

Time complexity: O(log n)

Space complexity: O(1)
code cpp

       
        int st=0,end=arr.size()-1;
        int mid=st+(end-st)/2;
        if(arr.size()==1) return arr[0];
        while(st<=end){
            if(mid==0 && arr[mid]!=arr[mid+1]) return arr[mid];
            if(mid==arr.size()-1 && arr[mid]!=arr[mid-1]) return arr[mid];
            if(arr[mid]!=arr[mid+1] && arr[mid]!=arr[mid-1]){
                return arr[mid];
            }
            if(mid%2==0){
            if(arr[mid]==arr[mid-1]){
                end=mid-1;
            }    
            else{
                st=mid+1;
            }
            }
            else{
                if(arr[mid]==arr[mid-1]){
                    st=mid+1;
                }
                else{
                    end=mid-1;
                }
            }
            
            
        }
        return -1;

    

