

# 🔢 Maximum 69 Number – Java Solution

## 📖 Problem Statement

You are given a positive integer that only contains the digits **6** and **9**.
You can **change at most one digit** (from `6 ➝ 9` or `9 ➝ 6`) to get the **maximum possible number**.

👉 Return the maximum number you can obtain.

**Example:**

```
Input: 9669
Output: 9969
```

✨ Explanation: Change the first `6` to `9`.

---

## 💡 Approach

1️⃣ Convert the number into an array of digits.
2️⃣ Traverse the digits from **left → right**.
3️⃣ Change the **first `6`** you encounter into a `9`.
4️⃣ Reconstruct the number and return it.

---

## 💻 Code (Java)

```java
class Solution {
    public int maximum69Number (int num) {
        if(num == 9999) return num;  // ✅ Already maximum
        
        int num1 = num;
        int[] a = new int[4];  // ℹ️ max 4 digits as per constraints
        int count = a.length - 1;
        
        // 🔄 Extract digits into array
        while(num1 > 0){
            a[count] = num1 % 10;
            num1 = num1 / 10;
            count--;
        }
       
        // ✏️ Change the first 6 to 9
        for(int i = 0; i < a.length; i++){
            if(a[i] == 6){
                a[i] = 9;
                break;
            }
        }
        
        // 🔢 Reconstruct the number
        int number = 0;
        for(int i = 0; i < a.length; i++){
            number = number * 10 + a[i];
        }

        return number;
    }
}
```

---

## 📊 Complexity Analysis

* ⏱ **Time Complexity:** `O(d)` where `d` = number of digits (max 4).
* 💾 **Space Complexity:** `O(d)` for digit storage.

---


