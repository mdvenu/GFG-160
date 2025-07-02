# 🤤 Problem: Second Largest Element in an Array

* **Tags:** Array, Traversal
* **Difficulty Level:** Easy
* **Problem Link:** https://www.geeksforgeeks.org/problems/second-largest3735/1

---

## 🎯 Problem Objective

Given an array of integers, find the second largest distinct element in it. If no such element exists, return -1.

> Example:
> Input: `arr[] = {12, 35, 1, 10, 34, 1}`
> Output: `34`
> Explanation: The largest element is 35, and the second largest is 34.

---

## 🧠 Core Logic / Intuition

The most efficient way to solve this is to find the second largest element in a single pass through the array. The core idea is to maintain two variables: `largest` and `second_largest`. As we iterate through the array, we compare each element with these two variables and update them as needed.

*   We initialize `largest` and `second_largest` to a very small value (or -1, since the problem deals with positive integers).
*   When we encounter a new element, we check if it's bigger than our current `largest`. If it is, the old `largest` becomes the new `second_largest`, and the current element becomes the new `largest`.
*   If the element is not the largest but is bigger than the `second_largest`, we update only the `second_largest`. This ensures we keep track of the top two distinct values seen so far.

---

## ⚙️ Approach (Step-by-Step)

1.  Initialize two variables, `largest` and `second_largest`, to `-1`.
2.  Iterate through the array from the first element to the last.
3.  For each element `arr[i]`:
    *   If `arr[i]` is greater than `largest`:
        *   Update `second_largest` to the current value of `largest`.
        *   Update `largest` to `arr[i]`.
    *   Else, if `arr[i]` is greater than `second_largest` AND `arr[i]` is not equal to `largest`:
        *   Update `second_largest` to `arr[i]`.
4.  After the loop finishes, `second_largest` will hold the second largest distinct element. If it's still `-1`, it means a second largest element was not found.
5.  Return `second_largest`.

---

## 🛠️ Code Snippet (Minimal Working Example)

```python
def print2largest(arr):
    largest = -1
    second_largest = -1

    # There must be at least two elements
    if len(arr) < 2:
        return -1

    for i in range(len(arr)):
        if arr[i] > largest:
            second_largest = largest
            largest = arr[i]
        elif arr[i] > second_largest and arr[i] != largest:
            second_largest = arr[i]

    return second_largest
```

> This snippet is in Python.

---

## 📈 Time and Space Complexity

*   **Time Complexity:** O(n) — We iterate through the array only once.
*   **Space Complexity:** O(1) — We only use a constant amount of extra space for the `largest` and `second_largest` variables.

---

## ⚠️ Edge Cases to Consider

*   **Array has less than two elements:** The function should return -1 as there's no second largest element.
*   **All elements are the same:** The function should return -1. For example, `[10, 10, 10]`.
*   **Array contains duplicates of the largest element:** The logic must handle this correctly by ensuring the `second_largest` is not the same as the `largest`. For example, `[10, 5, 10]`.

---

## ✅ Status & Revision Plan

*   **Solved?** ✅ Yes
*   **Need to Revise?**

    *   [ ] Tomorrow
    *   [ ] In 3 Days
    *   [ ] Before Next Interview

---

## 📌 Notes & Mistakes (Optional)

*   A common mistake is to initialize `largest` and `second_largest` with the first two elements without considering their order or if they are duplicates. Initializing to a value like -1 is safer.
*   Forgetting the `arr[i] != largest` check can lead to incorrect results if the largest element appears more than once.
*   A sorting-based approach `O(n log n)` is less optimal than the single-pass `O(n)` solution.

---
