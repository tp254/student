---
layout: post
title: 2020 College Board MC Reflection
description: Analysis of missed questions from the 2020 AP CSP Practice Exam
categories: [Blogs]
permalink: /blogs/2020-mc-reflection
---

## 2020 College Board Multiple Choice Reflection


**Question Number:** 11  

**The Question:**  
What color corresponds to the binary RGB triplet (11111111, 11111111, 11110000)?  

**My Answer:** B (Light yellow)  

**Correct Answer:** A (Ivory)  

**My Reflection:**  
I chose light yellow because the first two values convert to 255, which matched several yellow shades. However, I didn’t carefully convert the third value. 11110000 equals 240, making the full 
triplet (255, 255, 240), which corresponds to ivory. I confused it with light yellow, which has 224 (11100000). I need to fully convert binary values instead of relying on visual similarity.  

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

### Question 4

**Question Number:** 21

**The Question:**  
Which observation is most consistent with the file size distribution shown in the circle graph?

**My Answer:** A

**Correct Answer:** B

**My Reflection:**  
I chose A because I quickly estimated that most files were 1 MB or less, but I didn't add the percentages carefully. Files up to 1 MB total 17% + 24% + 25% = 66%, which is not over 75%. However, files up to 10 MB include those plus the 1–10 MB category (10%), totaling 76%, which is over 75%. I need to slow down and calculate totals precisely instead of estimating.
I chose A because I quickly estimated that most files were 1 MB or less, but I didn’t add the percentages carefully. Files up to 1 MB total 17% + 24% + 25% = 66%, which is not over 75%. However, files up to 10 MB include those plus the 1–10 MB category (10%), totaling 76%, which is over 75%. I need to slow down and calculate totals precisely instead of estimating.  

**College Board Skill:** Computational Thinking Practice 5.B  


**Question Number:** 28

**The Question:**  
Which code segments correctly swap the values of `alpha` and `beta` using `temp`?

**My Answer:** C

**Correct Answer:** B

**My Reflection:**  
I misunderstood how the assignments affected each variable. Code segment I correctly stores `alpha` in `temp`, assigns `beta` to `alpha`, then assigns `temp` to `beta`, successfully swapping them. I need to trace each assignment step-by-step to see how values change instead of assuming based on pattern recognition.
I misunderstood how the assignments affected each variable. Code segment I correctly stores `alpha` in `temp`, assigns `beta` to `alpha`, then assigns `temp` to `beta`, successfully swapping them. I need to trace each assignment step-by-step to see how values change instead of assuming based on pattern recognition.  

**College Board Skill:** Computational Thinking Practice 4.B  
### Question 6

**Question Number:** 29

**The Question:**  
Which scenario best demonstrates lossless compression?

**My Answer:** D

**Correct Answer:** A

**My Reflection:**  
I chose D, but that option doesn't involve compression at all. Lossless compression reduces file size while allowing the exact original file to be restored. Option A correctly describes compressing the file and then restoring it fully. I need to carefully distinguish between compression types and no compression.
**My Reflection:**  
I chose D, but that option doesn’t involve compression at all. Lossless compression reduces file size while allowing the exact original file to be restored. Option A correctly describes compressing the file and then restoring it fully. I need to carefully distinguish between compression types and no compression.  

**College Board Skill:** Computational Thinking Practice 1.D  



**Question Number:** 39

**The Question:**  
What change is needed for the program to correctly compute the sum of the first 10 elements?

**My Answer:** B

**Correct Answer:** C

**My Reflection:**  
I focused on the loop condition instead of the order of operations. The issue is that `i` is incremented before accessing `nums[i]`, which skips the first element. Lines 5 and 6 must be switched so the correct index is used before incrementing. I need to trace loop execution carefully to check indexing errors.
**My Reflection:**  
I focused on the loop condition instead of the order of operations. The issue is that `i` is incremented before accessing `nums[i]`, which skips the first element. Lines 5 and 6 must be switched so the correct index is used before incrementing. I need to trace loop execution carefully to check indexing errors.  

### Question 8

**Question Number:** 44

**The Question:**  
What is the minimum number of connections that must be removed so T cannot communicate with U?

**My Answer:** C

**Correct Answer:** B

**My Reflection:**  
I overestimated the number of connections needed. I didn't fully analyze all possible communication paths between T and U. Only two connections need to be removed to break every path. I need to systematically trace all routes in network problems instead of guessing conservatively.

**My Reflection:**  
I overestimated the number of connections needed. I didn’t fully analyze all possible communication paths between T and U. Only two connections need to be removed to break every path. I need to systematically trace all routes in network problems instead of guessing conservatively.  
### Question 9

**Question Number:** 60

**The Question:**  
Which code correctly counts the number of different values that appear in both lists?

**My Answer:** B

**Correct Answer:** D

**My Reflection:**  
I didn't account for duplicates properly. My answer used the original list lengths instead of the deduplicated combined list. Option D correctly removes duplicates after combining, then calculates the overlap. I need to carefully track how list transformations affect lengths and duplicates.

**My Reflection:**  
I didn’t account for duplicates properly. My answer used the original list lengths instead of the deduplicated combined list. Option D correctly removes duplicates after combining, then calculates the overlap. I need to carefully track how list transformations affect lengths and duplicates.  
10

**Question Number:** 62

**The Question:**  
Which selection statements will display true given `x = true` and `y = false`? (Select two)

**My Answer:** [Your answer]

**Correct Answer:** A

**My Reflection:**  
I misunderstood how the `IF` statement and Boolean logic interact. I overlooked that `x OR y` evaluates to true even though `y` is false, so the IF condition passes and displays true. I need to pay closer attention to the evaluation of logical operators in conditional statements.

**College Board Skill:** Computational Thinking Practice
### Question 11

**Question Number:** 64

**The Question:**  
Which procedure calls will NOT return the correct value using repeated addition for multiplication?

**My Answer:** [Your answer]

**Correct Answer:** D

**My Reflection:**  
I didn't account for negative numbers. The loop uses `REPEAT UNTIL count ≥ y`, which fails when `y` is negative because the condition is true from the start, so the loop never executes. I need to consider edge cases like negative integers when implementing loops.

**College Board Skill:** Computational Thinking Practice 4.C
**My Reflection:**
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

**Overall Patterns & Common Mistakes:**
- **Calculation errors:** I rushed through calculations (Q21) instead of carefully adding percentages
- **Incomplete conversions:** I didn't fully convert binary values (Q11) or trace all execution steps (Q14, Q28, Q39, Q65)
- **Edge cases:** I overlooked negative numbers (Q64) and special scenarios
- **Scope limitations:** I forgot that machine language is also binary (Q17) and underestimated data representation concepts
- **Network analysis:** I need to systematically trace all paths (Q44) rather than estimating

**Areas to Study More:**
1. Binary/data representation and careful conversion
2. Loop tracing and variable state tracking
3. String manipulation and sequential operations
4. Boolean logic evaluation in conditionals
5. Network path analysis and fault tolerance
6. Edge case testing (negative numbers, empty inputs, etc.)
---

## Summary
[Add an overall reflection on patterns you noticed, common mistakes, and areas to study more]
