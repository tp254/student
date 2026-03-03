---
layout: post
title: 2020 College Board MC Reflection
description: Analysis of missed questions from the 2020 AP CSP Practice Exam
categories: [Blogs]
permalink: /blogs/2020-mc-reflection
---

## 2020 College Board Multiple Choice Reflection

### Overall Score: 54/67

![2020 Practice Exam MCQ Score]({{site.baseurl}}/images/2020-mc-overall-score.png)

---

### Question 1

**Question Number:** 11  

**The Question:**  
What color corresponds to the binary RGB triplet (11111111, 11111111, 11110000)?  

**My Answer:** B (Light yellow)  

**Correct Answer:** A (Ivory)  

**My Reflection:**  
I chose light yellow because the first two values convert to 255, which matched several yellow shades. However, I didn't carefully convert the third value. 11110000 equals 240, making the full triplet (255, 255, 240), which corresponds to ivory. I confused it with light yellow, which has 224 (11100000). I need to fully convert binary values instead of relying on visual similarity.

**College Board Skill:** Computational Thinking Practice 2.B  

---


**Question Number:** 14

**The Question:**  
Which step 3 correctly allows the algorithm to display the digits of a positive integer from right to left?

**My Answer:** C

**Correct Answer:** B

**My Reflection:**  
I chose C because I thought displaying the integer quotient would help reduce the number correctly. However, storing the remainder in `number` causes the value to stay small and repeat, leading to an infinite loop. The algorithm needs to display the remainder (the last digit) and then store the integer quotient in `number` so the value decreases each iteration. I need to better trace variables step-by-step to check whether a loop will properly terminate.

**College Board Skill:** Computational Thinking Practice 4.B

---

### Question 3

**Question Number:** 17

**The Question:**  
Which of the following can be represented by a sequence of bits? (An integer, an alphanumeric character, a machine language instruction)

**My Answer:** C (I and II only)

**Correct Answer:** D (I, II, and III)

**My Reflection:**  
I knew integers and characters are represented in bits, but I overlooked that machine language instructions are also stored as binary. At the lowest level, all digital data—including instructions executed by the CPU—are sequences of bits. I need to remember that everything in a computer is ultimately represented in binary.

**College Board Skill:** Computational Thinking Practice 3.C

---

### Question 4

**Question Number:** 21

**The Question:**  
Which observation is most consistent with the file size distribution shown in the circle graph?

**My Answer:** A

**Correct Answer:** B

**My Reflection:**  
I chose A because I quickly estimated that most files were 1 MB or less, but I didn't add the percentages carefully. Files up to 1 MB total 17% + 24% + 25% = 66%, which is not over 75%. However, files up to 10 MB include those plus the 1–10 MB category (10%), totaling 76%, which is over 75%. I need to slow down and calculate totals precisely instead of estimating.


**College Board Skill:** Computational Thinking Practice 5.B

---

### Question 5

**Question Number:** 28

**The Question:**  
Which code segments correctly swap the values of `alpha` and `beta` using `temp`?

**My Answer:** C

**Correct Answer:** B

**My Reflection:**  
I misunderstood how the assignments affected each variable. Code segment I correctly stores `alpha` in `temp`, assigns `beta` to `alpha`, then assigns `temp` to `beta`, successfully swapping them. I need to trace each assignment step-by-step to see how values change instead of assuming based on pattern recognition.

**College Board Skill:** Computational Thinking Practice 4.B

---

### Question 6

**Question Number:** 29

**The Question:**  
Which scenario best demonstrates lossless compression?

**My Answer:** D

**Correct Answer:** A

**My Reflection:**  
I chose D, but that option doesn't involve compression at all. Lossless compression reduces file size while allowing the exact original file to be restored. Option A correctly describes compressing the file and then restoring it fully. I need to carefully distinguish between compression types and no compression.

**College Board Skill:** Computational Thinking Practice 1.D

---

### Question 7

**Question Number:** 39

**The Question:**  
What change is needed for the program to correctly compute the sum of the first 10 elements?

**My Answer:** B

**Correct Answer:** C

**My Reflection:**  
I focused on the loop condition instead of the order of operations. The issue is that `i` is incremented before accessing `nums[i]`, which skips the first element. Lines 5 and 6 must be switched so the correct index is used before incrementing. I need to trace loop execution carefully to check indexing errors.

**College Board Skill:** Computational Thinking Practice 4.C

---

### Question 8

**Question Number:** 44

**The Question:**  
What is the minimum number of connections that must be removed so T cannot communicate with U?

**My Answer:** C

**Correct Answer:** B

**My Reflection:**  
I overestimated the number of connections needed. I didn't fully analyze all possible communication paths between T and U. Only two connections need to be removed to break every path. I need to systematically trace all routes in network problems instead of guessing conservatively.

**College Board Skill:** Computational Thinking Practice 1.D

---

### Question 9

**Question Number:** 60

**The Question:**  
Which code correctly counts the number of different values that appear in both lists?

**My Answer:** B

**Correct Answer:** D

**My Reflection:**  
I didn't account for duplicates properly. My answer used the original list lengths instead of the deduplicated combined list. Option D correctly removes duplicates after combining, then calculates the overlap. I need to carefully track how list transformations affect lengths and duplicates.

**College Board Skill:** Computational Thinking Practice 3.B

---

### Question 10

**Question Number:** 62

**The Question:**  
Which selection statements will display true given `x = true` and `y = false`? (Select two)

**My Answer:** [Your answer]

**Correct Answer:** A

**My Reflection:**  
I misunderstood how the `IF` statement and Boolean logic interact. I overlooked that `x OR y` evaluates to true even though `y` is false, so the IF condition passes and displays true. I need to pay closer attention to the evaluation of logical operators in conditional statements.

**College Board Skill:** Computational Thinking Practice 2.B

---

### Question 11

**Question Number:** 64

**The Question:**  
Which procedure calls will NOT return the correct value using repeated addition for multiplication?

**My Answer:** [Your answer]

**Correct Answer:** D

**My Reflection:**  
I didn't account for negative numbers. The loop uses `REPEAT UNTIL count ≥ y`, which fails when `y` is negative because the condition is true from the start, so the loop never executes. I need to consider edge cases like negative integers when implementing loops.

**College Board Skill:** Computational Thinking Practice 4.C

---

### Question 12

**Question Number:** 65

**The Question:**  
Which sequence of `Concat` and `Substring` calls will store the string `"jackalope"` in `animal`?

**My Answer:** [Your answer]

**Correct Answer:** B

**My Reflection:**  
I didn't carefully trace the order of concatenation and substrings. The solution requires building `"jackalope"` step by step: extract `"lope"` from `"antelope"`, prepend `"a"` to get `"alope"`, then concatenate `"jack"` from `"jackrabbit"` at the front. I need to break string manipulations into sequential steps in future problems.

**College Board Skill:** Computational Thinking Practice 4.B

---

## Summary

### Performance Analysis

**Content & Skills Performance by Topic:**

![Skills Breakdown by Topic]({{site.baseurl}}/images/2020-mc-skills-breakdown.png)

### Skills I Struggled With Most:

**Most Missed Skills (by frequency):**
1. **Computational Thinking Practice 4.B** - 3 questions (Q14, Q28, Q65)
   - *Focus:* Tracing code execution, variable assignments, string operations
2. **Computational Thinking Practice 2.B** - 2 questions (Q11, Q62)
   - *Focus:* Binary conversions, Boolean logic evaluation
3. **Computational Thinking Practice 4.C** - 2 questions (Q39, Q64)
   - *Focus:* Loop behavior, edge cases in algorithms
4. **Computational Thinking Practice 1.D** - 2 questions (Q29, Q44)
   - *Focus:* Data compression concepts, network analysis

### Overall Patterns & Common Mistakes:
- **Incomplete tracing:** I didn't fully convert binary values or trace all execution steps
- **Edge cases:** I overlooked negative numbers and special scenarios
- **Calculation errors:** I rushed through calculations instead of carefully adding percentages
- **Conceptual gaps:** I confused compression types and forgot machine language is binary
- **Network analysis:** I need to systematically trace all paths rather than estimating

### Areas to Study More:
1. **Algorithm tracing & code execution (4.B)** - Variable state tracking, step-by-step execution
2. **Loop analysis (4.C)** - Edge cases, termination conditions, indexing
3. **Binary & Boolean operations (2.B)** - Complete conversions, logical operators
4. **Data concepts (1.D, 3.C)** - Compression, data representation, list operations

---

## Practice Questions

### Practice Question 1 - Skill 4.B (Code Tracing)
**Question:** Consider the following code segment:
```
a ← 5
b ← 10
c ← a
a ← b
b ← c
DISPLAY(a)
DISPLAY(b)
```
What values are displayed?

**A.** 5, 10  
**B.** 10, 5  
**C.** 10, 10  
**D.** 5, 5

<details>
<summary>Answer</summary>

**B (10, 5)**

Trace: a=5 → b=10 → c=5 → a=10 → b=5
</details>

---

### Practice Question 2 - Skill 2.B (Binary Conversion)
**Question:** What is the decimal value of the binary number 10110101?

**A.** 181  
**B.** 191  
**C.** 165  
**D.** 213

<details>
<summary>Answer</summary>

**A (181)**

128 + 32 + 16 + 4 + 1 = 181
</details>

---

### Practice Question 3 - Skill 4.C (Loop Analysis)
**Question:** How many times will "Hello" be displayed?
```
count ← 1
REPEAT UNTIL (count > 5)
{
    DISPLAY("Hello")
    count ← count + 2
}
```

**A.** 2  
**B.** 3  
**C.** 4  
**D.** 5

<details>
<summary>Answer</summary>

**B (3)**

count=1 displays, becomes 3; count=3 displays, becomes 5; count=5 displays, becomes 7; count=7 stops
</details>

---

### Practice Question 4 - Skill 2.B (Boolean Logic)
**Question:** Given: `a = true`, `b = false`, `c = true`. What is the result of: `(a AND b) OR (NOT b AND c)`?

**A.** true  
**B.** false  
**C.** Error  
**D.** Cannot be determined

<details>
<summary>Answer</summary>

**A (true)**

(true AND false) OR (true AND true) = false OR true = true
</details>

---

### Practice Question 5 - Skill 4.B (String Operations)
**Question:** What is the result?
```
text ← "programming"
result ← substring(text, 4, 7)
DISPLAY(result)
```
Assume substring uses 1-based indexing, inclusive.

**A.** "gram"  
**B.** "ogra"  
**C.** "ogram"  
**D.** "ramm"

<details>
<summary>Answer</summary>

**A ("gram")**

Positions 4-7: p(1)r(2)o(3)g(4)r(5)a(6)m(7) = "gram"
</details>

---

### Practice Question 6 - Skill 4.C (Edge Cases)
**Question:** What value is returned by Multiply(3, 0)?
```
PROCEDURE Multiply(x, y)
{
    result ← 0
    count ← 0
    REPEAT UNTIL (count ≥ y)
    {
        result ← result + x
        count ← count + 1
    }
    RETURN result
}
```

**A.** 0  
**B.** 3  
**C.** Infinite loop  
**D.** Error

<details>
<summary>Answer</summary>

**A (0)**

When y=0, condition (0 ≥ 0) is true immediately, loop never executes
</details>
