# 📱 Letter Combinations of a Phone Number (LeetCode #17)

## 🚀 Problem Statement

Given a string containing digits from **2–9**, return all possible letter combinations that the number could represent.

Each digit maps to letters just like on a telephone keypad:

```
2 → abc  
3 → def  
4 → ghi  
5 → jkl  
6 → mno  
7 → pqrs  
8 → tuv  
9 → wxyz  
```

Return the answer in **any order**.

---

## 🧠 Approach

This problem is solved using **Backtracking (Recursion)**:

* Start from the first digit
* For each digit, try all possible mapped letters
* Build combinations step by step
* When the combination length equals input length → store result

---

## ⏱ Complexity

* **Time Complexity:** `O(4^n)`
* **Space Complexity:** `O(n)` (recursion stack)

---

## 💻 C++ Implementation

```cpp
class Solution {
public:
    vector<string> result;

    void backtrack(string &digits, int index, string current, 
                   unordered_map<char, string> &mp) {
        
        if (index == digits.length()) {
            result.push_back(current);
            return;
        }

        string letters = mp[digits[index]];
        
        for (char ch : letters) {
            backtrack(digits, index + 1, current + ch, mp);
        }
    }

    vector<string> letterCombinations(string digits) {
        if (digits.empty()) return {};

        unordered_map<char, string> mp = {
            {'2', "abc"}, {'3', "def"},
            {'4', "ghi"}, {'5', "jkl"},
            {'6', "mno"}, {'7', "pqrs"},
            {'8', "tuv"}, {'9', "wxyz"}
        };

        backtrack(digits, 0, "", mp);
        return result;
    }
};
```

---

## 📌 Example

**Input:**

```
digits = "23"
```

**Output:**

```
["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

---

## 📚 Topics Covered

* Backtracking
* Recursion
* String Manipulation

---

## 🌟 Author

Ranjith
