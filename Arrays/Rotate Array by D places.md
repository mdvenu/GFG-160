---
# ⭐ Problem: Rotate Array to the Left by D Places

* **Tags:** Array, Rotation, In-place
* **Difficulty Level:** Easy
* **Problem Link:** [https://www.geeksforgeeks.org/proble...](https://www.geeksforgeeks.org/problems/rotate-array-by-n-elements-1587115621/1)

---

## 🎯 Problem Objective

Given an array `arr[]` of `n` integers, rotate the array to the left (counter-clockwise) by `d` steps. The operation should be performed in-place, meaning without using extra space.

> Example:
> Input: `arr[] = {1, 2, 3, 4, 5, 6, 7}`, `d = 2`
> Output: `{3, 4, 5, 6, 7, 1, 2}`

---

## 🧠 Core Logic / Intuition

The most efficient in-place method is the **Reversal Algorithm**. The core idea is to reverse specific parts of the array to achieve the final rotated state.

*   **Step 1: Reverse the first `d` elements.** This brings the last of the first `d` elements to the front.
*   **Step 2: Reverse the remaining `n-d` elements.** This arranges the rest of the array correctly among themselves.
*   **Step 3: Reverse the entire array.** This final reversal places both segments into their correct final positions.

Let's trace `arr[] = {1, 2, 3, 4, 5, 6, 7}` and `d = 2`:
1.  Reverse `arr[0...1]` (`{1, 2}`) → `{2, 1, 3, 4, 5, 6, 7}`
2.  Reverse `arr[2...6]` (`{3, 4, 5, 6, 7}`) → `{2, 1, 7, 6, 5, 4, 3}`
3.  Reverse the whole array `arr[0...6]` → `{3, 4, 5, 6, 7, 1, 2}` (Correct!)

---

## ⚙️ Approach (Step-by-Step)

1.  Handle the edge case where `d` is a multiple of `n`. If `d = d % n`, the effective rotation is `d % n`.
2.  Define a helper function `reverse(arr, start, end)` that reverses the elements of the array within the given `start` and `end` indices.
3.  Call the `reverse` function for the first `d` elements: `reverse(arr, 0, d-1)`.
4.  Call the `reverse` function for the rest of the elements: `reverse(arr, d, n-1)`.
5.  Call the `reverse` function for the entire array: `reverse(arr, 0, n-1)`.

---

## 🛠️ Code Snippet (Minimal Working Example)

```python
def reverse(arr, start, end):
    while start < end:
        arr[start], arr[end] = arr[end], arr[start]
        start += 1
        end -= 1

def rotate_left(arr, d):
    n = len(arr)
    if n == 0:
        return
    
    d = d % n # Handle cases where d >= n
    
    reverse(arr, 0, d - 1)
    reverse(arr, d, n - 1)
    reverse(arr, 0, n - 1)

```

---

## 📈 Time and Space Complexity

*   **Time Complexity:** O(n) — The array is traversed a constant number of times (reversing parts and then the whole).
*   **Space Complexity:** O(1) — The rotation is performed in-place with only a few extra variables for indices.

---

## ⚠️ Edge Cases to Consider

*   **Empty Array:** The code should handle an empty array gracefully.
*   **`d` is zero:** The array remains unchanged. The `d = d % n` logic handles this.
*   **`d` is equal to `n` or a multiple of `n`:** The array remains unchanged. The `d = d % n` logic handles this.
*   **`d` is greater than `n`:** The effective rotation is `d % n`.

---

## ✅ Status & Revision Plan

*   **Solved?** ✅ Yes
*   **Need to Revise?**
    *   [ ] In 3 Days

---
