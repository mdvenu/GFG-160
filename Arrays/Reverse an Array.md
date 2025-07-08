---

# ⭐ Problem: Reverse an Array

* **Tags:** Array, Two Pointers
* **Difficulty Level:** Easy
* **Problem Link:** [https://www.geeksforgeeks.org/write-a-program-to-reverse-an-array-or-string/](https://www.geeksforgeeks.org/write-a-program-to-reverse-an-array-or-string/)

---

## 🎯 Problem Objective

Given an array, write a function to reverse its elements.

> Example:
> Input:  arr[] = {1, 2, 3}
> Output: arr[] = {3, 2, 1}

---

## 🧠 Core Logic / Intuition

The most efficient way to reverse an array in-place is to use the **two-pointer** technique.

*   One pointer (`start`) starts at the beginning of the array.
*   Another pointer (`end`) starts at the end of the array.
*   Swap the elements at the `start` and `end` pointers.
*   Move the `start` pointer forward and the `end` pointer backward until they meet or cross each other.

This ensures that each element is swapped exactly once, resulting in a reversed array.

---

## ⚙️ Approach (Step-by-Step)

1.  Initialize two pointers: `start = 0` and `end = n - 1`, where `n` is the size of the array.
2.  Create a `while` loop that continues as long as `start < end`.
3.  Inside the loop, swap the elements `arr[start]` and `arr[end]`.
4.  Increment `start` by 1.
5.  Decrement `end` by 1.
6.  Once the loop finishes, the array will be reversed.

---

## 🛠️ Code Snippet (Minimal Working Example)

```python
def reverse_array(arr):
    start = 0
    end = len(arr) - 1
    while start < end:
        arr[start], arr[end] = arr[end], arr[start]
        start += 1
        end -= 1
    return arr
```

---

## 📈 Time and Space Complexity

*   **Time Complexity:** O(n) — We iterate through roughly half of the array, performing a constant number of operations at each step.
*   **Space Complexity:** O(1) — The reversal is done in-place, so we only use a constant amount of extra space for the pointers.

---

## ⚠️ Edge Cases to Consider

*   **Empty Array:** The code handles this correctly; the loop `while start < end` will not execute.
*   **Array with one element:** The code also handles this correctly; the loop condition will be false from the start.
*   **Array with even/odd number of elements:** The two-pointer approach works for both cases without any modification.

---

## ✅ Status & Revision Plan

*   **Solved?** ✅ Yes
*   **Need to Revise?**
    * [ ] Tomorrow
    * [ ] In 3 Days
    * [ ] Before Next Interview

---
