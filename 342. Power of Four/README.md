
# Check if a number is a Power of Four

## The code

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        return power(n, 1);
    }
    public boolean power(int n, int sum) {
        if (sum == n) return true;
        if (sum > n || sum > Integer.MAX_VALUE / 2) return false;

        return power(n, sum * 4);
    }
}
```

**In one sentence:**
We start from `1` and keep multiplying by `4` until we either match `n` (**success**) or pass it (**failure**).

---

## Tiny story

Imagine you have 1 candy.
You keep multiplying your candies by 4 each step: 1, 4, 16, 64, 256…
If you get exactly the number of candies your friend says, it’s a power of 4.
If you go past it, you stop — not a power of 4.

---

## Sample dry run — `n = 16`

| Step | sum value | Condition check   | What happens next        |
| ---- | --------- | ----------------- | ------------------------ |
| 1    | 1         | sum != n, sum < n | Multiply by 4 → sum = 4  |
| 2    | 4         | sum != n, sum < n | Multiply by 4 → sum = 16 |
| 3    | 16        | sum == n ✅        | Return true              |

**Final result:** true ✅

---

## Sample dry run — `n = 8`

| Step | sum value | Condition check   | What happens next        |
| ---- | --------- | ----------------- | ------------------------ |
| 1    | 1         | sum != n, sum < n | Multiply by 4 → sum = 4  |
| 2    | 4         | sum != n, sum < n | Multiply by 4 → sum = 16 |
| 3    | 16        | sum > n ❌         | Return false             |

**Final result:** false ❌

---

## How it works

1. **Start with 1** (`4^0`).
2. If current `sum` equals `n` → it’s a power of 4 → return true.
3. If `sum` is bigger than `n` or will overflow on next multiply → return false.
4. Multiply `sum` by `4` and repeat step 2.

---

## Edge cases

* **Negative numbers** → always false.
* **Zero** → false.
* **1** → true (since 4⁰ = 1).

