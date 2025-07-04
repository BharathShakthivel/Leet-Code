Here’s a clear and concise explanation of your `romanToInt` function that you can include in your README file on GitHub:

---

### 🏛️ Roman to Integer – LeetCode Problem

This function converts a Roman numeral string into its corresponding integer value.

#### 🔍 Problem Statement

Given a Roman numeral, convert it to an integer. Roman numerals are represented by seven different symbols:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

Roman numerals are usually written from largest to smallest left to right, but in some cases, a smaller numeral before a larger one indicates subtraction (e.g., IV = 4, IX = 9).

---

### ✅ Code Explanation

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        out = 0
        temp_dict = {"I" : 1, "V" : 5, "X" : 10, "L" : 50, "C" : 100, "D" : 500, "M" : 1000}
        for i in range(len(s)-1):
            if temp_dict[s[i]] < temp_dict[s[i+1]]:
                out -= temp_dict[s[i]]
            else:
                out += temp_dict[s[i]]          
        return out + temp_dict[s[-1]]
```

#### 💡 How It Works

* `temp_dict` stores the integer value for each Roman numeral symbol.
* The loop goes through each character **except the last one** and checks:

  * If the current numeral is **less than** the next one, it means this is a subtractive pair (e.g., `IV`), so subtract its value.
  * Otherwise, simply add the value.
* After the loop, we **add the value of the last character** (since it wasn’t included in the loop).
* This logic effectively handles all valid Roman numeral combinations.

#### 📦 Example

```python
Solution().romanToInt("MCMXCIV")  # Output: 1994
```

Explanation:
`M` (1000) + `CM` (900) + `XC` (90) + `IV` (4) = **1994**

---

### 🧠 Time and Space Complexity

* **Time Complexity:** O(n), where *n* is the length of the input string.
* **Space Complexity:** O(1), since the dictionary is constant-sized.

---


