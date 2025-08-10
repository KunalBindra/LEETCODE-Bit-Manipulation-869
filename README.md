# LEETCODE-Bit-Manipulation-869
---

## **Code Understanding**

You have two methods:

1. **`getsort(int n)`**

   * Converts the integer `n` to a string → `String.valueOf(n)`
   * Converts it to a `char[]` array → `toCharArray()`
   * Sorts the characters in ascending order → `Arrays.sort(arr)`
   * Returns the sorted characters back as a string.

   **Example:**
   `n = 241` → `"241"` → `['2','4','1']` → sort → `['1','2','4']` → `"124"`

2. **`reorderedPowerOf2(int n)`**

   * Gets the sorted version of `n`.
   * Checks all powers of 2 from `1 << 0` (which is 1) to `1 << 29` (which is 2^29 = 536870912).
   * For each power of 2, it sorts its digits and compares with the sorted digits of `n`.
   * If any matches, returns `true`; else returns `false`.

---

## **Dry Run Example**

Let’s say:

```java
Solution sol = new Solution();
boolean ans = sol.reorderedPowerOf2(128);
```

---

### Step 1: `reorderedPowerOf2(128)`

* `s = getsort(128)`

  * `"128"` → `['1','2','8']` → already sorted → `"128"`

---

### Step 2: Loop `i` from `0` to `29`

**Iteration 1:** `i = 0`

* `1 << 0 = 1`
* `getsort(1)` → `"1"`
* Compare `"128"` vs `"1"` → not equal.

**Iteration 2:** `i = 1`

* `1 << 1 = 2`
* `getsort(2)` → `"2"`
* Compare `"128"` vs `"2"` → not equal.

**Iteration 3:** `i = 2`

* `1 << 2 = 4`
* `getsort(4)` → `"4"`
* Compare `"128"` vs `"4"` → not equal.

...

**Iteration 8:** `i = 7`

* `1 << 7 = 128`
* `getsort(128)` → `"128"`
* Compare `"128"` vs `"128"` → equal ✅
* Return `true`.

---

## **Key Insight**

This algorithm works because:

* If two numbers are permutations of each other’s digits, their sorted digit strings will be equal.
* The loop only checks powers of 2 (since `1 << i` generates them).

---
