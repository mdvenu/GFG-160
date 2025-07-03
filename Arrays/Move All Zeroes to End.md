# ⭐ Problem: Move All Zeroes to End

* **Tags:** Array, Two Pointers
* **Difficulty Level:** Easy
* **Problem Link:** https://www.geeksforgeeks.org/move-zeroes-end-array/

---

## 🎯 Problem Objective

Given an array of random numbers, push all the zeros of a given array to the end of the array. For example, if the given arrays is `{1, 9, 8, 4, 0, 0, 2, 7, 0, 6, 0}`, it should be changed to `{1, 9, 8, 4, 2, 7, 6, 0, 0, 0, 0}`. The order of all other elements should be same.

> Example:
> Input: `arr[] = {1, 2, 0, 4, 3, 0, 5, 0}`
> Output: `{1, 2, 4, 3, 5, 0, 0, 0}`

---

## 🧠 Core Logic / Intuition

The core idea is to use a two-pointer approach. One pointer (`j`) keeps track of the position where the next non-zero element should be placed. The other pointer (`i`) iterates through the array. When a non-zero element is found at `arr[i]`, it's swapped with the element at `arr[j]`, and `j` is incremented. This partitions the array into non-zero elements at the beginning and zeros at the end, all in a single pass, while maintaining the relative order of the non-zero elements.

---

## ⚙️ Approach (Step-by-Step)

1.  Initialize a pointer `j` to 0. This pointer marks the boundary of the non-zero elements section.
2.  Iterate through the array with a pointer `i` from the first element to the last.
3.  For each element `arr[i]`:
    *   If `arr[i]` is not zero:
        *   Swap the element at the current position `i` with the element at the non-zero boundary `j`.
        *   Increment `j` to expand the non-zero section.
4.  After the loop finishes, all non-zero elements will have been swapped to the front of the array (up to index `j-1`), and the zeros will be at the end.

---

## 🛠️ Code Snippet (Minimal Working Example)

```python
def moveZeroes(arr):
    j = 0 # Pointer for the next non-zero element's position
    n = len(arr)
    # Iterate through the array
    for i in range(n):
        # If a non-zero element is found
        if arr[i] != 0:
            # Swap the non-zero element with the element at position j
            arr[i], arr[j] = arr[j], arr[i]
            # Increment j to the next position
            j += 1
```

> This snippet is in Python.

---

## 📈 Time and Space Complexity

*   **Time Complexity:** O(n) — We iterate through the array only once.
*   **Space Complexity:** O(1) — We are modifying the array in-place and using only a constant amount of extra space for the pointers.

---

## ⚠️ Edge Cases to Consider

*   **Array with all zeros:** The array should remain unchanged. `j` will stay at 0.
*   **Array with no zeros:** The array should remain unchanged. `j` will be incremented for every element, and each element will be swapped with itself.
*   **Empty array:** The code should handle this gracefully (the loop won't run).

---

## ✅ Status & Revision Plan

*   **Solved?** ✅ Yes
*   **Need to Revise?**

    *   [ ] Tomorrow
    *   [ ] In 3 Days
    *   [ ] Before Next Interview

---

## 📌 Notes & Mistakes (Optional)

*   This single-pass swap approach is highly efficient as it minimizes writes compared to the method of copying non-zero elements and then filling the rest with zeros.
*   It's crucial to understand that `j` only increments when a non-zero element is found and swapped, ensuring that all elements before `j` are non-zero.
*   The relative order of the non-zero elements is preserved because we process them from left to right.

---
