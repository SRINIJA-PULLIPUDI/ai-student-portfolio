# Day 3 — Lab 3A: Verification Chain
**Submitted by:** Srinija
**Date:** 11-06-2026  
**Lab Goal:** Verify 5 AI-generated placement statistics via the 3-step chain (AI → Perplexity → Primary Source)

---

## Step 1 — Claims Generated via Gemini

The following 5 claims were generated using the prompt:  
*"List 5 specific statistics about Indian campus placement in 2025-2026. For each: state the number, the year, and the source organisation. Format as a numbered list."*

1. The average B.Tech placement package in Indian engineering colleges in 2025 was ₹6.2 LPA (NASSCOM).
2. 78% of Tier-1 college students received at least one placement offer in 2025 (AICTE Annual Report).
3. TCS hired approximately 40,000 freshers in 2025 (TCS Annual Report).
4. The IT services sector accounted for 56% of all engineering placements in India in 2025 (NASSCOM).
5. The median placement package at IITs in 2025 was ₹18.5 LPA (India Skills Report 2025).

---

## Step 2 — Verification Matrix

| # | Claim | AI-Cited Source | Perplexity Check URLs | Primary Source URL Checked | Verdict |
|---|-------|----------------|-----------------------|---------------------------|---------|
| 1 | The average B.Tech placement package in Indian engineering colleges in 2025 was ₹6.2 LPA | NASSCOM | https://nasscom.in/knowledge-center ; https://placementpilot.ai/blog/best-placement-management-software-india | https://placementpilot.ai/blog/best-placement-management-software-india — AICTE/NASSCOM data cited here; no ₹6.2 LPA figure found on NASSCOM | ❌ FALSE |
| 2 | 78% of Tier-1 college students received at least one placement offer in 2025 | AICTE Annual Report | https://www.aicte-india.org ; https://careers360.com/university/national-institute-of-technology-delhi/placement | https://careers360.com/university/national-institute-of-technology-delhi/placement — NIT Delhi shows 86.28% via NIRF; AICTE does not publish a standalone "78% Tier-1" figure | ⚠️ PARTIAL |
| 3 | TCS hired approximately 40,000 freshers in 2025 | TCS Annual Report | https://www.tcs.com/careers/india/tcs-all-india-nqt-hiring ; https://abhyashsuchi.in/tcs-recruitment-2026-freshers-hiring-40000-vacanci/ | https://on.tcs.com/Annual-Report-2025 — page returned a server error; 40,000 figure found only on third-party coaching sites as a projected 2026 vacancy, not a confirmed 2025 hire count | 🔍 NO PRIMARY SOURCE FOUND |
| 4 | The IT services sector accounted for 56% of all engineering placements in India in 2025 | NASSCOM | https://nasscom.in ; https://wheebox.com/india-skills-report.htm | https://wheebox.com/news-pr.htm — India Skills Report 2025 reports graduate employability at 54.81%, a different metric entirely; no sector-share figure found on NASSCOM | ❌ FALSE |
| 5 | The median placement package at IITs in 2025 was ₹18.5 LPA | India Skills Report 2025 (Wheebox) | https://wheebox.com/india-skills-report.htm ; https://propelld.com/site/blog/iit-placements | https://wheebox.com/news-pr.htm — India Skills Report 2025 covers employability rates only, no IIT salary data; actual IIT medians from official T&P cells: IIT Madras ₹19.6 LPA, IIT Guwahati ₹21.6 LPA | ⚠️ PARTIAL |

---

## Step 3 — Verdict Summary

| # | Claim | Verdict |
|---|-------|---------|
| 1 | Average B.Tech package ₹6.2 LPA — NASSCOM | ❌ FALSE |
| 2 | 78% Tier-1 placement rate — AICTE Annual Report | ⚠️ PARTIAL |
| 3 | TCS hired ~40,000 freshers in 2025 — TCS Annual Report | 🔍 NO PRIMARY SOURCE FOUND |
| 4 | IT services = 56% of engineering placements — NASSCOM | ❌ FALSE |
| 5 | Median IIT package ₹18.5 LPA — India Skills Report 2025 | ⚠️ PARTIAL |

**VERIFIED: 0 / 5**

---

## Step 4 — Reflection

The claim that looked most authoritative but was actually weakest was **Claim 5**: *"The median placement package at IITs in 2025 was ₹18.5 LPA (India Skills Report 2025)."* Gemini cited the India Skills Report confidently — a well-known, legitimate annual publication by Wheebox/ETS — which made it feel credible. Perplexity initially seemed to support it, returning the Wheebox URL as a valid source. But when I opened the India Skills Report 2025 primary page, I found it covers *employability rates* (54.81% of graduates are employable) — a completely different metric. It contains no IIT-specific salary data whatsoever. Meanwhile, actual IIT placement cells (IIT Madras, IIT Guwahati) publish median packages of ₹19.6–21.6 LPA — higher than Gemini's figure. The lesson: **confidence does not equal correctness.** The AI chose a reputable-sounding source, attached a plausible-sounding number, and presented both as a single fact. The source doesn't contain the claim, and the number is off. The verification step belongs to the human — every time.

---

*Submitted as part of the AI Mentor Training Programme — Day 3 Lab 3A*
