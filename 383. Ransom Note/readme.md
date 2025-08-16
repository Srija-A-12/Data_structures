
# 📰 Ransom Note – Java Solution

## 📖 Problem Statement

Given two strings:

* **ransomNote**
* **magazine**

Return **true** if the ransomNote can be constructed from the magazine, otherwise return **false**.

👉 Each letter in magazine can only be used **once**.

**Example 1:**

```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**

```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3:**

```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

---

## 💡 Approach

1️⃣ Check if `magazine` is shorter than `ransomNote`. If yes, return **false** immediately.
2️⃣ Use an integer array of size **26** (for lowercase English letters) to store **letter frequencies**.
3️⃣ Count the frequency of each letter in `magazine`.
4️⃣ For each character in `ransomNote`, decrement the count.

* If any count goes **below 0**, it means `magazine` doesn’t have enough of that character → return **false**.
  5️⃣ If we finish the loop without issues, return **true**. ✅

---

## 💻 Code (Java)

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        if(magazine.length() < ransomNote.length()) return false; // 📏 Quick check
        
        int[] count = new int[26]; // 🔠 Frequency array
        
        // 🏗 Count characters in magazine
        for(int n : magazine.toCharArray()){
            count[n - 'a']++;
        }

        // 📉 Check ransomNote against magazine
        for(int n : ransomNote.toCharArray()){
            count[n - 'a']--;
            if(count[n - 'a'] < 0) return false; // ❌ Not enough characters
        }

        return true; // ✅ All characters available
    }
}
```

---

## 📊 Complexity Analysis

* ⏱ **Time Complexity:** `O(m + n)`

  * `m = length of ransomNote`
  * `n = length of magazine`
* 💾 **Space Complexity:** `O(1)` (only 26 letters).

---


The expression **`c - 'a'`** is the trick that maps a character (`a`–`z`) to an **array index (0–25)**.

---

### How it works:

* In Java, characters are actually stored as **Unicode integers** (like ASCII codes).
* `'a'` has a code (97), `'b'` = 98, `'c'` = 99 … `'z'` = 122.

So if:

```java
char c = 'a';
int index = c - 'a';   // 97 - 97 = 0
```

➡ `'a'` maps to **0**

```java
c = 'b';
index = c - 'a';   // 98 - 97 = 1
```

➡ `'b'` maps to **1**

```java
c = 'z';
index = c - 'a';   // 122 - 97 = 25
```

➡ `'z'` maps to **25**

---

### Why do we use this?

Because we want a simple array of size 26:

```java
int[] count = new int[26]; // slots for 'a' to 'z'
```

Now each letter directly points to its slot:

* `count[0]` → frequency of `'a'`
* `count[1]` → frequency of `'b'`
* …
* `count[25]` → frequency of `'z'`

---



