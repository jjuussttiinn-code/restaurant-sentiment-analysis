# Restaurant Sentiment Analysis  
### Understanding Customer Satisfaction Using Yelp Reviews (Hash House A Go Go – Las Vegas)

## Overview

This project analyzes **6,244 Yelp reviews** for *Hash House A Go Go (Las Vegas)* to uncover what drives customer satisfaction and dissatisfaction. Using multiple text‑mining techniques — keyword keyness, dependency‑based aspect extraction, transformer‑based ABSA, and an interactive widget — the project provides a consulting‑style analysis for a restaurant group seeking to understand:

- What customers talk about in **1‑star vs 5‑star** experiences  
- Which aspects of the dining experience (food, service, wait time, ambiance) matter most  
- How the restaurant compares to **competitors** in the same city/category  
- Whether automated text‑analysis tools are reliable enough for business use  

**Academic Context**  
This project was completed as part of **LING 583 — Statistical Methods in Text Analysis** at **San Diego State University**, demonstrating applied NLP techniques including keyword keyness, dependency‑based aspect extraction, transformer‑based ABSA, and interactive client‑facing tooling.

---

## Data Description

**Dataset:** Yelp reviews (`yelp.parquet`)  
**Restaurant:** Hash House A Go Go — Las Vegas  
**Categories:** Breakfast & Brunch, American (New), Bars  
**Review count:** 6,244  

### Key characteristics

- **Left‑skewed rating distribution** — most reviews are 4–5 stars  
- **Negative reviews are more extreme**, often citing wait times and service issues  
- **Large sample size** provides reliable sentiment patterns and strong competitor comparison  

---

## Methods  
### (Parts 1–4 nested inside this section)

This project uses three independent text‑analysis approaches plus an interactive widget. Their convergence strengthens confidence in the findings.

---

### Part 1 — Keyword Keyness & Competitor Comparison  
**Technique:** Log‑likelihood keyness (1‑star vs rest, 5‑star vs rest)

**Insights:**

- **1‑star distinctive words:** “worst”, “cold”, “horrible”  
- **5‑star distinctive words:** “huge”, “portion”, breakfast‑related terms  
- **Competitor comparison:**  
  - Hash House A Go Go stands out **positively** for huge portions and signature breakfast dishes  
  - It stands out **negatively** for long waits compared to similar Las Vegas restaurants  

---

### Part 2 — Dependency‑Based Aspect Extraction  
**Technique:** spaCy dependency parsing to extract aspect–opinion pairs + orientation scoring

**Insights:**

- Orientation scores **increase steadily** from 1‑star → 5‑star  
- Most frequent **positive aspects:** food quality, portion size  
- Most frequent **negative aspects:** wait times, slow service  
- Includes error analysis (sarcasm, mixed sentiment, complex syntax)

---

### Part 3 — Transformer‑Based ABSA (DeBERTa)  
**Technique:** Sentence‑level aspect extraction + sentiment classification

**Insights:**

- Handles **mixed sentiment** within a single review  
- Sentiment scores **rise smoothly** with star ratings  
- Aspect predictions align with intuitive human interpretation  
- Comparison with parser‑based method shows:  
  - High overlap in core aspects  
  - Transformer is more precise and robust  
  - Three reviews analyzed where methods disagree, with explanations

---

### Part 4 — Interactive Widget (ipywidgets)  
**Goal:** Allow non‑technical clients to explore results without reading code

**Features:**

- Select a restaurant and view keyword profiles or aspect summaries  
- Filter by star rating, city, or category  
- Compare restaurants side‑by‑side or against competitor sets  
- Designed to be **self‑explanatory** and business‑friendly  

---

## Key Findings

Across all methods, customers consistently focus on:

- **Food quality**  
- **Portion size**  
- **Service speed**  
- **Wait times**

### Positive drivers  
- Large portions  
- Signature breakfast dishes  
- Memorable food presentation  

### Negative drivers  
- Long waits  
- Slow or inconsistent service  
- Table/seating management issues  

The same themes appear across **keyness**, **parser‑based ABSA**, and **transformer‑based ABSA**, increasing trust in the results.

---

## Recommendations

### Strengthen existing strengths  
- Maintain large portions and high food quality  
- Highlight signature dishes in marketing  
- Ensure consistency in preparation  

### Reduce operational weaknesses  
- Improve staffing during peak hours  
- Tighten host stand and table‑turn processes  
- Monitor kitchen throughput to reduce delays  

### On automated text analysis  
- **Transformer‑based ABSA** is the most reliable and scalable  
- **Parser‑based methods** are useful for lightweight scenarios but need human oversight  
- Automated tools are trustworthy for **high‑level patterns**, but edge cases still require manual review  

---

## Repository Structure (Suggested)

```text
restaurant-sentiment-analysis/
├─ data/
│  └─ yelp.parquet
├─ notebooks/
│  ├─ 01_data_overview.ipynb
│  ├─ 02_keyness_analysis.ipynb
│  ├─ 03_parser_absa.ipynb
│  ├─ 04_transformer_absa.ipynb
│  └─ 05_interactive_widget.ipynb
├─ src/
│  ├─ keyness.py
│  ├─ parser_aspects.py
│  ├─ transformer_absa.py
│  └─ widgets.py
├─ report/
│  └─ hash_house_report.pdf
├─ README.md
└─ requirements.txt

