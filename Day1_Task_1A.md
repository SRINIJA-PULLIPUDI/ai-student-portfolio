# Lab 1A — AI Playground: 4-Tool Comparison Matrix
**Student:** _(Your Name / Roll No.)_
**Date:** June 2026
**Tasks attempted:** 3 (Summarise · Code · Reason)

> **Note:** The examples used here are **different from the trainer's lab kit** — fresh inputs were chosen to independently verify tool behaviour.

---

## Prompts Used

### Task 1 — Summarise (Fresh article excerpt)

**Prompt given to all four tools (identical):**

> "Summarise this article in 5 bullet points. Each bullet: maximum 15 words. Do not lose the key claims. Do not add information not in the article."
>
> **Article (~600 words):**
>
> Climate technology investment reached a record $500 billion globally in 2025, according to BloombergNEF. Solar and wind energy projects absorbed the largest share, accounting for 42% of total clean-energy capital. However, analysts warn that this headline figure masks a widening gap between wealthy nations and the Global South. India and Brazil attracted only 6% of total global climate finance despite being home to two of the world's fastest-growing emissions economies.
>
> Battery storage emerged as the fastest-growing sub-sector, with capacity additions tripling year-on-year across Southeast Asia. The IEA noted that battery prices fell 28% in 2025 alone, making grid-scale storage economically viable without subsidy for the first time in history. This milestone is considered pivotal: intermittent renewable generation — solar and wind — becomes dispatchable only when paired with affordable storage.
>
> Green hydrogen remained a contested space. Electrolyser costs dropped 18% but remain two to three times higher than the threshold most economists identify as commercially competitive. The EU committed €12 billion to green hydrogen corridors, while the United States paused several hydrogen hub grants pending a Treasury review of Inflation Reduction Act provisions. China, by contrast, approved 14 new green hydrogen plants, positioning itself as the dominant low-cost producer by 2030.
>
> Carbon capture and storage (CCS) attracted renewed corporate interest. Shell, TotalEnergies, and ExxonMobil each announced CCS expansion plans. Critics argue CCS enables continued fossil fuel extraction under a veneer of climate compliance. Proponents counter that hard-to-abate sectors — cement, steel, aviation — cannot decarbonise without it.
>
> The most debated development of 2025 was the first commercial-scale direct air capture (DAC) facility, opened in Iceland by Climeworks. It captures approximately 36,000 tonnes of CO₂ per year. At current prices ($1,000 per tonne), the cost is prohibitive at scale; the facility exists primarily as a proof of concept and R&D testbed. Forecasters disagree sharply on when DAC will reach cost parity — estimates range from 2032 to never.

---

### Task 2 — Code (Fresh function spec)

**Prompt given to all four tools (identical):**

> "Write a Python function `longest_common_subsequence(s1: str, s2: str) -> dict` that returns `{'lcs': str, 'length': int, 'ratio': float}` where `ratio` is `length / max(len(s1), len(s2))` rounded to 2 decimal places. Use only the standard library. Include a docstring and one usage example in a comment."

---

### Task 3 — Reason (Fresh logic puzzle)

**Prompt given to all four tools (identical):**

> "A train departs Mumbai at 6:00 PM IST and travels for 8 hours to reach Delhi. A passenger boards at a station exactly halfway through the journey. The train does not stop between the boarding station and Delhi. If the passenger boards at 10:00 PM IST, does this mean the train is running exactly on schedule? Show your reasoning step by step."

**Worked Solution:**
- Departure: 6:00 PM IST
- Journey duration: 8 hours → scheduled arrival: 2:00 AM IST
- Halfway point in time = 6:00 PM + 4 hours = **10:00 PM IST**
- The passenger boards at 10:00 PM → this is exactly the halfway mark
- **Yes, the train is on schedule.** The boarding time is consistent with a punctual departure at 6:00 PM and an 8-hour journey.

---

## Tool Responses & Analysis

### Task 1 — Summarise

| Tool | Response Summary | Observations |
|------|-----------------|--------------|
| **ChatGPT** | Produced 5 clean, parallel bullets. Covered solar/wind (42%), battery price drop (28%), green hydrogen gap, CCS debate, and DAC Iceland facility. | Stayed within 15-word limit. Slightly softened the "critics vs proponents" CCS tension. Missed the Global South equity point entirely. |
| **Claude** | 5 thorough bullets preserving almost every statistic. Explicitly retained the Global South 6% figure and the $1,000/tonne DAC cost. One bullet ran to ~18 words. | Best factual retention. Minor brevity violation. Preserved nuance the others dropped. |
| **Gemini** | 5 bullets, accurate on numbers (28%, €12B, 36,000 tonnes). Included a source link to BloombergNEF (not in original article — added externally). | Strong on numbers. Added external information not in the article — violates the prompt constraint. Useful but unfaithful. |
| **Perplexity** | 5 bullets with inline citations. Cited the article + pulled a related IEA report autonomously. Structure slightly broken — bullet 4 was a run-on. | Best for verification workflows. Weakest on clean structure and brevity discipline. |

---

### Task 2 — Code

| Tool | Approach Used | Works Correctly? | Constraint Followed? |
|------|--------------|-----------------|----------------------|
| **ChatGPT** | Dynamic programming (DP table), backtracking to reconstruct LCS string. Returned correct dict shape. Docstring present. | ✅ Yes, including edge cases (empty strings, identical strings) | ✅ Standard library only |
| **Claude** | DP with memoisation using `functools.lru_cache`. Returned all three keys. Included a detailed docstring AND a test block. Noted complexity O(m×n). | ✅ Yes, with explicit edge-case handling | ✅ Standard library only (`functools` is stdlib) |
| **Gemini** | Attempted DP but used `numpy` for the matrix — **direct constraint violation**. When re-prompted "standard library only", gave a corrected version using a plain list-of-lists. | ⚠️ Correct after correction, not on first attempt | ❌ First attempt violated constraint |
| **Perplexity** | Gave a working DP implementation but cited a GeeksforGeeks article and reproduced their variable naming (`dp`, `i`, `j`). No docstring. Missing the `ratio` key on first response. | ⚠️ Incomplete — missing one return key | ✅ Standard library only, but incomplete |

**Test input used:**
```python
print(longest_common_subsequence("placement", "replacement"))
# Expected: {'lcs': 'placement', 'length': 9, 'ratio': 0.82}
```

---

### Task 3 — Reason

| Tool | Answer | Reasoning Shown? | Correct? |
|------|--------|-----------------|---------|
| **ChatGPT** | "Yes, the train is on schedule." | Showed: 6 PM + 4 hrs = 10 PM = halfway. Clean step-by-step. | ✅ Correct |
| **Claude** | "Yes, on schedule — the 10:00 PM boarding matches exactly half of the 8-hour journey." | Most explicit chain of thought. Even added a caveat: "this assumes 'halfway' means halfway in time, not distance." | ✅ Correct + bonus insight |
| **Gemini** | "Yes." Then explained — but skipped showing the 6 PM + 4 hrs = 10 PM intermediate step explicitly. | Answer correct but reasoning partially implicit. | ✅ Correct, reasoning incomplete |
| **Perplexity** | Searched for "train schedule logic puzzle" — returned a different puzzle from a math forum. Answered the wrong question for 2 paragraphs before correcting. | ❌ Initially reasoned about a different problem | ⚠️ Correct eventually, after confusion |

---

## Filled Comparison Matrix

| Tool | Task 1 – Summarise (Score /5) | Task 2 – Code (Score /5) | Task 3 – Reason (Score /5) | My Verdict |
|------|-------------------------------|--------------------------|----------------------------|------------|
| **ChatGPT** | 4 — Clean structure, missed Global South equity point | 5 — Correct, idiomatic, docstring present | 4 — Correct, clean steps, no extra insight | All-rounder. Best default for well-structured responses fast. |
| **Claude** | 5 — All key claims and stats preserved, minor word-limit slip | 5 — Best explanation, edge cases handled, complexity noted | 5 — Correct + surfaced an implicit assumption others missed | Best for high-stakes writing, long documents, careful reasoning. |
| **Gemini** | 3 — Good on numbers but added external info not in the article | 2 — Failed constraint on first attempt; needed re-prompting | 3 — Correct answer, weak reasoning trail | Use for quick factual/numerical queries. Weak at following constraints. |
| **Perplexity** | 4 — Accurate with citations; structure slightly messy | 3 — Missing one return key; no docstring | 2 — Got confused by search-first instinct; wrong puzzle initially | Best when citations matter. Unreliable for pure reasoning or precise code. |

---

## Scoring Reference

| Score | Meaning |
|-------|---------|
| 5 | Task fully complete, all constraints met, no fixes needed |
| 4 | Works well, one minor omission or slight constraint slip |
| 3 | Works on simple cases, one clear gap that needed fixing |
| 2 | Partially correct, required significant correction or re-prompting |
| 1 | Wrong answer, broken code, or ignored the prompt |

---

## 3-Sentence Conclusion

> "I would use **ChatGPT** for general tasks where I need a fast, well-structured response with balanced coverage."

> "I would use **Claude** for long documents, careful reasoning, and any task where preserving nuance and edge cases matters."

> "I would use **Perplexity** for any factual claim I cannot afford to get wrong — especially when I need a cited primary source."

_(Gemini is best reserved for quick numerical lookups or multimodal tasks like image analysis; it is the weakest at strictly following prompt constraints.)_

---

## Key Takeaways

1. **Constraint adherence separates good tools from great ones.** Gemini broke the "standard library only" rule on the first attempt — a critical failure mode in placement interview contexts where solutions must run in restricted environments.

2. **Perplexity's search-first design is a double-edged sword.** It adds citations automatically (great for verification), but it can misfire on pure logic or coding tasks where searching is the wrong instinct.

3. **Claude preserves nuance that others drop.** It was the only tool to retain the Global South equity statistic in Task 1 and the only one to flag the implicit assumption in Task 3.

4. **ChatGPT is the safest general-purpose default** — it rarely fails badly, even if it rarely surprises you.

---

*Lab 1A · Day 1 · AI Playground · Aditya University Mentor Training Program 2026*