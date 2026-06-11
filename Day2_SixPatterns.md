# Day 2 — Six Prompt Patterns Lab

**Name:** SRINIJA PULLIPUDI
**Date:** 10-06-2026

---

# Pattern 1 — Persona

## Prompt

You are a senior placement coach at Aditya University. You have prepared 200 B.Tech CSE students for TCS, Infosys, and Cognizant placement interviews.
A 3rd-year CSE student with 7.5 CGPA asks you about Big-O notation.
Explain it the way you would in a 1-on-1 placement prep session. Make it conversational, practical, and interview-focused.

## Best Output

Big-O Notation — The Way I'd Actually Explain It to You
First, forget the textbook definition for a moment. Imagine you're searching for your roll number on a printed list of 200 students...

## Observation

The response adopted the placement-coach persona and tailored the explanation to a 3rd-year CSE student preparing for campus interviews. It included interview tips, common traps, and placement-specific examples.

**Self Score:** 5/5

**Peer Score:** 8/10

---

# Pattern 2 — Few-Shot

## Prompt

Here are example explanations from a placement coach:

Q: What is recursion?
A: A function calling itself with a smaller problem. Like Russian dolls. Stops at a base case. Example: factorial.
Q: What is a stack?
A: LIFO data structure. Push adds, pop removes. Like a stack of plates.
Q: What is Big-O notation?
A:

## Best Output

O(1), O(n), O(n²). How fast your code grows as input grows. One loop = O(n). Nested loops = O(n²). Binary search = O(log n). Drop constants: O(2n) is just O(n).

## Observation

The model copied the style of the provided examples. The answer became shorter, more concise, and easier to memorize compared to the Persona pattern.

**Self Score:** 4/5

**Peer Score:** 7/10

---

# Pattern 3 — Chain-of-Thought

## Prompt

Explain Big-O notation to a placement interview candidate.
Step 1: Define Big-O in one sentence.
Step 2: Give one concrete code example.
Step 3: Explain why interviewers ask about it.
Step 4: Summarise everything in 3 sentences.

## Best Output

### Step 1: Definition

Big-O describes how your algorithm's runtime grows as input size increases.

### Step 2: Code Example

for i in range(n):
print(i)

O(n) — runs once per element.

### Step 3: Why Interviewers Ask

They're not testing if your code works — they're testing if you know when it breaks. A solution that works for 100 inputs but crawls at 10 million is a production bug waiting to happen.

### Step 4: Summary

Big-O measures how code performance scales with input size. A single loop is O(n), nested loops are O(n²), and binary search is O(log n). Interviewers use it to check whether you write code that survives the real world.

## Observation

The prompt forced the model to reason through a sequence of steps instead of generating a direct explanation. This produced a more transparent and teachable answer.

**Self Score:** 5/5

**Peer Score:** 8/10

---

# Pattern 4 — Structured Output

## Prompt

Explain Big-O notation for a placement interview.

Return ONLY valid JSON with this exact shape:

{
"definition": "one-sentence definition",
"intuition": "concrete analogy",
"code_example": "Python snippet showing O(n) and O(n²)",
"common_pitfall": "what students get wrong",
"interview_test_question": "a follow-up question an interviewer might ask"
}

## Best Output

{
"definition": "Big-O describes how an algorithm's runtime grows relative to input size.",
"intuition": "Searching your name in a 1000-student list one by one is O(n); opening the middle and halving each time is O(log n).",
"code_example": "for i in range(n): print(i) # O(n)",
"common_pitfall": "Writing O(2n) or O(n/2) instead of simplifying to O(n).",
"interview_test_question": "If I replace my nested loop with a single loop and a hash map, what happens to the time complexity and why?"
}

## Observation

The model returned the answer in a predefined JSON schema instead of free-form text. This makes the output predictable and easy for software systems to process.

**Self Score:** 5/5

**Peer Score:** 8/10

---

# Pattern 5 — System Prompt

## System Prompt

You are a senior placement coach for B.Tech CSE students at an Indian engineering college.
You prepare students for TCS, Infosys, and Cognizant interviews.
Explain technical concepts in 50–80 words maximum.
Use a conversational style and one concrete code example.

## User Prompt

Explain Big-O notation.

## Best Output

Big-O notation describes how an algorithm's runtime (or space) grows as the input size n grows — specifically, the worst-case upper bound.

## Observation

The system prompt successfully made the answer placement-oriented without requiring a long user prompt. However, Claude did not fully obey the 50–80 word limit and generated a much longer response than requested.

**Self Score:** 4/5

**Peer Score:** 7/10

---

# Pattern 6 — Prompt Chaining

## Conversation 1 (Extract)

Prompt:

List the 5 most important sub-concepts a B.Tech student must understand about Big-O notation.

Output:

1. Worst-case analysis
2. Dropping constants and lower-order terms
3. Common complexity classes and their order
4. Time vs. space complexity
5. Amortized complexity

---

## Conversation 2 (Expand)

Prompt:

For each of these 5 sub-concepts, write one paragraph for a 3rd-year B.Tech CSE student preparing for placements.

Output:

1. Worst-case analysis
When we say an algorithm is O(n), we almost always mean it performs at most n steps for the worst possible input of size n. This is what interviewers care about — not how fast your code runs on a sorted array, but how it behaves when the input is adversarial. Linear search, for instance, is O(n) because the element you're looking for might be at the very last position. Always default to worst-case thinking unless a problem explicitly asks for average-case (like Quicksort analysis).
2. Dropping constants and lower-order terms
Big-O is about growth rate, not exact step counts. So 3n + 7 and 100n both simplify to O(n), because as n → ∞, the constant multiplier becomes irrelevant compared to the shape of the curve. Similarly, n² + n simplifies to O(n²) — the lower-order term n is swallowed entirely at large n. In placement interviews, if you write O(2n) instead of O(n), it signals a gap in understanding; always reduce to the dominant term with coefficient 1.
3. Common complexity classes and their order
You must instantly recognize and rank: O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!). Each step up is a dramatic real-world difference — an O(n²) solution that works for n = 1000 will time-out for n = 10⁶. In interviews, once you propose a solution, you're expected to state its complexity unprompted. Knowing this ladder also helps you identify the target complexity — if a sorted array is given, an O(log n) solution likely exists via binary search.
4. Time vs. space complexity
Every algorithm has two Big-O costs: time (number of operations) and space (extra memory used). Recursive solutions often look clean but carry O(n) or O(log n) space cost from the call stack — something many students overlook. Interviewers frequently ask you to optimize one at the expense of the other; for example, a hash map trades O(n) space for O(1) lookup time. Always analyze both dimensions, and when you state your solution's complexity, cover both — it immediately sets you apart.
5. Amortized complexity
Amortized analysis asks: what is the average cost per operation over a long sequence of operations, even if individual operations occasionally spike? The classic example is a dynamic array (like Python's list) — most append calls are O(1), but every so often the array doubles in size at O(n) cost. Spread across all n insertions, the per-operation cost averages to O(1) amortized. This comes up directly in questions about stacks, queues built from two stacks, and hash table resizing — knowing the term and the concept signals solid CS fundamentals to any interviewer.

---

## Conversation 3 (Polish)

Prompt:

Synthesise these 5 paragraphs into one concise 80-word placement-interview explanation.

Output:

Big-O measures how an algorithm's runtime or space grows as input scales — always think worst-case. Drop constants and lower terms: 3n + 7 is just O(n). Know the complexity ladder cold: O(1) → O(log n) → O(n) → O(n log n) → O(n²) → O(2ⁿ). Always state both time and space complexity. Finally, amortized complexity smooths out occasional spikes.

Practice question: Given an unsorted array, find if any two elements sum to a target value — state your solution's time and space complexity and justify both.

## Observation

The task was broken into three separate stages: identifying sub-concepts, expanding them, and then synthesizing them into a final explanation. This produced a more complete and refined answer than a single prompt.

**Self Score:** 5/5

**Peer Score:** 10/10

---

# Pair-Scoring Summary

| Pattern           | Self Score | Peer Score |
| ----------------- | ---------- | ---------- |
| Persona           | 5/5        | 8/10       |
| Few-Shot          | 4/5        | 7/10       |
| Chain-of-Thought  | 5/5        | 8/10       |
| Structured Output | 5/5        | 8/10       |
| System Prompt     | 4/5        | 7/10       |
| Prompt Chaining   | 5/5        | 10/10      |

---

# Reflection

For my placement-prep students, the patterns I will use most are Persona and Prompt Chaining.

Persona helps tailor explanations to the student's background, academic level, and placement goals. The responses feel more like coaching sessions than textbook answers.

Prompt Chaining is useful for complex topics because it breaks learning into stages: identifying key concepts, explaining them, and then refining them into a concise interview-ready answer. Among all six patterns, it consistently produced the most complete and structured explanations.
