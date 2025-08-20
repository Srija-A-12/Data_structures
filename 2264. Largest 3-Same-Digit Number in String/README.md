
# Find Largest Repeated Digit Substring

## 📌 Problem

Given a string `num` (containing only digits), return the **largest 3-digit substring made of the same digit** that appears in `num`.
If no such substring exists, return an empty string `""`.

### Example

```java
Input: num = "6777133339"
Output: "777"

Input: num = "2300019"
Output: "000"

Input: num = "42352338"
Output: ""
```

---

## 💡 Approach

1. Start from digit **9 down to 0**.
2. For each digit `i`, create a string of three repeated digits:

   ```java
   String s = String.valueOf(i).repeat(3);
   ```

   Example:

   * If `i = 9`, `s = "999"`.
   * If `i = 8`, `s = "888"`.
3. Check if `num` contains that substring:

   ```java
   if (num.contains(s)) return s;
   ```
4. If found, return immediately (since we started from 9, it’s the largest possible).
5. If nothing matches, return an empty string `""`.

---

## ✅ Code

```java
class Solution {
    public String largestGoodInteger(String num) {
        for (int i = 9; i >= 0; i--) {
            String s = String.valueOf(i).repeat(3);
            if (num.contains(s)) return s;
        }
        return "";
    }
}
```

---

## ⏱️ Complexity

* **Time:** `O(10 * n)` → effectively `O(n)` where `n` = length of `num`.
* **Space:** `O(1)` (only a few extra strings are used).


